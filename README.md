# <a name="jalpc"></a>Jalpc. [![Analytics](https://ga-beacon.appspot.com/UA-73784599-1/welcome-page)](https://github.com/Jack614/jalpc_jekyll_theme)

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)](https://opensource.org/licenses/mit-license.php)
[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)
[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/ellerbrock/open-source-badge/)

<http://www.jack003.com>

![Blog](readme_files/blog.gif)

* [Ad](#ad)
* [Getting Started](#getting-started)
    * [Fork, then clone](#fork-then-clone)
    * [Modify _config.yml](#modify-configyml)
    * [Index page](#index-page)
    * [Modify _data/\*.yml](#mofify-datayml)
    * [Jekyll Serve](#jekyll-serve)
    * [Using Github Pages](#using-github-pages)
    * [Categories in blog page](#categories-in-blog-page)
    * [Pagination](#pagination)
    * [Page views counter](#page-views-counter)
    * [Multilingual Page](#multilingual-page)
    * [Web analytics](#web-analytics)
    * [Comment](#comment)
    * [Share](#share)
    * [Search engines](#search-engines)
    * [Compress CSS and JS files](#compress-css-js)
    * [CNAME](#cname)
    * [Put in a Jalpc Plug](#put-in-a-jalpc-plug)
    * [Enjoy](#enjoy)
* [Upgrading Jalpc](#upgrading-jalpc)
    * [Ensure there's an upstream remote](#ensure-theres-an-upstream-remote)
    * [Pull in the latest changes](#pull-in-the-latest-changes)
* [Thanks to the following](#thanks-to-the-following)
* [Contributing](#contributing)

This is a simple, beautiful and swift theme for Jekyll. It's mobile first, fluidly responsive, and delightfully lightweight.

It's pretty minimal, but leverages large type and drastic contrast to make a statement, on all devices.

The landing page of the blog is multilingual page.

It is my pleasure to contact me, you can give me your website or some advice about my website. Let's build a wonderful Jekyll theme together!

## <a name="ad"></a>Ad

[Jalpc-A](https://github.com/Jack614/Jalpc-A): another Jekyll theme written by [AngularJS](https://angularjs.org/).

##  <a name="getting-started"></a>Getting Started

If you're completely new to Jekyll, I recommend checking out the documentation at <http://jekyllrb.com> or there's a tutorial by Smashing Magazine.

### <a name="fork-then-clone"></a> Fork, then clone

**Fork** the repo, and then **clone** it so you've got the code locally.

```
$ git clone https://github.com/<your githubname>/jalpc_jekyll_theme.git
$ cd jalpc_jekyll_theme
$ gem install jekyll # If you don't have jekyll installed
$ rm -rf _site && jekyll server
```

### <a name="modify-configyml"></a>Modify `_config.yml`

The _config.yml located in the root of the jalpc_jekyll_theme directory contains all of the configuration details for the Jekyll site. The defaults are:

``` yml
# Website settings
title: Jalpc
description: Jack's blog,use Jekyll and github pages.
keywords: 'Jack,Jalpc,blog,Jekyll,github,gh-pages'
baseurl: ''
url: 'http://www.jack003.com'
# url: "http://127.0.0.1:4000"
img_path: '/static/assets/img/blog'

# author
author:
  name: 'Jack'
  first_name: 'Kun'
  last_name: 'Jia'
  cv: 'http://cv.jack003.com'
  email: 'me@jack003.com'
  facebook_username: 'jiakunnj'
  github_username: 'JiaKunUp'
  avatar: '/static/img/landing/Jack.jpg'
...
```

### <a name="#index-page"></a>Index page

The index page is seprated into several sections and they are located in `_includes/sections`,the configuration is in `_data/landing.yml` and section's detail configuration is in `_data/*.yml`.

#### <a name="mofify-datayml"></a>Modify `_data/*.yml`

These files are used to dynamically render pages, so you almost don't have to edit *html files* to change your own theme, besides you can use `jekyll serve --watch` to reload changes.

The following is mapping between *yml file* to *sections*.

* landing.yml ==> index.html
* language.yml ==> index.html
* careers.yml  ==>  _includes/sections/career.html
* skills.yml  ==>  _includes/sections/skills.html
* projects.yml  ==>  _includes/sections/projects.html
* links.yml  ==>  _includes/sections/links.html

This *yml file* is about blog page navbar

* blog.yml ==> _includes/header.html

The following is mapping between *yml file* to *donation*

* donation.yml ==> blog/donate.html
* alipay.yml  ==>  blog/donate.html
* wechat_pay.yml ==> blog/donate.yml

### <a name="jekyll-serve"></a>Jekyll Serve

Then, start the Jekyll Server. I always like to give the --watch option so it updates the generated HTML when I make changes.

```
$ jekyll serve --watch
```

Now you can navigate to localhost:4000 in your browser to see the site.

### <a name="using-github-pages"></a>Using Github Pages

You can host your Jekyll site for free with Github Pages. Click [here](https://pages.github.com) for more information.

A configuration tweak if you're using a gh-pages sub-folder

In addition to your github-username.github.io repo that maps to the root url, you can serve up sites by using a gh-pages branch for other repos so they're available at github-username.github.io/repo-name.

This will require you to modify the _config.yml like so:

``` yml
# Website settings
title: Website Name
description: Website description
keywords: 'Website keywords'
baseurl: '' # if you have suburl as homepage like '/homepage', please change it to '/homepage'
url: 'https://github-username.github.io'
# url: "http://127.0.0.1:4000"
img_path: '/static/assets/img/blog'

# author
author:
  name: 'Jack'
  first_name: 'Kun'
  last_name: 'Jia'
  cv: 'http://cv.jack003.com'
  email: 'me@jack003.com'
  facebook_username: 'jiakunnj'
  github_username: 'JiaKunUp'
  avatar: '/static/img/landing/Jack.jpg'
...
```

If you start server on localhost, you can turn on `# url: "http://127.0.0.1:4000"`.

### <a name="categories-in-blog-page"></a>Categories in blog page

In blog page, we categorize posts into several categories by url, all category pages use same template html file - `_includes/category.html`.

For example: URL is `http://127.0.0.1:4000/python/`. In `_data/blog.yml`, we define this category named `Python`, so in `_includes/category.html` we get this URL(/python/) and change it to my category(Python), then this page are posts about **Python**. The following code is about how to get url and display corresponding posts in  `_includes/category.html`.

```html
<div class="row">
    <div class="col-lg-12 text-center">
        <div class="navy-line"></div>
        {% assign category = page.url | remove:'/' | capitalize %}
        {% if category == 'Html' %}
        {% assign category = category | upcase %}
        {% endif %}
        <h1>{{ category }}</h1>
    </div>
</div>
<div class="wrapper wrapper-content  animated fadeInRight blog">
    <div class="row">
        <ul id="pag-itemContainer" style="list-style:none;">
            {% assign counter = 0 %}
            {% for post in site.categories[category] %}
            {% assign counter = counter | plus: 1 %}
            <li>
```

### <a name="pagination"></a>Pagination

The pagination in jekyll is not very perfect,so I use front-end web method,there is a [blog](http://www.jack003.com/html/2016/06/04/jekyll-pagination-with-jpages.html) about the method and you can refer to [jPages](http://luis-almeida.github.io/jPages).

### <a name="page-views-counter"></a>Page views counter

Many third party page counter platforms are too slow,so I count my website page view myself,the javascript file is [static/js/count.min.js](https://github.com/JiaKunUp/jalpc_jekyll_theme/blob/gh-pages/static/js/count.min.js) ([static/js/count.js](https://github.com/JiaKunUp/jalpc_jekyll_theme/blob/gh-pages/static/js/count.js)),the backend API is written with flask on [Vultr VPS](https://www.vultr.com/), detail code please see [jalpc-flask](https://github.com/JiaKunUp/jalpc-flask).

### <a name="multilingual-page"></a>Multilingual Page

The landing page has multilingual support with the [i18next](http://i18next.com) plugin.

Languages are configured in the `config.yml` file.

> If you don't need this feature, please clear content in file `_data/language.yml` and folder `static/locales/`.

#### Step 1

Add a new language entry

```yml
languages:
  - locale: 'en'
    flag: 'static/img/flags/United-States.png'
  - locale: '<language_locale>'
    flag: '<language_flag_url>'
```

#### Step 2

Add a new json (`static/locales/<language_locale>.json`) file that contains the translations for the new locale.

Example `en.json`

```json
{
  "website":{
    "title": "Jalpc"
  },
  "nav":{
    "home": "Home",
    "about_me": "About",
    "skills": "Skills",
    "career": "Career",
    "blog": "Blog",
    "contact": "Contact"
  }
}
```

#### Step 3

Next you need to add html indicators in all place you want to use i18n.(`_includes/sections/*.html` and `index.html`)

Example:

``` html
<a class="navbar-brand" href="#page-top" id="i18_title"><span data-i18n="website.title">{{ site.title }}</span></a>
```

#### Step 4

Next you need to initialise the i18next plugin(`index.html`):

``` javascript
$.i18n.init(
    resGetPath: 'locales/__lng__.json',
    load: 'unspecific',
    fallbackLng: false,
    lng: 'en'
}, function (t)
    $('#i18_title').i18n();
});
```

### <a name="web-analytics"></a>Web analytics

I use [Baidu analytics](http://tongji.baidu.com/web/welcome/login), [Google analytics](https://www.google.com/analytics/) and [GrowingIO](https://www.growingio.com/) to do web analytics, you can choose either to realize it,just register a account and replace id in `_config.yml`.

### <a name="comment"></a>Comment

I use [Changyan](http://changyan.kuaizhan.com/) and [Disqus](https://disqus.com/) to realize comment.

#### Changyan
To configure Changyan, get the appid and conf in <http://changyan.kuaizhan.com/>. Then, in `_config.yml`, edit the changyan value to enable Changyan.

#### Disqus
To configure Disqus,you should set disqus_shortname and get public key and then, in `_config.yml`, edit the disqus value to enable Disqus.

### <a name="share"></a>Share

I use [bshare](http://www.bshare.cn/) to share my blog on other social network platform. You can register a count and get your share uuid.

### <a name="search-engines"></a>Search engines

I use javascript to realize blog search,you can double click `Ctrl` or click the icon at lower right corner of the page,the detail you can got to this repo: <https://github.com/androiddevelop/jekyll-search>.

Just use it.

![search](readme_files/search.gif)

### <a name="compress-css-js"></a>Compress CSS and JS files

All CSS and JS files are compressed at `/static/assets`.

I use [UglifyJS2](https://github.com/mishoo/UglifyJS2) and [clean-css](https://github.com/jakubpawlowicz/clean-css) to compress CSS and JS files. If you want to custom CSS and JS files, you need to do the following:

1. Install **UglifyJS2** and **clean-css**: `npm install -g uglifyjs; npm install -g clean-css`, then run `npm install` at root dir of project.
2. Compress script is **build.js**, index page has its own CSS and JS compressed files, they are :
  * **app-index-xxx.min.css**
  * **app-index-xxx.min.js**
  * **i18-xxx.min.js**

  other pages are
  * **app-xxx.min.css**
  * **app-xxx.min.js**
  * **jPage-xxx.min.js**

  404 page are
  * **fof-xxx.min.css**
  * **fof-xxx.min.js**

  **xxx** is date when you compress your files.
3. If you want to add/remove CSS/JS files, just edit **build.js**, and run `npm run compress` at root dir of project.
4. At last, edit `_includes/head.html` and `_includes/index_head.html` change CSS and JS files link to you generated just now.

### <a name="cname"></a>CNAME

Replace your website domain in **CNAME** file.

### <a name="put-in-a-jalpc-plug"></a>Put in a Jalpc Plug

If you want to give credit to the Jalpc theme with a link to my personal website <http://www.jack003.com>, that'd be awesome. No worries if you don't.

### <a name="enjoy"></a>Enjoy

Hope you enjoy using Jalpc. If you encounter any issues, please feel free to let me know by creating an issue. I'd love to help.

## <a name="upgrading-jalpc"></a>Upgrading Jalpc

Jalpc is always being improved by its users, so sometimes one may need to upgrade.

### <a name="ensure-theres-an-upstream-remote"></a>Ensure there's an upstream remote

If `git remote -v` doesn't have an upstream listed, you can do the following to add it:

```
git remote add upstream https://github.com/Jack614/jalpc_jekyll_theme.git
```

### <a name="pull-in-the-latest-changes"></a>Pull in the latest changes

```
git pull upstream gh-pages
```

There may be merge conflicts, so be sure to fix the files that git lists if they occur. That's it!

## <a name="thanks-to-the-following"></a>Thanks to the following

* [Jekyll](http://jekyllrb.com)
* [Bootstrap](http://www.bootcss.com)
* [jPages](http://luis-almeida.github.io/jPages)
* [i18next](http://i18next.github.io/i18next)
* [pixyll](https://github.com/johnotander)
* [androiddevelop](https://github.com/androiddevelop)
* [UglifyJS2](https://github.com/mishoo/UglifyJS2)
* [clean-css](https://github.com/jakubpawlowicz/clean-css)

## <a name="contributing"></a>Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
