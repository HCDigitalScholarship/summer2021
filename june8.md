June 8 ~ Forms
============================


[w3schools](https://www.w3schools.com/html/html_forms.asp)  
[Django docs forms](https://docs.djangoproject.com/en/3.0/topics/forms/)

```html
<form>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname">
</form>
```



### GET Form 


```html
<form method="get">
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname" value="John"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname" value="Doe">
  <input type="submit" value="Submit">
</form>
```

*note the GET requests in the logs*

In Django, add to `def index(request)`:
```python
if request.GET:
    context = {}
    first_name = request.GET.get('fname', None)
    last_name = request.GET.get('lname', None)
    context['message'] = f"Hello {first_name} {last_name}"
    return render(request, 'index.html', context)
else:
    return render(request, "index.html",)
```

FastAPI version would be: 
```python
app.get('/')
async def got_ya(fname:str, lname:str):
  return f"Hello {fname} {lname}"
```

add to index.html
```html
<script>
    {% if message%}
    alert('{{ message }}');
    {% endif %}
</script>
```




### POST Form 

change `index.html`
```html
<form method="post">
{% csrf_token%}
...
</form>
```
In Django:
change `views.py`
change GET to POST

In FastAPI:
```python
@app.post("/")
async def post_me(
    # field name, field type, get from Form(...) is required or Form(None) not required
    lang_name: str = Form(...),
    lang_code: str = Form(...),
    this_is_optional: Optional[str] = Form(None),
    and_files: List[UploadFile] = File(None),
):
```


### Django Forms 

`create a new file former_app/forms.py`

```python
from django import forms

class NameForm(forms.Form):
    first_name = forms.CharField(label='first_name', max_length=100)
    last_name = forms.CharField(label='last_name', max_length=100)
```

now edit `views.py`

```python
from former_app.forms import NameForm

def index(request):
    if request.POST:
        form = NameForm(request.POST)
        if form.is_valid():
          context = {}
          context['form'] = form
          first_name = form.cleaned_data['first_name']
          last_name = form.cleaned_data['last_name']
          context['message'] = f"Hello {first_name} {last_name}"
          return render(request, 'index.html', context)
    else:
        form = NameForm()
        return render(request, "index.html", {"form": form})
```
now edit `index.html`

```html
<form method="post">
{% csrf_token%}
  {{ form }}
  <input type="submit" value="Submit">
</form>
```
more on [Django forms](https://docs.djangoproject.com/en/3.0/topics/forms/)


--- 

<img src="https://target.scene7.com/is/image/Target/GUEST_4c383d0d-52f3-4190-adad-00dd21163e7f?wid=488&hei=488&fmt=pjpeg">

- Mad Libs is a game where you fill in missing words.  The player is asked to name an "adjective" or "verb."  The response is placed in the text to create funny stories.   
- Use the marked-up text below

```html
<p>A vacation is when you take a trip to some <span id="1" class="adjective"></span> place
with your <span id="2" class="adjective"></span> family. Usually you go to some place
that is near a/an <span id="3" class="noun"></span> or up on a/an <span id="4" class="noun"></span>.
A good vacation place is one where you can ride <span id="5" class="plural_noun"></span>
or play <span id="6" class="game"></span> or go hunting for <span id="7" class="plural_noun"></span>. I like
to spend my time <span id="8" class="ing_verb"></span> or <span id="9" class="ing_verb"></span>.
When parents go on a vacation, they spend their time eating
three <span id="10" class="plural_noun"></span> a day, and fathers play golf, and mothers
sit around <span id="11" class="ing_verb"></span>. Last summer, my little brother
fell in a/an <span id="12" class="noun"></span> and got poison <span id="13" class="plant"></span> all
over his<span id="14" class="body_part"></span>. My family is going to go to (the)
<span id="15" class="place"></span>, and I will practice <span id="16" class="ing_verb"></span>. Parents
need vacations more than kids because parents are always very
<span id="17" class="adjective"></span> and because they have to work <span id="18" class="number"></span>
hours every day all year making enough <span id="19" class="plural_noun"></span> to pay
for the vacation.</p>
``` 
[src](http://www.madlibs.com/content/uploads/2016/04/VacationFun_ML_2009_pg15.pdf)

- Using Beautifulsoup, Javascript, jQuery or pure Python, extract the id values from the spans to create a list of values.
For example `spans = ["adjective","adjective","noun"...]` or `spans = {"1":"adjective", "2":"adjective", "3":"noun"}`

- create a form with a field for each span with a label for the part of speech  
*hint* [field label](https://www.w3schools.com/tags/tag_label.asp)
- serve the form to a template 
- fill the spans in the text with the user's form responses. 
- return the completed mad lib to the user 

You can form teams or work on this alone. Ask for help at any time. You have until next Monday to complete the app. We will then look at all the entries and vote on our favorite as a group. 
