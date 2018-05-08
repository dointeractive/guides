# Rails Style Guide

  1. [Routes](#routes)
  2. [Controllers](#controllers)
  3. [Concerns](#concerns)

## Routes
  * Generating resourceful routes prefer `only` over `except`, `only` is easier to read, because you clearly see which routes will be generated.


## Controllers
  * Use instance variables only where it's absolutely needed.
    ```Ruby
    # don't
    class AddressesController < ApplicationController
      def index
        @user = User.find params[:id]
        @addresses = user.addresses
      end
    end

    ## app/views/addresses/index.html.slim
    - @addresses.each do |address|
      = address.street


    # do
    class AddressesController < ApplicationController
      def index
        user = User.find params[:id]
        @addresses = user.addresses
      end
    end
    ```


  * Avoid using `before_action/before_filter` for loading data. It's extremely frustrating, when instance variables appears from nowhere and used at random places at code.
    ```Ruby
    # don't
    class AddressesController < ApplicationController
      before_action :load_data

      def update
        @address.update params[:address]
      end

      private

      def load_data
        @address = Address
          .includes(:user)
          .find params[:id]
      end
    end

    # do
    class AddressesController < ApplicationController

      def update
        @address = get_address
        @address.update params[:address]
      end

      private

      def get_address
        Address
          .includes(:user)
          .find params[:id]
      end
    end

    # do
    class AddressesController < ApplicationController
      # for simple cases:
      def update
        @address = Address.find params[:id]
        @address.update params[:address]
      end
    end
    ```

## Concerns

* Use properly naming for your concerns. Name should reflect what is happening.

  Examples - concern for track changes on model

  ```ruby
  module ChangesTracking
    extend ActiveSupport::Concern

    attr_accessor :changes_history

    included do
      after_initialize do
        self.changes_history ||= []
      end

      after_save do
        self.changes_history << saved_changes
      end
    end
  end
  ```

  Name like:
  - `ChangesTracking` - normal
  - `TrackChanges` - not normal
  - `Trackable or Changeable` - bad
