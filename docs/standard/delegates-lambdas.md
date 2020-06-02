---
title: Delegáty a výrazy lambda
description: Přečtěte si, jak delegáti, které definují typ, který určuje konkrétní signaturu metody, mohou být volány přímo nebo předány jiné metodě a volána.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 43e896bfe267299d3b0cb12a8f71e42fe2c87a88
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280787"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="fa16d-103">Delegáty a výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="fa16d-103">Delegates and lambdas</span></span>

<span data-ttu-id="fa16d-104">Delegáti definují typ, který určuje konkrétní signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="fa16d-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="fa16d-105">Metoda (static nebo instance), která odpovídá tomuto podpisu, může být přiřazena proměnné tohoto typu, pak volána přímo (s příslušnými argumenty) nebo předána jako argument do jiné metody a následně volána.</span><span class="sxs-lookup"><span data-stu-id="fa16d-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="fa16d-106">Následující příklad ukazuje použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="fa16d-107">`public delegate string Reverse(string s);`Řádek vytvoří typ delegáta určité signatury, v tomto případě metodu, která přijímá řetězcový parametr a potom vrátí řetězcový parametr.</span><span class="sxs-lookup"><span data-stu-id="fa16d-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="fa16d-108">`static string ReverseString(string s)`Metoda, která má přesně stejný podpis jako definovaný typ delegáta, implementuje delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="fa16d-109">`Reverse rev = ReverseString;`Řádek ukazuje, že můžete přiřadit metodu proměnné odpovídajícího typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="fa16d-110">`Console.WriteLine(rev("a string"));`Čára ukazuje, jak použít proměnnou typu delegáta k vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="fa16d-111">Aby bylo možné zjednodušit proces vývoje, obsahuje rozhraní .NET sadu typů delegátů, které mohou programátory použít a nikoli vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="fa16d-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="fa16d-112">Tyto typy jsou `Func<>` , `Action<>` a a `Predicate<>` lze je použít bez nutnosti definovat nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="fa16d-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="fa16d-113">Existují některé rozdíly mezi třemi typy, které je třeba provést s způsobem, jakým byly určeny pro použití:</span><span class="sxs-lookup"><span data-stu-id="fa16d-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="fa16d-114">`Action<>`se používá v případě, že je potřeba provést akci pomocí argumentů delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="fa16d-115">Metoda, kterou zapouzdřuje, nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="fa16d-116">`Func<>`se obvykle používá v případě, že máte transformaci, to znamená, že je nutné transformovat argumenty delegáta na jiný výsledek.</span><span class="sxs-lookup"><span data-stu-id="fa16d-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="fa16d-117">Projekce jsou dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="fa16d-117">Projections are a good example.</span></span> <span data-ttu-id="fa16d-118">Metoda, kterou zapouzdřuje, vrátí zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="fa16d-119">`Predicate<>`se používá v případě, že potřebujete určit, jestli argument splňuje podmínky delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="fa16d-120">Může být také zapsána jako `Func<T, bool>` , což znamená, že metoda vrátí logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="fa16d-121">Nyní můžeme použít náš příklad a přepsat ho pomocí `Func<>` delegáta místo vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="fa16d-122">Program bude pokračovat v běhu přesně stejně.</span><span class="sxs-lookup"><span data-stu-id="fa16d-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="fa16d-123">V tomto jednoduchém příkladu se metoda definovaná mimo `Main` metodu jeví jako trochu nadbytečné.</span><span class="sxs-lookup"><span data-stu-id="fa16d-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="fa16d-124">.NET Framework 2,0 představil koncept *anonymních delegátů*, který umožňuje vytvořit "vložené" delegáty bez nutnosti zadat jakýkoliv další typ nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="fa16d-125">V následujícím příkladu anonymní delegát filtruje seznam pouze s sudými čísly a pak je vytiskne do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fa16d-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="fa16d-126">Jak vidíte, tělo delegáta je pouze sada výrazů, jako jakýkoli jiný delegát.</span><span class="sxs-lookup"><span data-stu-id="fa16d-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="fa16d-127">Ale namísto toho, že se jedná o samostatnou definici, zavedli jsme v našem volání metody _ad hoc_ <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa16d-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="fa16d-128">Nicméně i s tímto přístupem existuje stále spousta kódu, který můžeme vrátit.</span><span class="sxs-lookup"><span data-stu-id="fa16d-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="fa16d-129">Toto je místo, kde se dodávají *výrazy lambda* .</span><span class="sxs-lookup"><span data-stu-id="fa16d-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="fa16d-130">Výrazy lambda nebo pouze "výrazy lambda" pro krátkou hodnotu byly představeny v jazyce C# 3,0 jako jeden ze základních stavebních bloků jazyka LINQ (Language Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="fa16d-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="fa16d-131">Jsou to pouze pohodlnější syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="fa16d-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="fa16d-132">Deklaruje signaturu a tělo metody, ale nemají oficiální identitu své vlastní, pokud nejsou přiřazeni delegátovi.</span><span class="sxs-lookup"><span data-stu-id="fa16d-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="fa16d-133">Na rozdíl od delegátů lze přímo přiřadit jako levou stranu registrace události nebo v různých klauzulích a metodách LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa16d-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="fa16d-134">Vzhledem k tomu, že výraz lambda je pouze dalším způsobem určení delegáta, by měl být možné přepsat výše uvedený vzorek tak, aby namísto anonymního delegáta používal výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="fa16d-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="fa16d-135">V předchozím příkladu je použit výraz lambda `i => i % 2 == 0` .</span><span class="sxs-lookup"><span data-stu-id="fa16d-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="fa16d-136">Znovu je to pouze praktická syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="fa16d-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="fa16d-137">Co se stane v rámci pokrývání, je podobné tomu jako u anonymního delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa16d-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="fa16d-138">Výrazy lambda jsou znovu pouze delegáty, což znamená, že je možné je použít jako obslužná rutina události bez jakýchkoli problémů, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="fa16d-139">`+=`Operátor v tomto kontextu slouží k přihlášení k odběru [události](../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="fa16d-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="fa16d-140">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="fa16d-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="fa16d-141">Další materiály a materiály pro čtení</span><span class="sxs-lookup"><span data-stu-id="fa16d-141">Further reading and resources</span></span>

* [<span data-ttu-id="fa16d-142">Delegáti</span><span class="sxs-lookup"><span data-stu-id="fa16d-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="fa16d-143">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="fa16d-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="fa16d-144">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="fa16d-144">Lambda expressions</span></span>](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
