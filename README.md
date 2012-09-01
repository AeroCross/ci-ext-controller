## Description

By autoloading components of Codeigniter, it's easy to DRY up applications by autoloading views, adding the capaility of loading layouts depending on the class and method, logging, and other useful tasks.

## Usage
 
To use this core extension, is simple.
 
### Loading
 
Copy the `EXT_Controller.php` file to your `application/core` folder, and set your `$config['subclass_prefix']`. to EXT_ (or just rename the file with the value you want. EXT_ is just the default for this file, and MY_ for Codeigniter).

You can read this in detail in the [Codeigniter User Guide][Uer Guide] (section **Extending Core Class**).

### Extending controllers

After you do set up the controller core class, extend your controllers to the chosen prefix instead of the default (`CI_Controller`):

```php
class Controller extends EXT_Controller {
	public function __construct() {
		// code
	}
	
	public function index() {
		// more code
	}
}
```

### Auto-loading views

When creating your views, create them inside a `files/` directory inside your `views/` directory. The strcuture is:

	application/
		views/
			files/
				controller/
					method.php
					
The extension will auto-load the method.php view file (according to your method specified in your controller).

To change the default view use `$this->view = 'files/path/to/view'`

### Layouts

- Create a `layouts/` directory inside your `views/` directory and create a `default.php` file. 
- Add `<?php echo $content; >` to that file and the HTML that will contain it. `$content` sotres all the data inside your view (`loaded in application/view/files/controller/method`).
- To change the default layout, use `$this->layout = 'name' inside your controller.

## In-depth explanation

There's a detailed [blog post][Blog Post] on how I made this and what does this do on my website — be sure to check it out!

[Blog Post]: http://mariocuba.net/blog/post/35