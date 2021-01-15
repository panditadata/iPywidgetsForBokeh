# iPywidgetsForBokeh
iPywidgetsForBokeh

# Study of Friction Equation with ipywidgets and Bokeh



First all the necessary libraries and modules are downloaded


```python
from ipywidgets import interact
import numpy as np
from bokeh.io import push_notebook, show, output_notebook
from bokeh.plotting import figure
output_notebook()
```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="36fc63bc-23ec-4553-a9d3-babb3b0770e7">Loading BokehJS ...</span>
    </div>




The studdy is performed for a equation of friction for a block of mass m in on an inclined plane of angle tetha
Interactors displays the variations if friction depends on sin, cos, tan, angel value

gravity 10 m/s^2 for Earth

x =np.linspace(0,np.pi,2000)

mu=0.5 friction coefficient

The variables of the equation are defined:


```python

x=np.linspace(0,2*np.pi,2000)
x =np.rint(x)
y =0.5*1*10* np.sin(x)

p=figure(title = 'friction display depending on angle, friction coefficient, mass',plot_height=300, plot_width=600, y_range=(-35,35))  
r=p.line(x,y,color='#2222aa', line_width=3)
print(x)
print(y)


```

    [0. 0. 0. ... 6. 6. 6.]
    [ 0.          0.          0.         ... -1.39707749 -1.39707749
     -1.39707749]
    

Adding the equation into the funtion that will display the selection of main trigonometry functions


```python
def update(f, mu=1,  m=1, phi=0  ):
    if   f=="sin": func = np.sin
    elif f=="cos": func = np.cos
    elif f=="tan": func = np.tan
    r.data_source.data['y'] = mu*m*10*func(np.sin(x+phi))
    push_notebook()
```

Plotting the equation and the chart 


```python
show(p, notebook_handle=True)
```



<div class="bk-root">
    <div class="bk-plotdiv" id="3c862155-c624-42fc-b3a0-b627cc36a688"></div>
</div>







<p><code>&lt;Bokeh Notebook handle for <strong>In[15]</strong>&gt;</code></p>



Below the ipywidget to select the trigonometry function that will change the Friction equation.

Friction coefficient ipywidget follows next.

Then, the phase phi is displayed as well.


```python
interact(update, f=["sin", "cos", "tan"],mu=(0,1,0.1), m=(0,100), phi=(0,5,0.1))
```


    interactive(children=(Dropdown(description='f', options=('sin', 'cos', 'tan'), value='sin'), FloatSlider(value…





    <function __main__.update(f, mu=1, m=1, phi=0)>


