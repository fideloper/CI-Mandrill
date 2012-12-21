# Mandrill
A Codeigniter library for using [Mandrill's](http://mandrill.com/) super-fine [API](http://mandrillapp.com/api/docs/).

See Mandrill's [help docs](http://help.mandrill.com/home).

I use this library with [Mailman](https://github.com/fideloper/Mailman).

# Install
Add the `config/mandrill.php` file into your `application/config` directory. Optionally add that config to `config/autoload.php` so you do not need to do so manually.

Add the library/Mandrill.php file into your `application/libraries` directory.

# Usage
```php
//In some controller, far far away

$this->load->config('mandrill');

$this->load->library('mandrill');

$mandrill_ready = NULL;

try {

	$this->mandrill->init( $this->CI->config->item('mandrill_api_key') );
	$mandrill_ready = TRUE;
	
} catch(Mandrill_Exception $e) {

	$mandrill_ready = FALSE;
	
}

if( $mandrill_ready ) {

	//Send us some email!
	$email = array(
		'html' => '<p>This is my message<p>', //Consider using a view file
		'text' => 'This is my plaintext message',
		'subject' => 'This is my subject',
		'from_email' => 'me@ohmy.com',
		'from_name' => 'Me-Oh-My',
		'to' => array(array('email' => 'joe@example.com' )) //Check documentation for more details on this one
		);

	$result = $this->mandrill->messages_send($email);
	
}

```

 
