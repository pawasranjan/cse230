---
title: rectangle.h (Rectangle class header file)
layout: default
---

{% highlight cpp %}
#ifndef RECTANGLE_H
#define RECTANGLE_H

#include<iostream>
#include<cstdlib>
using namespace std;

class Rectangle
{
    private:
        int width;
        int height;

    public:
        void setProperties(int, int);

        int getWidth();
        int getHeight();

        void print();
        void grow();
        void shrink();
        void diminish();

};

// Since width and height private, we are forced to use setProperties(int, int) 
// to set them.This allows us to enforce conditions on the input and also on 
// how we set the values of width and height.
// For example, here we force the width to be greater than height, regardless 
// of the order in which the two numbers are supplied.
void Rectangle::setProperties(int a, int b)
{
    if(a > b)
    {
        width  = a;
        height = b;
    }
    else
    {
        width  = b;
        height = a;
    }
}

// Since a member function is called by a particular object, we can refer 
// the other members (both data and functions) directly, i.e. without the dot 
// notation (r.width, r.height etc).
int Rectangle::getWidth() {return width;}

int Rectangle::getHeight() {return height;}

void Rectangle::print()
{
    for(int i = 0; i < height; i++)
    {
        for(int j = 0; j < width; j++)
        {
            cout << "*";
        }
        cout << endl;
    }
    cout << endl;

}

void Rectangle::grow()
{
    width += 2;
    height += 2;
}

void Rectangle::shrink()
{
    width -= 2;
    height -= 2;
}

void Rectangle::diminish()
{
    while (width > 0 && height > 0)
    {
        print();
        shrink();
        usleep(200000);
        // On Windows, use:
        // Sleep(200);
    }
}

#endif
{% endhighlight %}
