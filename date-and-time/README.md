# JavaScript Date and Time Reference

## Date Object

**Definition:** The Date object represents a single moment in time in a platform-independent format, containing milliseconds since January 1, 1970 UTC.

**Syntax:**
```javascript
new Date()
new Date(milliseconds)
new Date(dateString)
new Date(year, month, day, hour, minute, second, millisecond)
```

**Examples:**
```javascript
const now = new Date();                           // Current date and time
const specificDate = new Date('2024-01-15');      // From string
const fromMillis = new Date(1705344000000);       // From milliseconds
const constructed = new Date(2024, 0, 15, 10, 30, 0); // Year, month(0-11), day, hour, min, sec
```

## Creating Date Objects

### Current Date and Time
```javascript
const now = new Date();
console.log(now); // Current date and time
```

### From String
```javascript
const date1 = new Date('2024-01-15');
const date2 = new Date('January 15, 2024');
const date3 = new Date('2024-01-15T10:30:00Z');
```

### From Components
```javascript
const date = new Date(2024, 0, 15, 10, 30, 0, 0); // Year, Month(0-11), Day, Hour, Min, Sec, Ms
```

## Get Methods (Retrieving Date Components)

### getFullYear()
**Definition:** Returns the year (4 digits) of the specified date.
```javascript
const date = new Date('2024-01-15');
console.log(date.getFullYear()); // 2024
```

### getMonth()
**Definition:** Returns the month (0-11) of the specified date.
```javascript
const date = new Date('2024-01-15');
console.log(date.getMonth()); // 0 (January)
```

### getDate()
**Definition:** Returns the day of the month (1-31) for the specified date.
```javascript
const date = new Date('2024-01-15');
console.log(date.getDate()); // 15
```

### getDay()
**Definition:** Returns the day of the week (0-6) where Sunday is 0.
```javascript
const date = new Date('2024-01-15');
console.log(date.getDay()); // 1 (Monday)
```

### getHours()
**Definition:** Returns the hour (0-23) for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.getHours()); // 10
```

### getMinutes()
**Definition:** Returns the minutes (0-59) for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.getMinutes()); // 30
```

### getSeconds()
**Definition:** Returns the seconds (0-59) for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:45');
console.log(date.getSeconds()); // 45
```

### getMilliseconds()
**Definition:** Returns the milliseconds (0-999) for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:45.123');
console.log(date.getMilliseconds()); // 123
```

### getTime()
**Definition:** Returns the numeric value of the date as milliseconds since January 1, 1970 UTC.
```javascript
const date = new Date('2024-01-15');
console.log(date.getTime()); // 1705276800000
```

### getTimezoneOffset()
**Definition:** Returns the time zone offset in minutes from UTC.
```javascript
const date = new Date();
console.log(date.getTimezoneOffset()); // e.g., -330 (for IST, UTC+5:30)
```

## Set Methods (Modifying Date Components)

### setFullYear()
**Definition:** Sets the year for the specified date.
```javascript
const date = new Date('2024-01-15');
date.setFullYear(2025);
console.log(date); // 2025-01-15
```

### setMonth()
**Definition:** Sets the month (0-11) for the specified date.
```javascript
const date = new Date('2024-01-15');
date.setMonth(11); // December
console.log(date.getMonth()); // 11
```

### setDate()
**Definition:** Sets the day of the month for the specified date.
```javascript
const date = new Date('2024-01-15');
date.setDate(25);
console.log(date.getDate()); // 25
```

### setHours()
**Definition:** Sets the hour for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
date.setHours(15);
console.log(date.getHours()); // 15
```

### setMinutes()
**Definition:** Sets the minutes for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
date.setMinutes(45);
console.log(date.getMinutes()); // 45
```

### setSeconds()
**Definition:** Sets the seconds for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
date.setSeconds(30);
console.log(date.getSeconds()); // 30
```

### setMilliseconds()
**Definition:** Sets the milliseconds for the specified date.
```javascript
const date = new Date('2024-01-15T10:30:00');
date.setMilliseconds(500);
console.log(date.getMilliseconds()); // 500
```

### setTime()
**Definition:** Sets the Date object to the time represented by milliseconds since January 1, 1970 UTC.
```javascript
const date = new Date();
date.setTime(1705344000000);
console.log(date); // Set to specific timestamp
```

## UTC Methods

### getUTCFullYear()
**Definition:** Returns the year in UTC time.
```javascript
const date = new Date();
console.log(date.getUTCFullYear()); // UTC year
```

### getUTCMonth()
**Definition:** Returns the month (0-11) in UTC time.
```javascript
const date = new Date();
console.log(date.getUTCMonth()); // UTC month
```

### getUTCDate()
**Definition:** Returns the day of the month in UTC time.
```javascript
const date = new Date();
console.log(date.getUTCDate()); // UTC day
```

### getUTCDay()
**Definition:** Returns the day of the week in UTC time.
```javascript
const date = new Date();
console.log(date.getUTCDay()); // UTC day of week
```

### getUTCHours(), getUTCMinutes(), getUTCSeconds(), getUTCMilliseconds()
**Definition:** Return the respective time components in UTC.
```javascript
const date = new Date();
console.log(date.getUTCHours());        // UTC hours
console.log(date.getUTCMinutes());      // UTC minutes
console.log(date.getUTCSeconds());      // UTC seconds
console.log(date.getUTCMilliseconds()); // UTC milliseconds
```

## Static Methods

### Date.now()
**Definition:** Returns the current timestamp in milliseconds since January 1, 1970 UTC.
```javascript
const timestamp = Date.now();
console.log(timestamp); // e.g., 1705344000000
```

### Date.parse()
**Definition:** Parses a date string and returns the number of milliseconds since January 1, 1970 UTC.
```javascript
const timestamp = Date.parse('2024-01-15T10:30:00Z');
console.log(timestamp); // 1705312200000
```

### Date.UTC()
**Definition:** Returns the number of milliseconds for a date since January 1, 1970 UTC.
```javascript
const timestamp = Date.UTC(2024, 0, 15, 10, 30, 0);
console.log(timestamp); // 1705312200000
```

## String Conversion Methods

### toString()
**Definition:** Returns a string representing the date in local time.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toString()); // "Mon Jan 15 2024 10:30:00 GMT+0530 (IST)"
```

### toDateString()
**Definition:** Returns the date portion as a readable string.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toDateString()); // "Mon Jan 15 2024"
```

### toTimeString()
**Definition:** Returns the time portion as a readable string.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toTimeString()); // "10:30:00 GMT+0530 (IST)"
```

### toISOString()
**Definition:** Returns a string in ISO 8601 format (YYYY-MM-DDTHH:mm:ss.sssZ).
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toISOString()); // "2024-01-15T05:00:00.000Z"
```

### toJSON()
**Definition:** Returns a JSON representation of the date (same as toISOString()).
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toJSON()); // "2024-01-15T05:00:00.000Z"
```

### toLocaleDateString()
**Definition:** Returns a localized date string.
```javascript
const date = new Date('2024-01-15');
console.log(date.toLocaleDateString()); // "1/15/2024" (US format)
console.log(date.toLocaleDateString('en-GB')); // "15/01/2024" (UK format)
```

### toLocaleTimeString()
**Definition:** Returns a localized time string.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toLocaleTimeString()); // "10:30:00 AM"
```

### toLocaleString()
**Definition:** Returns a localized date and time string.
```javascript
const date = new Date('2024-01-15T10:30:00');
console.log(date.toLocaleString()); // "1/15/2024, 10:30:00 AM"
```

## Common Date Operations

### Date Arithmetic
```javascript
const date = new Date('2024-01-15');
const tomorrow = new Date(date.getTime() + 24 * 60 * 60 * 1000);
const weekAgo = new Date(date.getTime() - 7 * 24 * 60 * 60 * 1000);
```

### Comparing Dates
```javascript
const date1 = new Date('2024-01-15');
const date2 = new Date('2024-01-20');

console.log(date1 < date2);  // true
console.log(date1 > date2);  // false
console.log(date1.getTime() === date2.getTime()); // false
```

### Formatting Examples
```javascript
const date = new Date();

// Custom formatting
const formatted = `${date.getDate()}/${date.getMonth() + 1}/${date.getFullYear()}`;
console.log(formatted); // "15/1/2024"

// With padding
const day = String(date.getDate()).padStart(2, '0');
const month = String(date.getMonth() + 1).padStart(2, '0');
const year = date.getFullYear();
console.log(`${day}/${month}/${year}`); // "15/01/2024"
```

## Timezone Considerations

JavaScript Date objects always store time in UTC internally but display in local timezone. Be aware of timezone differences when working with dates, especially when sending/receiving data from servers.

```javascript
const date = new Date('2024-01-15T10:30:00Z'); // UTC time
console.log(date.toString());    // Local timezone display
console.log(date.toISOString()); // UTC display
```
