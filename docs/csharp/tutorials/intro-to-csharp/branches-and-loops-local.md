---
title: Větve a smyčky – Úvod do C# kurz
description: V tomto kurzu o větvích a smyčkách napíšete C# kódu syntaxi jazyka, který podporuje podmíněné větvení a smyček opakovaně spouštět příkazy.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 4a116ae5294915770dec742c147cf2ba1bf6e284
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427250"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Další podmíněnou logiku s příkazy větve a smyčky

V tomto kurzu se naučíte, jak napsat kód, který vyhodnocuje proměnné a mění cestu provedení na základě těchto proměnných. Napíšete kód v C# a zobrazovat výsledky kompilace a spuštění. Tento kurz obsahuje sérii lekcí, které probírají konstrukty v větvení a smyček C#. Tato lekce vás naučí základy jazyka C#.

V tomto kurzu se očekává, že budete mít počítač, který používáte pro vývoj. Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux. Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodování pomocí `if` – příkaz

Vytvořte adresář **kurz větve**. Zkontrolujte, zda aktuální adresář a spusťte `dotnet new console -n BranchesAndLoops -o .`. Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

Otevřít **Program.cs** ve svém oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Vyzkoušejte tento kód tak, že zadáte `dotnet run` v okně konzoly. Zobrazí se zpráva "odpověď je větší než 10." vytiskne na konzolu.

Upravte deklaraci `b` tak, aby součet je menší než 10:

```csharp
int b = 3;
```

Typ `dotnet run` znovu. Protože odpověď je menší než 10, nic se nevytiskne. **Podmínku** jste testování má hodnotu false. Nemáte žádný kód spustit, protože jste zatím napsali jenom jednu z možných větví `if` – příkaz: větev pro splnění podmínky.

> [!TIP]
> Když se budete učit, C# (nebo libovolným programovacím jazykem), budete se při psaní kódu dělat chyby. Kompilátor vyhledá a ohlásit chyby. Prohlédněte si blíže chybový výstup a kód, který vytvořil chybu. Chyba kompilátoru obvykle můžete nalezení příčiny problému.

Tento první příklad ukazuje sílu příkazu `if` a logických typů. A *logická* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false`. C#definuje speciální typ `bool` pro proměnné typu Boolean. `if` Příkaz zkontroluje hodnotu vlastnosti `bool`. Pokud je hodnotou `true`, příkazu za příkazem `if` spustí. V opačném případě se přeskočí.

Tento proces kontroly podmínek a provádění příkazů na základě těchto podmínek je velmi výkonné.

## <a name="make-if-and-else-work-together"></a>If a else spolupracují

Chcete-li ve větvích true a false provést různý kód, vytvoříte `else` větev, která se provede, když podmínka není splněna. Vyzkoušejte to. Přidejte poslední dva řádky ve níže uvedeného kódu vaší `Main` – metoda (byste už měli mít první čtyři):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Následující příkaz `else` – klíčové slovo provede pouze, pokud je testovaná podmínka `false`. Kombinování `if` a `else` s logickými podmínkami poskytuje veškerou sílu, bude potřeba zpracovat oba `true` a `false` podmínku.

> [!IMPORTANT]
> Důvodem odsazení pod `if` a `else` příkazy je snadnější čtení pro uživatele.
> Jazyk C# nepovažuje odsazení a mezery za významné.
> Následující příkaz `if` nebo `else` – klíčové slovo se spustí na základě podmínky. Všechny ukázky v tomto kurzu dodržují běžnou praxi odsazování řádků podle toku řízení příkazů.

Protože odsazení není významné, je třeba použít `{` a `}` označte, když má více než jeden výraz jako součást podmíněně prováděného bloku. Programátoři v C# obvykle používají tyto složené závorky ve všech `if` a `else` klauzule. Následující příklad je stejný jako ten, který jste právě vytvořili. Upravte kód tak, aby odpovídala následující kód výše:

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
> Postupujte podle zbývajících kroků v tomto kurzu, patří ukázky složené závorky podle přijaté praxe.

Můžete testovat složitější podmínky. Přidejte následující kód do vašeho `Main` za jste zatím napsali kód:

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

`==` Symbol testy pro *rovnosti*. Pomocí `==` odlišuje od přiřazení, které jste viděli v testování rovnosti `a = 5`.

`&&` Představuje "a". Znamená to, že obě podmínky musí mít hodnotu true, má provést větev true.  Tyto příklady také ukazují, že můžete mít více příkazů v každé podmíněné větvi, je v uzavřete `{` a `}`.

Můžete také použít `||` představující "nebo". Přidejte následující kód za co jste napsali zatím:

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

Upravte hodnoty `a`, `b`, a `c` a přepínat mezi `&&` a `||` prozkoumat. Další vysvětlení, jak budete získat `&&` a `||` operátory fungovat.

Dokončili jste první krok. Předtím, než se pustíte do další části, přejdeme aktuální kód do samostatné metodě. Který usnadňuje začít pracovat s nový příklad. Přejmenovat váš `Main` metodu `ExploreIf` a napsat nový `Main` metodu, která volá `ExploreIf`. Jakmile budete hotovi, váš kód by měl vypadat takto:

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

Odkomentujte volání `ExploreIf()`. Bude výstup, který zaplněný při práci v této části:

```csharp
//ExploreIf();
```

`//` Spustí **komentář** v C#. Komentáře jsou jakýkoli text, který chcete ponechat ve zdrojovém kódu, ale nemůžou provést jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Použití smyček k opakování operací

V této části použijete **smyčky** k opakování příkazů. Vyzkoušejte tento kód ve vašich `Main` metody:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Příkaz zkontroluje podmínku a provede příkaz nebo blok příkazů následující `while`. Opakovaně zkontroluje podmínku a provádět příkaz, dokud podmínka není splněna.

V tomto příkladu je jeden nový operátor. `++` Po `counter` proměnná je **přírůstek** operátor. Přičte 1 k hodnotě z `counter` a uloží hodnotu v `counter` proměnné.

> [!IMPORTANT]
> Ujistěte se, že `while` smyčky změny stavu na hodnotu false, při spuštění kódu. V opačném případě můžete vytvořit **nekonečná smyčka** kde program nikdy neskončí. Který není ukázáno v této ukázce, protože budete muset vynutit ukončení pomocí vašeho programu **CTRL-C** nebo jiným způsobem.

`while` Smyčky otestuje podmínku před spuštěním kódu, který následuje `while`. `do` ... `while` smyčky nejdřív spustí kód a potom zkontrolujte tuto podmínku. Úkol, zatímco smyčky je znázorněno v následujícím kódu:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

To `do` smyčky a dřívější `while` smyčky generovat stejný výstup.

## <a name="work-with-the-for-loop"></a>Práce s smyčka for

**Pro** smyčky se běžně používá v C#. Vyzkoušejte tento kód v metodě Main():

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Funguje jako `while` smyčky a `do` smyčky, které jste už použili. `for` Příkaz má tři části, které řídí, jak to funguje.

První část je **pro inicializátor**: `int index = 0;` deklaruje, že `index` je proměnná smyčky a nastavuje její počáteční hodnotu `0`.

Prostřední část je **pro podmínku**: `index < 10` deklaruje, že tento `for` smyčky pokračuje v provádění za předpokladu, hodnota čítače je menší než 10.

Poslední část je **iterátoru**: `index++` Určuje, jak upravit proměnnou smyčky po provedení bloku následujícího `for` příkazu. V tomto poli, určuje, že `index` měli zvyšuje o 1 při každém provedení bloku.

Vyzkoušet sami. Vyzkoušejte všechny z následujících akcí:

- Změňte inicializační začínal jinou hodnotou.
- Změňte podmínku, která má zastavit na jinou hodnotu.

Až skončíte, přejdeme napsali kus kódu sami používat, co jste se naučili.

## <a name="combine-branches-and-loops"></a>Kombinace větví a smyček

Teď, když už víte, `if` příkazu a konstruktory cyklů v jazyce C# najdete v části Pokud můžete napsat kód jazyka C# pro zjistí součet všech celých čísel od 1 do 20, která jsou dělitelná 3.  Tady je několik tipů:

- `%` Operátor poskytuje zbytek operace dělení.
- `if` Příkaz poskytuje podmínku pro zjištění, pokud se číslo by mělo být součástí tohoto součtu.
- `for` Smyčky pomůže zopakovat sérii kroků pro všechna čísla od 1 do 20.

Vyzkoušejte si to sami. Zkontrolujte, jak jste to udělali. Měli byste obdržet 63 pro odpověď. Zobrazí jednu možnou odpověď podle [zobrazení dokončené kódu na Githubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Dokončili jste kurz "větve a smyčky".

Můžete pokračovat [pole a kolekce](arrays-and-collections.md) kurz ve svém vlastním vývojovém prostředí.

Další informace o těchto konceptech v těchto tématech:

- [Pokud a else – příkaz](../../language-reference/keywords/if-else.md)
- [while – příkaz](../../language-reference/keywords/while.md)
- [do – příkaz](../../language-reference/keywords/do.md)
- [For – příkaz](../../language-reference/keywords/for.md)
