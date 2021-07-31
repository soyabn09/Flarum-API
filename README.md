# Flarum API Docs

Flarum API but doesn't seem to have a official documentation on endpoints so I decided to make this.

## Authentication

* `POST /api/token` - Retrieve authentication token

Example:

	POST /api/token HTTP/1.1

	{
		"identification": "Toby", 
		"password": "pass7word"
	}
	
	HTTP/1.1 200 OK
	
	{
		"token": "YACub2KLfe8mfmHPcUKtt6t2SMJOGPXnZbqhc3nX",
		"userId": "1"
	}

You can then pass the token in an Authorization header in subsequent requests:

	GET /api HTTP/1.1
	Authorization: Token YACub2KLfe8mfmHPcUKtt6t2SMJOGPXnZbqhc3nX

> Note: The token is only available for a few minutes

## Forum

* `GET /api` - Get forum information

## Password Forgot

* `POST /api/forgot` - Send forgot password email

## Users

* `GET /api/users` - List users
    * `?filter[q]` - Filter by username
* `POST /api/users` - Register a user
* `GET /api/users/{id}` - Get a single user
* `PATCH /api/users/{id}` - Edit a user
* `DELETE /api/users/{id}` - Delete a user
* `POST /api/users/{id}/avatar` - Upload avatar
* `DELETE /api/users/{id}/avatar` - Remove avatar
* `POST /api/users/{id}/send-confirmation` - Send confirmation email

## Notifications

* `GET /api/notifications` - List notifications for the current user
* `POST /api/notifications/read` - Mark all notifications as read
* `PATCH /api/notifications/{id}` - Mark a single notification as read

## Discussions

* `GET /api/discussions` - List discussions
	* `?filter[q]` - Filter by username
* `POST /api/discussions` - Create a discussion
* `GET /api/discussions/{id}` - Show a single discussion
* `PATCH /api/discussions/{id}` - Edit a discussion
* `DELETE /api/discussions/{id}` - Delete a discussion

## Posts

* `GET /api/posts` - List posts, usually for a discussion
    * `?filter[discussion]` - Filter by discussion ID
    * `?filter[user]` - Filter by user ID
    * `?filter[number]` - Filter by number (position within the discussion)
    * `?filter[type]` - Filter by post type
* `POST /api/posts` - Create a post
* `GET /api/posts/{id}` - Show a single or multiple posts by ID
* `PATCH /api/posts/{id}` - Edit a post
* `DELETE /api/posts/{id}` - Delete a post

## Groups

* `GET /api/groups` - List groups
* `POST /api/groups` - Create a group
* `PATCH /api/groups/{id}` - Edit a group
* `DELETE /api/groups/{id}` - Delete a group

## Tags

* `GET /api/tags` - List tags
* `POST /api/tags` - Create a tag
* `PATCH /api/tags/{id}` - Edit a tag
* `DELETE /api/tags/{id}` - Delete a tag
* `POST /api/tags/order` - Re-order tags

## Admin

* `PATCH /api/extensions/{name}` - Toggle an extension
* `DELETE /api/extensions/{name}` - Uninstall an extension
* `POST /api/settings` - Update settings
* `POST /api/permission` - Update a permission
* `POST /api/logo` - Upload a logo
* `DELETE /api/logo` - Remove the logo
* `POST /api/favicon` - Upload a favicon
* `DELETE /api/favicon` - Remove the favicon
* `DELETE /api/cache` - Clear the cache
* `GET /api/mail/settings` - List available mail drivers, available fields and validation status
* `POST /api/mail/test` - Send test mail post

# References

* https://github.com/flarum/flarum.github.io/blob/20322c0e6011e4f304ae7e95f41594a0b086bc27/_docs/api.md - This document from the past helped a lot
* https://github.com/flarum/core/blob/master/src/Api/routes.php - Flarum API Routes
