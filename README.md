# Laravel Template

This repo is a template for new projects using:

- Laravel 10
- Backpack 6
- Backpack Pro (the requirement is there in the composer.json file. Remove it if you don't have the licence or don't want to use closed-source packages)

## Setup Process

### Authentication
This template was setup using Laravel Breeze for the authentication. The Backpack auth routes have not been enabled, and instead Backpack redirects / defers to the routes setup in the `routes/auth.php` file.

**Changes**: 

- The Logout button in the Backpack menu has been changed from an <a> tag to a form, because the default logout route from Breeze requires a POST request.
  - This change is in Theme Tabler. If you change backpack themes, you will need to make this change again in the other theme.
- The app redirects from `/` to `/admin` by default, assuming that you want to use Backpack as the main UI. This can be changed if you want to have a separate front-end. 

## Frontend Assets
Vite is setup as the default compiler. There are 2 sets of javascript and scss files. 
- `backpack.js` + `backpack.scss`, that get included in all backpack-rendered pages.
- `app.js` + `app.scss`, which are included in the `views/layouts` blade templates for use in a separate front-end.

Backpack's Theme Tabler uses Bootstrap 5, so any additional CSS written for the backpack panels should be compatible with Bootstrap. 

In this template, the front-end pages, including the Authentication views (login, password reset etc) use Tailwind. You can change this to Bootstrap by modifying the `views/layouts/` blade templates. 
