---
title: complex.h (Complex numbers header file)
layout: default
---

{% highlight cpp %}
#ifndef COMPLEX_H
#define COMPLEX_H

class Complex
{
	public:
		double r;
		double i;

	Complex(double, double);
	Complex(double );
	Complex();

	Complex add(Complex&);

	Complex operator+ (Complex&);
	Complex operator- (Complex&);
	Complex operator* (Complex&);
	Complex operator/ (Complex&);
	Complex operator/ (double);

	Complex conj();
	double  norm();
	void    print();

};

#endif
{% endhighlight %}
