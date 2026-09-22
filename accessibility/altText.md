
# Alt text guidelines

## Do:

* Aim for about 120 characters of text or 1-2 sentences
* Be specific & accurate with your alt-text
* Be objective & neutral in your descriptions
* Consider your intended audience and what they need to understand about the image
* Be careful when marking images as decorative

## Avoid:
* Starting your alt-text with "Image of" (Caveat: It's ok to indicate what kind of image has been included, including "Screenshot of", "Black and white image of", "graphic of", or "cartoon"; most screen readers say "Image:" leading into the alt-text, so starting with "Image" causes the word to be repeated)
* Including every detail in the image
* Confusing images captions with alt-text
* Blindly using AI generated alt-text

## Alt-text v captions

Alt-text:
* Describes what the user needs from the image
* Usually not visible on the page

Captions:
* Identify what the image is about: citation information
* Snippets of context
* Can be read on the page

(based on TTaDA's "Simple Images")

## Markdown

* Pandoc's markdown [includes alt text](https://pandoc.org/MANUAL.html#images) automatically
* R Markdown knitr code chunks need to have [`fig.alt="alt text"`](https://yihui.org/knitr/options/) (note that `lm.plot` creates separate figures, so fig.alt should be a character vector of the appropriate length)
