---
title: main.cpp (Source file with main() for using the complex numbers class)
layout: default
---

{% highlight cpp %}
#include<iostream>
#include<cmath>
using namespace std;

// include the complex numbers class
#include"complex.h"

int main()
{
	//a = 5 + 3i
	Complex a(5,3);
	cout << "Constructor with two values:\na = ";
	a.print();

	// b = 3 - 4i
	Complex b(3,-4);
	cout << "b = ";
	b.print();

	cout << endl;

	Complex c(4);
	cout << "Constructor with one value:\nc = ";
	c.print();

	// c  = a.add(b);
	c = a + b;
	cout << "\na + b = ";
	c.print();

	Complex d;
	cout << "\nDefault constructor:\n d = ";
	d.print();

	d = a - b;
	cout << "\na - b = ";
	d.print();

	Complex e = a * b;
	cout <<  "\na * b = ";
        e.print();

	Complex f = a / b;
	cout <<  "\na / b = ";
	f.print();

	cout << "\nNorm of b: " << b.norm() << endl;

	Complex h = a.conj();
	cout << "Complex conjugate of a = ";
	h.print();

	return 0;
}
{% endhighlight %}
