---
title: Čísla v C# úvodu k C# kurzu
description: Naučte C# se prozkoumat číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7537bb597665461021946a792e342149f29c0e95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694657"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulace s čísly integrálních a plovoucích bodů v jazyce C\#

V tomto kurzu se naučíte, aby se číselné C# typy v interaktivně. Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód. Kurz obsahuje řadu lekcí, které prozkoumají čísla a matematické operace v C#. V těchto kurzech se seznámíte se základy jazyka C#.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Seznámení s matematikou celých čísel

Vytvořte adresář s názvem *Numbers – rychlý Start*. Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte `Console.WriteLine("Hello World!");` řádku následujícím způsobem:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` v příkazovém okně.

Právě jste viděli jednu ze základních matematických operací s celými čísly. Typ `int` představuje **celé**číslo, nula, kladné nebo záporné celé číslo. Pro sčítání se používá symbol `+`. K dalším běžným matematickým operacím s celými čísly patří tyto:

- `-` pro odčítání
- `*` pro násobení
- `/` pro dělení

Nejdřív si vyzkoušejte uvedené operace. Přidejte tyto řádky za řádek, který zapíše hodnotu `c`:

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

Spusťte tento kód zadáním `dotnet run` v příkazovém okně.

Pokud chcete, můžete taky experimentovat a provést několik matematických operací na jednom řádku. Zkuste například `c = a + b - 12 * 17;`. Jsou povoleny kombinace proměnných a konstantních čísel.

> [!TIP]
> Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby. **Kompilátor** tyto chyby odhalí a upozorní vás na ně. Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.
> Toto cvičení vám pomůže seznámit se se strukturou kódu v C#.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte metodu `Main` na `WorkingWithIntegers` a zapište novou `Main` metodu, která volá `WorkingWithIntegers`. Až skončíte, váš kód by měl vypadat takto:

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

Odkomentujte volání `WorkingWithIntegers()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//WorkingWithIntegers();
```

`//` spustí **Komentář** v C#. Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

Jazyk C# definuje prioritu různých matematických operací v souladu se stejnými pravidly, jaká jste se naučili při hodinách matematiky.
Násobení a dělení mají přednost před sčítáním a odčítáním.
Prozkoumejte to přidáním následujícího kódu do metody `Main` a spuštěním `dotnet run`:

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

Teď prozkoumáme i další možnosti s kombinací několika různých operací. V dolní části metody `Main` přidejte něco jako na následující řádky. Znovu zkuste příkaz `dotnet run`.

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

Opětovným zadáním `dotnet run` zobrazíte výsledky.

Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody. Zavolejte novou metodu `OrderPrecedence`.
Měli byste skončit přibližně takto:

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
**Zbytek** můžete získat pomocí operátoru **modulo** , `%`ho znaku. Vyzkoušejte následující kód v metodě `Main`:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Od celých čísel v matematice se typ integer v jazyce C# se liší v jednom ohledu: typ `int` má minimální a maximální limit. Přidejte tento kód do metody `Main`, abyste viděli tato omezení:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud je výsledkem určitého výpočtu hodnota, která tyto limity překračuje, nastane stav **podtečení** nebo **přetečení**. Odpověď cyklicky přechází od jednoho limitu k druhému. Přidejte tyto dva řádky do metody `Main`, abyste viděli příklad:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Všimněte si, že se odpověď těsně blíží minimálnímu (zápornému) celému číslu. Je stejná jako při operaci `min + 2`.
Operace sčítání **přetekla** povolené hodnoty celých čísel.
Výsledkem je velmi velké záporné číslo, protože při přetečení došlo k „cyklickému přechodu“ od nejvyšší možné celočíselné hodnoty k nejnižší.

Existují i další číselné typy s různými limity a přesností, které můžete použít, pokud typ `int` nevyhovuje vašim potřebám. Pojďme se teď na ně podívat.

Později můžete kód, který jste napsali v této části, přesunout do samostatné metody. Pojmenujte ji `TestLimits`.

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

Víte, že hodnota `0.3` periodických přesně neodpovídá hodnotě `1/3`.

***Výzva***

Vyzkoušejte si různé výpočty s vysokými čísly, nízkými čísly, násobením a dělením za použití typu `double`. Zkuste zadat i složitější výpočty.

Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody. Pojmenujte novou metodu `WorkWithDoubles`.

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

***Výzva***

Seznámili jste se s různými typy čísel a teď můžete napsat kód, který vypočítá obsah kruhu s poloměrem 2,50 centimetru. Obsah kruhu se vypočítá jako poloměr na druhou krát číslo pí. Nápověda: Prostředí .NET obsahuje pro číslo pí konstantu <xref:System.Math.PI?displayProperty=nameWithType>, kterou můžete pro tuto hodnotu použít.

Měl by vám vyjít výsledek mezi 19 a 20.
Odpověď si můžete [prohlédnout na stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Jestli chcete, můžete si vyzkoušet i další vzorce.

Dokončili jste rychlý Start s čísly C#. Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.

Další informace o číslech v jazyce C# se dozvíte v následujících tématech:

- [Celočíselné číselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
- [Číselné typy s plovoucí desetinnou čárkou](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Předdefinované číselné převody](../../language-reference/builtin-types/numeric-conversions.md)
