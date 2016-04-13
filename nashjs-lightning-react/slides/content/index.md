class: center, middle

# whoami

### Jonathan Creamer

<img src="images/family.jpg" style="width: 80%;" />

---

# whoami

* Currently Senior Front End Engineer at [Lonely Planet](http://lonelyplanet.com)
* Past JavaScript Engineer appendTo
* Nashville, TN

<img src="images/lonelyplanet_bw.png" style="width: 10em" />

* Love JavaScript, tweet at [@jcreamer898](http://twitter.com/jcreamer898), blog at [jonathancreamer.com](http://jonathancreamer.com)
* [Microsoft IE MVP](https://mvp.microsoft.com/en-us/MyProfile/Preview?previewAs=Public), [Telerik Developer Expert](http://developer.telerik.com/community/developer-experts/)

???

---
class: center, middle

# The case for inline styles...

---

# Wait...

---
class: center, middle

### ...Wut?!

![](images/whut.gif)

---

### The good ole' days

```html
<h1 style="color: blue; font-size: 16px;"></h1>
```

* Remember the inline days
* Don't do this right? RIGHT?
--

* Wrong...
--

* Sorta...

---

### Why are we using React anyways?

* It's fast
* It's awesome
* It's components

---

### What's a component?

* *kuh m-poh-nuh nt*
* a constituent part; element; ingredient
* Basically...
--

* You make stuff with it

---

### What ever happened to the separation of the concerns?

* Which ones?
* Technical concerns?
* Nah...

---

### Stop splitting concerns by file type

* Instead of...
* HTML vs CSS vs JS
--

* Login vs Header vs Date Picker
--

* Component vs Component concerns

---
class: center, middle

### But why...?

![](images/butwhy.gif)

---
class: center, middle

### It's logical

![](images/logical.jpg)

---

### A functional react button

```js
function Button({ href, children, onClick }) {
  const Element = href ? "a" : "button";
  const role = Element === "a" ? "button" : "";

  return (
    <Element
      className="Button"
      href={href}
      onClick={onClick}
      role={role}
    >
        {children}
    </Element>
  );
}
```

* NO state here

---

### Add some style

```shell
npm install radium --save
```

```js
import radium from "radium";

// ...

export default radium(Button);
```

---

### JS Style Object

```js
const styles = {
  base: {
    cursor: "pointer",
    display: "inline-block",
    transition: "color 400ms, border 400ms, background-color 400ms",
    // ...

    ":hover": {
      textDecoration: "none",
    }
    // ...
  },
```

---

### JS Style Object

```js
  color: {
    blue: {
      backgroundColor: settings.color.blue,
      color: settings.color.white,

      ":hover": {
        backgroundColor: settings.color.blue, // + 15
        color: settings.color.white,
      },
      // ...
    },

    white: {
      // ...
    },
  },
```

---

### JS Style Object

```js
  size: {
    tiny: {},
    small: {},
    medium: {
      fontSize: "1.2rem",
    },
    large: {},
    huge: {},
  },

  height: {
    short: {
      paddingBottom: "1rem",
      paddingTop: "1.2rem",
    },
    normal: {
     // ...
    },
    tall: {
     // ...
    },
  },
```

---

### JS Style Object

```js
  type: {
    rounded: {
      borderRadius: "2.2rem",
    },
    full: {
      display: "block",
      width: "100%",
    },
  },
};
```

---

### Pass in some props

```js
function Button({ href, children, onClick, color, size, height, rounded, full }) {

  // ...

  return (
    <Element
      style={style}
      // ...
    >
        {children}
    </Element>
  );
}
```

---

### Change the styles based on those props

```js
const style = [styles.base];

if (color) {
  style.push(styles.color[color]);
}

if (size) {
  style.push(styles.size[size]);
}

if (height) {
  style.push(styles.height[height]);
}

if (rounded) {
  style.push(styles.type.rounded);
}

if (full) {
  style.push(styles.type.full);
}
```

---

### Prop Types

```js
Button.propTypes = {
  href: React.PropTypes.string,
  children: React.PropTypes.node.isRequired,
  onClick: React.PropTypes.func,
  color: React.PropTypes.oneOf([
    "blue",
    "white",
  ]),
  size: React.PropTypes.oneOf([
    "tiny",
    "small",
    "medium",
    "large",
    "huge",
  ]),
  height: React.PropTypes.oneOf([
    "short",
    "normal",
    "tall",
  ]),
  rounded: React.PropTypes.bool,
  full: React.PropTypes.bool,
};
```
---

### Default Props

```js
Button.defaultProps = {
  href: "",
  onClick: null,
  color: "blue",
  size: "medium",
  height: "normal",
  rounded: true,
  full: false,
};
````

---

### Demo

<iframe width="100%" height="300" src="//jsfiddle.net/jcreamer898/L1azfc4f/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

---

### Advantages

* Everything is in one place
* Logical separation
* Can export style object
* Static analysis on css

---

### Resources

* https://github.com/jxnblk/rebass
* https://github.com/FormidableLabs/radium
* http://stack.formidable.com/component-playground/
* http://codepen.io/somethingkindawierd/post/jsx-is-weird

---

class: center, middle

# Thanks

### [@jcreamer898](http://twitter.com/jcreamer898)
### [jonathancreamer.com](http://jonathancreamer.com)
