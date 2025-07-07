# laravel-best-practices

## Blade: {!! !!} and XSS Attack

Avoid using {!! !!} to prevent XSS attacks where malicious code can be inserted within the unescaped data.

As much as possible use the escaped syntax: {{}}

## Don't use $request->all() when storing data

Filter form first using $request->validate(), $request->only(), or $request()->except() before storing.

## File Upload: Client Data

The following methods are considered unsafe and can be tampered with:

  ```php
    $file->getClientOriginalName();
    $file->getClientOriginalExtension();
  ```

It is recommended to use the following methods instead:

  ```php
    $file->hashName();
    $file->extension();
  ```

## .env in production

Remember to set the following in your .env before deploying in production:

  ```.env
    ...
    APP_ENV=production
    ...
    APP_DEBUG=false
    APP_URL=https://your-app-url
  ```
