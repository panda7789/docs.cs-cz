---
title: Kurz větve a smyčky – C# místní – elementy QuickStart
description: V tento rychlý start o větve a smyčky můžete napsat kód C# a prozkoumejte syntaxi jazyka, která podporuje podmíněného větvení a smyčky provést příkazy opakovaně.
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9a52bafd1536783c59e9e1b92f3ad16b5000ca3b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="branches-and-loops"></a>Větve a smyčky

Tento rychlý start se naučíte, jak napsat kód, který hledá proměnné a změní cesta spuštění na základě těchto proměnných. Psaní kódu jazyka C# a zobrazit výsledky kompilace a jejím spuštěním. Rychlý Start obsahuje řadu lekce, které prozkoumat větvení a opakování ve smyčce konstrukce v jazyce C#. Tyto poznatky získají naučit základy jazyka C#.

Tento rychlý start se očekává, že budete mít počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodnutí, pomocí `if` – příkaz

Vytvořte adresář s názvem **větví – rychlý Start**. Ujistěte, že aktuální adresář a spusťte `dotnet new console -n BranchesAndLoops -o .`. Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Otevřete **Program.cs** v oblíbeném editoru a nahraďte řádku `Console.Writeline("Hello World!");` následujícím kódem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Zkuste tento kód zadáním `dotnet run` v vaše okna konzoly. Zobrazí se zpráva "odpověď je větší než 10." vytištěny konzole.

Upravit deklaraci `b` tak, aby součet menší než 10: 

```csharp
int b = 3;
```

Typ `dotnet run` znovu. Protože odpověď je menší než 10, nic vytisknout. **Podmínku** jste testování je false. Nemáte žádný kód provést, protože jste zapsat pouze jedním z možných větve pro `if` příkaz: true větev.

> [!TIP]
> Jak můžete prozkoumat jazyka C# (nebo žádný programovací jazyk), uděláte budete chyby při psaní kódu. Kompilátor vyhledá a ohlásit chyby. Prohlédněte si blíže výstup chyba a kód, který vytvořil chybu. Chyba compler obvykle vám může pomoci najít problém.

Tento první příklad ukazuje možnosti `if` a Boolean typy. A *Boolean* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`. C# definuje speciální typ `bool` pro logická hodnota proměnné. `if` Příkaz kontroluje hodnotu `bool`. Pokud je hodnota `true`, následující příkaz `if` provede. Jinak se přeskočí.

Tento proces probíhá kontrola podmínky a provádění příkazů na základě těchto podmínek je velice mocný nástroj.

## <a name="make-if-and-else-work-together"></a>Ujistěte se, pokud a jinak spolupracují

Ke spouštění různých kódu v true a false větve, vytvoříte `else` firemní pobočky, který provede, když je podmínka vyhodnocena jako false. Zkuste to. Přidejte poslední dva řádky v kódu níže na vaše `Main` – metoda (byste již měli mít první čtyři):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Následující příkaz `else` – klíčové slovo provede pouze, pokud je podmínka testuje `false`. Kombinování `if` a `else` s logickou hodnotu podmínky poskytuje všechny možnosti je nutné zpracovat oba `true` a `false` podmínku.

> [!IMPORTANT]
> Odsazení pod `if` a `else` příkazy je pro lidské čtečky.
> Jazyk C# nepodporuje považovat za odsazení nebo mezer významné. Následující příkaz `if` nebo `else` – klíčové slovo bude proveden podle stavu. Všechny ukázky tento rychlý start podle běžnou praxí odsazovat řádky založené na toku řízení příkazů.

Protože odsazení není důležité, budete muset použít `{` a `}` označte, když má více než jeden příkaz, který má být součástí blok, který provede podmíněně. Programátory v jazyce C# obvykle používají tyto složené závorky na všech `if` a `else` klauzule. Následující příklad je stejný jako ten, který jste právě vytvořili. Upravte kód výše tak, aby odpovídala následující kód:

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
> Procházení zbytku tento rychlý start, ukázky kódu, všechny zahrnují složené závorky, následující přijata postupy.

Složitější podmínky můžete otestovat. Přidejte následující kód ve vaší `Main` po napsání dosavadní kódu:

```csharp
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
```

`&&` Představuje "a". Znamená to, že musí být splněny příkaz nelze provést ve větvi true obě podmínky.  Tyto příklady také ukazují, že můžete mít více příkazů v každé větve podmíněného zadaný uzavřete je v `{` a `}`.

Můžete také použít `||` představují "nebo". Přidejte následující kód po co jste vytvořili, pokud:

```csharp
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
```

Prvním krokem dokončíte. Než začnete v další části, můžeme přesunout aktuálního kódu do samostatné metodě. Který usnadňuje začít pracovat s novou příklad. Přejmenujte vaše `Main` metodu `ExploreIf` a zápis nový `Main` metoda, která volá `ExploreIf`. Po dokončení, váš kód by měl vypadat například takto:

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

Komentář volání `ExploreIf()`. To bude dávat výstup, který menší zaplněny, při práci v této části:

```csharp
//ExploreIf();
```

`//` Spustí **komentář** v jazyce C#. Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nemůžou provést jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Používat smyčky opakování operace

V této části můžete použít **smyčky** opakování příkazy. Zkuste tento kód ve vaší `Main` metoda:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Příkaz kontroluje podmínku a spustí příkaz nebo blok příkazu následující `while`. Opakovaně kontroluje podmínku a provádění tyto příkazy, dokud je podmínka vyhodnocena jako false.

V tomto příkladu je jeden další nové operátor. `++` Po `counter` proměnná **přírůstek** operátor. Přidá 1 na hodnotu `counter` a uloží tuto hodnotu v `counter` proměnné.

> [!IMPORTANT]
> Ujistěte se, že `while` cykly změny stavu na hodnotu false, při spuštění kódu. Jinak, vytvoříte **nekonečná smyčka** které nikdy končí vašeho programu. Který není ukázáno v této ukázce, protože budete muset vynutit ukončení pomocí vašeho programu **CTRL-C** nebo jiným způsobem.

`while` Smyčky testuje podmínku před provedením následující kód `while`. `do` ... `while` smyček nejprve spustí kód a pak kontroluje podmínku. Proveďte při smyčky je znázorněno v následujícím kódu:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

To `do` smyčky a dříve `while` smyčky poskytnou stejný výsledek.

## <a name="work-with-the-for-loop"></a>Pracovat smyčky for

**Pro** smyčky se často používá v jazyce C#. Zkuste tento kód ve své metodě Main():

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Funguje jako `while` smyčky a `do` smyčky jste už použili. `for` Příkaz má tři části, které řídí, jak to funguje.

První část je **pro inicializátoru**: `for index = 0;` uvádí, že `index` je proměnná smyčky a nastaví počáteční hodnoty `0`.

Střední část je **pro podmínku**: `index < 10` deklaruje, že tato `for` smyčce bude pokračovat v provádění, dokud hodnota čítače je menší než 10.

Poslední část je **pro iterator**: `index++` Určuje, jak upravit proměnnou smyčky po provedení těchto bloku `for` příkaz. Zde, určuje, že `index` by se zvýší o 1 pokaždé, když provádí bloku.

Experimentujte s sami. Zkuste každou z následujících:

- Změňte inicializátoru spustit na jinou hodnotu.
- Změňte stav kdykoli zastavit jinou hodnotu.

Když jste hotovi, můžeme přesunout k zápisu některé sami používat co když jste se naučili kódu.

## <a name="combine-branches-and-loops"></a>Kombinace větví a smyčky

Teď, když jste viděli `if` prohlášení a opakování konstrukce v jazyce C#, najdete v části Pokud můžete napsat kód C# k vyhledání součet všech celá čísla 1 až 20, které jsou dělitelná 3.  Tady je několik pomocných parametrů:

- `%` Operátor vám dává zbytek operace dělení.
- `if` Příkaz vám dává stav chcete zobrazit, pokud číslo musí být součástí součet.
- `for` Smyčky vám může pomoct opakujte sérii kroků pro všechna čísla 1 až 20.

Vyzkoušejte si to. Potom zkontrolujte, jak jste to udělali. Měli byste obdržet 63 pro odpověď. Zobrazí jednu možnou odpověď podle [zobrazení Dokončený kód v Githubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Jste dokončili rychlé spuštění "větve a smyčky".

Můžete pokračovat [interpolované řetězce](interpolated-strings-local.md) rychlé spuštění ve vašem vývojovém prostředí.

Další informace o těchto konceptech v těchto tématech:

[Pokud a else – příkaz](../language-reference/keywords/if-else.md)  
[While – příkaz](../language-reference/keywords/while.md)  
[Do – příkaz](../language-reference/keywords/do.md)  
[For – příkaz](../language-reference/keywords/for.md)  
