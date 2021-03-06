# FixerSharp

C# library to assist with currency conversion and exchange rates. Leverages the [Fixer.io](http://fixer.io/) API.

[![FixerSharp Nuget](https://img.shields.io/nuget/v/FixerSharp.svg?style=flat)](https://www.nuget.org/packages/FixerSharp)

## Installation

Can be installed as a [NuGet package](https://www.nuget.org/packages/FixerSharp). In the package manager console, enter the following:

```text
Install-Package FixerSharp
```

## Usage

Perform a one-off conversion between two currencies:

```c#
using FixerSharp;

...

double oneHundredUsdInGbp = Fixer.Convert(Symbols.USD, Symbols.GBP, 100);
double oneThousandEurInUsd = Fixer.Convert("EUR", "USD", 1000);
```

If you wish to perform additional conversions, the current exchange rate can be saved and used to convert:

```c#
using FixerSharp;

...

ExchangeRate rateUsdGbp = Fixer.Rate(Symbols.USD, Symbols.GBP);

double oneHundredUsdInGbp = rateUsdGbp.Convert(100);
double oneThousandUsdInGbp = rateUsdGbp.Convert(1000);
double tenThousandUsdInGbp = rateUsdGbp.Convert(10000);
```

*This method is recommended if you have more than one conversion to perform, as data is only retrieved from Fixer.io once.* 

## Acknowledgements

This makes use of the [fixer-io](https://github.com/hakanensari/fixer-io) project to provide up-to-date exchange rates.