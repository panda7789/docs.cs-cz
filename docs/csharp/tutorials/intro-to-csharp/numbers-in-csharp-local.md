---
title: Čísla v C# - Úvod do kurzu Jazyka C#
description: Naučte se C# zkoumáním číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7e9af4b3b859f74d7e92ff10b3964ddd59d2473b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156542"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulace s čísly integrální choda a plovoucí desetinnou desetinnou tázkem v C\#

Tento kurz vás naučí o číselné typy v C# interaktivně. Napíšete malé množství kódu, pak budete kompilovat a spouštět tento kód. Kurz obsahuje řadu lekcí, které zkoumají čísla a matematické operace v C#. V těchto kurzech se seznámíte se základy jazyka C#.

Tento kurz očekává, že budete mít počítač, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS. Rychlý přehled příkazů, které budete používat, najdete v části [Seznamte se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Seznámení s matematikou celých čísel

Vytvořte adresář s názvem *numbers-quickstart*. Proveďte aktuální adresář a spusťte následující příkaz:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Otevřete *Program.cs* v oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spusťte tento `dotnet run` kód zadáním příkazového okna.

Právě jste viděli jednu ze základních matematických operací s celými čísly. Typ `int` představuje **celé číslo**, nulové, kladné nebo záporné celé číslo. Pro sčítání se používá symbol `+`. K dalším běžným matematickým operacím s celými čísly patří tyto:

- `-` pro odčítání
- `*` pro násobení
- `/` pro dělení

Nejdřív si vyzkoušejte uvedené operace. Za řádek, který zapisuje hodnotu `c`: : přidejte tyto řádky.

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

Spusťte tento `dotnet run` kód zadáním příkazového okna.

Pokud chcete, můžete taky experimentovat a provést několik matematických operací na jednom řádku. Zkuste `c = a + b - 12 * 17;` například. Míchání proměnných a konstantních čísel je povoleno.

> [!TIP]
> Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby. **Kompilátor** tyto chyby odhalí a upozorní vás na ně. Pokud výstup obsahuje chybové zprávy, podívejte se pozorně na ukázkový kód a kód v okně a zjistěte, co opravit.
> Toto cvičení vám pomůže seznámit se se strukturou kódu v C#.

Dokončil jsi první krok. Než začnete další část, přesuneme aktuální kód do samostatné metody. To usnadňuje začít pracovat s novým příkladem. Přejmenujte `Main` metodu na `WorkingWithIntegers` `Main` a napište novou metodu, která volá `WorkingWithIntegers`. Po dokončení by měl kód vypadat takto:

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

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
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

Zakomentujte `WorkingWithIntegers()`volání na . To bude výstup méně přeplněný, jak budete pracovat v této části:

```csharp
//WorkingWithIntegers();
```

Spustí `//` **komentář** v c#. Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nespustí jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

Jazyk C# definuje prioritu různých matematických operací v souladu se stejnými pravidly, jaká jste se naučili při hodinách matematiky.
Násobení a dělení mají přednost před sčítáním a odčítáním.
Prozkoumejte to přidáním následujícího kódu do metody `Main` a provedením `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Z výstupu vyplývá, že operace násobení se provede dřív než operace sčítání.

Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operace, které chcete provést jako první. Přidejte následující řádky a spusťte znovu:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Teď prozkoumáme i další možnosti s kombinací několika různých operací. V dolní části metody `Main` přidejte něco jako následující řádky. Znovu zkuste příkaz `dotnet run`.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Můžete si u celých čísel všimnout zvláštního chování. Výsledkem dělení celých čísel je vždycky celé číslo, i když byste očekávali, že bude výsledek obsahovat číslo s desetinnou čárkou nebo zlomek.

Pokud jste toto chování neviděli, vyzkoušejte na `Main` konci metody následující kód:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Chcete-li zobrazit výsledky, zadejte `dotnet run` znovu.

Než budete pokračovat, vezmeme veškerý kód, který jste napsali v této části, a vložíme jej do nové metody. Volání této `OrderPrecedence`nové metody .
Měli byste skončit s něčím jako toto:

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

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
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

            d = (a + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a>Seznámení s přesností a limity celých čísel

Z poslední ukázky jste se dozvěděli, že při dělení celých čísel dochází ke zkrácení výsledku.
Zbytek můžete **remainder** získat pomocí operátoru **modulo,** znaku. `%` Vyzkoušejte v metodě `Main` následující kód:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Od celých čísel v matematice se typ integer v jazyce C# se liší v jednom ohledu: typ `int` má minimální a maximální limit. Přidejte tento `Main` kód do metody, abyste viděli tyto limity:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud je výsledkem určitého výpočtu hodnota, která tyto limity překračuje, nastane stav **podtečení** nebo **přetečení**. Odpověď cyklicky přechází od jednoho limitu k druhému. Chcete-li zobrazit `Main` příklad, přidejte do metody tyto dva řádky:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Všimněte si, že se odpověď těsně blíží minimálnímu (zápornému) celému číslu. Je stejná jako při operaci `min + 2`.
Operace sčítání **přetekla** povolené hodnoty celých čísel.
Výsledkem je velmi velké záporné číslo, protože při přetečení došlo k „cyklickému přechodu“ od nejvyšší možné celočíselné hodnoty k nejnižší.

Existují i další číselné typy s různými limity a přesností, které můžete použít, pokud typ `int` nevyhovuje vašim potřebám. Pojďme se teď na ně podívat.

Ještě jednou přesuneme kód, který jste napsali v této části do samostatné metody. Pojmenujte ji `TestLimits`.

## <a name="work-with-the-double-type"></a>Práce s typem double

Číselný typ `double` představuje číslo s plovoucí desetinnou čárkou a dvojitou přesností. Tyto výrazy možná ještě neznáte. Číslo s **plovoucí desetinnou čárkou** slouží k reprezentaci jiných než celých čísel, která mohou být buď velmi nízká, nebo velmi vysoká. **Dvojitá přesnost** znamená, že se tato čísla ukládají s větší přesností než s **jednoduchou přesností**. V moderních počítačích se častěji používají čísla s dvojitou přesností než s jednoduchou přesností.
Pojďme se na to podívat blíž. Přidejte následující kód a podívejte se na výsledek:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Všimněte si, že odpověď obsahuje desetinnou část podílu. Teď zkusíme zadat o něco složitější výraz s čísly typu double:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

Rozsah hodnoty double je mnohem větší než u hodnot typu integer. Zkuste následující kód níže, co jste napsali tak daleko:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Hodnoty jsou uvedené za použití vědeckého zápisu čísel. Číslu vlevo od písmene `E` se říká mantisa. Číslo vpravo se označuje jako exponent a značí násobky 10.

Stejně jako desetinná čísla v matematice můžou mít i hodnoty typu double v C# chyby zaokrouhlení. Vyzkoušejte tento kód:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Víte, že hodnota `0.3` periodických přesně neodpovídá hodnotě `1/3`.

***Úloha***

Vyzkoušejte si různé výpočty s vysokými čísly, nízkými čísly, násobením a dělením za použití typu `double`. Zkuste zadat i složitější výpočty.

Poté, co jste strávili nějaký čas s výzvou, vezměte kód, který jste napsali, a umístěte jej do nové metody. Pojmenujte `WorkWithDoubles`tuto novou metodu .

## <a name="work-with-fixed-point-types"></a>Práce s typy s pevnou desetinnou čárkou

Seznámili jste se se základními typy čísel v jazyce C#: celými čísly a čísly s dvojitou přesností.  Zbývá už jenom jeden další typ, `decimal`. Typ `decimal` má menší rozsah, ale zato větší přesnost než typ `double`. Výraz **pevná desetinná čárka** znamená, že se desetinná (neboli řádová) čárka nepohybuje. Podívejme se na to:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Všimněte si, že je rozsah menší než u typu `double`. Větší přesnost typu decimal si můžete ověřit zadáním následujícího kódu:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Přípona `M` za čísly představuje způsob, jak naznačit, že má konstanta používat typ `decimal`.

Všimněte si, že výsledek s typem decimal má napravo od desetinné čárky víc číslic.

***Úloha***

Seznámili jste se s různými typy čísel a teď můžete napsat kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru. Obsah kruhu se vypočítá jako poloměr na druhou krát číslo pí. Nápověda: Prostředí .NET obsahuje pro číslo pí konstantu <xref:System.Math.PI?displayProperty=nameWithType>, kterou můžete pro tuto hodnotu použít.

Měl by vám vyjít výsledek mezi 19 a 20.
Odpověď můžete zkontrolovat [tak, že se podíváte na hotový ukázkový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Jestli chcete, můžete si vyzkoušet i další vzorce.

Dokončili jste rychlý start "Čísla v C#". Můžete pokračovat s [větvemi a smyčkami](branches-and-loops-local.md) rychlý start ve vlastním vývojovém prostředí.

Další informace o číslech v jazyce C# se dozvíte v následujících tématech:

- [Celočíselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Předdefinované číselné převody](../../language-reference/builtin-types/numeric-conversions.md)
