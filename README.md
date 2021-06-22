# Flask Code Cheat Sheet

## Table of Contents
- [Mix Function](#mix-function)
- [Cookies and Session](#cookies-and-session)
- [Handling Error Page](#handling-error-page)

## Mix Function
- Redirect to other URL
```python
from flask import redirect, url_for
@app.route('/redirect')
    return redirect(url_for('user.registration'))
```

## Cookies and Session
- Set Cookies
```python
from flask import render_template, make_response
import datetime

@user.route('/set_cookie')
def cart():
    # Render template
    template = render_template('user/set_cookie.html')
    resp = make_response(template)
    
    # Add expiry date for cookies. Expiry date is optional.
    expire_date = datetime.datetime.now()
    expire_date = expire_date + datetime.timedelta(days=7)
    
    # Add/update cookies
    resp.set_cookie('product_name', 'Fujifilm X100T', expires=expire_date)
    resp.set_cookie('qty', '2')
    
    return resp
```

## Handling Error Page
- Change the number based on [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes). No need to set the route handling.
```python
from flask import render_template

def page_not_found(e):
    # note that we set the 404 status explicitly
    return render_template('error/404.html'), 404

def page_forbidden(e):
    return render_template('error/403.html'), 403
```

