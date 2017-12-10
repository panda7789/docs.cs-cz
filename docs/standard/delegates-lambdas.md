---
title: "Delegáti a lambdas"
description: "Zjistěte, jak delegáti definice typu, který zadejte podpis konkrétní metody, které je možné volat přímo nebo předán na jinou metodu a volat."
keywords: "Rozhraní .NET, .NET core"
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: c348c36caeaf703a99336f1d2a8f6cdbe5968b99
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="delegates-and-lambdas"></a>Delegáti a lambdas

Delegáti definice typu, který zadejte podpis konkrétní metody. Metody (statické nebo instance), splňuje tento podpis může být přiřazený k proměnné tohoto typu, pak volat přímo (s odpovídající parametry) nebo předat jako argument sám sebe na jinou metodu a pak volat. Následující příklad ukazuje použití delegáta.

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

*   Na řádku 4 vytvoříme typem delegáta určité podpisu v takovém případě metodu která přijímá řetězcový parametr a vrátí parametr řetězce.
*   Na řádku 6 jsme definovali implementace delegát tím, že poskytuje metodu, která má přesný stejným podpisem.
*   Na řádku 13 metodu přiřazen typ, který odpovídá `Reverse` delegovat.
*   Nakonec na řádku 15 jsme vyvolání delegáta předávání řetězec tak, aby vrátit zpět.

Zjednodušilo procesu vývoje, .NET zahrnuje sadu delegáta typy, které můžete opakovaně používat a není nutné vytvářet nové typy programátory v jazyce. Jedná se o `Func<>`, `Action<>` a `Predicate<>`, a že lze použít na různých místech .NET API bez nutnosti definování nových typů delegáta. Samozřejmě existují určité rozdíly mezi tří jak uvidíte v jejich podpisy, které se většinou mají způsobem, jakým, které byly určeny k použití:

*   `Action<>`používá se při je zapotřebí k provedení akce pomocí argumentů delegáta.
*   `Func<>`používá se obvykle při transformaci mít k dispozici, to znamená, budete muset transformace argumenty delegáta do jiné výsledky. Projekce jsou typickým příkladem tohoto objektu.
*   `Predicate<>`používá se při potřebujete zjistit, pokud argument splňuje podmínky delegáta. Můžete zapsat také jako `Func<T, bool>`.

Jsme teď můžete provést v našem příkladu výše a přepište pomocí `Func<>` delegovat místo vlastního typu. Tento program bude dále běžet stejně.

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

V tomto příkladu jednoduché s metody definované mimo metodu Main() zdá se, že trochu nadbytečné. Je to způsobeno tím, který rozhraní .NET Framework 2.0 zaveden koncept **anonymní delegáti**. S jejich podporu budete moci vytvořit delegáti "vložené" bez nutnosti zadávat žádné další typ nebo metoda. Můžete jednoduše vložené definici delegáta, kde je nutné.

Příklad přidáme přepnout nahoru a pak použijte naše anonymní delegáta filtrovat seznam pouze sudým číslům a pak je tisk do konzoly.

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

Všimněte si, zvýrazněné řádky. Jak je vidět text delegáta je jenom sada výrazů, jako ostatní delegáta. Místo bylo definici samostatné zavedli jsme ji, ale _ad hoc_ naše volání `FindAll()` metodu `List<T>` typu.

Ale i s tímto přístupem přetrvává mnohem kód, který jsme ji okamžitě výjimku. To je, kdy **výrazy lambda** možné uplatnit.

Lambda – výrazy nebo jednoduše "lambdas" pro zkrácení, byly zavedeny nejprve v C# 3.0, jako jednu ze základní stavební bloky z jazyka integrovaného dotazu (LINQ). Jsou to jenom pohodlnější syntaxe pro použití delegátů. Deklarovat podpis a metoda text, ale nemají své vlastní, formální identity, pokud jsou přiřazeny k delegáta. Na rozdíl od delegáti se může být přímo přiřazeni jako na levé straně registrace události nebo v různých klauzule Linq a metody.

Výraz lambda je další způsob, jak zadávání delegáta, jsme byste měli mít přepisování ukázka výše pro použití výrazu lambda místo delegáta anonymní.

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

Pokud jste si prohlédněte zvýrazněné řádky, uvidíte, jak vypadá výrazu lambda. Znovu, je právě **velmi** vhodné syntaxe pro použití delegátů, co se stane skrytě je podobná co se stane s anonymní delegáta.

Lambdas znovu, jsou právě delegáti, což znamená, že je lze použít jako obslužnou rutinu události bez problémů, jak ukazuje následující fragment kódu.

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

## <a name="further-reading-and-resources"></a>Další čtení a prostředky

*   [Delegáti](../../docs/csharp/programming-guide/delegates/index.md)
*   [Anonymní funkce](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Lambda – výrazy](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
