# Client Testimonials Component

## Overview

This Vue 3 component creates a dynamic and visually appealing client testimonials section. It's designed to showcase customer feedback in an interactive carousel format, enhancing the credibility of your website or application.

## Preview

![Overflow Slider Preview](https://github.com/AroshaRavishan/Overflow-Slider-with-progressBar-Vue/blob/main/Overflow%20Slider%20Preview.png)

## Features

- Responsive design adapting to various screen sizes (mobile to desktop)
- Interactive carousel powered by Splide.js
- Custom-styled testimonial cards with rotating background colors
- Dynamic content loading for testimonials
- Progress indicator showing current position in the carousel
- Manual navigation controls (prev/next buttons)
- Trustpilot integration for additional social proof

## Technical Details

### Vue 3 and Composition API
- Utilizes Vue 3's Composition API for efficient state management and logic organization
- Uses `ref` and `onMounted` for reactive data and lifecycle hooks

### Inertia.js Integration
- Leverages Inertia.js for seamless page transitions and data passing

### Splide.js Configuration
- Custom configuration for the Splide carousel, including:
  - Center-focused slides
  - Auto-width adjustment
  - Wheel navigation
  - Custom gap and move settings

### Dynamic Asset Loading
- Uses `$page.props.assetURL` for dynamic loading of images and assets

### Responsive Design
- Implements responsive classes for optimal display across devices
- Custom CSS for text truncation and layout adjustments

## Component Breakdown

### Data Management
- Predefined array of testimonial objects, each containing:
  - Unique ID
  - Customer name and country
  - Testimonial text
  - Profile image URL
  - Background color

### Carousel Controls
- Custom functions for slide navigation (`prevSlide`, `nextSlide`)
- Progress tracking using `onMoved` event handler

### Styling
- Scoped CSS for component-specific styling
- Custom classes for text truncation and progress bar

## Usage

To use this component:

1. Import it into your Vue application
2. Ensure all dependencies are installed (Vue 3, Inertia.js, Splide.js, FontAwesome)
3. Provide the necessary asset URLs through Inertia.js page props
4. Customize the testimonial data as needed

## Customization

The component can be easily customized by:
- Modifying the `slides` array to update testimonial content
- Adjusting the `colors` array to change card background colors
- Tweaking the Splide options in `contentSplideOptions`
- Modifying the scoped CSS for visual adjustments

## Performance Considerations

- Lazy loading is implemented for images to improve load times
- CSS line clamping is used to manage text overflow efficiently

This component offers a robust solution for displaying client testimonials, combining aesthetic appeal with smooth functionality to enhance user engagement and trust.
