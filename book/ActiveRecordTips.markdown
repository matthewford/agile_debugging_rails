ActiveRecord Tips
-----------------

### Law of Demeter

The [Law of Demeter][] in a Rails context can be interpreted as, do not
chain multiple method calls, for example:

    @user.account.company_name
    
You can make use of the delegate method to expose the methods of the
associated models on the current model.

    class User < ActiveRecord::Base
      belongs_to :account
      
      delegate :company_name, :to => :account
    end
    
The first example can now be rewritten as:

    @user.company_name

If your association can be `nil` set the following option,
`:allow_nil => true` otherwise an exception will be raised

[Law of Demeter]:http://en.wikipedia.org/wiki/Law_of_Demeter
