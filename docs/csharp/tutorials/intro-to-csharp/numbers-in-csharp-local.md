---
title: Čísla v C# – kurz Úvod do C#
description: Naučte se v jazyce C# prozkoumat číselné typy, jejich použití, vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 3dc2a5afc6321da45351525a632f586cb84bf7fe
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794608"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulace s čísly integrálových a plovoucích bodů v jazyce C\#

V tomto kurzu se naučíte, že číselné typy v C# interaktivně. Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód. Kurz obsahuje řadu lekcí, které probírají čísla a matematické operace v jazyce C#. V těchto kurzech se seznámíte se základy jazyka C#.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Seznámení s matematikou celých čísel

Vytvořte adresář s názvem *Numbers – rychlý Start*. Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

V oblíbeném editoru otevřete *program.cs* a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` do příkazového okna.

Viděli jste jednu ze základních matematických operací s celými čísly. `int` Typ představuje **celé číslo**, nula, kladné nebo záporné celé číslo. Pro sčítání se používá symbol `+`. K dalším běžným matematickým operacím s celými čísly patří tyto:

- `-` pro odčítání
- `*` pro násobení
- `/` pro dělení

Nejdřív si vyzkoušejte uvedené operace. Přidejte tyto řádky za řádek, který zapisuje hodnotu `c`:

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

Spusťte tento kód zadáním `dotnet run` do příkazového okna.

Můžete také experimentovat vytvořením více matematických operací na stejném řádku, pokud byste chtěli. Zkuste `c = a + b - 12 * 17;` například. Jsou povoleny kombinace proměnných a konstantních čísel.

> [!TIP]
> Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby. **Kompilátor** tyto chyby odhalí a upozorní vás na ně. Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.
> Toto cvičení vám pomůže seznámit se se strukturou kódu v C#.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `Main` metodu `WorkingWithIntegers` na a napište novou `Main` metodu, která `WorkingWithIntegers`volá. Až skončíte, váš kód by měl vypadat takto:

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

Zakomentujte volání do `WorkingWithIntegers()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//WorkingWithIntegers();
```

`//` Spustí **Komentář** v jazyce C#. Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

Jazyk C# definuje prioritu různých matematických operací v souladu se stejnými pravidly, jaká jste se naučili při hodinách matematiky.
Násobení a dělení mají přednost před sčítáním a odčítáním.
Prozkoumejte to přidáním následujícího kódu do `Main` metody a provedením příkazu: `dotnet run`

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Z výstupu vyplývá, že operace násobení se provede dřív než operace sčítání.

Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operací, které chcete provést jako první. Přidejte následující řádky a spusťte znovu:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Teď prozkoumáme i další možnosti s kombinací několika různých operací. V dolní části `Main` metody přidejte něco podobného jako následující řádky. Znovu zkuste příkaz `dotnet run`.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Můžete si u celých čísel všimnout zvláštního chování. Výsledkem dělení celých čísel je vždycky celé číslo, i když byste očekávali, že bude výsledek obsahovat číslo s desetinnou čárkou nebo zlomek.

Pokud jste toto chování neviděli, vyzkoušejte následující kód na konci vaší `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Pro `dotnet run` zobrazení výsledků zadejte znovu.

Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody. Zavolejte tuto novou metodu `OrderPrecedence`.
Měli byste napsat něco podobného:

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
**Zbytek** můžete získat pomocí operátoru **modulo** , `%` znaku. Vyzkoušejte následující kód v `Main` metodě:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Od celých čísel v matematice se typ integer v jazyce C# se liší v jednom ohledu: typ `int` má minimální a maximální limit. Přidejte tento kód do `Main` metody, abyste viděli tato omezení:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud je výsledkem určitého výpočtu hodnota, která tyto limity překračuje, nastane stav **podtečení** nebo **přetečení**. Odpověď cyklicky přechází od jednoho limitu k druhému. Přidejte tyto dva řádky do `Main` metody, abyste viděli příklad:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Všimněte si, že se odpověď těsně blíží minimálnímu (zápornému) celému číslu. Je stejná jako při operaci `min + 2`.
Operace sčítání **přetekla** povolené hodnoty celých čísel.
Výsledkem je velmi velké záporné číslo, protože při přetečení došlo k „cyklickému přechodu“ od nejvyšší možné celočíselné hodnoty k nejnižší.

Existují i další číselné typy s různými limity a přesností, které můžete použít, pokud typ `int` nevyhovuje vašim potřebám. Pojďme prozkoumat další typy.

Později můžete kód, který jste napsali v této části, přesunout do samostatné metody. Pojmenujte ji `TestLimits`.

## <a name="work-with-the-double-type"></a>Práce s typem double

Číselný typ `double` představuje číslo s plovoucí desetinnou čárkou a dvojitou přesností. Tyto výrazy možná ještě neznáte. Číslo s **plovoucí desetinnou čárkou** slouží k reprezentaci jiných než celých čísel, která mohou být buď velmi nízká, nebo velmi vysoká. **Dvojitá přesnost** je relativní termín, který popisuje počet binárních číslic, které se použily k uložení hodnoty. Čísla **Dvojitá přesnosti** mají dvojnásobek počtu binárních číslic jako s **jednoduchou přesností**. Na moderních počítačích je častější používat dvojitou přesnost než čísla s jednoduchou přesností. Čísla s **jednou přesností** jsou deklarována pomocí `float` klíčového slova.
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

Rozsah hodnoty double je mnohem větší než u hodnot typu integer. Vyzkoušejte následující kód, který jste doposud napsali:

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

Víte, že `0.3` opakování není přesně stejné jako `1/3`.

***Úloha***

Vyzkoušejte další výpočty s velkými čísly, malými čísly, násobení a dělení `double` pomocí typu. Zkuste zadat i složitější výpočty.

Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody. Pojmenujte tuto `WorkWithDoubles`novou metodu.

## <a name="work-with-decimal-types"></a>Práce s typy Decimal

Seznámili jste se se základními typy čísel v jazyce C#: celými čísly a čísly s dvojitou přesností.  Existuje jeden další typ, který se naučí: `decimal` typ. Typ `decimal` má menší rozsah, ale zato větší přesnost než typ `double`. Podívejme se na to:

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

Přípona `M` za čísly představuje způsob, jak naznačit, že má konstanta používat typ `decimal`. V opačném případě kompilátor předpokládá `double` typ.

> [!NOTE]
> Písmeno `M` bylo vybráno jako nejvizuálně jedinečné písmeno mezi klíčovými `double` slovy `decimal` a.

Všimněte si, že výsledek s typem decimal má napravo od desetinné čárky víc číslic.

***Úloha***

Seznámili jste se s různými typy čísel a teď můžete napsat kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru. Obsah kruhu se vypočítá jako poloměr na druhou krát číslo pí. Nápověda: Prostředí .NET obsahuje pro číslo pí konstantu <xref:System.Math.PI?displayProperty=nameWithType>, kterou můžete pro tuto hodnotu použít. <xref:System.Math.PI?displayProperty=nameWithType>Podobně jako všechny konstanty deklarované v `System.Math` oboru názvů je `double` hodnota. Z `double` `decimal` tohoto důvodu byste měli použít místo hodnot pro tuto výzvu.

Měl by vám vyjít výsledek mezi 19 a 20.
Odpověď si můžete [prohlédnout na stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Jestli chcete, můžete si vyzkoušet i další vzorce.

Dokončili jste rychlý Start "Numbers in C#". Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.

Další informace o číslech v jazyce C# najdete v následujících článcích:

- [Celočíselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Předdefinované číselné převody](../../language-reference/builtin-types/numeric-conversions.md)
