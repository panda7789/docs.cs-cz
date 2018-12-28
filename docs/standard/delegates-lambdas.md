---
title: Delegáty a výrazy lambda
description: Zjistěte, jak delegáti definice typu, která zadejte konkrétní metody podpis, můžete volat přímo nebo předány jiné metodě a názvem.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 3d4aa5e60ab9bb134716bddcf90b6fc6b07c2ea0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656151"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="4806c-103">Delegáty a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="4806c-103">Delegates and lambdas</span></span>

<span data-ttu-id="4806c-104">Delegáti definice typu, která zadejte konkrétní metody podpis.</span><span class="sxs-lookup"><span data-stu-id="4806c-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="4806c-105">Metody (statická nebo instance), který splňuje tento podpis být přiřazen proměnné tohoto typu, pak můžete volat přímo (s příslušnými argumenty) nebo předán jako samotný argument jiné metodě a následném zavolání.</span><span class="sxs-lookup"><span data-stu-id="4806c-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="4806c-106">Následující příklad ukazuje použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* <span data-ttu-id="4806c-107">`public delegate string Reverse(string s);` Řádek vytvoří delegát typu určité podpis, v tomto případě metodu, která přijímá řetězcový parametr a vrátí parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="4806c-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="4806c-108">`static string ReverseString(string s)` Metodu, která má přesně stejný podpis jako typ definovaný delegát, implementuje delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="4806c-109">`Reverse rev = ReverseString;` Čára ukazuje, že můžete přiřadit metody proměnné odpovídající typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="4806c-110">`Console.WriteLine(rev("a string"));` Řádku ukazuje, jak použít proměnné typu delegáta k vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="4806c-111">Aby bylo možné zjednodušit proces vývoje, .NET obsahuje sadu typy delegátu, které programátoři můžou opakovaně používat a není nutné vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="4806c-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="4806c-112">Jedná se o `Func<>`, `Action<>` a `Predicate<>`, a že lze použít na různých místech v rámci rozhraní .NET API bez nutnosti definovat nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="4806c-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="4806c-113">Samozřejmě existují určité rozdíly mezi třemi jak uvidíte v jejich podpisy, které většinou se tak, jak byly určeny pro použití:</span><span class="sxs-lookup"><span data-stu-id="4806c-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="4806c-114">`Action<>` se používá, když je potřeba provést akci na základě argumentů delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="4806c-115">`Func<>` se používá, obvykle v případě, že máte transformaci na stranu, to znamená, je potřeba získat argumenty delegáta z jiné výsledky.</span><span class="sxs-lookup"><span data-stu-id="4806c-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="4806c-116">Projekce jsou typickým příkladem tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="4806c-116">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="4806c-117">`Predicate<>` používá se při je potřeba určit, pokud argument splňuje podmínky delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="4806c-118">Lze zapsat také jako `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="4806c-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="4806c-119">Jsme teď můžete provést v našem příkladu výše a jeho pomocí přepsání `Func<>` delegovat místo vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="4806c-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="4806c-120">Program bude dál běžet stejně.</span><span class="sxs-lookup"><span data-stu-id="4806c-120">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

<span data-ttu-id="4806c-121">Tento jednoduchý příklad, s definované mimo metodu `Main` metoda vypadá trochu nadbytečný.</span><span class="sxs-lookup"><span data-stu-id="4806c-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="4806c-122">Je proto, že rozhraní .NET Framework 2.0 byl zaveden koncept **anonymní delegáti**.</span><span class="sxs-lookup"><span data-stu-id="4806c-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="4806c-123">Díky jejich podpoře je možné k vytváření delegátů "vloženě" bez nutnosti zadávat žádné další typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="4806c-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="4806c-124">Můžete jednoduše vložené definice delegáta, kde ji potřebujete.</span><span class="sxs-lookup"><span data-stu-id="4806c-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="4806c-125">Příklad budeme přepínání nahoru a pomocí našich anonymního delegáta vyfiltrovat seznam pouze sudých čísel a zapisuje je do konzole.</span><span class="sxs-lookup"><span data-stu-id="4806c-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="4806c-126">Jak je vidět text delegáta je jenom sada výrazů, jako jakýkoli delegát.</span><span class="sxs-lookup"><span data-stu-id="4806c-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="4806c-127">Místo je samostatný definice, zavedli jsme ji, ale _ad hoc_ v našich volání <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4806c-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4806c-128">Ale i s tímto přístupem je stále, jaká část kódu, který jsme může vyvolat okamžitě.</span><span class="sxs-lookup"><span data-stu-id="4806c-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="4806c-129">Tady **výrazy lambda** souvisejí.</span><span class="sxs-lookup"><span data-stu-id="4806c-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="4806c-130">Výrazy lambda, nebo jenom "výrazy lambda" zkráceně, byly zavedeny nejprve v C# 3.0 jako jeden ze základních stavebních bloků z Language Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="4806c-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="4806c-131">Jsou to jenom pohodlnější syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="4806c-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="4806c-132">Deklarovat podpis a tělo metody, ale nemají své vlastní, formální identitu, pokud jsou přiřazeny k delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="4806c-133">Na rozdíl od delegáty se může být přímo přiřazeni jako na levé straně, registrace událostí nebo v různých klauzule LINQ a metody.</span><span class="sxs-lookup"><span data-stu-id="4806c-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="4806c-134">Výraz lambda je další způsob určení delegáta, jsme měli být schopni přepsat předchozí ukázka použití lambda výrazů namísto anonymního delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="4806c-135">V předchozím příkladu používá výraz lambda je `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="4806c-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="4806c-136">Znovu jde jenom **velmi** pohodlné syntaxe pro použití delegátů, tak co se stane, že na pozadí je podobný co se stane s anonymního delegáta.</span><span class="sxs-lookup"><span data-stu-id="4806c-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="4806c-137">Znovu výrazy lambda jsou pouze delegáty, což znamená, že může sloužit jako obslužná rutina události bez problémů, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="4806c-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

<span data-ttu-id="4806c-138">`+=` Operátor v tomto kontextu se používá k přihlášení k odběru [události](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="4806c-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="4806c-139">Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="4806c-139">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="4806c-140">Další materiály a zdroje</span><span class="sxs-lookup"><span data-stu-id="4806c-140">Further reading and resources</span></span>

*   [<span data-ttu-id="4806c-141">Delegáti</span><span class="sxs-lookup"><span data-stu-id="4806c-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="4806c-142">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="4806c-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="4806c-143">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="4806c-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
