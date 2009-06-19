ThinkingSphinx
--------------

### Error: The index will not build

    ERROR: index 'model_core': sql_range_query: Unknown column 'model.attr' in 'field list'
    
### Action
* Ensure that your define_index is defined after any associations used in the
index, otherwise it will try and find the field on the current model
* Run `rake ts:config`
