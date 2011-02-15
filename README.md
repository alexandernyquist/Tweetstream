# What's tweetstream?

Tweetstream is a (yet) simple wrapper around twitters streaming api for php.

## Features
 * Track all tweets for given keywords (sample usage below)

## Usage

$streamer = new TweetStream();
$streamer->setCredentials('alexnyquist', 'password');
$streamer->setCallback(function($message) {
	$message = sprintf('%s says: %s', $message->user->screen_name, $message->text);
	file_put_contents('log.txt', $message . PHP_EOL, FILE_APPEND); // Write tweets to file
});
$streamer->track('twitter', 'foobar');