---
title: Delegáti a lambdas
description: Zjistěte, jak delegáti definice typu, který zadejte podpis konkrétní metody, které je možné volat přímo nebo předán na jinou metodu a volat.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: f8184b87fc62f378fe72138733f87de924da60f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574555"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="d5518-103">Delegáti a lambdas</span><span class="sxs-lookup"><span data-stu-id="d5518-103">Delegates and lambdas</span></span>

<span data-ttu-id="d5518-104">Delegáti definice typu, který zadejte podpis konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="d5518-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="d5518-105">Metody (statické nebo instance), splňuje tento podpis může být přiřazený k proměnné tohoto typu, pak volat přímo (s odpovídající parametry) nebo předat jako argument sám sebe na jinou metodu a pak volat.</span><span class="sxs-lookup"><span data-stu-id="d5518-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="d5518-106">Následující příklad ukazuje použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-106">The following example demonstrates delegate use.</span></span>

```csharp
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

*   <span data-ttu-id="d5518-107">Na řádku 4 vytvoříme typem delegáta určité podpisu v takovém případě metodu která přijímá řetězcový parametr a vrátí parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="d5518-107">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="d5518-108">Na řádku 6 jsme definovali implementace delegát tím, že poskytuje metodu, která má přesný stejným podpisem.</span><span class="sxs-lookup"><span data-stu-id="d5518-108">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="d5518-109">Na řádku 13 metodu přiřazen typ, který odpovídá `Reverse` delegovat.</span><span class="sxs-lookup"><span data-stu-id="d5518-109">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="d5518-110">Nakonec na řádku 15 jsme vyvolání delegáta předávání řetězec tak, aby vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="d5518-110">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="d5518-111">Zjednodušilo procesu vývoje, .NET zahrnuje sadu delegáta typy, které můžete opakovaně používat a není nutné vytvářet nové typy programátory v jazyce.</span><span class="sxs-lookup"><span data-stu-id="d5518-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="d5518-112">Jedná se o `Func<>`, `Action<>` a `Predicate<>`, a že lze použít na různých místech .NET API bez nutnosti definování nových typů delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="d5518-113">Samozřejmě existují určité rozdíly mezi tří jak uvidíte v jejich podpisy, které se většinou mají způsobem, jakým, které byly určeny k použití:</span><span class="sxs-lookup"><span data-stu-id="d5518-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="d5518-114">`Action<>` používá se při je zapotřebí k provedení akce pomocí argumentů delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="d5518-115">`Func<>` používá se obvykle při transformaci mít k dispozici, to znamená, budete muset transformace argumenty delegáta do jiné výsledky.</span><span class="sxs-lookup"><span data-stu-id="d5518-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="d5518-116">Projekce jsou typickým příkladem tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="d5518-116">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="d5518-117">`Predicate<>` používá se při potřebujete zjistit, pokud argument splňuje podmínky delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="d5518-118">Můžete zapsat také jako `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="d5518-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="d5518-119">Jsme teď můžete provést v našem příkladu výše a přepište pomocí `Func<>` delegovat místo vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="d5518-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="d5518-120">Tento program bude dále běžet stejně.</span><span class="sxs-lookup"><span data-stu-id="d5518-120">The program will continue running exactly the same.</span></span>

```csharp
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

<span data-ttu-id="d5518-121">V tomto příkladu jednoduché s metody definované mimo metodu Main() zdá se, že trochu nadbytečné.</span><span class="sxs-lookup"><span data-stu-id="d5518-121">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="d5518-122">Je to způsobeno tím, který rozhraní .NET Framework 2.0 zaveden koncept **anonymní delegáti**.</span><span class="sxs-lookup"><span data-stu-id="d5518-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="d5518-123">S jejich podporu budete moci vytvořit delegáti "vložené" bez nutnosti zadávat žádné další typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="d5518-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="d5518-124">Můžete jednoduše vložené definici delegáta, kde je nutné.</span><span class="sxs-lookup"><span data-stu-id="d5518-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="d5518-125">Příklad přidáme přepnout nahoru a pak použijte naše anonymní delegáta filtrovat seznam pouze sudým číslům a pak je tisk do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d5518-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="d5518-126">Všimněte si, zvýrazněné řádky.</span><span class="sxs-lookup"><span data-stu-id="d5518-126">Notice the highlighted lines.</span></span> <span data-ttu-id="d5518-127">Jak je vidět text delegáta je jenom sada výrazů, jako ostatní delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-127">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="d5518-128">Místo bylo definici samostatné zavedli jsme ji, ale _ad hoc_ naše volání `FindAll()` metodu `List<T>` typu.</span><span class="sxs-lookup"><span data-stu-id="d5518-128">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="d5518-129">Ale i s tímto přístupem přetrvává mnohem kód, který jsme ji okamžitě výjimku.</span><span class="sxs-lookup"><span data-stu-id="d5518-129">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="d5518-130">To je, kdy **výrazy lambda** možné uplatnit.</span><span class="sxs-lookup"><span data-stu-id="d5518-130">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="d5518-131">Lambda – výrazy nebo jednoduše "lambdas" pro zkrácení, byly zavedeny nejprve v C# 3.0, jako jednu ze základní stavební bloky z jazyka integrovaného dotazu (LINQ).</span><span class="sxs-lookup"><span data-stu-id="d5518-131">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="d5518-132">Jsou to jenom pohodlnější syntaxe pro použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="d5518-132">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="d5518-133">Deklarovat podpis a metoda text, ale nemají své vlastní, formální identity, pokud jsou přiřazeny k delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-133">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="d5518-134">Na rozdíl od delegáti se může být přímo přiřazeni jako na levé straně registrace události nebo v různých klauzule Linq a metody.</span><span class="sxs-lookup"><span data-stu-id="d5518-134">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="d5518-135">Výraz lambda je další způsob, jak zadávání delegáta, jsme byste měli mít přepisování ukázka výše pro použití výrazu lambda místo delegáta anonymní.</span><span class="sxs-lookup"><span data-stu-id="d5518-135">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
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

<span data-ttu-id="d5518-136">Pokud jste si prohlédněte zvýrazněné řádky, uvidíte, jak vypadá výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="d5518-136">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="d5518-137">Znovu, je právě **velmi** vhodné syntaxe pro použití delegátů, co se stane skrytě je podobná co se stane s anonymní delegáta.</span><span class="sxs-lookup"><span data-stu-id="d5518-137">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="d5518-138">Lambdas znovu, jsou právě delegáti, což znamená, že je lze použít jako obslužnou rutinu události bez problémů, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="d5518-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

## <a name="further-reading-and-resources"></a><span data-ttu-id="d5518-139">Další čtení a prostředky</span><span class="sxs-lookup"><span data-stu-id="d5518-139">Further reading and resources</span></span>

*   [<span data-ttu-id="d5518-140">Delegáti</span><span class="sxs-lookup"><span data-stu-id="d5518-140">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="d5518-141">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="d5518-141">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="d5518-142">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="d5518-142">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
