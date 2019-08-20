---
title: Větve a smyčky – Úvod k C# kurzu
description: V tomto kurzu o větvích a smyčkách napíšete C# kód pro zkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 0da446a71f5d7a7183a8323c470087c8726bc02f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587222"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Další informace o podmíněné logice s příkazy větví a smyček

V tomto kurzu se naučíte, jak napsat kód, který kontroluje proměnné a mění cestu spuštění na základě těchto proměnných. Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které se seznámí s konstrukcemi větvení a smyček v C#. V těchto lekcích se naučíte základy C# jazyka.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Téma rozhraní .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v počítačích Mac, PC nebo Linux. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodnutí pomocí `if` příkazu

Vytvořte adresář s názvem **větve – kurz**. Zajistěte, aby byl aktuální `dotnet new console -n BranchesAndLoops -o .`adresář a běžel. Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

V oblíbeném editoru otevřete **program.cs** a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Tento kód zkuste zadat `dotnet run` v okně konzoly. Měla by se zobrazit zpráva "odpověď je větší než 10." vytištěno do konzoly.

Upravte deklaraci `b` tak, aby součet byl menší než 10:

```csharp
int b = 3;
```

Zadejte `dotnet run` znovu. Vzhledem k tomu, že odpověď je menší než 10, nic se nevytiskne. **Podmínka** , kterou testujete, je nepravdivá. Nemáte žádný kód, který by bylo možné provést, protože jste zadali pouze jednu z možných větví pro `if` příkaz: jedinou větví.

> [!TIP]
> Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby. Kompilátor najde a nahlásí chyby. Prohlédněte si úzce na výstupu chyby a kódu, který chybu generoval. Chyba kompilátoru může obvykle pomohly najít problém.

Tento první příklad ukazuje sílu `if` a logické typy. *Logická hodnota* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`. C#definuje speciální typ `bool` pro logické proměnné. Příkaz kontroluje hodnotu `bool`. `if` Pokud je `true`hodnota, příkaz `if` následující po spuštění. V opačném případě se přeskočí.

Tento proces kontroly podmínek a provádění příkazů založených na těchto podmínkách je velmi výkonný.

## <a name="make-if-and-else-work-together"></a>Nastavit, zda a jinak spolupracovat

Chcete-li spustit jiný kód v větvích true i false, vytvořte `else` větev, která se spustí, když je podmínka nepravdivá. Zkuste to. Přidejte poslední dva řádky v kódu níže do vaší `Main` metody (měli byste už mít první čtyři):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Příkaz následující `else` za klíčovým slovem se spustí pouze v případě, `false`že podmínka je testována. `if` Kombinování `else` a s logickými podmínkami poskytuje veškerou sílu, kterou `true` potřebujete ke `false` zpracování podmínky a.

> [!IMPORTANT]
> Odsazení pod `if` příkazy a `else` je pro lidské čtenáře.
> C# Jazyk nezpracovává odsazení ani prázdné znaky jako významné.
> Příkaz následující `if` za klíčovým `else` slovem nebo se spustí na základě podmínky. Všechny ukázky v tomto kurzu se řídí běžným postupem odsazení řádků na základě toku řízení příkazů.

Vzhledem k tomu, že odsazení není důležité, je nutné `{` použít `}` a k označení, zda chcete, aby bylo více než jeden příkaz součástí bloku, který je spuštěn podmíněně. C#programátoři obvykle používají tyto složené závorky u `if` všech `else` klauzulí a. Následující příklad je stejný jako ten, který jste právě vytvořili. Upravte kód výše tak, aby odpovídal následujícímu kódu:

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Ve zbývající části tohoto kurzu obsahuje ukázka kódu všechny složené závorky, a to po přijatých postupech.

Můžete testovat složitější podmínky. Do své `Main` metody přidejte následující kód za dosud napsaný kód:

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

Testy symbolů pro *rovnost.* `==` Použití `==` rozlišuje test pro rovnost z přiřazení, které jste viděli v `a = 5`.

`&&` Představuje "a". To znamená, že obě podmínky musí mít hodnotu true, aby se příkaz spustil ve větvi true.  Tyto příklady také ukazují, že můžete mít více příkazů v každé podmíněných větvích za předpokladu, `{` že `}`jsou uzavřeny v a.

Můžete také použít `||` k reprezentaci "nebo". Po tom, co jste napsali, přidejte následující kód:

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

Umožňuje `a`upravit hodnoty `||` , `b`a `c` a přepínat mezi `&&` a a prozkoumat. Získáte lepší znalosti o tom, jak `&&` operátory a `||` fungují.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `ExploreIf` `Main` `ExploreIf`metodu na a napište novou metodu, která volá. `Main` Až budete hotovi, váš kód by měl vypadat takto:

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Zakomentujte volání do `ExploreIf()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//ExploreIf();
```

Spustí komentář v C#. `//` Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Opakování operací pomocí smyček

V této části použijete **smyčky** k opakování příkazů. Vyzkoušejte tento kód v `Main` metodě:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Příkaz zkontroluje podmínku a spustí blok příkazu nebo příkazu `while`za. `while` Opakovaně kontroluje podmínku a spouští tyto příkazy, dokud podmínka nevrátí hodnotu false.

V tomto příkladu je druhý operátor New. Po proměnné je operátor přírůstku. `++` `counter` Přidá 1 k hodnotě `counter` a uloží tuto hodnotu `counter` do proměnné.

> [!IMPORTANT]
> Ujistěte se, že `while` se podmínka smyčky při spuštění kódu změní na false. V opačném případě vytvoříte nekonečnou smyčku, ve které program nikdy nekončí. To není v této ukázce znázorněno, protože je nutné vynutit ukončení programu pomocí **kombinace kláves CTRL-C** nebo jiným způsobem.

Smyčka testuje podmínku před spuštěním kódu `while`za. `while` `do` ... `while` smyčka nejprve spustí kód a poté zkontroluje podmínku. Cyklus do while je zobrazen v následujícím kódu:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Tato `do` smyčka a předchozí `while` smyčka vytvoří stejný výstup.

## <a name="work-with-the-for-loop"></a>Práce s cyklem for

Smyčka **for** se běžně používá v C#. Vyzkoušejte tento kód v metodě Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

To funguje stejně jako `while` smyčka `do` a smyčka, kterou jste už použili. `for` Příkaz má tři části, které řídí, jak to funguje.

První část je **pro inicializátor inicializátoru**: `int index = 0;` deklaruje, že `index` je proměnná smyčky, a nastaví její počáteční hodnotu na `0`.

Střední část je **pro podmínku**: `index < 10` deklaruje, že se tato `for` smyčka pokračuje, dokud hodnota čítače není menší než 10.

Poslední část je **for iterátor**: `index++` určuje, jak se má změnit proměnná smyčky po provedení bloku `for` po příkazu. V tomto případě určuje, `index` že se má při každém spuštění bloku zvýšit o 1.

Vyzkoušejte si je sami. Vyzkoušejte následující:

- Změňte inicializátor tak, aby začínal na jiné hodnotě.
- Změňte podmínku tak, aby se zastavila s jinou hodnotou.

Až to budete mít, pojďme přejít k tomu, abyste si sami napsali kód, abyste mohli používat, co jste se naučili.

## <a name="combine-branches-and-loops"></a>Kombinování větví a smyček

Teď, když jste viděli `if` příkaz a konstruktory cyklů v C# jazyce, se podívejte, jestli můžete napsat C# kód, abyste našli součet všech celých čísel od 1 do 20, která jsou dělitelná 3.  Tady je několik tipů:

- `%` Operátor poskytuje zbytek operace dělení.
- `if` Příkaz poskytuje podmínku pro zjištění, zda číslo by mělo být součástí součtu.
- `for` Smyčka vám může pomáhat zopakovat řadu kroků pro všechna čísla od 1 do 20.

Vyzkoušejte si to sami. Potom zkontrolujte, jak jste to provedli. Měli byste pro odpověď získat 63. Můžete zobrazit jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Dokončili jste kurz "větve a smyčky".

Kurz pro [pole a kolekce](arrays-and-collections.md) můžete pokračovat ve svém vlastním vývojovém prostředí.

Další informace o těchto konceptech najdete v těchto tématech:

- [IF a else – příkaz](../../language-reference/keywords/if-else.md)
- [While – příkaz](../../language-reference/keywords/while.md)
- [Do – příkaz](../../language-reference/keywords/do.md)
- [Příkaz for](../../language-reference/keywords/for.md)
