---
title: "Čísla v jazyce C# kurzu - C# místní – elementy QuickStart"
description: "Výuka C# prozkoumáním číselnými typy, jejich vlastnosti a metody."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9a8b28d840d3c8ef63611e9f584e5984e1dcb1a3
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="numbers-in-c-quickstart"></a>Čísla v jazyce C# rychlý start

Tento rychlý start se dozvíte, jaké číslo typy v jazyku C# interaktivně. Napíšete malé množství kódu a potom budete zkompilování a spuštění tohoto kódu. Rychlý Start obsahuje řadu lekce, které prozkoumat matematické operace v jazyce C# a čísla. Tyto poznatky získají naučit základy jazyka C#.

Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Prozkoumejte matematické celé číslo

Vytvořte adresář s názvem **čísla – rychlý Start**. Ujistěte, že aktuální adresář a spusťte `dotnet new console -n NumbersInCSharp -o .`.

Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.Writeline("Hello World!");` následujícím kódem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spuštění tohoto kódu zadáním `dotnet run` v příkazovém okně. 

Seznámili jste se právě jeden z základní matematické operace s celými čísly. `int` Zadejte představuje **celé číslo**, kladné a záporné celé číslo. Můžete použít `+` symbol pro přidání. Další běžné matematické operace pro celá čísla zahrnují:

- `-`pro odčítání
- `*`pro násobení
- `/`pro dělení

Začít seznamovat se tyto jiné operace. Přidejte tyto řádky po řádek, který zapíše hodnota `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Spuštění tohoto kódu zadáním `dotnet run` v příkazovém okně. 
    
Můžete vyzkoušet tak, že provedete více operací Matematika na stejném řádku, pokud vás zajímají. Zkuste `c = a + b - 12 * 17;` třeba. Kombinování proměnné a čísla konstantní je povolen.

> [!TIP]
> Jak můžete prozkoumat jazyka C# (nebo žádný programovací jazyk), uděláte budete chyby při psaní kódu. **Kompilátoru** vyhledá tyto chyby a sestav je pro vás. Když výstup obsahuje chybové zprávy, podívejte se úzce na ukázkový kód a kód v okně zobrazíte co opravit.
> Tento úkol vám pomohou naučit struktury kódu C#.     

Prvním krokem dokončíte. Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě. Který usnadňuje začít pracovat s novou příklad. Přejmenujte vaše `Main` metodu `WorkingWithIntegers` a zápis nový `Main` metoda, která volá `WorkingWithIntegers`. Po dokončení, váš kód by měl vypadat například takto:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>Prozkoumejte pořadí operací

Komentář volání `WorkingWithIntegers()`. To bude dávat výstup, který menší zaplněny, při práci v této části:

```csharp
//WorkingWithIntegers();
```

`//` Spustí **komentář** v jazyce C#. Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nemůžou provést jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

Jazyk C# definuje prioritu různých Matematika operací s pravidly konzistentní s pravidly, že jste se naučili v Matematika.
Násobení a dělení mají přednost před sčítání a odečítání.
Prozkoumejte, přidáním následující kód do vaší `Main` metoda a execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Výstup ukazuje, že násobení se provádí před přidání.

Můžete vynutit jiném pořadí operace přidáním v závorkách operaci nebo operace, které chcete provést první. Přidejte následující řádky a znovu spusťte:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Prozkoumejte více kombinací mnoha různých operací. Přidat něco jako následující řádky na konci vaší `Main` metoda. Zkuste `dotnet run` znovu.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Možná jste si všimli zajímavé chování celých čísel. Celočíselné dělení vždy vytvoří celé číslo, i v případě, že by uživatel očekával výsledek, který má zahrnout desetinné nebo zlomkové části.

Pokud toto chování ještě neviděli, zkuste následující kód na konci vaší `Main` metoda:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Typ `dotnet run` znovu a zobrazte si výsledky.

Než budete pokračovat, podívejme všechny kód jsme vytvořené v této části a umístí jej do nové metody. Volání této nové metody `OrderPrecedence`.
Měli skončili s přibližně takto:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Prozkoumejte přesnost celé číslo a omezení
Tento posledního vzorku vám ukázal, že celočíselné dělení zkrátí výsledek.
Můžete získat **zbývající** pomocí **modulo** operátor, `%` znak. Zkuste následující kód ve vaší `Main` metoda:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ integer jazyka C# se liší od matematickém celých čísel jeden jiným způsobem: `int` typ má minimální a maximální meze. Přidejte tento kód, aby vaše `Main` metoda zobrazíte tato omezení:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud výpočtu slouží k vytvoření hodnoty, které tato omezení překročí, máte **podtečení** nebo **přetečení** podmínku. Zdá se, že odpověď zabalení z limitu jeden na druhý. Přidejte tyto dva řádky do vaší `Main` metoda zobrazíte příklad:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Všimněte si, že odpověď je velmi brzy bude dosaženo minimální (záporné) celé číslo. Je stejný jako `min + 2`. Operace přidání **došlo k přetečení** povolené hodnoty pro celá čísla.
Odpověď je velmi velké záporné číslo, protože přetečení "obtéká" z největší možné celočíselnou hodnotu po nejmenší.

Existují další číselnými typy s jinou omezení a přesnost, že by se použijte, když `int` typ nevyhovuje vašim potřebám. Podíváme se na tyto další.

Přejděme znovu, kód, který jste napsali v této části do samostatné metodě. Pojmenujte ji `TestLimits`. 

## <a name="work-with-the-double-type"></a>Práce s typ double

`double` Číselného typu představuje číslo s plovoucí desetinnou dvojitou přesností. Tyto podmínky může být pro vás nový. A **plovoucí desetinnou čárkou** číslo je užitečné k reprezentaci bez integrální čísla, která může být velmi velké nebo malé řádově. **Dvojitá přesnost** znamená, že tato čísla ukládat pomocí přesností větší než **jednoduchou přesností**. Na počítačích moderní je dnes běžné používat Dvojitá přesnost než čísla s jednoduchou přesností.
Podíváme se na. Přidejte následující kód a zobrazit výsledky:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Všimněte si, že odpověď obsahuje desetinná část podílu. Zkuste něco víc složitý výraz s hodnoty Double:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Rozsah hodnota typu double je mnohem větší než celočíselné hodnoty. Zkuste následující kód níže, co jste vytvořili, pokud:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Tyto hodnoty jsou vytiskne v exponenciální notace. Číslo směrem doleva od `E` je mantisy. Číslo, které má právo je exponent, jako druhou mocninou 10. 

Stejně jako desetinná čísla v matematické může mít hodnoty Double v jazyce C# zaokrouhlení chyby. Zkuste tento kód:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Víte, že `0.3` opakující se právě není stejný jako `1/3`.

***Výzvy***

Zkuste jiné výpočty s velká čísla, malá čísla, násobení a dělení pomocí `double` typu.  Zkuste složitější výpočty.

Jakmile jste stráví chvíli s otázkou, trvat kód jsme zapsané a jeho následné uložení do nové metody. Název této nové metody `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Práce s pevnou bodu typy

Seznámili jste se základní číselnými typy v jazyku C#: celá čísla a hodnoty Double.  Neexistuje jeden další typ. Další: `decimal` typu. `decimal` Typ má menší oblast ale přesností větší než `double`. Termín **pevné bodu** znamená, že se nepřesune desetinné čárky (nebo binární bodu). Podívejme se:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Všimněte si, že rozsah je menší, než `double` typu. Větší přesnost s typ decimal, můžete zjistit tak, že zkusíte následující kód:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Příponu na čísla, která je, jak můžete označit, že by měl použít konstanta `decimal` typu.

Všimněte si, že výpočty pomocí typu decimal obsahuje více číslic vpravo od desetinné čárky. 

***Výzvy***

Teď, když jste se seznámili s různými typy číselné, napište kód, který vypočítá oblasti jejichž radius je 2.50 palce kruh. Mějte na paměti, že oblast kruhu je radius spolehlivosti násobí hodnotou platformy. Jeden pomocný parametr: .NET obsahuje konstanty pro platformy, <xref:System.Math.PI?displayProperty=nameWithType> , můžete použít pro tuto hodnotu. 

Měli byste obdržet odpověď až 19, 20.
Můžete zkontrolovat vaše odpověď podle [prohlížení dokončení ukázkový kód na Githubu](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

Pokud chcete, zkuste některé jiné vzorce. 

Jste dokončili rychlé spuštění "čísla v C#". Můžete pokračovat [větve a smyčky](branches-and-loops-local.md) rychlé spuštění ve vašem vývojovém prostředí.

Další informace o čísla v jazyce C# v následujících tématech:

[Tabulka celočíselných typů](../language-reference/keywords/integral-types-table.md)   
[Tabulka typů s plovoucí desetinnou čárkou](../language-reference/keywords/floating-point-types-table.md)   
[Tabulka předdefinovaných typů](../language-reference/keywords/built-in-types-table.md)   
[Tabulka implicitních číselných převodů](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tabulka explicitních číselných převodů](../language-reference/keywords/explicit-numeric-conversions-table.md)

