---
title: rectangle_pointers.cpp (Rectangle code using functions with pointer arguments)
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

// '*' added to denote passing of pointers
void grow_rectangle(Rectangle*);
void shrink_rectangle(Rectangle*);

int main() {
    Rectangle ra;
    ra.width = 16;
    ra.height = 9;

    print_rectangle(ra);

    // The argument changes to the address of the object.
    grow_rectangle(&ra);
    print_rectangle(ra);

    shrink_rectangle(&ra);
    print_rectangle(ra);

    return 0;
}

// Since we are not modifying the rectangle, we can simply make a call by value.
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

// The way in which class members are accessed changes as well.
// We do not return the modified object, since we followed the pointer back to  
// the original object and modified the original object itself.
void grow_rectangle(Rectangle* pr)
{
    (*pr).width += 2;
    (*pr).height += 2;
    // Equivalent code: (shorthand)
    // pr->width += 2;
    // pr->height += 2;
}

void shrink_rectangle(Rectangle* pr)
{
    (*pr).width -= 2;
    (*pr).height -= 2;
    // Equivalent code: (shorthand)
    // pr->width -= 2;
    // pr->height -= 2;
}
{% endhighlight %}
