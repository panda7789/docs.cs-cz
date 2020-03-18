---
title: Delegáty a výrazy lambda
description: Zjistěte, jak delegáti definují typ, který určuje podpis konkrétní metody, který lze volat přímo nebo předán jiné metodě a volán.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75345544"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="73415-103">Delegáty a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="73415-103">Delegates and lambdas</span></span>

<span data-ttu-id="73415-104">Delegáti definují typ, který určuje podpis konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="73415-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="73415-105">Metoda (statická nebo instance), která splňuje tento podpis, může být přiřazena proměnné tohoto typu, poté volána přímo (s příslušnými argumenty) nebo předána jako samotný argument jiné metodě a poté volána.</span><span class="sxs-lookup"><span data-stu-id="73415-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="73415-106">Následující příklad ukazuje použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="73415-107">Řádek `public delegate string Reverse(string s);` vytvoří typ delegáta určitého podpisu, v tomto případě metoda, která přebírá parametr řetězce a pak vrátí parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="73415-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="73415-108">Metoda, `static string ReverseString(string s)` která má přesně stejný podpis jako definovaný typ delegáta, implementuje delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="73415-109">Řádek `Reverse rev = ReverseString;` ukazuje, že můžete přiřadit metodu proměnné odpovídajícího typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="73415-110">Řádek `Console.WriteLine(rev("a string"));` ukazuje, jak použít proměnnou typu delegáta k vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="73415-111">Za účelem zjednodušení procesu vývoje obsahuje rozhraní .NET sadu typů delegátů, které mohou programátoři znovu použít a nemusí vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="73415-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="73415-112">Jedná `Func<>`se `Action<>` `Predicate<>`o , a , a mohou být použity na různých místech v rámci rozhraní API .NET bez nutnosti definovat nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="73415-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="73415-113">Samozřejmě, tam jsou některé rozdíly mezi těmito třemi, jak uvidíte v jejich podpisy, které většinou mají co do činění s tím, jak byly určeny k použití:</span><span class="sxs-lookup"><span data-stu-id="73415-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="73415-114">`Action<>`se používá, když je potřeba provést akci pomocí argumentů delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
* <span data-ttu-id="73415-115">`Func<>`se obvykle používá, když máte transformace na skladě, to znamená, že je třeba transformovat argumenty delegáta do jiného výsledku.</span><span class="sxs-lookup"><span data-stu-id="73415-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="73415-116">Projekce jsou toho ukázkovým příkladem.</span><span class="sxs-lookup"><span data-stu-id="73415-116">Projections are a prime example of this.</span></span>
* <span data-ttu-id="73415-117">`Predicate<>`se používá, když potřebujete zjistit, zda argument splňuje podmínku delegáta.</span><span class="sxs-lookup"><span data-stu-id="73415-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="73415-118">To může být také `Func<T, bool>`napsáno jako .</span><span class="sxs-lookup"><span data-stu-id="73415-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="73415-119">Nyní můžeme vzít náš příklad výše a `Func<>` přepsat jej pomocí delegáta namísto vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="73415-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="73415-120">Program bude pokračovat v spuštění přesně stejný.</span><span class="sxs-lookup"><span data-stu-id="73415-120">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="73415-121">Pro tento jednoduchý příklad, s metodou `Main` definovanou mimo metodu se zdá být trochu nadbytečné.</span><span class="sxs-lookup"><span data-stu-id="73415-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="73415-122">Je to proto, že rozhraní .NET Framework 2.0 představil koncept **anonymních delegátů**.</span><span class="sxs-lookup"><span data-stu-id="73415-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="73415-123">S jejich podporou můžete vytvořit "inline" delegáty bez nutnosti zadávat další typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="73415-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="73415-124">Jednoduše zařazujete definici delegáta tam, kde ji potřebujete.</span><span class="sxs-lookup"><span data-stu-id="73415-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="73415-125">Například ji přepneme a použijeme anonymního delegáta k odfiltrování seznamu pouze sudých čísel a jejich vytištění do konzole.</span><span class="sxs-lookup"><span data-stu-id="73415-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

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

<span data-ttu-id="73415-126">Jak můžete vidět, tělo delegáta je jen sada výrazů, jako každý jiný delegát.</span><span class="sxs-lookup"><span data-stu-id="73415-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="73415-127">Ale místo toho, aby to byla samostatná definice, zavedli jsme <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> ji _ad hoc_ v našem volání k metodě.</span><span class="sxs-lookup"><span data-stu-id="73415-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73415-128">Nicméně, i s tímto přístupem, je stále mnoho kódu, který můžeme vyhodit.</span><span class="sxs-lookup"><span data-stu-id="73415-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="73415-129">To je místo, kde **lambda výrazy** přicházejí do hry.</span><span class="sxs-lookup"><span data-stu-id="73415-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="73415-130">Lambda výrazy, nebo jen "lambdas" v krátkosti, byly zavedeny nejprve v Jazyce C# 3.0, jako jeden z základních stavebních bloků jazyka integrovaný dotaz (LINQ).</span><span class="sxs-lookup"><span data-stu-id="73415-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="73415-131">Jsou to jen pohodlnější syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="73415-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="73415-132">Deklarují podpis a tělo metody, ale nemají vlastní formální identitu, pokud nejsou přiřazeny delegátovi.</span><span class="sxs-lookup"><span data-stu-id="73415-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="73415-133">Na rozdíl od delegátů mohou být přímo přiřazeny jako levá strana registrace událostí nebo v různých klauzulích a metodách LINQ.</span><span class="sxs-lookup"><span data-stu-id="73415-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="73415-134">Vzhledem k tomu, že výraz lambda je pouze dalším způsobem určení delegáta, měli bychom být schopni přepsat výše uvedenou ukázku tak, aby místo anonymního delegáta použilvýraz lambda.</span><span class="sxs-lookup"><span data-stu-id="73415-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="73415-135">V předchozím příkladu je `i => i % 2 == 0`použitý výraz lambda .</span><span class="sxs-lookup"><span data-stu-id="73415-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="73415-136">Opět je to jen **velmi** výhodná syntaxe pro použití delegátů, takže to, co se děje pod kryty, je podobné tomu, co se děje s anonymním delegátem.</span><span class="sxs-lookup"><span data-stu-id="73415-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="73415-137">Opět lambdas jsou pouze delegáti, což znamená, že mohou být použity jako obslužná rutina události bez problémů, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="73415-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="73415-138">Operátor `+=` v tomto kontextu se používá k odběru [události](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="73415-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="73415-139">Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="73415-139">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="73415-140">Další čtení a zdroje</span><span class="sxs-lookup"><span data-stu-id="73415-140">Further reading and resources</span></span>

* [<span data-ttu-id="73415-141">Delegáty</span><span class="sxs-lookup"><span data-stu-id="73415-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="73415-142">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="73415-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="73415-143">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="73415-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
