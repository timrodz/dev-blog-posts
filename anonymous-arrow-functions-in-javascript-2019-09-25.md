# Anonymous & arrow functions in Javascript

I've been exploring with javascript anonymous & arrow functions, and found this quite an interesting puzzle: what are the return types of these functions? Bonus points for an explanation of how some of these work (or not)

```javascript
export const values = {
    key: 'value',
    getKey: function () {
        return function() {
            return this.key;
        }
    },
    getKeyArrow: function () {
        return () => this.key;
    },
    getKeyArrowCall: function () {
        return (() => this.key)();
    }
};

const v1 = values.getKey(); // function
v1(); // undefined
const v2 = values.getKeyArrow(); // function
const v3 = values.getKeyArrowCall(); // value
```

**Edit**: I changed getKey to be a bit more difficult. The previous version executed `return this.key;`
