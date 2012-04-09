---
title: rectangle_value.cpp (Rectangle code using functions with arguments passed by value)
layout: default
---

{% highlight cpp %}
#include<iostream>
using namespace std;

class Rectangle
{
    public:
        int width;
        int height;
};

void print_rectangle(Rectangle);

Rectangle grow_rectangle(Rectangle);

Rectangle shrink_rectangle(Rectangle);

int main() {
    Rectangle ra;
    ra.width = 16;
    ra.height = 9;

    print_rectangle(ra);

    // We have to save the return value back into 'ra' since grow_rectangle 
    // modifies a copy of 'ra' that it recieved due to call by value.
    ra = grow_rectangle(ra);
    print_rectangle(ra);

    ra = shrink_rectangle(ra);
    print_rectangle(ra);

    return 0;
}


void print_rectangle(Rectangle r)
{
    for(int i = 0; i < r.height; i++)
    {
        for(int j = 0; j < r.width; j++)
        {
            cout << "*";
        }
        cout << endl;
    }
    cout << endl;
}

Rectangle grow_rectangle(Rectangle r)
{
    r.width += 2;
    r.height += 2;
    return r;
}

Rectangle shrink_rectangle(Rectangle r)
{
    r.width -= 2;
    r.height -= 2;
    return r;
}
{% endhighlight %}
