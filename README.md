This is a helper package that extends Django HTML5 Boilerplate for mobile support. By default it uses jQuery Mobile, but it is designed in a way that you could easily replace the two references to jQuery Mobile with another library. This package does assume that you want to load the JavaScript in the `head` tag. It also includes optimized support for iOS applications, so that putting your application on the iOS home screen will make it look like a native app.

Find out for about HTML5 Boilerplate at:

> https://github.com/h5bp/html5-boilerplate

And Django HTML5 Boilerplate at:

> https://github.com/mattsnider/django-html5-boilerplate

And the `Add To Home` plugin at:

> http://plugins.jquery.com/addToHome/

Installation
============

Code is found at::

> https://github.com/mattsnider/django-html5-mobile-boilerplate

The easiest way to install is using pip::

> pip install django-html5-mobile-boilerplate

Requirements
============

To consume the package, you need only have a version of Django >= 1.3 and Django HTML5 Boilerplate >= 1.0.5.

This library has been tested on Python >= 2.6.

Usage
=====

All static files and templates are namespaced under the directory DH5BP. You will need to include DH5BP in your `settings.py`:

    INSTALLED_APPS = (
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.sites',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        # Uncomment the next line to enable the admin:
        'django.contrib.admin',
        # Uncomment the next line to enable admin documentation:
        'django.contrib.admindocs',
        ...
        'dh5mbp',
        ...
    )

H5MBP Template
-------------
Any template you want to inherit the H5BP page architecture include the following:

    {% extends 'dh5mbp/base.html' %}
    {% load url from future %}
    {% load staticfiles %}
    {% block title %}YOUR TITLE HERE{% endblock %}
    {% block content %}YOUR JQUERY MOBILE MARKUP HERE{% endblock %}

To add your styles or other tags to the `head`:

    {% block head %}
        {% block.super %}
        <link rel="stylesheet" href="{% static "css/YOUR_CSS.css" %}">
        <meta name="keywords" content="YOUR KEYWORD">
        ...
    {% endblock %}

To override the mobile library:

    {% block dh5mbp_css %}
    <link rel="stylesheet" href="{% static 'YOUR_LIBRARY_CSS_HERE' %}" />
    {% endblock %}
    {% block dh5mbp_js %}
    <script src="{% static 'YOUR_LIBRARY_JS_HERE' %}"></script>
    {% endblock %}

By default the iOS Add To Home message will be shown, but you can turn this off by setting the template var `skip_add_to_home` to `True`.

Lastly, the iOS icons will be links will be included automatically, looking for the static directory `images/ios/...`. You will need to put your iOS put the following four files there:

	startup-image.png
	touch-icon-ipad.png
	touch-icon-iphone-retina.png
	touch-icon-ipad-retina.png
	
If those paths don't work for you, then use the follow block to replace them:

	
    {% block dh5mbp_ios_icons %}{
    <link rel="apple-touch-startup-image" href="{% static 'YOUR_PATH/startup-image.png' %}">
    <link rel="apple-touch-icon" href="{% static 'YOUR_PATH/touch-icon-ipad.png' %}" />
    <link rel="apple-touch-icon" sizes="72x72" href="{% static 'YOUR_PATH/touch-icon-ipad.png' %}" />
    <link rel="apple-touch-icon" sizes="114x114" href="{% static 'YOUR_PATH/touch-icon-iphone-retina.png' %}" />
    <link rel="apple-touch-icon" sizes="144x144" href="{% static 'YOUR_PATH/touch-icon-ipad-retina.png' %}" />
    {% endblock %}

Roadmap
=======

I intend to maintain this package, fixing bugs and keeping up-to-date with jQuery mobile and Django, but plan little other development.

The system currently pulls the CSS from the jquery CDN, so that we don't have to worry about relative image paths therein. If there is a strong demand for the CSS to be served from the local static files, then I'll consider including a local CSS by default and writing a script to replace the image URLs in the default CSS.

Issues
======

https://github.com/mattsnider/django-html5-mobile-boilerplate/issues

Licensing
=========

Apache 2.0; see LICENSE file