# Solidus Drop Ship

[![Build Status](https://travis-ci.org/rohitpai-na/solidus_drop_ship.png)](https://travis-ci.org/rohitpai-na/solidus_drop_ship)
[![Code Climate](https://codeclimate.com/github/rohitpai-na/solidus_drop_ship.png)](https://codeclimate.com/github/rohitpai-na/solidus_drop_ship)
[![Dependency Status](https://gemnasium.com/rohitpai-na/solidus_drop_ship.png?travis)](https://gemnasium.com/rohitpai-na/solidus_drop_ship)

What is drop shipping?

"Drop shipping is a supply chain management technique in which the retailer does not keep goods in stock, but instead transfers customer orders
and shipment details to either the manufacturer or a wholesaler, who then ships the goods directly to the customer." - [wikipedia](http://en.wikipedia.org/wiki/Drop_shipping)

So the main goal with solidus_drop_ship is to link products to suppliers and forward orders to the appropriate suppliers.

Once an order is placed for a product that belongs to a supplier a shipment is created for the product's supplier.
This shipment is then sent to the supplier (via Email by default). The supplier then follows a link to the shipment
within the email where they are prompted to confirm the shipment.

Solidus Drop Ship used with [Solidus Marketplace](https://github.com/rohitpai-na/solidus_marketplace) allows multiple suppliers to offer products at different prices making solidus a multi-vendor marketplace.
.


Installation
------------

Here's how to install solidus_drop_ship into your existing spree site AFTER you've installed Spree:

Add the following to your Gemfile:

    gem 'solidus_drop_ship', github: 'rohitpai-na/solidus_drop_ship'

Make your bundle happy:

    bundle install

Now run the generator:

    rails g solidus_drop_ship:install

Then migrate your database if you did not run during installation generator:

    bundle exec rake db:migrate

And reboot your server:

    rails s

You should be up and running now!

Sample Data
-----------

If you'd like to generate sample data, use the included rake tasks:

```shell
rake spree_sample:load               # Loads sample data into the store
rake spree_sample:suppliers          # Create sample suppliers and randomly link to products
rake spree_sample:drop_ship_orders   # Create sample drop ship orders
```

Demo
----

You can easily use the spec/dummy app as a demo of spree_drop_ship. Just `cd` to where you develop and run:

```shell
git clone git://github.com/rohitpai-na/solidus_drop_ship.git
cd spree_drop_ship
bundle install
bundle exec rake test_app
cd spec/dummy
rake db:migrate db:seed spree_sample:load spree_sample:suppliers spree_sample:drop_ship_orders
rails s
```

Testing
-------

Be sure to bundle your dependencies and then create a dummy test app for the specs to run against.

```shell
bundle
bundle exec rake test_app
bundle exec rspec spec
```

Credits
-------

This is forked off of the 2-4-stable branch of [Spree Drop Ship](https://github.com/spree-contrib/spree_drop_ship/tree/2-4-stable) and modified to work with [Solidus](https://github.com/solidusio/solidus). Credit to the original author of the spree_drop_ship, Jeff Dutil.

Copyright (c) 2012-2014 Jeff Dutil, released under the [New BSD License](https://github.com/jdutil/spree_drop_ship/tree/master/LICENSE).
