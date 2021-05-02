---
layout: page
title: CNNs for Visual Recognition
---

## Backpropogation example

<div class="fig figleft fighighlight">
<img src="{{site.baseurl}}/assets/images/backprop_eg.svg" alt="">
<div class="figcaption">
  The figure above is an example of a computational graph.

</div>
<div style="clear:both;"></div>
</div>

The computational graph represents the following function
$$ \\\\
y = f(x_1,x_2;w_1,w_2,b) = \frac {1} {1+e^{-(w_1x_1 + w_2x_2 + b)}} 
\\\\
y = \frac {1}{y_1}
\\\\
y_1 = y_2 + 1
\\\\
y_2 = e^{y_3}
\\\\
y_3 = -y_4
\\\\
y_4 = y_5 + b
\\\\
y_5 = y_6 + y_7
\\\\
y_6 = w_1x_1
\\\\
y_7 = w_2x_2
\\\\
\frac {\partial y} {\partial y_1} = -\frac {1}{y_1^2} 
\\\\
\frac {\partial y}{\partial y_2} = \frac {\partial y} {\partial y_1} \frac {\partial y_1} {\partial y_2} = \frac {\partial y} {\partial y_1} * 1
\\\\
\frac {\partial y}{\partial y_3} = \frac {\partial y} {\partial y_2} \frac {\partial y_2} {\partial y_3} = \frac {\partial y} {\partial y_2} e^{y_3}
\\\\
\frac {\partial y}{\partial y_4} = \frac {\partial y} {\partial y_3} \frac {\partial y_3} {\partial y_4} = \frac {\partial y} {\partial y_3} * -1
\\\\
\frac {\partial y}{\partial y_5} = \frac {\partial y} {\partial y_4} \frac {\partial y_4} {\partial y_5} = \frac {\partial y} {\partial y_4} * 1
\\\\
\frac {\partial y}{\partial b} = \frac {\partial y} {\partial y_4} \frac {\partial y_4} {\partial b} = \frac {\partial y} {\partial y_4} * 1
\\\\
\frac {\partial y}{\partial y_6} = \frac {\partial y} {\partial y_5} \frac {\partial y_5} {\partial y_6} = \frac {\partial y} {\partial y_5} * 1
\\\\
\frac {\partial y}{\partial y_7} = \frac {\partial y} {\partial y_5} \frac {\partial y_5} {\partial y_7} = \frac {\partial y} {\partial y_5} * 1
\\\\
\frac {\partial y}{\partial w_1} = \frac {\partial y} {\partial y_6} \frac {\partial y_6} {\partial w_1} = \frac {\partial y} {\partial y_6} x_1
\\\\
\frac {\partial y}{\partial w_2} = \frac {\partial y} {\partial y_7} \frac {\partial y_7} {\partial w_2} = \frac {\partial y} {\partial y_7} x_2
\\\\
\nabla_{(w_1,w_2,b)}f(x_1,x_2;w_1,w_2,b)  = [\frac {\partial y}{\partial w_1} \frac {\partial y}{\partial w_2} \frac {\partial y}{\partial b}]^T 
$$
