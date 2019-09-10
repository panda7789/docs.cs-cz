---
title: Čísla v C# úvodu k C# kurzu
description: Naučte C# se prozkoumat číselné typy, jejich vlastnosti a metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850691"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipulace s čísly integrálových a plovoucích bodů v jazyce C\#

V tomto kurzu se naučíte, aby se číselné C# typy v interaktivně. Budete psát malé množství kódu, potom zkompilujete a spustíte tento kód. Kurz obsahuje řadu lekcí, které prozkoumají čísla a matematické operace v C#. V těchto lekcích se naučíte základy C# jazyka.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="explore-integer-math"></a>Prozkoumat celočíselné matematické

Vytvořte adresář s názvem **Numbers – rychlý Start**. Zajistěte, aby byl aktuální `dotnet new console -n NumbersInCSharp -o .`adresář a běžel.

V oblíbeném editoru otevřete **program.cs** a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` do příkazového okna.

Právě jste viděli jednu ze základních matematických operací s celými čísly. Typ představuje celé číslo, kladné nebo záporné celé číslo. `int` `+` Symbol se používá pro sčítání. Mezi další běžné matematické operace pro celá čísla patří:

- `-`pro odčítání
- `*`pro násobení
- `/`pro dělení

Začněte tím, že prozkoumáte tyto různé operace. Přidejte tyto řádky za řádek, který zapisuje hodnotu `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Spusťte tento kód zadáním `dotnet run` do příkazového okna.

Můžete také experimentovat při provádění více matematických operací na stejném řádku, pokud byste chtěli. Zkuste `c = a + b - 12 * 17;` například. Jsou povoleny kombinace proměnných a konstantních čísel.

> [!TIP]
> Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby. **Kompilátor** tyto chyby vyhledá a nahlásí je. Pokud výstup obsahuje chybové zprávy, Prohlédněte si v příkladu kód a kód v okně, co je třeba opravit.
> Toto cvičení vám pomůže zjistit strukturu C# kódu.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `WorkingWithIntegers` `Main` `WorkingWithIntegers`metodu na a napište novou metodu, která volá. `Main` Až budete hotovi, váš kód by měl vypadat takto:

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

## <a name="explore-order-of-operations"></a>Prozkoumat pořadí operací

Zakomentujte volání do `WorkingWithIntegers()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//WorkingWithIntegers();
```

Spustí komentář v C#. `//` Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

C# Jazyk definuje prioritu různých matematických operací s pravidly, která jsou v souladu s pravidly, která jste se naučili v matematice.
Násobení a dělení mají přednost před sčítáním a odčítáním.
Prozkoumejte to přidáním následujícího kódu do `Main` metody a provedením příkazu: `dotnet run`

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Výstup ukazuje, že násobení je provedeno před sčítáním.

Můžete vynutit jiné pořadí operací přidáním závorek kolem operace nebo operací, které chcete provést jako první. Přidejte následující řádky a spusťte znovu:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Kombinování různých operací vám umožní prozkoumat víc. V dolní `Main` části metody přidejte něco podobného jako následující řádky. Zkuste `dotnet run` to znovu.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Možná jste si všimli zajímavého chování pro celá čísla. Celočíselné dělení vždy vytváří celočíselný výsledek, i když byste očekávali, že by výsledek zahrnoval desítkovou nebo zlomkovou část.

Pokud jste toto chování neviděli, vyzkoušejte následující kód na konci vaší `Main` metody:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Pro `dotnet run` zobrazení výsledků zadejte znovu.

Než začnete pokračovat, Pojďme si z tohoto oddílu pořizovat veškerý kód, který jste napsali, a vložte ho do nové metody. Zavolejte tuto novou metodu `OrderPrecedence`.
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

## <a name="explore-integer-precision-and-limits"></a>Prozkoumat celočíselnou přesnost a omezení

Poslední ukázka ukázala, že dělení celého čísla zkráte výsledek.
**Zbytek** můžete získat pomocí `%` operátoru **modulo** , znaku. Vyzkoušejte následující kód v `Main` metodě:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# Celočíselný typ se liší od matematických celých čísel jiným způsobem: `int` typ má minimální a maximální limity. Přidejte tento kód do `Main` metody, abyste viděli tato omezení:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Pokud výpočet vytvoří hodnotu, která překračuje tato omezení, **dojde k podtečení nebo** **podtečení** . Odpověď se zobrazí jako zabalení od jednoho limitu k druhému. Přidejte tyto dva řádky do `Main` metody, abyste viděli příklad:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Všimněte si, že odpověď se velmi blíží minimálnímu (zápornému) celému číslu. Je stejný jako `min + 2`.
Operace sčítání **přetéká** povolené hodnoty pro celá čísla.
Odpověď je velmi velké záporné číslo, protože přetečení se zalomí od největší možné celočíselné hodnoty k nejmenší.

Existují i jiné číselné typy s různými limity a přesností, které byste použili, `int` když typ nevyhovuje vašim potřebám. Pojďme se podívat na další.

Později můžete kód, který jste napsali v této části, přesunout do samostatné metody. Pojmenujte ji `TestLimits`.

## <a name="work-with-the-double-type"></a>Práce s typem Double

`double` Číselný typ představuje číslo s dvojitou přesností a plovoucí desetinnou čárkou. Tyto výrazy můžou být pro vás nové. Číslo s **plovoucí desetinnou** čárkou je užitečné k vyjádření neintegrálních čísel, která mohou být velmi velká nebo malá. **Dvojitá přesnost** znamená, že se tato čísla ukládají s větší přesností než s **jednoduchou přesností**. Na moderních počítačích je častější používat dvojitou přesnost než čísla s jednoduchou přesností.
Pojďme prozkoumat. Přidejte následující kód a podívejte se na výsledek:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Všimněte si, že odpověď obsahuje desetinnou část podílu. Vyzkoušejte trochu složitější výraz s dvojitou přesností:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Rozsah hodnoty Double je mnohem větší než celočíselné hodnoty. Vyzkoušejte následující kód, který jste doposud napsali:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Tyto hodnoty se tisknou v matematickém zápisu. Číslo nalevo od `E` je mantisa. Číslo vpravo je exponent, jako mocnina 10.

Stejně jako desítková čísla v matematických případech můžou C# být v uvozovkách chyby zaokrouhlení. Vyzkoušejte tento kód:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Víte, že `0.3` opakování není přesně stejné jako. `1/3`

***Výzev***

Zkuste další výpočty s velkými čísly, malými čísly, násobení a `double` dělení pomocí typu.  Vyzkoušejte složitější výpočty.

Po vykonání nějakého času u výzvy Vezměte kód, který jste napsali, a umístěte ho do nové metody. Pojmenujte tuto `WorkWithDoubles`novou metodu.

## <a name="work-with-fixed-point-types"></a>Práce s pevnými typy bodů

Viděli jste základní číselné typy v C#: celá čísla a Dvojitá přesnost.  Existuje jeden další typ, který se naučí: `decimal` typ. Typ má menší rozsah, ale větší přesnost než `double`. `decimal` **Pevný** bod znamená, že desetinná čárka (nebo binární bod) nepřesouvá. Podívejme se na to:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Všimněte si, že rozsah je menší než `double` typ. Větší přesnost s typem Decimal můžete zobrazit tak, že zkusíte následující kód:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Přípona čísel představuje způsob, jakým by měl být `decimal` typ konstanty použit. `M`

Všimněte si, že matematický použití typu Decimal má na pravé straně desetinné čárky více číslic.

***Výzev***

Teď, když jste viděli různé číselné typy, napište kód, který vypočítá oblast kruhu, jehož poloměr je 2,50 centimetrů. Pamatujte, že oblast kruhu je poloměr čtvercového vynásobený hodnotou pí. Jedna Nápověda: .NET obsahuje konstantu pro PI, <xref:System.Math.PI?displayProperty=nameWithType> kterou můžete použít pro tuto hodnotu.

Měli byste získat odpověď mezi 19 a 20.
Svou odpověď si můžete prohlédnout na [stránce dokončený vzorový kód na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) .

Pokud chcete, zkuste použít jiné vzorce.

Dokončili jste rychlý Start s čísly C#. Můžete pokračovat v rychlém startu [větví a smyček](branches-and-loops-local.md) ve vlastním vývojovém prostředí.

Další informace o číslech v C# najdete v následujících tématech:

- [Celočíselné typy](../../language-reference/builtin-types/integral-numeric-types.md)
- [Tabulka typů s plovoucí desetinnou čárkou](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Tabulka předdefinovaných typů](../../language-reference/keywords/built-in-types-table.md)
- [Tabulka implicitních číselných převodů](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../../language-reference/keywords/explicit-numeric-conversions-table.md)
