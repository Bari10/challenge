---
layout: component
title: Thumbnail
intro-text: "A thumbnail is a preview of an image or document that can be used in different contexts to improve page loading performance, enhance the user experience, and improve accessibility."
research-title: thumbnail
figma-link: https://www.figma.com/design/rGGJbQMmy6391gsavkMss2/VADS-Thumbnail?node-id=0-1&p=f&t=4afHcXWMVmoMEaVY-0
status: use-with-caution-candidate
web-component: va-thumbnail
anchors:
  - anchor: Examples
  - anchor: Usage
  - anchor: How this component works
  - anchor: Behavior
  - anchor: Placement
  - anchor: Code usage
  - anchor: Content considerations
  - anchor: Accessibility considerations
  - anchor: Related
  - anchor: Component checklist
---

## Examples

### Web

#### Default

{% include storybook-preview.html height="375px" story="components-thumbnail-va-web--basic" link_text=page.web-component %}

#### With va-card

{% include storybook-preview.html height="400px" story="components-thumbnail-va-web--card" link_text=page.web-component %}

#### Profile

{% include storybook-preview.html height="250px" story="components-thumbnail-va-web--headshot" link_text=page.web-component %}

#### Circle

{% include storybook-preview.html height="400px" story="components-thumbnail-va-web--with-circle" link_text=page.web-component %}

#### Caption

{% include storybook-preview.html height="400px" story="components-thumbnail-va-web--with-caption" link_text=page.web-component %}

### Mobile

### Default

{% include storybook-preview.html height="400px" story="components-thumbnail-va-mobile--basic" link_text=page.web-component %}

### With va-card

{% include storybook-preview.html height="400px" story="components-thumbnail-va-mobile--in-card" link_text=page.web-component %}

### Profile

{% include storybook-preview.html height="250px" story="components-thumbnail-va-mobile--profile" link_text=page.web-component %}

### Circle

{% include storybook-preview.html height="300px" story="components-thumbnail-va-mobile--circle" link_text=page.web-component %}

{% include component-docs.html component_name=page.web-component %}

## Usage

### When to use the thumbnail component

- **Adding an image to a page.** Generally, the thumbnail component can be used in most cases when an image is used on a page. The thumbnail component has properties that allow consistent [aspect ratios]({{ site.baseurl }}/foundation/image-aspect-ratios), reduce page load times, and add accessibility improvements to images. The thumbnail component can be used in a variety of applications and is not limited to those listed below:
  - **A user avatar, headshot, or profile image.** Avatar images are often circular or square with a 1:1 aspect ratio to maintain the shape.
  - **File and document thumbnails.** The thumbnail component is used in the [File input]({{ site.baseurl }}/components/form/file-input). Use the thumbnail component when displaying previews of documentation.
  - **Hidden images.** Images in menus or carousels can benefit from using the thumbnail component so that features like lazy loading can be applied.
  - **Logos.** Most images should apply a set aspect ratio but logos might have unique dimensions. You can still use the thumbnail component for logos by using a custom aspect ratio if the logo is a flat file. If your logo is a SVG consider something else. 
  - **Banners or hero images.** Use the 7:2 aspect ratio and optimize images to decrease image sizes, as these images are usually larger in size than other images on the page.
  - **Teaser images for news stories or "Promo blocks" on benefit hub landing pages.** Use a 3:2 aspect ratio and consider a card layout for news stories and "promo blocks".
  - **Medical imagery.** Medical imagery can include large quantities of images and require high resolution images. Use the thumbnail component to benefit from improved page load speeds and consistent aspect ratios. 
- **Improve page performance.** The thumbnail component supports lazy loading that can significantly decrease initial web page loading time and conserve bandwidth to improve the user experience.
- **Both mobile and web options.** This component supports mobile and web platforms. Use this component to create consistent experiences between mobile and web.
- **Large quantities of images.** Re-evaluate the use of images. Remember that all images affect the total download speed and responsiveness. Ensure that any images that are included support the context and are necessary. If large quantities of images are necessary use the thumbnail component and look into modern image formats like [WebP and AVIF](#other-file-formats-that-can-be-beneficial-in-different-use-cases) to help reduce the size of the image. We will be adding new features in v2 that will provide more performance loading features. 

### When to consider something else

- **Icons or SVG logos.** The thumbnail component is not recommended for SVG formats due to accessibility issues. SVGs have no implicit aria roles applied on their own, while images do have aria roles. If you used the thumbnail component for SVG's, it would be flagged for accessibility issues due to no role being present.
- **When the image does not improve the understanding of the written content.** Too many images on a page can increase page load times and degrade the experience. Only use images when they help the user better understand the written content.
- **Images as links.** Aside from logos, we discourage using images as links. They can be ambiguous and complicated to demonstrate clickable actions. Instead, use text links alongside images or in the captions if a link is needed.
- **Images are unnecessary.** Does the image create a better understanding of the written content? If there is no need for an image consider omitting the image to improve page performance.
- **Interactive charts, maps, or infographics.** The thumbnail component should only be used for PDFs and flattened image types.
- **Images of text.** Use real text as all page content, and use CSS to visually style it as you need.

This thumbnail component can be used in a variety of use cases. Contact the [Design System Team]({{ site.baseurl }}/about/feedback) if you need further help.

## How this component works

### Lazy loading

The thumbnail component supports [lazy loading](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#lazy) by only loading images when needed, resulting in a faster initial page load time, reduced bandwidth usage, and a better user experience. Lazy loading should be used for images in most situations but can be turned off if needed.

### Sizing the thumbnail

The thumbnail component has different properties to attain the correct fit and sizing listed below.

#### Fit

Fit determines how the thumbnail is sized to fit the container. The image can be set as cover, contain, or none. Cover is the preferred option as it provides optimal image scaling and ensures the container is filled.

##### Cover
{% include component-example.html alt="Example of image using the fit property set to cover" file="/images/components/thumbnail/cover.jpg" caption="In this example, the original image is on the left. When 'Fit' is applied to the container, the image is stretched to fill the container." class="x2" reverse="true" %}

Cover will scale the image to fit within the container while maintaining the aspect ratio. Parts of the original image that don't fit in the container are cropped.

##### Contain
{% include component-example.html alt="Example of image using the fit property set to contain" file="/images/components/thumbnail/contain.jpg" caption="In this example, when 'contain' is applied to the container, the image maintains its aspect ratio but scales to the size of the container, cropping some of the image out." class="x2" reverse="true" %}

Contain scales the image to fit within the container while maintaining the aspect ratio. The image is not cropped to fill the container.

##### None
{% include component-example.html alt="Example of image using the fit property set to none" file="/images/components/thumbnail/none.jpg" caption="In this example, the image is added to the container with 'none' used, and the image overflows the image in height and width. The image container crops any part of the image that goes beyond the container." class="x2" reverse="true" %}

None will not resize the image and maintain the aspect ratio of the original image. Any part of the image that doesn't fit in the container will be cropped out.

#### Height

Specifies the natural height of the image. Setting the **height** and **width** helps the browser define and reserve the space for the image before it loads, preventing a "jarring" effect and content reflow.

#### Placeholder

Use height and width with the placeholder adds a background color to the image while it loads. 

**What color should be used for the placeholder background?**

Any color can be added as the placeholder. Use a color that provides enough contrast between the background and the image placeholder. Lighter VADS base colors are safe options to use.
<div class="vads-u-display--flex">
    <div class="vads-u-border--1px vads-u-border-color--gray-lighter vads-u-padding--5 vads-u-margin-right--1 medium-screen:vads-u-flex--2" style="background-color: #a9aeb1"></div>
    <br />
    <div class="vads-u-width--full vads-u-flex--2">
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        <strong>vads-color-base-light</strong>
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        #a9aeb1
      </div>
<div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        uswds-system-color-gray-cool-30
        </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        vads-color-gray-light
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        $color-vads-color-base-light
      </div>
    </div>
  </div>
<br />
<div class="vads-u-display--flex">
    <div class="vads-u-border--1px vads-u-border-color--gray-lighter vads-u-padding--5 vads-u-margin-right--1 medium-screen:vads-u-flex--2" style="background-color: #dfe1e2"></div>
    <!-- div class="vads-u-border--1px vads-u-border-color--gray-lighter vads-u-padding--5 vads-u-background-color--base-lighter vads-u-margin-right--1 medium-screen:vads-u-flex--2"></div -->
    <div class="vads-u-width--full vads-u-flex--2">
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        <strong>vads-color-base-lighter</strong>
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        #dfe1e2
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        uswds-system-color-gray-cool-10
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        vads-color-gray-lighter
      </div>
      <div class="vads-u-border-bottom--1px vads-u-border-color--gray-lighter">
        $color-vads-color-base-lighter</div>
    </div>
  </div>

#### Minimum image size
Use images to enhance the experience and provide a better understanding of the content. If the image is too small the image loses its purpose. Don't use images that are less than 40x40px in any situation.

| Example | Minimum image size | 
| ------- | ------------------ | 
| ![Example of an image that is 32x32px in size that is too small](/images/components/thumbnail/thumbnail-is-too-small.jpg "Do not use a image that is to small") | Thumbnails should be no less than 40x40px. | 
| ![Example of the minimum image size of 40x40px that should be used for file inputs](/images/components/thumbnail/thumbnail-for-file-input.jpg "Do not use a image less than 40x40px in size for file inputs") | File inputs thumbnails should be a 40 x 40px size minimum. | 
| ![Example of the minimum image size of 80x80px that should be used for news stories](/images/components/thumbnail/thumbnail-for-news.jpg "Do not use a image less than 80x80px in size for file inputs") | News story thumbnails should be a 80 x 80px minimum. | 

## Behavior

### Captions
{% include storybook-preview.html height="400px" story="components-thumbnail-va-web--with-caption" link_text=page.web-component %}

A caption is a brief explanation of the related thumbnail that can take the form of commentary, attributions, or quotations. See the [content considerations](#content-considerations) for guidance on writing captions for thumbnails.

### Preferred image resolutions

Reducing image resolutions can improve page loading speeds, but it can be challenging to determine the best resolution that will maximize optimization without reducing image quality. For most web content, 72 DPI should be used, and 144 DPI can be used for detailed images and Retina displays.

Follow the instructions in [Figma](https://help.figma.com/hc/en-us/articles/13402894554519-Export-formats-and-settings#h_01J7C8EZEKVYFGXF82FMQBN192) for the correct export settings.  

### Which image format should you choose

#### Preferred File Formats

The thumbnail component has no restriction on the file formats you can use. Use caution when using other file formats beyond JPEG, PNG, and PDF.

* **JPEG** is generally the preferred image format in most cases as JPEG balances file size, image quality, and browser support. JPEG is a lossy compression that loses some image quality when compressed.
* **PDF** is a versatile and reliable way to present and exchange documents.
* **PNG** format does not reduce image quality when file size is reduced and supports transparent backgrounds. PNG file formats are often larger than JPEGs but can be a good option for detailed graphics like screenshots and logos with transparent backgrounds.

#### Other file formats that can be beneficial in different use cases
* **GIF** can support simple animations, but animations are not recommended due to accessibility considerations. Follow [accessibility guidelines](https://equalizedigital.com/accessibility-checker/image-animated-gif/) when using gifs. 
* **WebP and AVIF** are modern image formats that can reduce image file sizes significantly while not losing image quality. These image formats can greatly improve website load times but are not yet universally supported like JPEG or PDF formats. You will need a fallback method to [detect browser support](https://developers.google.com/speed/webp/faq#how_can_i_detect_browser_support_for_webp) for images using these file formats. Consider using these image formats when you require large quantities of images to be loaded. 

#### File formats not recommended

**SVG** is not supported by the thumbnail component.

### Mobile Application vs. Web

Use the thumbnail component for both web and mobile applications.

## Placement

### Aspect Ratios

Every image should be applying an aspect ratio to create a consistent and more visually appealing experience throughout the site. Apply the correct aspect ratio for the use case.

{% include content/aspect-ratios.md %}

### Using images as links

Using images as links can make it challenging to convey that they are clickable and the action that happens when the image is clicked can be unexpected. Does clicking on the image navigate to a different page or open up a larger version of the image? On mobile devices this can be even more difficult as you have no cursor to indicate a hover over event. This puts a lot of the discovery process on the user. Instead of making the image clickable associate actions for the image in a link or button that can clearly indicate the expected action. Use a card layout and make the whole card clickable if needed. Read the [card element states]({{ site.baseurl }}/components/card#element-states) guidance for more information about clickable cards. 

## Content considerations

* Captions should contain a description of the image and a credit if required.
* Captions are text that appear adjacent to an image. They convey additional information that is not present in the image itself or information that is tangentially related to the image.
* Captions are different from alternative text (or alt text). Alt text's purpose is to describe what is visually present in an image. Also, alternative text only appears visually on a page when an image fails to display, whereas image captions are typically always visible. Alt text is always required, even if the value is null, whereas caption text is optional.
* An image's caption should never be the same as its alternative text. Using the same text for captions and alt text causes screen reader users to hear the same content twice.

**To help you write captions and alt text you can answer the following questions:**
* Alt text: What is happening in this image?
* Captions: Why is this image included on this page or in this particular spot? 

Is there something about this image that needs more explanation beyond what is shown in the image or described by the alternative text? Captions should also be complete sentences with proper punctuation.

## Accessibility considerations

-  **Alternative text (also known as alt text) is required for each image.** Alternative text is not visible on the screen, but is programmatically associated with the image. When alt text is defined, screen reader users can hear the image being described. This allows people who are blind or have low vision to understand the the content on the page. Alt text also allows users who've turned off images on their device because they have low internet bandwidth to read the alt text description instead. Follow the [alternative text for images]({{ site.baseurl }}/content-style-guide/alternative-text-for-images) content guidance on how to write alternative text.
-   **Don’t use images of text. Use real text as all page content, and use CSS to visually style it as you need.** When we use photos of text, the text is not accessible to screen readers, not scalable on multiple devices, and is difficult to read with screen magnifyiers.
  - If images of text are absolutely necessary, for example in logos, always provide an alt text describing or naming the company in the logo.

Related
-------

-   [Card]({{ site.baseurl }}/components/card)
-   [File input]({{ site.baseurl }}/components/form/file-input)

{% include _component-checklist.html component_name=page.web-component %}