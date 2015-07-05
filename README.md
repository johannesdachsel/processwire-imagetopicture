# ImageToPicture

Module for [Processwire](https://processwire.com) that adds a new Pageimage method for rendering proper picture element markup from a given image with.

## Usage

You can call the `toPicture()` method on any image in Processwire like this:

	$image->toPicture();

There are some options available, to define queries and image sizes. These are the defaults:

	$image->toPicture(array(
	  'fallback' => 450, // width for fallback image
	  'altText' => '', // alternative text (default is image description)
	  'sources' => array(
	    '(min-width: 64em)' => 600, // queries and image widths
	    '(min-width: 45em)' => 520 
	  )
	));

Using `toPicture()` without any options renders the following output:

	<picture>
	  <source media="(min-width: 64em)" srcset="img-600px.jpg">
	  <source media="(min-width: 45em)" srcset="img-520px.jpg">
	  <img src="img-450px.jpg" alt="Image description">
	</picture>

A customised call might look like this:

	$image->toPicture(array(
	  'fallback' => 300,
	  'altText' => 'My new description',
	  'sources' => array(
	    '(min-width: 55em)' => 860,
	    '(min-width: 27em)' => 450 
	  )
	));

Which produces:

	<picture>
	  <source media="(min-width: 55em)" srcset="img-860px.jpg">
	  <source media="(min-width: 27em)" srcset="img-450px.jpg">
	  <img src="img-300px.jpg" alt="My new description">
	</picture>

