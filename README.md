# blog
> A jekyll site.

This is a wrapper on the jekyll minima theme. You can use it by cloning the repo.

## Usage

Make sure you have jekyll and minima installed. Then, clone the repo and put it
on top of current file structure of jekyll.

## Features

- **Adding posts in different sections**: One can add posts in two different sections, namely 
`Infocus` and `Top Posts`. In order to do that simply add `infocus` or `top_posts` inside your
post content front matter under `categories` ([example](https://raw.githubusercontent.com/ayan-b/blog/master/_posts/2018-08-30-Computer-An-Introduction.md)).

- **Tags**: You can add tags to all posts. In order to do that, simply add the tag in the front
matter of your post ([example](https://raw.githubusercontent.com/ayan-b/blog/master/_posts/2018-08-30-Computer-An-Introduction.md)). Once, the tag has been added make sure you have a markdown file of same name 
inside the `tag` directory.

- **Intro Pic**: You can also add a picture for your post and it will be shown on the top of your
post and in the home page. Simply add the link of the picture in the front mattter.

- **Related Posts**: If you set `related-post` as true, some posts will be mentioned at the bottom 
of your post by matching the tags.

- **Recommended Posts**: You can add `recommended-post`s for your blog post in hyperlink format ([example](https://raw.githubusercontent.com/ayan-b/blog/master/_posts/2018-08-25-The-Internet.markdown)).

## TODO

- Release as a gem.

## Contributing

Want to contribute? Awesome! Please have a look at our [Contributing](./CONTRIBUTING.md) page.
