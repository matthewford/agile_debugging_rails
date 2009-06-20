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
Calling `model.save` returns `false` but the model is valid.

### Action
Check for before_* callbacks that are returning false, as this will halt all
further callbacks and not save the model. This can occur when the last line in
in a callback sets an attribute to false.

	before_update :need_to_set_attribute
	
	def need_to_set_attribute
	  self.never_updated = false
	 end
	 
One way to avoid this is to make sure that all callbacks return true. In 
the previous example this could be done by using `update_attribute` (calls 
`save(false)` to skip validations) or as Ruby sets the return value of methods
as their last expression, simply add `true` before ending the method.

Another way to prevent this is to call `.save!` and rescue the 
`ActiveRecord::RecordNotSaved` exception that occurs when a callback returns 
`false`.

* * *

### Error: Mysql duplicate key
    ActiveRecord::StatementInvalid: Mysql::Error: Duplicate entry for key 'PRIMARY

### Action
* Duplicate primary keys are likely to occur with `has_and_belongs_to_many`
relations check the join table does *not* have an id column
* use :id => false in future migrations for join tables