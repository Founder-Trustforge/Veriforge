# Vercel Speed Insights Setup Guide

This guide documents how Vercel Speed Insights has been integrated into the VeriChain project.

## Overview

Vercel Speed Insights is a performance monitoring tool that helps you understand how real users experience your website. It collects performance metrics like Core Web Vitals and sends them to the Vercel dashboard for analysis.

## Prerequisites

- A Vercel account (sign up at https://vercel.com/signup)
- A Vercel project (create one at https://vercel.com/new)
- Vercel CLI installed (`npm i vercel`)

## Installation

The `@vercel/speed-insights` package has been added to `package.json`. To install it:

```bash
npm install
# or
yarn install
# or
pnpm install
```

## Implementation for VeriChain (Static HTML)

Since VeriChain is currently a static HTML project, Speed Insights has been integrated using the standard HTML implementation method.

### What was added to `index.html`:

```html
<!-- Vercel Speed Insights -->
<script>
  window.si = window.si || function () { (window.siq = window.siq || []).push(arguments); };
</script>
<script defer src="/_vercel/speed-insights/script.js"></script>
```

These scripts should be placed before the closing `</body>` tag and will:
1. Initialize the Speed Insights queue
2. Load the Speed Insights tracking script after page load

## Enabling Speed Insights

To enable Speed Insights:

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Select your VeriChain project
3. Click the **Speed Insights** tab
4. Click **Enable** in the dialog

Note: Speed Insights will add new routes at `/_vercel/speed-insights/*` after your next deployment.

## Deployment

Deploy to Vercel using:

```bash
vercel deploy
```

Or connect your git repository to enable automatic deployments.

## Viewing Data

Once deployed and users visit your site:

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Select your project
3. Click the **Speed Insights** tab
4. After a few days of traffic, you'll see performance metrics

## Framework Migration

If VeriChain is converted to a framework-based project in the future, refer to the [Vercel Speed Insights documentation](https://vercel.com/docs/speed-insights) for framework-specific instructions:

- **Next.js**: Use `@vercel/speed-insights/next`
- **React/CRA**: Use `@vercel/speed-insights/react`
- **Vue**: Use `@vercel/speed-insights/vue`
- **Nuxt**: Use `@vercel/speed-insights/vue`
- **SvelteKit**: Use `injectSpeedInsights` from `@vercel/speed-insights/sveltekit`
- **Remix**: Use `@vercel/speed-insights/remix`
- **Astro**: Use `@vercel/speed-insights/astro`

## Privacy & Compliance

Vercel Speed Insights complies with privacy and data protection standards. For more information, see the [Privacy Policy documentation](https://vercel.com/docs/speed-insights/privacy-policy).

## More Information

- [Full Package Documentation](https://vercel.com/docs/speed-insights/package)
- [Understanding Metrics](https://vercel.com/docs/speed-insights/metrics)
- [Troubleshooting](https://vercel.com/docs/speed-insights/troubleshooting)
- [Limits and Pricing](https://vercel.com/docs/speed-insights/limits-and-pricing)
