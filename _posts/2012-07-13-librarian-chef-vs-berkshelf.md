---
layout: post
title: "librarian-chef vs. berkshelf"
date: 2012-07-13 18:55
comments: true
tags:
- chef
- productivity
---

This is a brief comparison between [librarian-chef](https://github.com/applicationsonline/librarian) an [berkshelf](https://github.com/RiotGames/berkshelf) to point out the main differences in *managing cookbooks*. Please refer to [the offical announcement for berkshelf](http://lists.opscode.com/sympa/arc/chef/2012-06/msg00294.html) for a in-depth introduction / comparison for all features.

## Rational

I'm a big fan of librarian-chef and I currently use it in every chef-driven project.

It helped my a lot taking back control when I got -confused- overwhelmed by cookbooks. Thanks to librarian-chef I finally could seperate my patched cookbooks, get rid of git-submodules in a sensible way with an easy to manage `Cheffile` that can be stored in version control. Everything was wunderbar!

When I first heard of berkshelf [via this blog post](http://devopsanywhere.blogspot.it/2012/07/stash-those-logs-set-up-logstash.html) I got slightly [confused](https://twitter.com/ctrabold/statuses/220093903653699584): *Is someone re-inventing the wheel here?*
It turned out that I should have read [the offical announcement for berkshelf](http://lists.opscode.com/sympa/arc/chef/2012-06/msg00294.html) before [posting my Tweet](https://twitter.com/ctrabold/statuses/220093903653699584) :) Hope this post helps you as well.

## What is the difference?

Both berkshelf and librarian-chef download cookbooks from various locations. If that sounds totally new to you I highly encourage you to adopt either one of thoses tools to your workflow.
The main difference is where and how the cookbook files are stored in the current repository / project:

### librarian-chef

[librarian-chef](https://github.com/applicationsonline/librarian) will load all cookbooks defined in a `Cheffile` to a `cookbooks`folder within the *current* directory.

It also helps you keeping the cookbooks folder in shape by providing commands to show you outdated cookbooks etc. To do so it caches the checksums of theses files in a tmp folder within the current folder.

I did not find a way to change the default "cookbooks" folder which can be a bit painful if you want a different folder strucuture.

### berkshelf

[berkshelf](https://github.com/RiotGames/berkshelf) (by default) loads all cookbooks from the Berksfile into one centralized repository in `~/.berkshelf` (customize via `BERKSHELF_PATH`) and NOT into the current directory.

After downloading all the cookbooks and their dependencies you can *link* those into *whatever* folder you like with `berks install --shims your_desired_path`. Default is `cookbooks`.
Berkshelf creates *hard links* to cookbooks in the repository. You have to take care of outdated cookbooks etc.

## Final thoughts

I'm very new to Berkshelf (just installed the gem, run the examples provided on [their website](http://berkshelf.com/)) and yes it looks very promising.

Berkshelf's aproach with ONE repository that builds "the single source of truth" for all your chef-repos makes sense to me because these cookbooks should never change and kept away from your modifications. And Berkshelf does not spoil the repo with an "tmp" folder which confused some of my colleagues. Also the other features like "metadata" sound cool.

Again: Please refer to [the offical announcement for berkshelf](http://lists.opscode.com/sympa/arc/chef/2012-06/msg00294.html) for a in-depth introduction for all features.
Although I found the installation of berkshelf a bit more complicated than librarian-chef (because of gecode) I will definitly dig deeper into Berkshelf.

The only thing I don't really get is the name "Berkshelf" / "Berksfile" and I could't find a proper translation. Yeah call me picky :)

Maybe a native speaker can give me a hint on that one :)

I'm very interested in your experiences with either of these tools.

– Cheers Christian
