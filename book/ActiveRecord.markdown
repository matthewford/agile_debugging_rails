ActiveRecord
------------

### Error: undefined method
    undefined method `attribute' for #<Object:0xb70fad18>

### Action
* Run/write migrations
* Define attribute in model
* If object comes from a session ensure you are not just passing an integer 
`@object = MyModel.find(session[:my_model])` not `@object = session[:my_model]`

* * *

### Error: model not saving
A model will not save but is valid

### Action
* check custom callbacks, returning false (ie, .save) will halt the chain,
 instead use save! and rescue the exception

* * *

### Error: Mysql duplicate key
    ActiveRecord::StatementInvalid: Mysql::Error: Duplicate entry for key 'PRIMARY

### Action
* Duplicate primary keys are likely to occure with `has_and_belongs_to_many`
relations check the join table does *not* have an id column
* use :id => false in future migrations for join tables