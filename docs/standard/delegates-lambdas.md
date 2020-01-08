---
title: Delegáty a výrazy lambda
description: Přečtěte si, jak Delegáti definují typ, který určuje konkrétní signaturu metody, kterou lze volat přímo nebo předat jiné metodě a volána.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345544"
---
# <a name="delegates-and-lambdas"></a>Delegáty a výrazy lambda

Delegáti definují typ, který určuje konkrétní signaturu metody. Metoda (static nebo instance), která odpovídá tomuto podpisu, může být přiřazena proměnné tohoto typu, pak volána přímo (s příslušnými argumenty) nebo předána jako argument do jiné metody a následně volána. Následující příklad ukazuje použití delegáta.

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

* `public delegate string Reverse(string s);` řádek vytvoří typ delegáta určité signatury, v tomto případě metodu, která přijímá řetězcový parametr a potom vrátí řetězcový parametr.
* Metoda `static string ReverseString(string s)`, která má přesně stejný podpis jako definovaný typ delegáta, implementuje delegáta.
* `Reverse rev = ReverseString;` řádek ukazuje, že můžete přiřadit metodu proměnné odpovídajícího typu delegáta.
* `Console.WriteLine(rev("a string"));` řádek ukazuje, jak použít proměnnou typu delegáta k vyvolání delegáta.

Aby bylo možné zjednodušit proces vývoje, obsahuje rozhraní .NET sadu typů delegátů, které mohou programátory použít a nikoli vytvářet nové typy. Jedná se o `Func<>`, `Action<>` a `Predicate<>`a dají se použít na různých místech rozhraní API .NET, aniž by bylo potřeba definovat nové typy delegátů. Samozřejmě existuje několik rozdílů mezi těmito třemi, jak vidíte ve svých signaturách, které se většinou musí provádět s způsobem, jakým byly určeny k použití:

* `Action<>` se používá v případě, že je potřeba provést akci pomocí argumentů delegáta.
* `Func<>` se obvykle používá, když máte transformaci, to znamená, že je nutné transformovat argumenty delegáta na jiný výsledek. Projekce jsou hlavními příklady.
* `Predicate<>` se používá v případě, že potřebujete určit, jestli argument splňuje podmínky delegáta. Může být také zapsána jako `Func<T, bool>`.

Nyní můžeme použít náš příklad výše a přepsat ho pomocí `Func<>` delegáta místo vlastního typu. Program bude pokračovat v běhu přesně stejně.

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

V tomto jednoduchém příkladu se metoda definovaná mimo metodu `Main` jeví jako trochu nadbytečné. Důvodem je to, že .NET Framework 2,0 představil koncept **anonymních delegátů**. S jejich podporou můžete vytvořit "vložené" delegáty bez nutnosti zadat jakýkoliv další typ nebo metodu. Stačí jednoduše vložit definici delegáta, kde ho potřebujete.

V tomto příkladu ho převedeme a pomocí našeho anonymního delegáta vyfiltrujete seznam jenom s čísly a pak je vytisknete do konzoly.

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

Jak vidíte, tělo delegáta je pouze sada výrazů, jako jakýkoli jiný delegát. Ale namísto toho, že se jedná o samostatnou definici, jsme v našem volání metody <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> zavedli _ad hoc_ .

Nicméně i s tímto přístupem existuje stále spousta kódu, který můžeme vrátit. Toto je místo, kde se dodávají **výrazy lambda** .

Lambda výrazy nebo pouze "výrazy lambda" pro krátké, byly představeny jako první C# v 3,0 jako jeden ze základních stavebních bloků jazyka LINQ (Language Integrated Query). Jsou to pouze pohodlnější syntaxe pro použití delegátů. Deklaruje signaturu a tělo metody, ale nemají oficiální identitu své vlastní, pokud nejsou přiřazeni delegátovi. Na rozdíl od delegátů lze přímo přiřadit jako levou stranu registrace události nebo v různých klauzulích a metodách LINQ.

Vzhledem k tomu, že výraz lambda je pouze dalším způsobem určení delegáta, by měl být možné přepsat výše uvedený vzorek tak, aby namísto anonymního delegáta používal výraz lambda.

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

V předchozím příkladu je použit výraz lambda `i => i % 2 == 0`. Znovu je to pouze **velmi** pohodlná syntaxe pro použití delegátů, takže co se stane v rámci pokrývání je podobné tomu jako u anonymního delegáta.

Výrazy lambda jsou znovu pouze delegáty, což znamená, že je možné je použít jako obslužná rutina události bez jakýchkoli problémů, jak ukazuje následující fragment kódu.

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

Operátor `+=` v tomto kontextu slouží k přihlášení k odběru [události](../../docs/csharp/language-reference/keywords/event.md). Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.

## <a name="further-reading-and-resources"></a>Další materiály a materiály pro čtení

* [Delegáti](../../docs/csharp/programming-guide/delegates/index.md)
* [Anonymní funkce](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Výrazy lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
