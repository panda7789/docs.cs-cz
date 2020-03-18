---
title: Větve a smyčky – úvod do kurzu jazyka C#
description: V tomto kurzu o větvích a smyčkách napíšete kód Jazyka C# k prozkoumání syntaxe jazyka, která podporuje podmíněné větve a smyčky k opakovanému spouštění příkazů.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73739122"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Naučte se podmíněnou logiku pomocí příkazů větvea smyčka

Tento kurz vás naučí, jak psát kód, který zkoumá proměnné a změní cestu spuštění na základě těchto proměnných. Napíšete kód Jazyka C# a zobrazí výsledky kompilace a spuštění. Kurz obsahuje řadu lekcí, které prozkoumat větvení a opakování konstrukce v C#. V těchto kurzech se seznámíte se základy jazyka C#.

Tento kurz očekává, že budete mít počítač, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS. Rychlý přehled příkazů, které budete používat, najdete v části [Seznamte se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="make-decisions-using-the-if-statement"></a>Rozhodování pomocí příkazu `if`

Vytvořte adresář s názvem *větve-tutorial*. Proveďte aktuální adresář a spusťte následující příkaz:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Tento příkaz vytvoří novou aplikaci konzoly .NET Core v aktuálním adresáři.

Otevřete *Program.cs* v oblíbeném editoru a nahraďte řádek `Console.WriteLine("Hello World!");` následujícím kódem:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Zkuste tento kód `dotnet run` zadáním do okna konzole. Měli byste vidět zprávu "Odpověď je větší než 10." vytištěny na konzoli.

Upravte deklaraci `b`, aby součet byl menší než 10:

```csharp
int b = 3;
```

Napište `dotnet run` znovu. Protože odpověď je menší než 10, nic se nevytiskne. Testovaná **podmínka** není splněná. Nemáte žádný kód, který by bylo možné provést, protože jste zatím napsali jenom jednu z možných větví příkazu `if`: větev pro splnění podmínky.

> [!TIP]
> Když se budete učit pracovat s C# (nebo každým jiným programovacím jazykem), budete při psaní kódu dělat chyby. Kompilátor najde a ohlásí chyby. Podívejte se pozorně na výstup chyby a kód, který vygeneroval chybu. Chyba kompilátoru může obvykle pomoci najít problém.

Tato první ukázka `if` ukazuje výkon a logické typy. Logická *hodnota* je proměnná, která může `true` `false`mít jednu ze dvou hodnot: nebo . C# definuje zvláštní typ `bool` pro logické proměnné. Příkaz `if` kontroluje hodnotu typu `bool`. Pokud je tato hodnota `true`, provede se příkaz následující za `if`. V opačném případě se přeskočí.

Tento proces kontroly podmínek a provádění příkazů na základě těchto podmínek je velmi účinný.

## <a name="make-if-and-else-work-together"></a>Spolupráce if a else

Chcete-li ve větvích True a False provést různý kód, vytvoříte větev `else`, která se provede, když podmínka není splněná. Zkus tohle. Přidejte poslední dva řádky v `Main` kódu níže do metody (první čtyři byste již měli mít):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Příkaz následující za klíčovým slovem `else` se provede jen tehdy, když má testovaná podmínka hodnotu `false`. Kombinace `if` a `else` s boolean podmínky poskytuje veškerou sílu, kterou potřebujete ke zpracování i `true` podmínku. `false`

> [!IMPORTANT]
> Důvodem odsazení pod příkazy `if` a `else` je snadnější čtení pro uživatele.
> Jazyk C# nepovažuje odsazení nebo prázdné místo za významné.
> Příkaz následující za klíčovým slovem `if` nebo `else` se provede na základě podmínky. Všechny ukázky v tomto kurzu postupujte podle běžné praxe odsadit řádky založené na toku řízení příkazů.

Protože odsazení není významné, je potřeba pomocí `{` a `}` vyznačit, když chcete, aby jako součást podmíněně prováděného bloku bylo víc příkazů. Programátoři v C# obvykle používají tyto složené závorky pro všechny klauzule `if` a `else`. Následující příklad je stejný jako ten, který jste právě vytvořili. Upravte výše uvedený kód tak, aby odpovídal následujícímu kódu:

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
> Prostřednictvím zbytku tohoto kurzu ukázky kódu všechny obsahují závorky, následující přijaté postupy.

Můžete testovat složitější podmínky. Přidejte do `Main` metody následující kód za kód, který jste dosud napsali:

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

Symbol `==` testuje *rovnost*. Použití `==` odlišuje test rovnosti od `a = 5`přiřazení, které jste viděli v .

Zápis `&&` představuje „a zároveň“. To znamená, že když se má provést větev True, musí být splněny obě podmínky.  Tyto příklady také ukazují, že můžete mít v každé podmíněné větvi víc příkazů, pokud je uzavřete mezi `{` a `}`.

Můžete také `||` použít k reprezentaci "nebo". Za to, co jste dosud napsali, přidejte následující kód:

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

Upravte hodnoty `a` `b`, `c` a a `&&` `||` přepněte mezi a prozkoumat. Získáte větší pochopení toho, `&&` jak `||` a operátoři pracují.

Dokončil jsi první krok. Než začnete další část, přesuneme aktuální kód do samostatné metody. To usnadňuje začít pracovat s novým příkladem. Přejmenujte `Main` metodu na `ExploreIf` `Main` a napište novou metodu, která volá `ExploreIf`. Po dokončení by měl váš kód vypadat takto:

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

Zakomentujte `ExploreIf()`volání na . To bude výstup méně přeplněný, jak budete pracovat v této části:

```csharp
//ExploreIf();
```

Spustí `//` **komentář** v c#. Komentáře jsou jakýkoli text, který chcete zachovat ve zdrojovém kódu, ale nespustí jako kód. Kompilátor negeneruje žádný spustitelný kód z komentářů.

## <a name="use-loops-to-repeat-operations"></a>Použití smyček k opakování operací

V této části můžete použít **smyčky** opakovat příkazy. Zkuste tento kód `Main` ve vaší metodě:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Příkaz `while` zkontroluje podmínku a provede příkaz nebo `while`blok příkazu za . Opakovaně kontroluje podmínku a provádění těchto příkazů, dokud podmínka je false.

V tomto příkladu je ještě jeden nový operátor. Zápis `++` za proměnnou `counter` je operátor **inkrementace**. Přidá 1 k hodnotě `counter` a ukládá `counter` tuto hodnotu v proměnné.

> [!IMPORTANT]
> Ujistěte se, že `while` podmínka smyčky se při spuštění kódu změní na false. Jinak vytvoříte **nekonečnou smyčku**, ve které program nikdy neskončí. To není prokázáno v této ukázce, protože je třeba vynutit program ukončit pomocí **CTRL-C** nebo jinými prostředky.

Smyčka `while` otestuje podmínku před spuštěním kódu, který následuje za `while`. Smyčka `do` ... `while` nejdřív spustí kód a potom zkontrolujte tuto podmínku. Smyčka do while je zobrazena v následujícím kódu:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Tato `do` smyčka a `while` dřívější smyčka vytvářejí stejný výstup.

## <a name="work-with-the-for-loop"></a>Práce se smyčkou for

Smyčka **for** se běžně používá v c#. Zkuste tento kód v main() metoda:

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Dělá to samé jako smyčky `while` a `do`, které jste už použili. Příkaz `for` má tři části, které řídí jeho fungování.

První část je **pro inicializátor**: `int index = 0;` deklaruje, že `index` je proměnná smyčky a nastaví jeho počáteční hodnotu . `0`

Střední část je **for** `index < 10` condition : `for` deklaruje, že tato smyčka pokračuje v provádění, dokud je hodnota čítače menší než 10.

Poslední část je **for iterator**: `index++` určuje, jak upravit proměnnou smyčky `for` po provedení bloku po příkazu. V tomto případě určuje, že `index` se má po každém provedení bloku zvýšit o 1.

Zkuste si s touto ukázkou zaexperimentovat. Vyzkoušejte všechny následující možnosti:

- Změňte inicializační výraz, aby začínal jinou hodnotou.
- Změňte podmínku tak, aby se zastavila při jiné hodnotě.

Až skončíte, přejdeme k tomu, abyste si vyzkoušeli, co jste se naučili, a napsali kus kódu sami.

## <a name="combine-branches-and-loops"></a>Kombinace větví a smyček

Teď když jste viděli příkaz `if` a konstruktory cyklů v jazyce C#, zkuste, jestli dokážete v jazyce C# napsat kód, který zjistí součet všech celých čísel od 1 do 20, která jsou dělitelná 3.  Tady je několik tipů:

- Operátor `%` vrací zbytek po operaci dělení.
- Příkaz `if` poskytuje podmínku pro zjištění, jestli konkrétní číslo má být součástí tohoto součtu.
- Smyčka `for` pomůže zopakovat sérii kroků pro všechna čísla od 1 do 20.

Vyzkoušejte si to sami. A potom se podívejte, jak jste si vedli. Měl bys dostat 63 za odpověď. Můžete vidět jednu možnou odpověď [zobrazením dokončeného kódu na GitHubu](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Dokončili jste kurz "větve a smyčky".

Můžete pokračovat v kurzu [Pole a kolekce](arrays-and-collections.md) ve vlastním vývojovém prostředí.

Více se o těchto konceptech dozvíte v těchto tématech:

- [Příkaz If a else](../../language-reference/keywords/if-else.md)
- [Zatímco prohlášení](../../language-reference/keywords/while.md)
- [Příkaz Do](../../language-reference/keywords/do.md)
- [Pro výpis](../../language-reference/keywords/for.md)
