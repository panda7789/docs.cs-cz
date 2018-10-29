---
title: Čísla v C# – Úvod do C# kurz
description: Přečtěte si C# prozkoumáním číselné typy, vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 52feb91fc011902f1e30f6b747512a7e0908bfbf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197454"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Čísla s plovoucí desetinnou čárkou a integrální bod v manipulaci sC# #

V tomto kurzu se dozvíte, jaké typy čísel v C# interaktivně. Budete psát malé množství kódu a pak budete kompilace a spuštění tohoto kódu. Tento kurz obsahuje sérii lekcí, které se zabývají čísly a matematickými operacemi v C#. Tato lekce vás naučí základy jazyka C#.

V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj. Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux. Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Prozkoumejte matematikou celých čísel

Vytvořte adresář **čísla quickstart**. Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console -n NumbersInCSharp -o .`.

Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.Writeline("Hello World!");` následujícím kódem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Tento kód spustit zadáním `dotnet run` v příkazovém okně. 

Právě jste viděli jednu ze základních matematických operací s celými čísly. `int` Zadejte představuje **celé číslo**, kladné nebo záporné celé číslo. Můžete použít `+` symbol pro přidání. Dalším běžným matematickým operacím pro celá čísla zahrnují:

- `-` pro odčítání
- `*` pro násobení
- `/` pro dělení

Nejdřív si vyzkoušejte uvedené operace. Přidejte tyto řádky po řádek, který zapíše hodnoty `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Tento kód spustit zadáním `dotnet run` v příkazovém okně. 
    
Můžete taky experimentovat a provést několik matematických operací na jednom řádku, pokud byste o ni. Zkuste `c = a + b - 12 * 17;` třeba. Kombinování proměnné a konstanty čísla je povolen.

> [!TIP]
> Když se budete učit, C# (nebo libovolným programovacím jazykem), budete se při psaní kódu dělat chyby. **Kompilátoru** se tyto chyby odhalí a dejte nám o nich na vás. Pokud výstup obsahuje chybové zprávy, prohlédněte si blíže ukázkový kód a kód v okně zobrazit, co je potřeba opravit.
> Toto cvičení vám pomůže seznámit se se strukturou kódu jazyka C#.     

Dokončili jste první krok. Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě. Který usnadňuje začít pracovat s nový příklad. Přejmenovat váš `Main` metodu `WorkingWithIntegers` a napsat nový `Main` metodu, která volá `WorkingWithIntegers`. Jakmile budete hotovi, váš kód by měl vypadat takto:

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

## <a name="explore-order-of-operations"></a>Seznámení s pořadím operací

Odkomentujte volání `WorkingWithIntegers()`. Bude výstup, který zaplněný při práci v této části:

```csharp
//WorkingWithIntegers();
```

`//` Spustí **komentář** v C#. Komentáře jsou jakýkoli text, který chcete ponechat ve zdrojovém kódu, ale nemůžou provést jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

Jazyk C# definuje prioritu různých matematických operací pravidla souladu se stejnými pravidly, že jste se naučili v matematice.
Úlohy násobení a dělení přednost před sčítáním a odčítáním.
Vyzkoušejte si to tak, že přidáte následující kód do vašeho `Main` metoda a provádění `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Z výstupu vyplývá, operace násobení se provede dřív než operace sčítání.

Jiné pořadí operací můžete vynutit závorek uzavřením operace nebo operací, které chcete provést jako první. Přidejte následující řádky a znovu spusťte:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Teď prozkoumáme i další kombinací několika různých operací. Přidat něco podobného následující řádky na konci vaší `Main` metody. Zkuste `dotnet run` znovu.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Mohli jste si všimnout zvláštního chování pro celá čísla. Dělení celého čísla vždy vytváří celé číslo výsledku, i když byste očekávali bude výsledek obsahovat desetinné nebo zlomkové části.

Pokud toto chování nezaznamenali, zkuste následující kód na konci vaší `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Typ `dotnet run` znovu, abyste viděli výsledek.

Než budete pokračovat, Pojďme se na veškerý kód jsme napsané v této části a vložit ho do nové metody. Volání této nové metody `OrderPrecedence`.
By měla skončit s vypadat přibližně takto:

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

## <a name="explore-integer-precision-and-limits"></a>Prozkoumat celé číslo přesnosti a omezení
Z poslední ukázky vám ukázal, že dělení celého čísla zkrátí výsledek.
Můžete získat **zbývající** pomocí **modulo** operátoru `%` znak. Následující kód ve vašich `Main` metody:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Typ integer jazyka C# se liší od matematické celých čísel v jednom ohledu: `int` typ má minimální a maximální mezí. Přidejte tento kód, aby vaše `Main` metoda tyto limity zjistíte:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud výsledkem určitého výpočtu hodnota, která tyto limity překračuje, máte **podtečení** nebo **přetečení** podmínku. Zobrazí se odpověď cyklicky přechází od jednoho limitu k druhému. Přidejte následující dva řádky do vaší `Main` metoda k prohlédnutí příkladu:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Všimněte si, že odpověď těsně blíží minimální (zápornému) celému číslu. Je stejný jako `min + 2`. Operace sčítání **došlo k přetečení** povolené hodnoty celých čísel.
Odpověď je velmi velké záporné číslo, protože přetečení "cyklickému přechodu" od nejvyšší možné celočíselné hodnoty k nejnižší.

Existují další číselné typy s různými limity a přesností, můžete použít, pokud `int` typu nevyhovuje vašim potřebám. Podíváme se na ně podívat.

Ještě jednou přejdeme kód, který jste napsali v této části do samostatné metodě. Pojmenujte ji `TestLimits`. 

## <a name="work-with-the-double-type"></a>Práce s typem double

`double` Číselného typu představuje číslo s plovoucí desetinnou dvojitou přesností. Tyto výrazy možná pro vás nová. A **s plovoucí desetinnou čárkou** číslo slouží k reprezentaci jiných než celých čísel, která může být velmi velké nebo velmi vysoká. **Dvojité přesnosti** znamená, že tato čísla ukládají s větší přesností než **jednoduchou přesností**. V moderních počítačích se častěji používají s dvojitou přesností než čísla a jednoduchou přesností.
Zkusíme zjistit. Přidejte následující kód a zobrazit výsledek:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Všimněte si, že odpověď obsahuje desetinnou část podílu. Try – o něco složitější výraz s čísly typu Double:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Rozsah hodnoty double je mnohem větší než u hodnot typu integer. Vyzkoušejte následující co jste napsali zatím následující kód:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Tyto hodnoty jsou vytiskne zapsaný exponenciální notací. Číslo vlevo od `E` se říká mantisa. Exponent, je číslo vpravo jako mocninu 10. 

Stejně jako desetinná čísla v matematice můžou mít typu Double v C# chyby zaokrouhlení. Vyzkoušejte tento kód:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Víte, že `0.3` periodických přesně neodpovídá stejný jako `1/3`.

***Výzvy***

Vyzkoušejte si různé výpočty s velkým, malé čísly, násobením a dělením za použití `double` typu.  Zkuste složitější výpočty.

Jakmile strávili jste už nějakou dobu s výzvou, trvat, než kód napsali a umístěte ho do nové metody. Název této nové metody `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Práce s typy s pevnou desetinnou čárkou

Seznámili jste se základními typy čísel v jazyce C#: celými čísly a čísly typu Double.  Existuje jeden další typ: `decimal` typu. `decimal` Má menší rozsah, ale zato větší přesnost než typ `double`. Termín **Pevná desetinná** znamená, že desetinné čárky (nebo řádová) čárka nepohybuje. Podívejme se na to:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Všimněte si, že je rozsah menší, než `double` typu. Větší přesnost typu decimal můžete zobrazit pomocí následujícího kódu:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Přípona u čísel je způsob, jak naznačit, že má konstanta používat `decimal` typu.

Všimněte si, že výsledek s typem decimal má napravo od desetinné čárky víc číslic. 

***Výzvy***

Teď, když jste se seznámili s různými typy čísel, psát kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru. Mějte na paměti, že obsah kruhu je jako poloměr na druhou krát číslo PÍ. Jeden pomocný parametr: .NET obsahuje pro číslo PÍ konstantu <xref:System.Math.PI?displayProperty=nameWithType> , můžete použít pro tuto hodnotu. 

By vám vyjít výsledek mezi 19 a 20.
Můžete zkontrolovat odpověď podle [prohlížení dokončení ukázkového kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

Pokud chcete, vyzkoušejte i další vzorce. 

Dokončili jste "čísla v C#" rychlý start. Můžete pokračovat [větve a smyčky](branches-and-loops-local.md) rychlý start ve svém vlastním vývojovém prostředí.

Další informace o číslech v jazyce C# v následujících tématech:

[Tabulka celočíselných typů](../../language-reference/keywords/integral-types-table.md)   
[Tabulka typů s plovoucí desetinnou čárkou](../../language-reference/keywords/floating-point-types-table.md)   
[Tabulka předdefinovaných typů](../../language-reference/keywords/built-in-types-table.md)   
[Tabulka implicitních číselných převodů](../../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tabulka explicitních číselných převodů](../../language-reference/keywords/explicit-numeric-conversions-table.md)
