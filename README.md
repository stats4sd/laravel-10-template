r# Laravel Template

This repo is a template for new projects using:

- Laravel 10
- Backpack 6
- Backpack Pro (the requirement is there in the composer.json file. Remove it if you don't have the licence or don't want to use closed-source packages)

## Setup Process

To start using this template for a new application:

1. Clone this repository, e.g. `git clone git@github.com:stats4sd/laravel-10-template.git my-new-laravel-app`
2. Remove the remote from the local repo: 
   - `cd my-new-laravel-app`
   - `git remote remove origin`
3. Add a new remote repo. E.g:
   - Create a new empty repository on Github
   - Follow the instructions given on Github to add that as a new remote to your local repository.


## How is this template different from a clean installation? 

The template is intended as a quick-start to Stats4SD projects, and is opinionated in a few ways:

### Authentication
This template was setup using Laravel Breeze for the authentication. The Backpack auth routes have not been enabled, and instead Backpack redirects / defers to the routes setup in the `routes/auth.php` file.

**Changes**: 

- The Logout button in the Backpack menu has been changed from an <a> tag to a form, because the default logout route from Breeze requires a POST request.
  - This change is in Theme Tabler. If you change backpack themes, you will need to make this change again in your chosen theme.
- The app redirects from `/` to `/admin` by default, assuming that you want to use Backpack as the main UI. This can be changed if you need a separate front-end. 

### Frontend Assets
Vite is set up as the default compiler. There are 2 sets of javascript and scss files. 
- `backpack.js` + `backpack.scss`, which get included in all backpack-rendered pages, to allow quick modifications to the theme or the addition of custom JS to the whole admin panel.
- `app.js` + `app.scss`, which are included in the `views/layouts` blade templates for use in a separate front-end if required.

### Front-end frameworks 

- Backpack's Theme Tabler uses Bootstrap 5, so the easiest approach to styling the admin panel is to write Bootstrap-compatible css. 
- The front-end pages, including the Authentication views (login, password reset etc) use Tailwind. If needed, you can change this to Bootstrap by modifying the `views/layouts/` and `views/auth` blade templates.

### VueJS

There is a `vuedefault.js` file that includes the boilerplate for adding VueJS components to pages. We often have a few pages that include a VueJS component, so you could create one vue setup file for each page that uses it, and only register the components required for that page. That way, Vue is not loaded when it is not needed. Alternatively, if Vue is used everywhere, one single setup file that registers *all* the components will be fine. 
