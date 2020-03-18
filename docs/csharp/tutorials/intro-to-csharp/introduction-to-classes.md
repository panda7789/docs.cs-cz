---
title: Třídy a objekty – úvod do kurzu jazyka C#
description: Vytvořte si svůj první c# program a prozkoumejte objektově orientované koncepty
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: b6ad72997647b80b981f1a1871e384791404bdf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156590"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Prozkoumejte objektově orientované programování pomocí tříd a objektů

Tento kurz očekává, že máte počítač, který můžete použít pro vývoj. Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS. Rychlý přehled příkazů, které budete používat, najdete v části [Seznamte se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="create-your-application"></a>Vytvoření aplikace

Pomocí okna terminálu vytvořte adresář s názvem *classes*. Budete stavět svou aplikaci tam. Změňte na tento `dotnet new console` adresář a zadejte do okna konzoly. Tento příkaz vytvoří aplikaci. Otevřít *Program.cs*. Mělo by to vypadat takto:

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

V tomto kurzu budete vytvářet nové typy, které představují bankovní účet. Vývojáři obvykle definují každou třídu v jiném textovém souboru. To usnadňuje správu, protože se velikost programu zvětšuje. Vytvořte nový soubor s názvem *BankAccount.cs* v adresáři *tříd.*

Tento soubor bude obsahovat definici ***bankovního účtu***. Objektově orientované programování uspořádá kód vytvořením typů ve formě ***tříd***. Tyto třídy obsahují kód, který představuje konkrétní entitu. Třída `BankAccount` představuje bankovní účet. Kód implementuje konkrétní operace prostřednictvím metod a vlastností. V tomto kurzu bankovní účet podporuje toto chování:

1. Má desetimístné číslo, které jednoznačně identifikuje bankovní účet.
1. Má řetězec, který ukládá název nebo názvy vlastníků.
1. Zůstatek lze načíst.
1. Přijímá vklady.
1. Přijímá výběry.
1. Počáteční zůstatek musí být kladný.
1. Výběry nemohou mít za následek záporný zůstatek.

## <a name="define-the-bank-account-type"></a>Definování typu bankovního účtu

Můžete začít vytvořením základů třídy, která definuje toto chování. Vypadalo by to takto:

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Než půjdete dál, podívejme se na to, co jste vybudovali.  Deklarace `namespace` poskytuje způsob, jak logicky uspořádat kód. Tento kurz je relativně malý, takže veškerý kód vložíte do jednoho oboru názvů.

`public class BankAccount`definuje třídu nebo typ, který vytváříte. Vše uvnitř `{` `}` a které následuje deklarace třídy definuje stav a chování třídy. Ve `BankAccount` třídě je pět ***členů.*** První tři jsou ***vlastnosti***. Vlastnosti jsou datové prvky a může mít kód, který vynucuje ověření nebo jiná pravidla. Poslední dvě jsou ***metody***. Metody jsou bloky kódu, které provádějí jednu funkci. Čtení názvů každého z členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře pochopit, co třída dělá.

## <a name="open-a-new-account"></a>Otevření nového účtu

První funkcí, kterou je třeba implementovat, je otevření bankovního účtu. Když si zákazník otevře účet, musí zadat počáteční zůstatek a informace o vlastníkovi nebo vlastnících tohoto účtu.

Vytvoření nového objektu `BankAccount` typu znamená definování ***konstruktoru,*** který přiřadí tyto hodnoty. ***Konstruktor*** je člen, který má stejný název jako třída. Používá se k inicializaci objektů tohoto typu třídy. Přidejte do `BankAccount` typu následující konstruktor:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory jsou volány při [`new`](../../language-reference/operators/new-operator.md)vytváření objektu pomocí . Nahraďte `Console.WriteLine("Hello World!");` řádek v *Program.cs* následujícím `<name>` kódem (nahraďte se svým jménem):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Zadejte, `dotnet run` abyste viděli, co se stane.  

Všimli jste si, že číslo účtu je prázdné? Je čas to napravit. Číslo účtu by mělo být přiřazeno při vytvoření objektu. Ale to by nemělo být odpovědností volajícího k jeho vytvoření. Kód `BankAccount` třídy by měl vědět, jak přiřadit nová čísla účtů.  Jednoduchý způsob, jak to udělat, je začít s 10-místné číslo. Při každém vytvoření nového účtu jej směřuje. Nakonec uložte číslo aktuálního účtu při vytvoření objektu.

Do třídy přidejte `BankAccount` následující deklaraci člena:

```csharp
private static int accountNumberSeed = 1234567890;
```

Toto je datový člen. Je to `private`, což znamená, že lze přistupovat pouze kód uvnitř třídy. `BankAccount` Je to způsob, jak oddělit veřejné odpovědnosti (jako je číslo účtu) od soukromé implementace (způsob generování čísel účtů). Je také `static`, což znamená, že `BankAccount` je sdílena všemi objekty. Hodnota nestatické proměnné je jedinečná pro každou `BankAccount` instanci objektu. Přidejte k konstruktoru následující dva řádky a přiřaďte číslo účtu:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Zadáním `dotnet run` zobrazíte výsledky.

## <a name="create-deposits-and-withdrawals"></a>Vytváření vkladů a výběrů

Vaše třída bankovního účtu musí přijímat vklady a výběry, aby fungovaly správně. Pojďme implementovat vklady a výběry vytvořením deníku každé transakce pro účet. To má několik výhod oproti pouhé aktualizaci zůstatku na každé transakci. Historii lze použít k auditu všech transakcí a správě denních zůstatků. Výpočtem zůstatku z historie všech transakcí v případě potřeby se všechny chyby v jedné transakci, které jsou opraveny, správně projeví v zůstatku při dalším výpočtu.

Začněme vytvořením nového typu představujícího transakci. Jedná se o jednoduchý typ, který nemá žádné povinnosti. Potřebuje pár nemovitostí. Vytvořte nový soubor s názvem *Transaction.cs*. Přidejte do ní následující kód:

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

Nyní přidáme do <xref:System.Collections.Generic.List%601> třídy `Transaction` objekty. `BankAccount` Přidejte následující prohlášení:

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

Třída <xref:System.Collections.Generic.List%601> vyžaduje import ovat jiný obor názvů. Na začátku BankAccount.cs se přidejte k *nejtento*:

```csharp
using System.Collections.Generic;
```

Nyní změníme způsob, `Balance` jakým je hlášen.  Lze jej nalézt sečtením hodnot všech transakcí. Upravte deklaraci `Balance` `BankAccount` ve třídě takto:

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Tento příklad ukazuje důležitý aspekt ***vlastností***. Nyní počítačjete zůstatek, když jiný programátor požádá o hodnotu. Výpočty počadnou všechny transakce a poskytuje součet jako aktuální zůstatek.

Dále implementujte `MakeDeposit` `MakeWithdrawal` metody a. Tyto metody budou prosazovat poslední dvě pravidla: že počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvářet záporný zůstatek.

Tím se zavádí pojem ***výjimky***. Standardní způsob označení, že metoda nemůže úspěšně dokončit svou práci, je vyvolat výjimku. Typ výjimky a zprávy s ním spojené popisují chybu. Zde `MakeDeposit` metoda vyvolá výjimku, pokud je částka vkladu záporná. `MakeWithdrawal` Metoda vyvolá výjimku, pokud je částka výběru záporná nebo pokud použití výběru vede k zápornému zůstatku:

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

Příkaz [`throw`](../../language-reference/keywords/throw.md) **vyvolá** výjimku. Spuštění aktuálního bloku končí a řízení se `catch` přenese do prvního odpovídajícího bloku nalezeného v zásobníku volání. Přidáte `catch` blok pro testování tohoto kódu o něco později.

Konstruktor by měl získat jednu změnu tak, aby přidá počáteční transakce, spíše než aktualizovat zůstatek přímo. Vzhledem k `MakeDeposit` tomu, že jste již napsali metodu, zavolejte ji z konstruktoru. Hotový konstruktor by měl vypadat takto:

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrací aktuální datum a čas. Otestujte to přidáním několika vkladů a výběrů ve vaší `Main` metodě:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Dále otestujte, že zachycujete chybové stavy, a to pokusem o vytvoření účtu se záporným zůstatkem:

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Pomocí [ `try` příkazy `catch` a](../../language-reference/keywords/try-catch.md) označit blok kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte. Stejnou techniku můžete použít k testování kódu, který vyvolá výjimku pro záporné saldo:

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Uložte soubor `dotnet run` a zadejte jej vyzkoušejte.

## <a name="challenge---log-all-transactions"></a>Výzva - protokolovat všechny transakce

Chcete-li dokončit tento kurz, můžete napsat metodu, `GetAccountHistory` která vytvoří `string` pro historii transakcí. Přidejte tuto `BankAccount` metodu do typu:

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

To používá <xref:System.Text.StringBuilder> třídu k formátování řetězce, který obsahuje jeden řádek pro každou transakci. Viděli jste kód formátování řetězce dříve v těchto kurzech. Jeden nový `\t`znak je . To vloží kartu pro formátování výstupu.

Přidejte tento řádek a otestujte jej v *Program.cs*:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Zadáním `dotnet run` zobrazíte výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste uvízli, můžete vidět zdroj pro tento výukový program [v našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).

Gratulujeme, jste dokončili všechny naše úvod do c# kurzy. Pokud se chcete dozvědět více, vyzkoušejte více našich [výukových programů](../index.md).
