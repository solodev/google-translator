# google-translator
In this tutorial, [Solodev](https://www.solodev.com/) will show how to customize the default Google Website Translator toolbar so that it, rather, displays a stylish dropdown with flags as a language reference.

## Tutorial

For detailed instructions, view Solodev's [Using Google Translate with your Content](https://www.solodev.com/blog/web-design/using-google-translate-with-your-content.stml) article.

## Demo

Try out a working example on [JSFiddle](https://jsfiddle.net/solodev/0stLrpqg/).

## HTML

The translation toolbar is created with the following HTML:

```
<div class="ct-topbar">
  <div class="container">
	<ul class="list-unstyled list-inline ct-topbar__list">
	  <li class="ct-language">Language <i class="fa fa-arrow-down"></i>
		<ul class="list-unstyled ct-language__dropdown">
		  <li><a href="#googtrans(en|en)" class="lang-en lang-select" data-lang="en"><img src="https://www.solodev.com/assets/google-translate/flag-usa.png" alt="USA"></a></li>
		  <li><a href="#googtrans(en|es)" class="lang-es lang-select" data-lang="es"><img src="https://www.solodev.com/assets/google-translate/flag-mexico.png" alt="MEXICO"></a></li>
		  <li><a href="#googtrans(en|fr)" class="lang-es lang-select" data-lang="fr"><img src="https://www.solodev.com/assets/google-translate/flag-france.png" alt="FRANCE"></a></li>
		  <li><a href="#googtrans(en|zh-CN)" class="lang-es lang-select" data-lang="zh-CN"><img src="https://www.solodev.com/assets/google-translate/flag-china.png" alt="CHINA"></a></li>
		  <li><a href="#googtrans(en|ja)" class="lang-es lang-select" data-lang="ja"><img src="https://www.solodev.com/assets/google-translate/flag-japan.png" alt="JAPAN"></a></li>
		</ul>
	  </li>
	</ul>
  </div>
</div>
 
<nav class="navbar navbar-default">
  <div class="container">
	<div class="navbar-header">
	  <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
		<span class="sr-only">Toggle navigation</span>
		<span class="icon-bar"></span>
		<span class="icon-bar"></span>
		<span class="icon-bar"></span>
	  </button>
	  <a class="navbar-brand" href="#"> <img src="https://www.solodev.com/assets/email/logo.png" alt="Logo Solodev"></a>
	</div>
	<div id="navbar" class="collapse navbar-collapse">
	  <ul class="nav navbar-nav">
		<li><a href="#">Home</a></li>
		<li><a href="#about">About</a></li>
		<li><a href="#contact">Contact</a></li>
		<li class="dropdown">
		  <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Dropdown <span class="caret"></span></a>
		  <ul class="dropdown-menu">
			<li><a href="#">Action</a></li>
			<li><a href="#">Another action</a></li>
			<li><a href="#">Something else here</a></li>
			<li role="separator" class="divider"></li>
			<li class="dropdown-header">Nav header</li>
			<li><a href="#">Separated link</a></li>
			<li><a href="#">One more separated link</a></li>
		  </ul>
		</li>
	  </ul>
	</div><!--/.nav-collapse -->
  </div>
</nav>

<div class="container">
	<h1>Use Google Translate with your Website</h1>
	
	<p>Select a language from the upper-right dropdown menu and watch as the content of the page automatically translates.</p>
	
	<hr />

	<p>Solodev is the world’s first enterprise web experience platform available on-demand and created by developers for developers. It allows organizations to create amazing websites with unparalleled levels of security, scalability and total design freedom.</p>

	<p>Fully optimized for the Amazon Web Services (AWS) Cloud, Solodev provides you with unparalleled scalability, security, and accessibility and total design freedom without the need to compromise on design and functionality.</p>

	<p>Trusted by nationally recognized brands, Solodev is used to build and host engaging websites that drive meaningful results. Available for instant online purchase, Solodev empowers designers and developers to create dynamic, award-winning websites without compromise.</p>
</div>
```

## CSS

All required CSS is in google-translate.css


## External Includes

This tutorial contains the following third party resources.

```
<link rel="stylesheet" type="text/css" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">

<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script type="text/javascript" src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
```

## Initialize Google Translate Scripts

Include the following JavaScript on the page itself to initialize the translation capababilities.

```
<script type="text/javascript">
    function googleTranslateElementInit() {
      new google.translate.TranslateElement({pageLanguage: 'en', layout: google.translate.TranslateElement.FloatPosition.TOP_LEFT}, 'google_translate_element');
    }

	function triggerHtmlEvent(element, eventName) {
	  var event;
	  if (document.createEvent) {
		event = document.createEvent('HTMLEvents');
		event.initEvent(eventName, true, true);
		element.dispatchEvent(event);
	  } else {
		event = document.createEventObject();
		event.eventType = eventName;
		element.fireEvent('on' + event.eventType, event);
	  }
	}

	jQuery('.lang-select').click(function() {
	  var theLang = jQuery(this).attr('data-lang');
	  jQuery('.goog-te-combo').val(theLang);

	  //alert(jQuery(this).attr('href'));
	  window.location = jQuery(this).attr('href');
	  location.reload();

	});
</script>
<script type="text/javascript" src="https://translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>
```
