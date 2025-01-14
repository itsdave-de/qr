# QR Code Generator for Frappe

![itsdave qr](itsdave-www-qr.png "itsdave qr")

QR Code Generator for Frappe Framework, based on Segno

Its mainly intended to be used inside print formats.

It includes a utility function `get_qr_code` that generates QR codes with customizable colors, formats, and sizes. The generated QR codes can be embedded directly as HTML `<img>` tags or returned as base64-encoded strings.

## Function: `get_qr_code`

The get_qr_code function generates a QR code for a given string, with customizable colors, formats, and sizes. This versatile function supports both SVG and PNG formats, ensuring high-quality and scalable output. The generated QR code can be returned either as a base64-encoded string or directly embedded as an HTML <div> tag containing an <img> element for seamless integration into web pages.

### Parameters:
- **data** (`str`): The data to encode in the QR code.
- **dark** (`str`, optional): Color of the QR code's dark modules (default is 'black').
- **light** (`str`, optional): Color of the QR code's light modules (default is 'white').
- **return_html** (bool, optional): If True, returns an HTML <div> tag with an embedded <img>; if False, returns a base64-encoded string (default is True).
- **size** (int, optional): The size (width and height) of the QR code image in pixels (default is 200).
- **format** (`str`, optional): The format of the QR code ('svg' or 'png', default is 'svg').
- **scale** (`int`, optional): The scaling factor for PNG output (default is 10).

### Returns:
- **str**: An HTML <div> tag with an embedded <img> and CSS to maintain aspect ratio, or a base64-encoded string, depending on the return_html parameter.

This function is ideal for generating QR codes on the fly, with options to customize colors and formats to fit any design or application requirement.

### Usage

You can use the get_qr_code function in a custom HTML field inside the print format builder. Some examples:

## Example 1: Static Text

```
  {{ get_qr_code("Static QR Code Data") }}
```

## Example 2: Using a Variable

```
  {{ get_qr_code(doc.some_field) }}
```

## Example 3: Using a Child Table

```
  {% for row in doc.child_table %}
    {{ get_qr_code(row.qrdata) }}
  {% endfor %}
```

## Example 4: Custom Colors and Formats

```
  {{ get_qr_code("Custom Data", dark='blue', light='yellow', format='png', scale=5) }}
```