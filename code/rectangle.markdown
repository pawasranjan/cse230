---
title: rectangle.cpp (Rectangle code using functions inside class)
layout: default
---

{% highlight cpp %}
#include <iostream>
#include <cstdlib>
using namespace std;

#include "rectangle.h"

int main() {
    Rectangle ra;
    ra.setProperties(50,22);

    ra.print();

    ra.grow();
    ra.print();

    ra.shrink();
    ra.print();

    cout << endl << "::Shrinking Rectangle::" << endl << endl;
    ra.diminish();

    cout << "Final width and height: " << ra.getWidth() 
                               << ", " << ra.getHeight() << endl;

    return 0;
}
{% endhighlight %}
