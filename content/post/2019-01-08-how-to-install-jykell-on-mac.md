---
layout: post
title:  "How to install jykell on mac!"
date:   2019-01-08 18:46:41 +0800
categories: jekyll update
---

如何在mac上安装jykell

1.安装rvm

    curl -L get.rvm.io | bash -s stable

    source ~/.rvm/scripts/rvm

    rvm -v

2.安装ruby

    rvm install 2.6.0

    rvm list

3.安装jykell

    gem source

    gem install jekyll

    jekyll -version

4.安装bundle

    gem install bundle

    运行bundle，安装Gemfile里的插件

    bundle install

5.初始化web项目

    jekyll new r2ys-site

    cd r2ys-site/

6.本地localhost:4000测试

    jekyll serve
    jekyll serve --watch --baseurl '/blog'

7.内容生成

    jekyll build


You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight java %}
System.out.prinln("");
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

{% highlight oc %}
NSString *str = @"suck";
{% endhighlight %}

![avatar]({{ site.baseurl }}/assets/201812121137485b3b6458f4023.jpg)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
