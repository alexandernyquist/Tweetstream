# What's tweetstream?

Tweetstream is a (yet) simple wrapper around Twitters streaming api for php.

## Features
 * Track all tweets for given keywords (sample usage below). This is useful since Twitter does not make tweets available forever.

## Usage

This will track all tweets containing either "twitter" or "foobar" and save it to log.txt. You can easily modify the callback to save all tweets to a database or similar.

	$streamer = new TweetStream();
	$streamer->setCredentials('alexnyquist', 'password');
	$streamer->setCallback(function($message) {
		$message = sprintf('%s says: %s', $message->user->screen_name, $message->text);
		file_put_contents('log.txt', $message . PHP_EOL, FILE_APPEND); // Write tweets to file
	});
	$streamer->track('twitter', 'foobar');
	
Do you want to track everything said by/to a specific user? Just provide "@username" as a keyword.