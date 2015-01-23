# CSS3 Responsive Clock

Original version: https://github.com/iliadraznin/CSS3clock (http://codepen.io/iliadraznin/pen/JcqbE)

## This Version vs. Original one

- Basic version: without minute marks, digits, etc
- Responsive

## Challenge

The biggest challenge was to position hours. This could have been done using `position: absolute`, but as
the original version uses `translateX` / `translateY`, I wanted to give it a shot.
Original clock has fixed size and with that using e.g `translateX` to move a digit `300px` (parent height) to the right
is a butter and cheese.

When the size is not known (responsive), we can't use it, as `translateX(100%)` is taken from the element the property
is used on. Instead of `300px` we can for example `20px` (or whatever the size the digit can be).
To fixed that we can wrap our digits (`.watch .digits li`) with a container (`.digit-wrapper`) and get it
inherit 100% size of the parent. Then moving `.digit-wrapper` is as simple as this:

```
.watch .digits .digit-wrapper:nth-child(1) {transform:translate(75%, 10%);}
.watch .digits .digit-wrapper:nth-child(1) li  {transform:translate(-100%, 0%);}
```

To see how it works add some `border` to `.digit-wrapper`, e.g:

```
.watch .digits .digit-wrapper {
  border: 1px solid red;
  ...
}

```

## Todo

- prettify formatting
- add browser prefixes
- SASS / LESS version
- add live demo
- short note on coderwall
