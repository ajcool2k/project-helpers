# Selectors

## CSS Selectors

```js
document.querySelector("div")
document.querySelectorAll("div")
```

## XPath Selectors

```js
$x("//div")
```

**Traverse to parent until element is found**

```js
$x("//*[@class="childClass"]//ancestor::div[@class='parentTargetClass']")
```

more at https://devhints.io/xpath
