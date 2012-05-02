---
title: complex.cpp (Complex numbers functions' bodies)
layout: default
---

{% highlight cpp %}
#include <iostream>
#include <cmath>
using namespace std;

#include "complex.h"

// Constructor with two arguments
Complex::Complex(double _r, double _i)
{
    r = _r;
    i = _i;
}

// Constructor with one argument
Complex::Complex(double _r)
{
    r = _r;
    i = 0.0;
}

// default constructor
Complex::Complex()
{
    r = 0.0;
    i = 0.0;
}

/*
*    Simple function to add two complex numbers. To add a and b, we have 
*     to make the following call: a.add(b); This looks a little artificial
*    but can be changed to a more natural a + b by using operator 
*    overloading.
*/
Complex Complex::add(Complex &rhs)
{
    // (a + bi) + (c + di) = (a+c) + (b+d)i

    double a = r;
    double b = i;

    double c = rhs.r ;
    double d = rhs.i;

    double nr = a + c;
    double ni = b + d;

    Complex tmp(nr, ni);
    return tmp;
}


/* Operator overloading
*    Normally, we can use operators like +, -, * etc only for primitive 
*    data types in C++, like int, char  float double etc.
*    However, C++ allows us to extend these operators to work on our 
*    classes by by overloading them. The following function overloads
*    the '+' operator so that we can use a simple command like c = a + b
*    to add two objects of type Complex.
*/
Complex Complex::operator+ (Complex &rhs)
{
    // (a + bi) + (c + di) = (a+c) + (b+d)i
    // double a = r     ; double b = i;
    // double c = rhs.r ; double d = rhs.i;
    // double nr = a + c;
    // double ni = b + d;
    // Complex tmp(nr, ni);
    // return tmp;
    return Complex(r + rhs.r, i + rhs.i);
}

// Overloaded '-' operator
Complex Complex::operator- (Complex &rhs)
{
    // (a + bi) - (c + di) = (a-c) + (b-d)i
    // double a = r     ; double b = i;
    // double c = rhs.r ; double d = rhs.i;
    //double nr = a - c;
    //double ni = b - d;
    //Complex tmp(nr, ni);
    //return tmp;
    return Complex(r - rhs.r, i - rhs.i);
}

// Overloaded '*' operator
Complex Complex::operator* (Complex &rhs)
{
    //(a + bi)*(c + di) = (ac - bd) + (ad + dc)i
    // double a = r     ; double b = i;
    // double c = rhs.r ; double d = rhs.i;
    // double nr = (a*c) - (b*d);
    // double ni = (a*d) + (b*c);
    // Complex tmp(nr, ni);
    // return tmp;
    return Complex((r * rhs.r) - (i * rhs.i), (r * rhs.i) + (i * rhs.r));
}


// To be completed in next class
Complex Complex::operator/ (Complex &rhs)
{
    Complex c = rhs.conj();
    double n = rhs.norm();
    // Complex tmp = (*this)*c;
    // tmp = tmp / (n*n);
    // return tmp;
    return ((*this) * c) / (n * n);
}

Complex Complex::operator/ (double rhs)
{
    return Complex(r/rhs, i/rhs);
}

// returns the conjugate of the complex number for which it is called
Complex Complex::conj()
{
    // conj a + bi = a - bi
    return Complex(r, -i);
}

// returns the norm of the complex number for which it is called
double Complex::norm()
{
    // norm a + bi = square_root(a^2 + b^2)
    return sqrt(r*r + i*i);
}

// prints the complex number
void Complex::print()
{
    if(i < 0)
        cout << r << " - " << (-i) << "i" << endl;
    else
        cout << r << " + " << i << "i" << endl;
}
{% endhighlight %}
