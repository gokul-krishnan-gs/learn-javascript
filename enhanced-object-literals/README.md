# JavaScript Enhanced Object Literals Reference

## Definition
Enhanced Object Literals are ES6 (ES2015) improvements to JavaScript object literal syntax that provide shorter, more convenient ways to define objects. They include shorthand property notation, computed property names, and method definitions.

## Key Features Overview
1. **Property Shorthand** - Shorter syntax when property name matches variable name
2. **Method Shorthand** - Concise method definitions
3. **Computed Property Names** - Dynamic property names using expressions
4. **Super Calls** - Call parent object methods in object literals

---

## Property Shorthand

### Basic Property Shorthand
```javascript
// Traditional object literal
const name = "Alice";
const age = 25;
const city = "New York";

const userOld = {
    name: name,
    age: age,
    city: city
};

// Enhanced object literal - property shorthand
const user = {
    name,
    age,
    city
};

console.log(user); // { name: "Alice", age: 25, city: "New York" }
```

### Real-World Example
```javascript
function createUser(firstName, lastName, email, isActive = true) {
    // Instead of repeating property names
    return {
        firstName,
        lastName,
        email,
        isActive,
        fullName: `${firstName} ${lastName}`,
        createdAt: new Date()
    };
}

const newUser = createUser("John", "Doe", "john@example.com");
console.log(newUser);
// {
//   firstName: "John",
//   lastName: "Doe", 
//   email: "john@example.com",
//   isActive: true,
//   fullName: "John Doe",
//   createdAt: 2023-12-25T...
// }
```

### Function Parameters Destructuring
```javascript
// API response processing
function processApiResponse(data) {
    const { id, username, email, profile } = data;
    const { firstName, lastName, avatar } = profile;
    
    // Return object with shorthand properties
    return {
        id,
        username,
        email,
        firstName,
        lastName,
        avatar,
        processed: true,
        timestamp: Date.now()
    };
}
```

---

## Method Shorthand

### Basic Method Definitions
```javascript
// Traditional method definition
const calculatorOld = {
    add: function(a, b) {
        return a + b;
    },
    subtract: function(a, b) {
        return a - b;
    }
};

// Enhanced object literal - method shorthand
const calculator = {
    add(a, b) {
        return a + b;
    },
    
    subtract(a, b) {
        return a - b;
    },
    
    multiply(a, b) {
        return a * b;
    },
    
    // Method with complex logic
    calculate(operation, a, b) {
        switch(operation) {
            case 'add': return this.add(a, b);
            case 'subtract': return this.subtract(a, b);
            case 'multiply': return this.multiply(a, b);
            default: throw new Error('Unknown operation');
        }
    }
};

console.log(calculator.add(5, 3)); // 8
console.log(calculator.calculate('multiply', 4, 7)); // 28
```

### Object with Mixed Properties and Methods
```javascript
const userService = {
    // Properties
    baseUrl: 'https://api.example.com',
    timeout: 5000,
    
    // Methods using shorthand
    async fetchUser(id) {
        const response = await fetch(`${this.baseUrl}/users/${id}`);
        return response.json();
    },
    
    async updateUser(id, userData) {
        const response = await fetch(`${this.baseUrl}/users/${id}`, {
            method: 'PUT',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(userData)
        });
        return response.json();
    },
    
    validateUser(user) {
        return user.name && user.email && user.email.includes('@');
    }
};
```

### Getter and Setter Methods
```javascript
const person = {
    firstName: 'John',
    lastName: 'Doe',
    
    // Getter method
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    
    // Setter method
    set fullName(name) {
        [this.firstName, this.lastName] = name.split(' ');
    },
    
    // Regular methods
    greet() {
        return `Hello, I'm ${this.fullName}`;
    },
    
    updateName(first, last) {
        this.firstName = first;
        this.lastName = last;
    }
};

console.log(person.fullName); // "John Doe"
person.fullName = "Jane Smith";
console.log(person.firstName); // "Jane"
console.log(person.greet()); // "Hello, I'm Jane Smith"
```

---

## Computed Property Names

### Basic Computed Properties
```javascript
// Dynamic property names
const propertyName = 'color';
const propertyValue = 'blue';

const obj = {
    [propertyName]: propertyValue,
    ['size']: 'large',
    [`is${propertyName.charAt(0).toUpperCase() + propertyName.slice(1)}`]: true
};

console.log(obj); 
// { color: "blue", size: "large", isColor: true }
```

### Function-Based Computed Properties
```javascript
function createKey(prefix, id) {
    return `${prefix}_${id}`;
}

const userId = 123;
const sessionData = {
    [createKey('user', userId)]: 'John Doe',
    [createKey('session', userId)]: 'abc123xyz',
    [`timestamp_${Date.now()}`]: new Date()
};

console.log(sessionData);
// { user_123: "John Doe", session_123: "abc123xyz", timestamp_1703507892123: ... }
```

### Dynamic Method Names
```javascript
const actions = ['create', 'read', 'update', 'delete'];

const apiClient = {
    baseUrl: 'https://api.example.com',
    
    // Dynamically create methods
    ...actions.reduce((methods, action) => {
        methods[`${action}User`] = function(id, data = null) {
            const url = `${this.baseUrl}/users${id ? `/${id}` : ''}`;
            const config = {
                method: action === 'create' ? 'POST' : 
                       action === 'update' ? 'PUT' : 
                       action === 'delete' ? 'DELETE' : 'GET'
            };
            
            if (data) {
                config.body = JSON.stringify(data);
                config.headers = { 'Content-Type': 'application/json' };
            }
            
            return fetch(url, config);
        };
        return methods;
    }, {}),
    
    // Regular methods
    authenticate(token) {
        this.token = token;
    }
};

// Now we have: apiClient.createUser(), apiClient.readUser(), etc.
```

### Computed Properties with Template Literals
```javascript
const createConfigObject = (environment, version) => {
    return {
        [`${environment}_url`]: `https://${environment}.example.com`,
        [`${environment}_timeout`]: environment === 'prod' ? 5000 : 10000,
        [`api_v${version}`]: true,
        [environment.toUpperCase()]: {
            debug: environment !== 'prod',
            logging: true
        }
    };
};

const config = createConfigObject('staging', 2);
console.log(config);
// {
//   staging_url: "https://staging.example.com",
//   staging_timeout: 10000,
//   api_v2: true,
//   STAGING: { debug: true, logging: true }
// }
```

---

## Advanced Examples

### Combining All Features
```javascript
function createUserManager(apiUrl, defaultRole = 'user') {
    const cache = new Map();
    const created = Date.now();
    
    return {
        // Properties with shorthand
        apiUrl,
        defaultRole,
        created,
        
        // Computed property
        [`cache_${created}`]: cache,
        
        // Methods with shorthand
        async getUser(id) {
            if (cache.has(id)) {
                return cache.get(id);
            }
            
            const user = await this.fetchFromApi(`users/${id}`);
            cache.set(id, user);
            return user;
        },
        
        async createUser(userData) {
            const newUser = {
                ...userData,
                role: userData.role || defaultRole,
                id: this.generateId(),
                createdAt: new Date()
            };
            
            const result = await this.fetchFromApi('users', {
                method: 'POST',
                body: JSON.stringify(newUser)
            });
            
            cache.set(result.id, result);
            return result;
        },
        
        // Computed method name
        [createUserManager.getMethodName('fetch')]() {
            return cache.size;
        },
        
        // Private-like methods
        async fetchFromApi(endpoint, options = {}) {
            const response = await fetch(`${apiUrl}/${endpoint}`, {
                headers: { 'Content-Type': 'application/json' },
                ...options
            });
            return response.json();
        },
        
        generateId() {
            return Math.random().toString(36).substr(2, 9);
        }
    };
}

// Static method for dynamic method naming
createUserManager.getMethodName = (action) => `${action}CacheSize`;

const userManager = createUserManager('https://api.example.com', 'member');
```

### Factory Pattern with Enhanced Literals
```javascript
function createAnimalFactory() {
    const animals = [];
    
    return {
        animals,
        
        // Factory methods using computed names
        ...['dog', 'cat', 'bird'].reduce((factory, animal) => {
            factory[`create${animal.charAt(0).toUpperCase() + animal.slice(1)}`] = (name, age) => {
                const newAnimal = {
                    name,
                    age,
                    type: animal,
                    id: animals.length + 1,
                    
                    // Method based on animal type
                    [`make${animal === 'dog' ? 'Bark' : animal === 'cat' ? 'Meow' : 'Chirp'}`]() {
                        const sound = animal === 'dog' ? 'Woof!' : 
                                    animal === 'cat' ? 'Meow!' : 'Tweet!';
                        return `${this.name} says ${sound}`;
                    },
                    
                    describe() {
                        return `${this.name} is a ${this.age} year old ${this.type}`;
                    }
                };
                
                animals.push(newAnimal);
                return newAnimal;
            };
            return factory;
        }, {}),
        
        getAllAnimals() {
            return [...animals];
        },
        
        findByType(type) {
            return animals.filter(animal => animal.type === type);
        }
    };
}

const animalFactory = createAnimalFactory();
const dog = animalFactory.createDog('Buddy', 3);
const cat = animalFactory.createCat('Whiskers', 2);

console.log(dog.makeBark()); // "Buddy says Woof!"
console.log(cat.describe()); // "Whiskers is a 2 year old cat"
```

---

## Configuration Objects

### Dynamic Configuration Builder
```javascript
function createConfig(environment, features = [], customSettings = {}) {
    const timestamp = Date.now();
    const version = '1.2.3';
    
    return {
        // Basic properties
        environment,
        version,
        timestamp,
        
        // Computed environment-specific properties
        [`${environment}Enabled`]: true,
        [environment]: {
            debug: environment !== 'production',
            logging: true,
            apiUrl: `https://api-${environment}.example.com`
        },
        
        // Feature flags as computed properties
        ...features.reduce((flags, feature) => {
            flags[`${feature}Enabled`] = true;
            flags[`${feature}Config`] = customSettings[feature] || {};
            return flags;
        }, {}),
        
        // Methods for config management
        isFeatureEnabled(feature) {
            return this[`${feature}Enabled`] || false;
        },
        
        getEnvironmentConfig() {
            return this[environment];
        },
        
        updateFeature(feature, enabled) {
            this[`${feature}Enabled`] = enabled;
        },
        
        // Computed method based on environment
        [`get${environment.charAt(0).toUpperCase() + environment.slice(1)}Url`]() {
            return this[environment].apiUrl;
        }
    };
}

const appConfig = createConfig('staging', ['analytics', 'chat', 'notifications'], {
    analytics: { trackingId: 'GA-123456' },
    chat: { maxUsers: 100 }
});

console.log(appConfig.analyticsEnabled); // true
console.log(appConfig.getStagingUrl()); // "https://api-staging.example.com"
console.log(appConfig.analyticsConfig); // { trackingId: 'GA-123456' }
```

---

## Best Practices

### When to Use Enhanced Object Literals

#### ✅ Good Use Cases
```javascript
// Property shorthand for variable assignment
function processUserData(name, email, age) {
    return { name, email, age, processed: true };
}

// Method shorthand for cleaner syntax
const utils = {
    formatCurrency(amount) {
        return `$${amount.toFixed(2)}`;
    },
    
    validateEmail(email) {
        return email.includes('@');
    }
};

// Computed properties for dynamic object creation
const createApiEndpoints = (baseUrl) => ({
    [`${baseUrl}/users`]: 'users',
    [`${baseUrl}/posts`]: 'posts'
});
```

#### ❌ Avoid When
```javascript
// Don't use computed properties for static names
const badExample = {
    ['name']: 'John', // Just use name: 'John'
    ['age']: 25       // Just use age: 25
};

// Don't use method shorthand when you need traditional function behavior
const obj = {
    // This won't work as constructor
    Person() {
        this.name = 'John';
    }
};
```

### Style Guidelines
```javascript
// ✅ Good - consistent formatting
const user = {
    name,
    email,
    age,
    
    greet() {
        return `Hello, I'm ${this.name}`;
    },
    
    [computedProp]: value
};

// ✅ Good - group related properties and methods
const apiClient = {
    // Configuration
    baseUrl,
    timeout,
    retries,
    
    // Core methods
    get(endpoint) { /* ... */ },
    post(endpoint, data) { /* ... */ },
    
    // Utility methods
    buildUrl(endpoint) { /* ... */ },
    handleError(error) { /* ... */ }
};
```

---

## Browser Compatibility

- **Property Shorthand**: ES6 (2015) - supported in all modern browsers
- **Method Shorthand**: ES6 (2015) - supported in all modern browsers  
- **Computed Property Names**: ES6 (2015) - supported in all modern browsers
- **IE 11 and below**: Not supported (use Babel for transpilation)

## Performance Considerations

- Enhanced object literals have no significant performance impact
- Computed property names are evaluated at object creation time
- Method shorthand creates the same function objects as traditional syntax
- Use these features for readability and maintainability, not performance

## Migration Tips

```javascript
// Gradually migrate existing code
const oldStyle = {
    name: name,
    getValue: function() {
        return this.value;
    }
};

// Can be updated incrementally
const newStyle = {
    name,               // Updated property shorthand
    getValue: function() {  // Keep if needed for specific behavior
        return this.value;
    }
};

// Or fully modernized
const modernStyle = {
    name,
    getValue() {
        return this.value;
    }
};
```
