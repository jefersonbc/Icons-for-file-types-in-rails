# Icons for file types in rails
A easy way to show icons for file types in rails/ruby (Paperclip, CarrierWave, etc.)

Requirements
------------
- Ruby and Ruby on Rails (:P) - Tested in Ruby 2.0.0 and Rails 4.1.8.
- Put the images for the icons on the folder ```file_type_icons```, inside the ```/public``` folder.

Usage
-----

Put this in a helper:

```ruby
def icon_file_type(filename, options={})
  ext = filename.match(/[^\\]*\.(\w+)$/)[1]
  size = "#{options[:size]}/" if options[:size]
  "/file_type_icons/#{size ||=""}#{ext}.png"
end
```

Now, calling ```icon_file_type(filename, options = {})``` in a view, with the file name (with extension) as an argument, you'll have the image address that corresponds with the file extension.

```
<%= icon_file_type("file_name.extension") %>
```

Ex.:

```ruby
<img src="<%= icon_file_type(pdf_file.pdf) %>">
```
The address of the image (icon) will be ```/public/file_type_icons/pdf.png```

Example using Paperclip:

```ruby
<img src="<%= icon_file_type(upload.uploaded_file_file_name) %>">
```

Options
-------

One of the Implemented options (the only) is ```:size```. It allows you tell the size of the image that will be used. In this way the image that will be loaded will be an image inside the folder with the same name of the argument ```:size```.


Ex.:

```ruby
<img src="<%= icon_file_type(pdf_file.pdf, "36x36") %>">
```
The address of the image (icon) will be ```/public/file_type_icons/36x36/pdf.png```

```:size``` can be whatever you want (```small```, ```medium```, ```large```, ```48x48```, etc.), as long as a folder with the same name exists inside ```/public/file_type_icons/```.


Credits
-------

Jeferson Brito

E-mail: nashbox@gmail.com or jeferson@nimbus42.com.br

Website: www.jefersonbc.com or www.nimbus42.com.br
