the index par has problem,  do not set card-content,

The issue you're facing seems to be with the interaction of the styles outside and inside the `@media` query. Here's what I observed:

1. **Typo in `.card.card:foucus-within`**: It should be `.card:focus-within`.

2. **Overlapping `@media` Query**: In the `@media(hover)` query, you're setting the `.card-title::after` to have `transform: scaleX(0);`. This means it will always be hidden, and the hover effect outside the media query won't work since the hover effect outside is expecting it to be `scaleX(1)` by default. 

3. **Media Query Condition**: The `@media(hover)` is not a standard media query condition. If you want to apply styles when a device has hover capabilities, it should be `@media (hover: hover)`.

To fix the issue:

1. Correct the typo.
2. Adjust the transform property outside the media query to ensure it's the default state.
3. Update the media query condition.

Here's the corrected CSS:

```css
.card-title {
    position: relative;
    width: max-content;
}

.card-title::after {
    content: "";
    height: 4px;
    position: absolute;
    bottom: -2px;
    left: calc(var(--padding) * -1);
    width: calc(100% + var(--padding));
    background: var(--color-accent-400);
    transform-origin: left;
    transform: scaleX(0);  /* Set the default state to 0 */
    transition: transform 500ms ease;
}

.card:hover .card-title::after,
.card:focus-within .card-title::after {
    transform: scaleX(1);
}

@media (hover: hover) {
    .card-content > *:not(.card-title) {
        opacity: 0;
        transition: opacity 500ms linear;
    }

    .card:hover .card-content > *:not(.card-title),
    .card:focus-within .card-content > *:not(.card-title) {
        opacity: 1;
        transition-delay: 1000ms;
    }
}
```

The `transform: scaleX(0);` is set outside of the media query, so the default state is 0 scale (hidden). The hover and focus effects then expand it to full width (`scaleX(1)`). The media query condition is also updated. Try using this corrected CSS and see if the effect works as expected.