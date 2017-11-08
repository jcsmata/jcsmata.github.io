---
title: "Extension methods in .NET"
permalink: /blog/extension-methods
tags:
    - .NET
    - Programming
    - Software Engineering 
excerpt: "A post about extension methods and how to create them."
modified: 2016-12-21T00:00:00-01:00
---

<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

{% include toc title="Extension methods" %}

## What are Extension methods?
The most complete description of what are extension methods can be found in following quotes:

> Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. Extension methods are a special kind of static method, but they are called as if they were instance methods on the extended type. For client code written in C# and Visual Basic, there is no apparent difference between calling an extension method and the methods that are actually defined in a type.
<cite><a href="https://msdn.microsoft.com/en-us/library/bb311042.aspx">MSDN Documentation</a></cite>

> Extension methods allow developers to add new methods to the public contract of an existing CLR type, without having to sub-class it or recompile the original type.  Extension Methods help blend the flexibility of "duck typing" support popular within dynamic languages today with the performance and compile-time validation of strongly-typed languages.
<cite><a href="https://weblogs.asp.net/scottgu/new-orcas-language-feature-extension-methods">Scott Gu</a></cite>

**Info Notice:** You can add an extension method to the `Object` type so it can be used in all the other types of the framework.
{: .notice--info}

**Warning Notice:** Extension methods present no specific security vulnerabilities. They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself. Extension methods cannot access any private data in the extended class.
{: .notice--warning}

## When to use

Consider the following to determined wheter or not a method should be used as an extension method: 

* Its primary parameter is an instance?
* The method logically operates on that instance?
* Do you want it to appear to others when using that instance?

## How to create

The creation of an Extension Method is quite simple, just follow this steps:

1. Define a `static` class to contain the extension method. The class must be visible to client code.

2. Implement the extension method as a `static` method with at least the same visibility as the containing class.

3. The first parameter of the method specifies the type that the method operates on; it must be preceded with the `this` modifier.

4. In the calling code, add a `using` directive to specify the namespace that contains the extension method class.

5. Call the methods as if they were instance methods on the type.

## Example

The following code shows you how to add an extension method to the `Datetime` type. It allows you to retrieve the number of the week according to the international standard ISO 8601.

```csharp
public static class GlobalFunctions
{
    public static int WeekOfYearISO8601(this DateTime date)
    {
        var day = (int)CultureInfo.CurrentCulture.Calendar.GetDayOfWeek(date);
        var week = CultureInfo.CurrentCulture.Calendar.GetWeekOfYear(date.AddDays(4 - (day == 0 ? 7 : day)), CalendarWeekRule.FirstFourDayWeek, DayOfWeek.Monday);

        return week;
    }
}
```

Two conditions were added to validate the method. As you can see calling the extension method is straight forward once you have created.

```csharp
public void TestISO8601WeekDates()
{
    // According to wikipedia
    // Monday 29 December 2008 is week 1
    // Sunday 3 January 2010 is written week 53

    // Ready 
    DateTime dt1 = new DateTime(2008, 12, 29);
    DateTime dt2 = new DateTime(2010, 1, 3);

    // Set
    int week4dt1 = dt1.WeekOfYearISO8601();
    int week4dt2 = dt2.WeekOfYearISO8601();

    // Go
    Assert.AreEqual(1, week4dt1);
    Assert.AreEqual(53, week4dt2);
}
```

You can download the full solution for VS2015 here:

<!-- Place this tag where you want the button to render. -->
<a class="github-button" href="https://github.com/jcsmata/extension-methods/archive/master.zip" data-icon="octicon-cloud-download" data-style="mega" aria-label="Download jcsmata/extension-methods on GitHub">Download</a>
