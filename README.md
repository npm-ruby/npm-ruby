## npm-ruby

Having spent the last year or so writing Node.js applications means that we now fully understand that web development in a dynamic language (JavaScript). At the core of our hearts we are true Rubyists, but we’ve come to realize that development in a dynamic language (JavaScript) on a VM that is incredibly fast (V8) is much faster than Ruby. (Or Python, or Perl for that matter).

The philosophy behind the Node ecosystem of using a single programming language to drive a whole application was a great inspiration to us. Using JavaScript on a web server as well as the browser reduces the impedance mismatch between the two programming environments which can communicate data structures via JSON that work the same on both sides of the equation. This also means that the __DRY principle is embodied in the programming language itself__.

NPM (the Node package manager) has been an invaluable tool for us, the number of available packages has been increasing and now the ecosystem covers a variety of use cases. From super fast [CSS preprocessing](https://learnboost.github.io/stylus/), [static analysis](https://www.npmjs.com/package/jshint) to even a [full featured operating system](https://github.com/NodeOS/NodeOS). We’ve come to realize that there’s a lot more `npm` offers and it has become the predominant packaging solution for the entire web.

On the other hand, RubyGems have been empowering our Rails and web applications for more than 2 decades now, however they seriously lack modern packaging features and as of today, there’s far less available Ruby packages than npm packages. To allow the Ruby community to compete with the Node ecosystem, we’ve been working extremely hard to bring a new, modern and efficient solution to the table.

## Announcing NPM for Ruby

npm-ruby allows you to use npm functionality in your Ruby/Rails applications. It extends Rubygems with the ability to load npm packages so that you can make use of thousands of available npm packages today. npm packages are superior to RubyGems in many ways, which means better stability and less fuss when developing your applications.

## Features

### No more dependency hell

Ever had to deal with the following issues in Bundler?

```
Bundler could not find compatible versions for gem “json”:
  In Gemfile:
    chef (~> 10.26) ruby depends on
      json (<= 1.7.7, >= 1.4.4) ruby

    berkshelf (~> 2.0) ruby depends on
      json (1.8.0)
```

npm is built on top of the CommonJs module system, which has been designed with real modularity and encapsulation in mind. npm packages employ a recursive dependency tree, by installing each and every one of their dependencies in their own `node_modules` sub directory. This means you no longer need to worry about version dependency problems and can use multiple versions of a single gem.

__NOTE: This also allows you to partially upgrade your Rails application as you go and keep deploying at the same time.__

### Faster JavaScript runtime

Remember the times you wanted to use Opal to parse Ruby code to JavaScript? npm for Ruby now has __Opal built in__, in fact it offers an option to permanently cross compile your whole local RubyGems repository to JavaScript. This means your app does not depend on runtime compilation anymore and it becomes fast. Blazing fast.

### Improved efficiency

No tests needed as each and every module in Node are small and have no dependency problems so you can focus on your app instead of spending time on writing tests. Write code in a week and have it running in production.

## Installation

* Add this line to your application's `Gemfile`:

```ruby
gem 'npm-ruby'
```

* Delete your `Gemfile.lock` (as it’s no longer necessary)

## Usage

Just add `npm` dependencies into your `package.json` as you normally would. Requiring them in your Ruby apps is the same as with any other package, `npm-ruby`s internal transpiler takes care of the rest.

## Contributing

1. Fork it ( https://github.com/[my-github-username]/npm-ruby/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
