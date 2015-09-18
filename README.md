# Email template notes
Some notes about email template development


## Email cliente preprocess your HTML

#### Changes
- Removes or change HTML tags
- Removes or change CSS
- Ovewrite style with app style
- Change the entire document structure

#### Signature changes
- Remove all javascript

### Gmails preprocessor

#### Changes
- Remove any `<link>` tag
- Ovewrite style with app CSS
- Changes teh entire document structure

#### Signature changes
- Removes `<style>` tag

## Engines
**Gmail uses chrome**
![gmail][gmail] ![arrow][arrow] ![chrome][chrome]

**Outlook 2003 uses ie**
![mso][mso] ![arrow][arrow] ![ie][ie]

**Outlook 2007> uses Word**
![mso][mso] ![arrow][arrow] ![msw][msw]

[More detailed information](http://templates.mailchimp.com/concepts/email-clients)

## Features which don't work
- `height`
- `display`
- `float`
- `position`

#### Don't work in `p` and `div` tags
- `width`
- `padding`

#### Don't work in outlook.com
- `margin`

## Tips
**Always use absolute url**
```html
<!-- bad -->
<img src="/images/my-img.png">

<!-- good -->
<img src="http://mysite.com/images/my-img.png">
```
**Tables :(**
- Use tables to do a cross service layout
- Reset styles from table

```html
<!-- basic reset -->
<table
  cellspacing="0"
  cellpadding="0"
  border="0"
>...</table>
```

**Always define your font style**
Gmail will apply `font-family` and Aol applies their color to all `td`s. If you want you own font, make sure to overwirte that.

**Microsoft Outlook `line-heigh` bug**
Outlook has a lot of problems with `line-height`. An easy way to fix this is by changing this Outlook property:

```css
mso-line-heigh-rule: exactly; /* now your line-heigh will work */
```

**Some services don’t allow smaller fonts**
Gmail and other services have a minimum font-size. In Gmail, this size is `14px`. If you want to use a smaller font than this, you'll need to use this CSS property:

```css
-ms-text-size-adjust: none;
-webkit-text-size-adjust: none;
```

**Outlook uses Microsoft Word as processor, and it doesn’t have the common behavior when stylizing the `a` tag as a button**
Outlook is using Microsoft Word as engine, which doesn’t use the right way styles on ‘a’ tags. To have a beautiful button in your email, use this service instead: [button.cm](button.cm).

**Conditional comments**
As IE had in the past, Outlook works with conditional comments:.

- Outlook 2000 - Version 9
- Outlook 2002 - Version 10
- Outlook 2003 - Version 11
- Outlook 2007 - Version 12
- Outlook 2010 - Version 14
- Outlook 2013 - Version 15

```html
<!--[if gte mso 9]>
<![endif]-->
```

You can use operators:
- `gte`: greater than or equal
- `lte`: less than or equal
- etc...

**Use a inline css tool**
[CSS Inliner](http://templates.mailchimp.com/resources/inline-css/)

## More about
- [CSS conditional Outlook](http://templates.mailchimp.com/development/css/outlook-conditional-css/)
- [Reset Style from Mailchimp](http://templates.mailchimp.com/development/css/reset-styles/)

[arrow]:  images/arrow.png
[gmail]:  images/gmail.png
[chrome]: images/chrome.png
[ie]:     images/ie.png
[mso]:    images/mso.png
[msw]:    images/msw.png