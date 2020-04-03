---
title: Delegáty a výrazy lambda
description: Zjistěte, jak delegáti, které definují typ, který určuje podpis konkrétní metody, mohou být voláni přímo nebo předáni jiné metodě a voláni.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: a9ca935814d1a7f77ded5f371ccd496c3859c523
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635931"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="40064-103">Delegáty a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="40064-103">Delegates and lambdas</span></span>

<span data-ttu-id="40064-104">Delegáti definují typ, který určuje podpis konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="40064-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="40064-105">Metoda (statická nebo instance), která splňuje tento podpis, může být přiřazena proměnné tohoto typu, poté volána přímo (s příslušnými argumenty) nebo předána jako samotný argument jiné metodě a poté volána.</span><span class="sxs-lookup"><span data-stu-id="40064-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="40064-106">Následující příklad ukazuje použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="40064-107">Řádek `public delegate string Reverse(string s);` vytvoří typ delegáta určitého podpisu, v tomto případě metoda, která přebírá parametr řetězce a pak vrátí parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="40064-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="40064-108">Metoda, `static string ReverseString(string s)` která má přesně stejný podpis jako definovaný typ delegáta, implementuje delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="40064-109">Řádek `Reverse rev = ReverseString;` ukazuje, že můžete přiřadit metodu proměnné odpovídajícího typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="40064-110">Řádek `Console.WriteLine(rev("a string"));` ukazuje, jak použít proměnnou typu delegáta k vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="40064-111">Za účelem zjednodušení procesu vývoje obsahuje rozhraní .NET sadu typů delegátů, které mohou programátoři znovu použít a nemusí vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="40064-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="40064-112">Tyto typy `Func<>` `Action<>` jsou `Predicate<>`, a , a lze je použít bez nutnosti definovat nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="40064-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="40064-113">Existují určité rozdíly mezi těmito třemi typy, které mají co do činění se způsobem, jakým byly určeny k použití:</span><span class="sxs-lookup"><span data-stu-id="40064-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="40064-114">`Action<>`se používá, když je potřeba provést akci pomocí argumentů delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="40064-115">Metoda zapouzdřuje nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40064-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="40064-116">`Func<>`se obvykle používá, když máte transformace na skladě, to znamená, že je třeba transformovat argumenty delegáta do jiného výsledku.</span><span class="sxs-lookup"><span data-stu-id="40064-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="40064-117">Projekce jsou dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="40064-117">Projections are a good example.</span></span> <span data-ttu-id="40064-118">Metoda, kterou zapouzdřuje vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40064-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="40064-119">`Predicate<>`se používá, když potřebujete zjistit, zda argument splňuje podmínku delegáta.</span><span class="sxs-lookup"><span data-stu-id="40064-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="40064-120">Může být také zapsán `Func<T, bool>`jako , což znamená, že metoda vrátí logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40064-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="40064-121">Nyní můžeme vzít náš příklad výše a `Func<>` přepsat jej pomocí delegáta namísto vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="40064-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="40064-122">Program bude pokračovat v spuštění přesně stejný.</span><span class="sxs-lookup"><span data-stu-id="40064-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="40064-123">Pro tento jednoduchý příklad, s metodou `Main` definovanou mimo metodu se zdá být trochu nadbytečné.</span><span class="sxs-lookup"><span data-stu-id="40064-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="40064-124">Rozhraní .NET Framework 2.0 zavedlo koncept *anonymních delegátů*, které umožňují vytvářet "vložkové" delegáty bez nutnosti zadávat další typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="40064-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="40064-125">V následujícím příkladu anonymní delegát filtruje seznam pouze na sudá čísla a poté je vytiskne do konzoly.</span><span class="sxs-lookup"><span data-stu-id="40064-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="40064-126">Jak můžete vidět, tělo delegáta je jen sada výrazů, jako každý jiný delegát.</span><span class="sxs-lookup"><span data-stu-id="40064-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="40064-127">Ale místo toho, aby to byla samostatná definice, zavedli jsme <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> ji _ad hoc_ v našem volání k metodě.</span><span class="sxs-lookup"><span data-stu-id="40064-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="40064-128">Nicméně, i s tímto přístupem, je stále mnoho kódu, který můžeme vyhodit.</span><span class="sxs-lookup"><span data-stu-id="40064-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="40064-129">To je místo, kde *lambda výrazy* přicházejí do hry.</span><span class="sxs-lookup"><span data-stu-id="40064-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="40064-130">Lambda výrazy, nebo jen "lambdas" v krátkosti, byly zavedeny v Jazyce C# 3.0 jako jeden z základních stavebních bloků jazyka integrovaný dotaz (LINQ).</span><span class="sxs-lookup"><span data-stu-id="40064-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="40064-131">Jsou to jen pohodlnější syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="40064-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="40064-132">Deklarují podpis a tělo metody, ale nemají vlastní formální identitu, pokud nejsou přiřazeny delegátovi.</span><span class="sxs-lookup"><span data-stu-id="40064-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="40064-133">Na rozdíl od delegátů mohou být přímo přiřazeny jako levá strana registrace událostí nebo v různých klauzulích a metodách LINQ.</span><span class="sxs-lookup"><span data-stu-id="40064-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="40064-134">Vzhledem k tomu, že výraz lambda je pouze dalším způsobem určení delegáta, měli bychom být schopni přepsat výše uvedenou ukázku tak, aby místo anonymního delegáta použilvýraz lambda.</span><span class="sxs-lookup"><span data-stu-id="40064-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="40064-135">V předchozím příkladu je `i => i % 2 == 0`použitý výraz lambda .</span><span class="sxs-lookup"><span data-stu-id="40064-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="40064-136">Opět je to jen pohodlná syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="40064-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="40064-137">To, co se děje pod kryty, je podobné tomu, co se děje s anonymním delegátem.</span><span class="sxs-lookup"><span data-stu-id="40064-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="40064-138">Opět lambdas jsou pouze delegáti, což znamená, že mohou být použity jako obslužná rutina události bez problémů, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="40064-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="40064-139">Operátor `+=` v tomto kontextu se používá k odběru [události](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="40064-139">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="40064-140">Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="40064-140">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="40064-141">Další čtení a zdroje</span><span class="sxs-lookup"><span data-stu-id="40064-141">Further reading and resources</span></span>

* [<span data-ttu-id="40064-142">Delegáty</span><span class="sxs-lookup"><span data-stu-id="40064-142">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="40064-143">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="40064-143">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="40064-144">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="40064-144">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
