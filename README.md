# CSS `calc()` Gotcha: Percentage Subtraction Inconsistency

This repository demonstrates a subtle but potentially problematic issue with CSS's `calc()` function when combining percentage widths with pixel subtractions. The problem manifests most noticeably in dynamic layouts where parent container widths aren't fixed.

## The Problem

The `calc()` function, while powerful, has nuances in its order of operations. When subtracting pixels from a percentage, the percentage is calculated first, and *then* the subtraction occurs. This can lead to unexpected results if the parent container's width depends on other percentage-based calculations or is responsive.

## The Solution

The best solution usually involves avoiding mixed percentage and pixel calculations within `calc()` if the parent width is dynamic. Consider using alternative approaches, such as:

* **Using viewport units (vw):**  Instead of relying on parent percentages, use `vw` (viewport width) to create more predictable results.
* **Media Queries:** Responsively adjust widths using media queries to handle different screen sizes instead of trying to force dynamic calculations with `calc()`
* **JavaScript:** If precise calculations are essential and complex, use JavaScript to calculate widths based on available space and window dimensions.  This will provide the most control but adds complexity.

## How to Reproduce

1. Clone this repository.
2. Open `bug.html` in a web browser.
3. Resize the browser window to observe the inconsistent behavior of the `.container` element's width.   The `bug.css` file exhibits the problem.
4. Now open `bugSolution.html`. This demonstrates using viewport units (`vw`) as a more reliable approach in dynamic situations (see `bugSolution.css`).