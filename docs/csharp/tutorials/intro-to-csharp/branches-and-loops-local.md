---
title: Větve a smyčky – Úvod do kurzu jazyka C#
description: V tomto kurzu o větvích a smyčkách napíšete kód v jazyce C# pro zkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396883"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Další informace o podmíněné logice s příkazy větví a smyček

V tomto kurzu se naučíte, jak napsat kód, který kontroluje proměnné a mění cestu spuštění na základě těchto proměnných. Napíšete kód v jazyce C# a zobrazíte výsledky jeho kompilace a spuštění. Kurz obsahuje řadu lekcí, které se seznámí s konstrukcemi větvení a smyček v jazyce C#. V těchto kurzech se seznámíte se základy jazyka C#.

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodnutí pomocí `if` příkazu

Vytvořte adresář s názvem *větve – kurz*. Zajistěte, aby byl aktuální adresář, a spusťte následující příkaz:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Tento příkaz vytvoří novou konzolovou aplikaci .NET Core v aktuálním adresáři.

V oblíbeném editoru otevřete *program.cs* a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Tento kód zkuste zadat `dotnet run` v okně konzoly. Měla by se zobrazit zpráva "odpověď je větší než 10." vytištěno do konzoly.

Upravte deklaraci `b`, aby součet byl menší než 10:

```csharp
int b = 3;
```

Zadejte `dotnet run` znovu. Protože odpověď je menší než 10, nic se nevytiskne. Testovaná **podmínka** není splněná. Nemáte žádný kód, který by bylo možné provést, protože jste zatím napsali jenom jednu z možných větví příkazu `if`: větev pro splnění podmínky.

> [!TIP]
> Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby. Kompilátor najde a nahlásí chyby. Prohlédněte si úzce na výstupu chyby a kódu, který chybu generoval. Chyba kompilátoru může obvykle pomohly najít problém.

Tento první příklad ukazuje sílu `if` a logické typy. *Logická hodnota* je proměnná, která může mít jednu ze dvou hodnot: `true` nebo `false` . Jazyk C# definuje speciální typ `bool` pro logické proměnné. Příkaz `if` kontroluje hodnotu typu `bool`. Pokud je tato hodnota `true`, provede se příkaz následující za `if`. V opačném případě se přeskočí.

Tento proces kontroly podmínek a provádění příkazů založených na těchto podmínkách je účinný.

## <a name="make-if-and-else-work-together"></a>Spolupráce if a else

Chcete-li ve větvích True a False provést různý kód, vytvoříte větev `else`, která se provede, když podmínka není splněná. Zkuste to. Přidejte poslední dva řádky v kódu níže do vaší `Main` metody (měli byste už mít první čtyři):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Příkaz následující za klíčovým slovem `else` se provede jen tehdy, když má testovaná podmínka hodnotu `false`. Kombinování `if` a `else` s logickými podmínkami poskytuje veškerou sílu, kterou potřebujete ke zpracování `true` `false` podmínky a.

> [!IMPORTANT]
> Důvodem odsazení pod příkazy `if` a `else` je snadnější čtení pro uživatele.
> Jazyk C# nezpracovává odsazení ani prázdné znaky jako významné.
> Příkaz následující za klíčovým slovem `if` nebo `else` se provede na základě podmínky. Všechny ukázky v tomto kurzu se řídí běžným postupem odsazení řádků na základě toku řízení příkazů.

Vzhledem k tomu, že odsazení není důležité, je nutné použít `{` a `}` k označení, zda chcete, aby bylo více než jeden příkaz součástí bloku, který je spuštěn podmíněně. Programátoři v C# obvykle používají tyto složené závorky pro všechny klauzule `if` a `else`. Následující příklad je stejný jako ten, který jste vytvořili. Upravte kód výše tak, aby odpovídal následujícímu kódu:

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

Můžete testovat složitější podmínky. Do své metody přidejte následující kód `Main` za dosud napsaný kód:

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

`==`Testy symbolů pro *rovnost*. Použití `==` rozlišuje test pro rovnost z přiřazení, které jste viděli v `a = 5` .

Zápis `&&` představuje „a zároveň“. To znamená, že když se má provést větev True, musí být splněny obě podmínky.  Tyto příklady také ukazují, že můžete mít v každé podmíněné větvi víc příkazů, pokud je uzavřete mezi `{` a `}`.

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

Umožňuje upravit hodnoty `a` , `b` a a `c` přepínat mezi `&&` a a `||` prozkoumat. Získáte lepší znalosti o tom, jak `&&` operátory a `||` fungují.

Dokončili jste první krok. Než začnete s další částí, přesuňte aktuální kód do samostatné metody. Díky tomu je snazší začít pracovat s novým příkladem. Přejmenujte `Main` metodu na `ExploreIf` a napište novou `Main` metodu, která volá `ExploreIf` . Až budete hotovi, váš kód by měl vypadat takto:

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

Zakomentujte volání do `ExploreIf()` . Výsledkem je, že při práci v této části bude výstup méně zbytečný:

```csharp
//ExploreIf();
```

`//`Spustí **Komentář** v jazyce C#. Komentáře jsou libovolný text, který chcete zachovat ve zdrojovém kódu, ale ne spustit jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Použití smyček k opakování operací

V této části použijete **smyčky** k opakování příkazů. Vyzkoušejte tento kód v `Main` metodě:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while`Příkaz zkontroluje podmínku a spustí blok příkazu nebo příkazu za `while` . Opakovaně kontroluje podmínku a spouští tyto příkazy, dokud podmínka nevrátí hodnotu false.

V tomto příkladu je ještě jeden nový operátor. Zápis `++` za proměnnou `counter` je operátor **inkrementace**. Přidá 1 k hodnotě `counter` a uloží tuto hodnotu do `counter` proměnné.

> [!IMPORTANT]
> Ujistěte se, že se `while` podmínka smyčky při spuštění kódu změní na false. Jinak vytvoříte **nekonečnou smyčku**, ve které program nikdy neskončí. To není v této ukázce znázorněno, protože je nutné vynutit ukončení programu pomocí **kombinace kláves CTRL-C** nebo jiným způsobem.

Smyčka `while` otestuje podmínku před spuštěním kódu, který následuje za `while`. Smyčka `do` ... `while` nejdřív spustí kód a potom zkontrolujte tuto podmínku. Cyklus do *while* je zobrazen v následujícím kódu:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Tato `do` smyčka a předchozí `while` smyčka vytvoří stejný výstup.

## <a name="work-with-the-for-loop"></a>Práce se smyčkou for

Smyčka **for** se běžně používá v jazyce C#. Vyzkoušejte tento kód v metodě Main ():

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Předchozí kód provede stejnou práci jako `while` smyčka a `do` smyčka, kterou jste již použili. Příkaz `for` má tři části, které řídí jeho fungování.

První část je **pro inicializátor inicializátoru**: `int index = 0;` deklaruje, že `index` je proměnná smyčky, a nastaví její počáteční hodnotu na `0` .

Střední část je **pro podmínku**: `index < 10` deklaruje, že se tato `for` smyčka pokračuje, dokud hodnota čítače není menší než 10.

Poslední část je **for iterátor**: Určuje, `index++` jak se má změnit proměnná smyčky po provedení bloku po `for` příkazu. V tomto případě určuje, že `index` se má po každém provedení bloku zvýšit o 1.

Experimentujte sami. Vyzkoušejte každou z těchto variant:

- Změňte inicializační výraz, aby začínal jinou hodnotou.
- Změňte podmínku tak, aby se zastavila při jiné hodnotě.

Až skončíte, přejdeme k tomu, abyste si vyzkoušeli, co jste se naučili, a napsali kus kódu sami.

Existuje jeden další příkaz smyčky, který není popsaný v tomto kurzu: `foreach` příkaz. `foreach`Příkaz opakuje svůj příkaz pro každou položku v sekvenci položek. Nejčastěji se používá u *kolekcí*, takže je zahrnutá v dalším kurzu.

## <a name="created-nested-loops"></a>Vytvořené vnořené smyčky

`while` `do` Smyčka, nebo `for` může být vnořena do jiné smyčky, aby vytvořila matici pomocí kombinace každé položky ve vnější smyčce s každou položkou uvnitř vnitřní smyčky. Pojďme to udělat pro sestavení sady alfanumerických párů reprezentujících řádky a sloupce.

Jedna `for` smyčka může vygenerovat řádky:

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

Další smyčka může vygenerovat sloupce:

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

Můžete vnořit jednu smyčku dovnitř do dvojice formulářů:

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

Můžete vidět, že vnější smyčka se jednou zvýší pro každé úplné spuštění vnitřní smyčky. Zaměnit vnořování řádků a sloupců a Prohlédněte si změny sami.

## <a name="combine-branches-and-loops"></a>Kombinace větví a smyček

Teď když jste viděli příkaz `if` a konstruktory cyklů v jazyce C#, zkuste, jestli dokážete v jazyce C# napsat kód, který zjistí součet všech celých čísel od 1 do 20, která jsou dělitelná 3.  Tady je několik tipů:

- Operátor `%` vrací zbytek po operaci dělení.
- Příkaz `if` poskytuje podmínku pro zjištění, jestli konkrétní číslo má být součástí tohoto součtu.
- Smyčka `for` pomůže zopakovat sérii kroků pro všechna čísla od 1 do 20.

Vyzkoušejte si to sami. A potom se podívejte, jak jste si vedli. Měli byste pro odpověď získat 63. Můžete zobrazit jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Dokončili jste kurz "větve a smyčky".

Kurz pro [pole a kolekce](arrays-and-collections.md) můžete pokračovat ve svém vlastním vývojovém prostředí.

Další informace o těchto konceptech najdete v těchto článcích:

- [Příkaz If a else](../../language-reference/keywords/if-else.md)
- [While – příkaz](../../language-reference/keywords/while.md)
- [Příkaz Do](../../language-reference/keywords/do.md)
- [Příkaz for](../../language-reference/keywords/for.md)
