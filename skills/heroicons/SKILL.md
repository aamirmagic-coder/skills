---
name: heroicons
description: Select, install, integrate, and maintain Heroicons in web interfaces. Use whenever a user asks to add icons, replace interface icons, standardize iconography, use Heroicons SVGs, or implement icons in React, Vue, or plain HTML/CSS. Prefer official Heroicons assets and framework packages; preserve accessibility, visual consistency, and bundle efficiency.
---

# Heroicons

Use this skill to integrate the official Heroicons icon set into web applications with consistent styling and accessible markup.

## 1. Identify the project context

Before changing files:
- Inspect the existing project structure, package manager, framework, icon dependencies, design system, and current icon usage.
- Check whether Heroicons is already installed. Avoid duplicate dependencies or replacing an established icon system without a clear reason.
- Identify the needed icon by its meaning and visual role. Prefer an existing Heroicon over drawing a new icon.
- Choose the appropriate size and style: outline, solid, mini (20px), or micro (16px), based on the surrounding interface.

## 2. Choose the integration

Use the official framework package when applicable:

- React: `@heroicons/react`
  - 24px outline: `@heroicons/react/24/outline`
  - 24px solid: `@heroicons/react/24/solid`
  - 20px solid: `@heroicons/react/20/solid`
  - 16px solid: `@heroicons/react/16/solid`
- Vue: `@heroicons/vue`
  - 24px outline: `@heroicons/vue/24/outline`
  - 24px solid: `@heroicons/vue/24/solid`
  - 20px solid: `@heroicons/vue/20/solid`
  - 16px solid: `@heroicons/vue/16/solid`
- Plain HTML, CSS, or other frameworks: use the SVG assets from the official Heroicons repository or inline an SVG when the project needs a self-contained asset.

Install only the package needed by the project's framework and package manager. Do not install the repository root package as a substitute for the React or Vue integrations. Do not clone the whole repository into an application unless the user specifically needs the source assets.

## 3. Implement accessible icons

For decorative icons next to a visible text label:
- Hide the icon from assistive technology (for example, use `aria-hidden="true"`).
- Keep the visible text as the accessible name.
- Use consistent dimensions and stroke weight within the same control.

For icon-only buttons:
- Give the button an accessible name with visible text or an appropriate `aria-label`.
- Do not rely on the SVG shape, color, or tooltip alone to communicate the action.
- Preserve keyboard focus, target size, and existing interaction states.

For meaningful standalone graphics:
- Provide an accessible name using an appropriate title or accessible label.
- Avoid redundant announcements when the adjacent text already conveys the same meaning.

Do not use color as the only way to distinguish icon meaning or state.

## 4. Maintain visual consistency

- Match icon size to the component scale and align icons optically with text.
- Use outline icons for neutral navigation and general-purpose actions when that matches the existing system; use solid variants for emphasis or selected states when appropriate.
- Avoid mixing outline and solid styles arbitrarily in the same navigation group.
- Use CSS classes or existing design tokens for size, color, spacing, and hover/focus states. Do not hard-code a new palette if the project already defines one.
- Keep SVGs crisp and preserve their viewBox. Avoid distorting icons with non-uniform width and height.
- Do not add unnecessary wrapper elements or duplicate decorative icons.

## 5. Verify the result

After implementation:
- Confirm imports resolve and the app builds or type-checks when the available environment permits.
- Check that the icon renders at the intended size and alignment.
- Check keyboard operation and accessible names for icon-only controls.
- Check responsive layouts and light/dark themes if the project supports them.
- Report exactly what was changed and which checks were actually run. Do not claim a build or test passed unless it was executed.

## 6. Licensing and source integrity

Heroicons is distributed under the MIT license. Preserve required license and copyright notices when copying or redistributing source assets. Prefer official package releases and repository assets; do not modify the underlying SVG path data merely to make an icon fit a layout. Adjust presentation through supported props and CSS instead.

## Common patterns

### React

```jsx
import { HomeIcon } from "@heroicons/react/24/outline";

export function HomeLink() {
  return (
    <a href="/" className="inline-flex items-center gap-2">
      <HomeIcon className="h-5 w-5" aria-hidden="true" />
      <span>Home</span>
    </a>
  );
}
```

### Vue

```vue
<script setup>
import { HomeIcon } from "@heroicons/vue/24/outline";
</script>

<template>
  <a href="/" class="inline-flex items-center gap-2">
    <HomeIcon class="h-5 w-5" aria-hidden="true" />
    <span>Home</span>
  </a>
</template>
```

### Icon-only button

```jsx
<button type="button" aria-label="Close dialog">
  <XMarkIcon className="h-5 w-5" aria-hidden="true" />
</button>
```

Use the project's existing component conventions and styling utilities in place of these illustrative class names.
