---
title: rectangle_reference.cpp (Rectangle code using functions with arguments passed by reference)
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

// added '&' to denote call by reference. The system will now pass another name  
// of the input variable to the function, instead of a copy of the variable.
void grow_rectangle(Rectangle&);
void shrink_rectangle(Rectangle&);

int main() {
    Rectangle ra;
    ra.width = 16;
    ra.height = 9;

    print_rectangle(ra);

    // The argument for the function call remains unchanged. One can think of 
    // call by reference as creating a new name for the argument variable, 
    // as opposed to call by value, which creates a copy of the argument variable
    grow_rectangle(ra);
    print_rectangle(ra);

    shrink_rectangle(ra);
    print_rectangle(ra);

    return 0;
}

// Since we are not modifying the rectangle, 
// we can simply make a call by value.
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

// The way in which class members are accessed also remains unchanged.
// We do not return the modified object, since the modifications were 
// done on the original object itself.
void grow_rectangle(Rectangle& r)
{
    r.width += 2;
    r.height += 2;
}

void shrink_rectangle(Rectangle& r)
{
    r.width -= 2;
    r.height -= 2;
}
{% endhighlight %}
