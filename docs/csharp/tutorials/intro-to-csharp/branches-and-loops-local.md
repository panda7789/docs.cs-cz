---
title: Větve a smyčky – Úvod k C# kurzu
description: V tomto kurzu o větvích a smyčkách napíšete C# kód pro zkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: a0701a63d6c3aece6bac4263cbcf8a682a623cf7
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834115"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Další informace o podmíněné logice s příkazy větví a smyček

V tomto kurzu se naučíte, jak napsat kód, který kontroluje proměnné a mění cestu spuštění na základě těchto proměnných. Napíšete C# kód a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které se seznámí s konstrukcemi větvení a smyček v C#. V těchto lekcích se naučíte základy C# jazyka.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodování pomocí příkazu `if`

Vytvořte adresář s názvem *větve – kurz*. Zajistěte, aby byl aktuální adresář a běžel `dotnet new console -n BranchesAndLoops -o .`. Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Ve svém oblíbeném editoru otevřete *program.cs* a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

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

Zadejte `dotnet run` znovu. Vzhledem k tomu, že odpověď je menší než 10, nic se nevytiskne. **Podmínka** , kterou testujete, je nepravdivá. Nemáte žádný kód, který by bylo možné spustit, protože jste zapsali pouze jednu z možných větví pro příkaz `if`: jediná větev true.

> [!TIP]
> Při prozkoumávání C# (nebo jakémkoli programovacím jazyce) budete při psaní kódu dělat chyby. Kompilátor najde a nahlásí chyby. Prohlédněte si úzce na výstupu chyby a kódu, který chybu generoval. Chyba kompilátoru může obvykle pomohly najít problém.

Tento první příklad ukazuje sílu `if` a logických typů. *Logická hodnota* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`. C#definuje speciální typ, `bool` pro logické proměnné. Příkaz `if` kontroluje hodnotu `bool`. Když je hodnota `true`, příkaz následující po `if` se spustí. V opačném případě se přeskočí.

Tento proces kontroly podmínek a provádění příkazů založených na těchto podmínkách je velmi výkonný.

## <a name="make-if-and-else-work-together"></a>Nastavit, zda a jinak spolupracovat

Chcete-li spustit jiný kód v větvích true i false, vytvořte větev `else`, která se spustí, když je podmínka nepravdivá. Zkuste to. Přidejte poslední dva řádky v kódu níže do vaší metody `Main` (měli byste už mít první čtyři):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Příkaz následující za klíčovým slovem `else` se spustí pouze v případě, že podmínka, která je testována, je `false`. Kombinování `if` a `else` s logickými podmínkami poskytuje veškerou sílu, kterou potřebujete ke zpracování podmínky `true` a `false`.

> [!IMPORTANT]
> Odsazení pod příkazy `if` a `else` je pro lidské čtecí zařízení.
> C# Jazyk nezpracovává odsazení ani prázdné znaky jako významné.
> Příkaz následující za klíčovým slovem `if` nebo `else` bude proveden na základě podmínky. Všechny ukázky v tomto kurzu se řídí běžným postupem odsazení řádků na základě toku řízení příkazů.

Vzhledem k tomu, že odsazení není důležité, je nutné použít `{` a `}` k označení, zda chcete, aby více než jeden příkaz byl součástí bloku, který se podmíněně spouští. C#programátoři obvykle používají tyto složené závorky u všech klauzulí `if` a `else`. Následující příklad je stejný jako ten, který jste právě vytvořili. Upravte kód výše tak, aby odpovídal následujícímu kódu:

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

Můžete testovat složitější podmínky. Do své metody `Main` přidejte následující kód za dosud napsaný kód:

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

Testy symbolů `==` pro *rovnost*. Použití `==` rozlišuje test pro rovnost z přiřazení, které jste viděli v `a = 5`.

@No__t-0 představuje "a". To znamená, že obě podmínky musí mít hodnotu true, aby se příkaz spustil ve větvi true.  Tyto příklady také ukazují, že můžete mít v každé podmíněnou větev více příkazů, za předpokladu, že je uzavíráte do `{` a `}`.

@No__t-0 můžete také použít k reprezentaci "nebo". Po tom, co jste napsali, přidejte následující kód:

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

Upravte hodnoty `a`, `b` a `c` a přepínejte mezi `&&` a `||`. Získáte lepší znalosti o tom, jak operátory `&&` a `||` fungují.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte metodu `Main` na `ExploreIf` a zapište novou metodu `Main`, která volá `ExploreIf`. Až budete hotovi, váš kód by měl vypadat takto:

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

Odkomentujte volání `ExploreIf()`. Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//ExploreIf();
```

@No__t-0 spustí **Komentář** v C#. Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Opakování operací pomocí smyček

V této části použijete **smyčky** k opakování příkazů. Vyzkoušejte tento kód v metodě `Main`:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Příkaz `while` zkontroluje podmínku a spustí blok příkazu nebo příkazu za `while`. Opakovaně kontroluje podmínku a spouští tyto příkazy, dokud podmínka nevrátí hodnotu false.

V tomto příkladu je druhý operátor New. @No__t-0 za proměnnou `counter` je operátorem **přírůstku** . Přičte 1 k hodnotě `counter` a uloží tuto hodnotu do proměnné `counter`.

> [!IMPORTANT]
> Ujistěte se, že se při provádění kódu změní podmínka smyčky `while` na hodnotu false. V opačném případě vytvoříte **nekonečnou smyčku** , ve které program nikdy nekončí. To není v této ukázce znázorněno, protože je nutné vynutit ukončení programu pomocí **kombinace kláves CTRL-C** nebo jiným způsobem.

Smyčka `while` testuje podmínku před spuštěním kódu za `while`. Smyčka `do`... `while` spustí nejprve kód a poté zkontroluje podmínku. Cyklus do while je zobrazen v následujícím kódu:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Tato smyčka `do` a předchozí smyčka `while` vytvoří stejný výstup.

## <a name="work-with-the-for-loop"></a>Práce s cyklem for

Smyčka **for** se běžně používá v C#. Vyzkoušejte tento kód v metodě Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

To funguje stejně jako smyčka `while` a smyčka `do`, kterou jste už použili. Příkaz `for` má tři části, které řídí, jak funguje.

První část je **pro inicializátor**: `int index = 0;` deklaruje, že `index` je proměnná smyčky, a nastaví její počáteční hodnotu na `0`.

Střední část je **pro podmínku**: `index < 10` deklaruje, že se tato smyčka `for` bude nadále spouštět, dokud hodnota čítače není menší než 10.

Poslední část je **for iterátor**: `index++` určuje, jak se má změnit proměnná smyčky po provedení bloku následujícího po příkazu `for`. V tomto případě určuje, že `index` by se měla při každém spuštění bloku zvyšovat o 1.

Vyzkoušejte si je sami. Vyzkoušejte následující:

- Změňte inicializátor tak, aby začínal na jiné hodnotě.
- Změňte podmínku tak, aby se zastavila s jinou hodnotou.

Až to budete mít, pojďme přejít k tomu, abyste si sami napsali kód, abyste mohli používat, co jste se naučili.

## <a name="combine-branches-and-loops"></a>Kombinování větví a smyček

Teď, když jste viděli příkaz `if` a konstrukce smyček v C# jazyce, se podívejte, jestli můžete napsat C# kód, abyste našli součet všech celých čísel od 1 do 20, která jsou dělitelná 3.  Tady je několik tipů:

- Operátor `%` poskytuje zbývající část operace dělení.
- Příkaz `if` poskytuje podmínku pro zjištění, zda číslo by mělo být součástí součtu.
- Cyklus `for` vám může pomáhat opakovat řadu kroků pro všechna čísla od 1 do 20.

Vyzkoušejte si to sami. Potom zkontrolujte, jak jste to provedli. Měli byste pro odpověď získat 63. Můžete zobrazit jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Dokončili jste kurz "větve a smyčky".

Kurz pro [pole a kolekce](arrays-and-collections.md) můžete pokračovat ve svém vlastním vývojovém prostředí.

Další informace o těchto konceptech najdete v těchto tématech:

- [IF a else – příkaz](../../language-reference/keywords/if-else.md)
- [While – příkaz](../../language-reference/keywords/while.md)
- [Do – příkaz](../../language-reference/keywords/do.md)
- [Příkaz for](../../language-reference/keywords/for.md)
