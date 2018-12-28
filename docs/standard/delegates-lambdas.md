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
# <a name="delegates-and-lambdas"></a>Delegáty a výrazy lambda

Delegáti definice typu, která zadejte konkrétní metody podpis. Metody (statická nebo instance), který splňuje tento podpis být přiřazen proměnné tohoto typu, pak můžete volat přímo (s příslušnými argumenty) nebo předán jako samotný argument jiné metodě a následném zavolání. Následující příklad ukazuje použití delegáta.

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

* `public delegate string Reverse(string s);` Řádek vytvoří delegát typu určité podpis, v tomto případě metodu, která přijímá řetězcový parametr a vrátí parametr řetězce.
* `static string ReverseString(string s)` Metodu, která má přesně stejný podpis jako typ definovaný delegát, implementuje delegáta.
* `Reverse rev = ReverseString;` Čára ukazuje, že můžete přiřadit metody proměnné odpovídající typ delegáta.
* `Console.WriteLine(rev("a string"));` Řádku ukazuje, jak použít proměnné typu delegáta k vyvolání delegáta.

Aby bylo možné zjednodušit proces vývoje, .NET obsahuje sadu typy delegátu, které programátoři můžou opakovaně používat a není nutné vytvářet nové typy. Jedná se o `Func<>`, `Action<>` a `Predicate<>`, a že lze použít na různých místech v rámci rozhraní .NET API bez nutnosti definovat nové typy delegátů. Samozřejmě existují určité rozdíly mezi třemi jak uvidíte v jejich podpisy, které většinou se tak, jak byly určeny pro použití:

*   `Action<>` se používá, když je potřeba provést akci na základě argumentů delegáta.
*   `Func<>` se používá, obvykle v případě, že máte transformaci na stranu, to znamená, je potřeba získat argumenty delegáta z jiné výsledky. Projekce jsou typickým příkladem tohoto objektu.
*   `Predicate<>` používá se při je potřeba určit, pokud argument splňuje podmínky delegáta. Lze zapsat také jako `Func<T, bool>`.

Jsme teď můžete provést v našem příkladu výše a jeho pomocí přepsání `Func<>` delegovat místo vlastního typu. Program bude dál běžet stejně.

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

Tento jednoduchý příklad, s definované mimo metodu `Main` metoda vypadá trochu nadbytečný. Je proto, že rozhraní .NET Framework 2.0 byl zaveden koncept **anonymní delegáti**. Díky jejich podpoře je možné k vytváření delegátů "vloženě" bez nutnosti zadávat žádné další typu nebo metody. Můžete jednoduše vložené definice delegáta, kde ji potřebujete.

Příklad budeme přepínání nahoru a pomocí našich anonymního delegáta vyfiltrovat seznam pouze sudých čísel a zapisuje je do konzole.

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

Jak je vidět text delegáta je jenom sada výrazů, jako jakýkoli delegát. Místo je samostatný definice, zavedli jsme ji, ale _ad hoc_ v našich volání <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.

Ale i s tímto přístupem je stále, jaká část kódu, který jsme může vyvolat okamžitě. Tady **výrazy lambda** souvisejí.

Výrazy lambda, nebo jenom "výrazy lambda" zkráceně, byly zavedeny nejprve v C# 3.0 jako jeden ze základních stavebních bloků z Language Integrated Query (LINQ). Jsou to jenom pohodlnější syntaxe pro použití delegátů. Deklarovat podpis a tělo metody, ale nemají své vlastní, formální identitu, pokud jsou přiřazeny k delegáta. Na rozdíl od delegáty se může být přímo přiřazeni jako na levé straně, registrace událostí nebo v různých klauzule LINQ a metody.

Výraz lambda je další způsob určení delegáta, jsme měli být schopni přepsat předchozí ukázka použití lambda výrazů namísto anonymního delegáta.

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

V předchozím příkladu používá výraz lambda je `i => i % 2 == 0`. Znovu jde jenom **velmi** pohodlné syntaxe pro použití delegátů, tak co se stane, že na pozadí je podobný co se stane s anonymního delegáta.

Znovu výrazy lambda jsou pouze delegáty, což znamená, že může sloužit jako obslužná rutina události bez problémů, jak ukazuje následující fragment kódu.

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

`+=` Operátor v tomto kontextu se používá k přihlášení k odběru [události](../../docs/csharp/language-reference/keywords/event.md). Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Další materiály a zdroje

*   [Delegáti](../../docs/csharp/programming-guide/delegates/index.md)
*   [Anonymní funkce](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Výrazy lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
