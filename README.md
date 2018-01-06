# cells-hamlit2 [![Build Status](https://travis-ci.org/hamlit/cells-hamlit2.svg?branch=master)](https://travis-ci.org/hamlit/cells-hamlit2)

Temporary workaround version of [cells-hamlit](https://github.com/trailblazer/cells-hamlit) until https://github.com/trailblazer/cells-hamlit/issues/6 is closed.


## Installation

Add these lines to your application's Gemfile:

```ruby
gem "cells-hamlit2"
gem "hamlit"
```

If you use rails, add `gem "cells-rails"`, too.

## HTML Escaping

Cells doesn't escape except when you tell it to do. However, you may run into problems when using Rails helpers. Internally, those helpers often blindly escape. This is not Cells' fault but a design flaw in Rails.

As a first step, try this and see if it helps.

```ruby
class SongCell < Cell::ViewModel
  include ActionView::Helpers::FormHelper
  include Cell::Hamlit # include Haml _after_ AV helpers.

  # ..
end
```

If that doesn't work, [read the docs](http://trailblazerb.org/gems/cells/cells4.html#html-escaping).

## Dependencies

This gem works with Tilt 1.4 and 2.0, and hence allows you to use it from Rails 3.2 upwards.
