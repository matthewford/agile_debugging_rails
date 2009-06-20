ThinkingSphinx
--------------

### Error: sql_range_query: Unknown column
The index will not build as an attribute is not found on the model

    ERROR: index 'model_core': sql_range_query: Unknown column 'model.attr' in 'field list'
    
### Action
* Ensure that your define_index is defined after any associations used in the
index, otherwise it will try and find the field on the current model
* Run `rake ts:config`

### Error: Warning: Error loading model
When you generate your search configuration file it says there is an error 
loading the models and the generated config is empty. When `rake ts:in`
is run there will be the following error:
    
	FATAL: no sources found in config file
	
### Action
Check your define_index methods that attributes or fields do not use a 
reserved name such as `tags.id`, if this is the case use a symbol:

    has tags(:id), :as => :tag_ids

	