---
title: Delegáty a výrazy lambda
description: Přečtěte si, jak delegáti, které definují typ, který určuje konkrétní signaturu metody, mohou být volány přímo nebo předány jiné metodě a volána.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 1307599a3832be5f48cd62a7b8c1be7f76a3d4a5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063741"
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

* `public delegate string Reverse(string s);`Řádek vytvoří typ delegáta určité signatury, v tomto případě metodu, která přijímá řetězcový parametr a potom vrátí řetězcový parametr.
* `static string ReverseString(string s)`Metoda, která má přesně stejný podpis jako definovaný typ delegáta, implementuje delegáta.
* `Reverse rev = ReverseString;`Řádek ukazuje, že můžete přiřadit metodu proměnné odpovídajícího typu delegáta.
* `Console.WriteLine(rev("a string"));`Čára ukazuje, jak použít proměnnou typu delegáta k vyvolání delegáta.

Aby bylo možné zjednodušit proces vývoje, obsahuje rozhraní .NET sadu typů delegátů, které mohou programátory použít a nikoli vytvářet nové typy. Tyto typy jsou `Func<>` , `Action<>` a a `Predicate<>` lze je použít bez nutnosti definovat nové typy delegátů. Existují některé rozdíly mezi třemi typy, které je třeba provést s způsobem, jakým byly určeny pro použití:

* `Action<>`se používá v případě, že je potřeba provést akci pomocí argumentů delegáta. Metoda, kterou zapouzdřuje, nevrací hodnotu.
* `Func<>`se obvykle používá v případě, že máte transformaci, to znamená, že je nutné transformovat argumenty delegáta na jiný výsledek. Projekce jsou dobrým příkladem. Metoda, kterou zapouzdřuje, vrátí zadanou hodnotu.
* `Predicate<>`se používá v případě, že potřebujete určit, jestli argument splňuje podmínky delegáta. Může být také zapsána jako `Func<T, bool>` , což znamená, že metoda vrátí logickou hodnotu.

Nyní můžeme použít náš příklad a přepsat ho pomocí `Func<>` delegáta místo vlastního typu. Program bude pokračovat v běhu přesně stejně.

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

V tomto jednoduchém příkladu se metoda definovaná mimo `Main` metodu jeví jako trochu nadbytečné. .NET Framework 2,0 představil koncept *anonymních delegátů*, který umožňuje vytvořit "vložené" delegáty bez nutnosti zadat jakýkoliv další typ nebo metodu.

V následujícím příkladu anonymní delegát filtruje seznam pouze s sudými čísly a pak je vytiskne do konzoly.

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

Jak vidíte, tělo delegáta je pouze sada výrazů, jako jakýkoli jiný delegát. Ale namísto toho, že se jedná o samostatnou definici, zavedli jsme v našem volání metody _ad hoc_ <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> .

Nicméně i s tímto přístupem existuje stále spousta kódu, který můžeme vrátit. Toto je místo, kde se dodávají *výrazy lambda* . Výrazy lambda nebo pouze "výrazy lambda" pro krátkou hodnotu byly představeny v jazyce C# 3,0 jako jeden ze základních stavebních bloků jazyka LINQ (Language Integrated Query). Jsou to pouze pohodlnější syntaxe pro použití delegátů. Deklaruje signaturu a tělo metody, ale nemají oficiální identitu své vlastní, pokud nejsou přiřazeni delegátovi. Na rozdíl od delegátů mohou být přímo přiřazeny jako pravá strana registrace události nebo v různých klauzulích a metodách LINQ.

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

V předchozím příkladu je použit výraz lambda `i => i % 2 == 0` . Znovu je to pouze praktická syntaxe pro použití delegátů. Co se stane v rámci pokrývání, je podobné tomu jako u anonymního delegáta.

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

`+=`Operátor v tomto kontextu slouží k přihlášení k odběru [události](../csharp/language-reference/keywords/event.md). Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.

## <a name="further-reading-and-resources"></a>Další materiály a materiály pro čtení

* [Delegáty](../csharp/programming-guide/delegates/index.md)
* [Anonymní funkce](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Výrazy lambda](../csharp/language-reference/operators/lambda-expressions.md)
