Controllers
-----------

### Error: Flash messages occuring twice
The flash message is not cleared between requests

### Action
    
    flash.now[:notice] = "This is a flash notice, that won't stick around"