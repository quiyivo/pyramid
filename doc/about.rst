.. _about:

=================
About the project
=================

Pyramid is designed to behave as similarly to R's well-known
`auto.arima <https://www.rdocumentation.org/packages/forecast/versions/8.4/topics/auto.arima>`_
as possible.

The project emerged as a result of a long-standing personal debate between
my colleagues and `me <https://github.com/tgsmith61591>`_ about why python is
vastly superior to R. Since R's forecasting capabilities far superceded those of Python's
existing libraries, Pyramid was created to close that gap and give analysts/researchers
one less reason why R is a viable language for practical machine learning.

*(Of course, take my soapbox speech with a grain of salt... I once was an R addict but am now recovering)*


How it works
------------

Pyramid is essentially a Python & Cython wrapper of several different statistical
and machine learning libraries (statsmodels and scikit-learn), and operates by generalizing
all ARIMA models into a single class (unlike statsmodels).

It does this by wrapping the respective statsmodels interfaces
(``ARMA``, ``ARIMA`` and ``SARIMAX``) inside the ``pyramid.ARIMA`` class,
and as a result there is a bit of monkey patching that happens beneath the hood.

How ``auto_arima`` works
~~~~~~~~~~~~~~~~~~~~~~~~

The ``auto_arima`` function itself operates a bit like a grid search, in that it
tries various sets of ``p`` and ``q`` (also ``P`` and ``Q`` for seasonal models)
parameters, selecting the model that minimizes the AIC (or BIC, or whatever
information criterion you select). To select the differencing terms, ``auto_arima``
uses a test of stationarity (such as an augmented Dickey-Fuller test) and seasonality
(such as the Canova-Hansen test) for seasonal models.

For more in-depth information on the process by which ``auto_arima`` selects
the best model, check out the :ref:`tips_and_tricks` section.

Feedback
--------

This is an open-source (read: *FREE*) project. That means several things:

* It is not infallible
* It's a community effort
* Making demands doesn't go over well

I know that there are those who have built models with Pyramid as a tool
to support their work. I also know that people can depend on the functionality of
this library in order to do their job well. And for that, I'm committed to
keeping things running smoothly.

However, as I'm the sole maintainer, things can sometimes stack up.
Please feel free to make pull requests (see :ref:`contrib`), file issues, and
make feature requests. But note the third point: :ref:`contributors` to this
project do it for fun. Let's keep it cordial.

**If you encounter any issues in the project, please see the** :ref:`filing_bugs` **section for how to file an issue.**
