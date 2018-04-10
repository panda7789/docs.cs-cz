---
title: Úvod do třídy kurz – C# místní – elementy QuickStart
description: Vytvoření vaší první programu C# a prozkoumat objektově orientované koncepty
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: dd3fff6f74c92a45545e8e36f28eab351b39b37e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="introduction-to-classes"></a>Úvod do třídy

Tento rychlý start očekává, že máte počítače, které můžete použít pro vývoj. Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux. Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní quickstarts](local-environment.md) s odkazy na další podrobnosti.

## <a name="create-your-application"></a>Vytvoření aplikace

Pomocí okna terminálu, vytvořte adresář s názvem **třídy**. Budete sestavit aplikaci existuje. Tento adresář a zadejte `dotnet new console` v okně konzoly. Tento příkaz vytvoří vaší aplikace. Otevřete **Program.cs**. Ho by měl vypadat takto:

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

V tento rychlý start se chystáte vytvořit nové typy, které představují účet bank. Vývojáři obvykle definujte každá třída v různých textového souboru. Tím je snazší správa růstem program velikost.  Vytvořte nový soubor s názvem **BankAccount.cs** v **třídy** adresáře. 

Tento soubor bude obsahovat definice ***bankovní účet***. Objekt Oriented programování organizuje kód tak, že vytvoříte typy ve formě ***třídy***. Tyto třídy obsahovat kód, který představuje konkrétní entitu. `BankAccount` Třída reprezentuje účet bank. Kód implementuje konkrétní operací prostřednictvím metody a vlastnosti. V tento rychlý start účet bank podporuje toto chování:

1. Má 10 číslice, která jednoznačně identifikuje účet bank.
1. Obsahuje řetězec, který ukládá název nebo názvy vlastníky.
1. Zůstatek je možné načíst.
1. Přijímá vkladů.
1. Přijímá stažení.
1. Počáteční zůstatek musí být kladná.
1. Stažení nesmí mít záporný zůstatek výsledek.

## <a name="define-the-bank-account-type"></a>Zadejte typ účtu bank

Můžete spustit tak, že vytvoříte základní informace o třídu, která definuje tento chování. Ho bude vypadat takto:

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

Před přechodem, Podívejme se na co jste vytvořili.  `namespace` Deklarace poskytuje způsob, jak logicky uspořádat vašeho kódu. Tento rychlý start je poměrně malý, takže všechny kód budete chápat jeden obor názvů. 

`public class BankAccount` definuje třídu, nebo typu, kterou vytváříte. Všechno uvnitř `{` a `}` třídy, které následuje deklarace definuje chování třídy. Existují pět ***členy*** z `BankAccount` třídy. První tři ***vlastnosti***. Vlastnosti jsou datové prvky a může mít kód, který vynucuje ověřování nebo jinými pravidly. Poslední dva jsou ***metody***. Metody jsou bloky kódu, že či jedné funkce. Čtení názvy všech členů, měl by poskytnout dostatek informací pro vás nebo jiné vývojář zjistit, jaké jsou třídy.

## <a name="open-a-new-account"></a>Otevřete nový účet

První funkce pro implementaci je otevřete účet bank. Když zákazník otevře účet, musíte zadat v příslušné počáteční zůstatek a informace o vlastníkovi nebo vlastníky tohoto účtu. 

Vytvoření nového objektu `BankAccount` typ znamená definovat ***konstruktor*** , přiřadí tyto hodnoty. A ***konstruktor*** je člen, který má stejný název jako třída. Slouží k chybě při inicializaci objekty daného typu třídy. Přidejte následující konstruktor `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory jsou volány při vytvoření objektu pomocí [ `new` ](../language-reference/keywords/new.md). Nahraďte řádku `Console.WriteLine("Hello World!");` v ***program.cs*** tento řádek (Nahraďte `<name>` nahraďte názvem):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Typ `dotnet run` chcete zobrazit, co se stane.  

Všimli jste, že číslo účtu je prázdné? Je třeba to opravíme. Číslo účtu měli přiřazen, když se objekt. Ale by neměl být odpovědnost volajícího k jeho vytvoření. `BankAccount` Kód třídy měli vědět, jak přiřadit nový účet čísla.  Jednoduchý způsob, jak to udělat se dá začít s číslem 10 číslic. Zvýší ho, když se vytvoří každý nový účet. Nakonec uložte aktuální číslo účtu, když se objekt.

Přidejte následující deklarace členů k `BankAccount` třídy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Toto je datový člen. Má `private`, což znamená, že můžete přistupovat pouze kód `BankAccount` třídy. Jedná se o způsob oddělení veřejné odpovědnosti (např. nutnosti číslo účtu) od implementace rozhraní privátní (čísla účtů generování.) Přidejte následující dva řádky konstruktoru přiřadit číslo účtu:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Typ `dotnet run` a zobrazte si výsledky.

## <a name="create-deposits-and-withdrawals"></a>Vytvoření vkladů a stažení z

Třídě bankovní účet je potřeba přijmout vkladů a stažení z fungovala správně. Umožňuje implementovat vkladů a stažení z vytvořením deník každé transakci pro účet. Který má několik výhod oproti jednoduše aktualizace zůstatku na každou transakci. Historie lze provádět audit všechny transakce a správu denní zůstatky. Podle computing vyrovnávání z historie všech transakcí v případě potřeby, všechny chyby v rámci jedné transakce opravené správně projeví v rovnováhu mezi na další výpočet.

Začněme vytvořením nového typu představují transakce. Toto je jednoduchý typ, který nemá žádné odpovědnosti. Je několik vlastností. Vytvořte nový soubor s názvem ***Transaction.cs***. Přidejte do ní následující kód:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Nyní Pojďme přidat <xref:System.Collections.Generic.List%601> z `Transaction` objekty ke `BankAccount` – třída. Přidejte následující prohlášení:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Třídy, musíte k importu jiný obor názvů. Přidejte následující na začátku **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Nyní změníme jak `Balance` se použije v hlášení.  Je možné najít jako součet hodnot všech transakcí. Upravit deklaraci `Balance` v `BankAccount` třídy pro následující:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Tento příklad ukazuje důležitým aspektem ***vlastnosti***. Jste nyní computing rovnováhu mezi, když jiné programátory požádá o hodnotě. Vaše výpočetní vytvoří výčet všech transakcí a poskytuje součet jako aktuální zůstatek.

V dalším kroku implementovat `MakeDeposit` a `MakeWithdrawal` metody. Tyto metody vynutí poslední dvě pravidla: že počáteční zůstatek, musí být kladné a že každé odstoupení nesmí vytvořit záporné rovnováhu. 

To zavádí koncepci ***výjimky***. Standardní způsob vyjadřuje, že nelze úspěšně dokončit metodu svou práci je vyvolána výjimka. Typ výjimky a zprávy s ním spojená popisují chybu. Zde `MakeDeposit` metoda vyvolá výjimku, pokud množství uložení je záporná. `MakeWithdrawal` Metoda vyvolá výjimku, pokud částka stažení je záporná, nebo pokud použití stažení výsledkem záporný zůstatek:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../language-reference/keywords/throw.md) Příkaz **vyvolá** výjimku. Spouštění aktuální metody skončí a bude pokračovat, až odpovídající `catch` bloku se nachází. Přidáte `catch` bloku k testování této kódu trochu později.

Konstruktor měli získat jeden změnit tak, aby ho přidá počáteční transakce, nikoli přímo aktualizace zůstatku. Vzhledem k tomu, že jste již napsali `MakeDeposit` metody volat z vašeho konstruktor. Dokončení konstruktoru by měl vypadat takto:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> je vlastnost, která vrátí aktuální datum a čas. Otestování tohoto přidáním několik vkladů a ke stažení v vaší `Main` metoda:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

V dalším kroku testovací, že jsou zachytávání chybové stavy tak, že zkusíte vytvořte účet s záporné vyrovnávání:

```csharp
// Test that the initial balances must be positive:
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

Můžete použít [ `try` a `catch` příkazy](../language-reference/keywords/try-catch.md) označit blok kódu, který může vyvolat výjimky a k zachycení tyto chyby, které byste očekávali. Stejný postup můžete použít k testování kódu, který vyvolá záporný zůstatek:

```csharp
// Test for a negative balance
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

Uložte soubor a typ `dotnet run` vyzkoušejte si to.

## <a name="challenge---log-all-transactions"></a>Challenge - protokolovat všechny transakce

Chcete-li dokončit tento rychlý start, můžete napsat `GetAccountHistory` metodu, která vytvoří `string` pro historii transakce. Přidejte tuto metodu za účelem `BankAccount` typu:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Se používá <xref:System.Text.StringBuilder> třídy se naformátovat řetězec, který obsahuje jeden řádek pro každou transakci. Seznámili jste se formátování kódu dříve v těchto – elementy QuickStart řetězec. Je jeden znak nového `\t`. Která vloží na kartě k formátování výstupu.

Přidejte tento řádek k testování v **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Typ `dotnet run` a zobrazte si výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste získali zablokuje, zobrazí se zdroji pro tento rychlý Start [v našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Blahopřejeme, jste dokončili všechny naše Quickstarts. Pokud jste přes další, zkuste naši [kurzy](../tutorials/index.md)
