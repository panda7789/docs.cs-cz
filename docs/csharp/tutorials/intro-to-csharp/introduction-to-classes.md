---
title: Třídy a objekty – Úvod do C# kurz
description: Vytvořte svůj první program C# a seznamte se s koncepty objektově orientované
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 6ce0c86a4b746b8ea2db82899a82734a68e46957
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066064"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Prozkoumejte objektově orientované programování pomocí třídy a objekty

V tomto kurzu očekává, že máte počítač, který používáte pro vývoj. Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux. Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.

## <a name="create-your-application"></a>Vytvoření aplikace

Pomocí okna terminálu vytvořte adresář s názvem **třídy**. Vytvoříte aplikaci existuje. Tento adresář a zadejte `dotnet new console` v okně konzoly. Tento příkaz vytvoří vaší aplikace. Otevřít **Program.cs**. Mělo by to vypadat takto:

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

V tomto kurzu budete vytvářet nové typy, které představují bankovním účtu. Vývojáři obvykle definovat každá třída v různých textového souboru. Který usnadňuje spravovat stejným způsobem jako program roste velikost.  Vytvořte nový soubor s názvem **BankAccount.cs** v **třídy** adresáře. 

Tento soubor bude obsahovat definici ***bankovním účtu***. Objekt Oriented programování slouží k uspořádání kódu tak, že vytvoříte typů ve formě ***třídy***. Tyto třídy obsahovat kód, který představuje konkrétní entity. `BankAccount` Třída reprezentuje bankovním účtu. Kód implementuje konkrétní operace, ať už metody a vlastnosti. V tomto kurzu bankovním účtu podporuje toto chování:

1. Obsahuje číslo 10 číslic, které jednoznačně identifikuje bankovním účtu.
1. Obsahuje řetězec, který ukládá název nebo názvy vlastníků.
1. Je možné načíst zůstatek na účtu.
1. Přijímá vkladů.
1. Přijímá stažení.
1. Počáteční zůstatek musí být kladná.
1. Výsledkem stažení nesmí být záporný zůstatek.

## <a name="define-the-bank-account-type"></a>Definování typu bankovním účtu

Můžete spustit tak, že vytvoříte základní třídu, která definuje chování. To bude vypadat takto:

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

Před přechodem na, Pojďme se podívat, co jste vytvořili.  `namespace` Deklarace poskytuje způsob, jak logické uspořádání vašeho kódu. Tento kurz je poměrně malý, takže umístění vyberu veškerý kód v jednom oboru názvů. 

`public class BankAccount` Definuje třídy nebo typu, kterou vytváříte. Všechno, co je uvnitř `{` a `}` , který sleduje třídy prohlášení definuje chování třídy. Existuje pět ***členy*** z `BankAccount` třídy. První tři ***vlastnosti***. Vlastnosti jsou prvky dat a může mít kód, který vynucuje ověření nebo jiná pravidla. Poslední dvě ***metody***. Metody jsou bloky kódu, které provádějí jednu funkci. Názvy jednotlivých členů pro čtení by měly poskytnout dostatek informací pro vás nebo jiný vývojář zjistit, co dělá třídy.

## <a name="open-a-new-account"></a>Otevřete nový účet

První funkce k implementaci je otevřete bankovním účtu. Po otevření účtu zákazníka, musíte zadat počáteční zůstatek a informace o vlastník nebo vlastníci tohoto účtu. 

Vytvoření nového objektu `BankAccount` typ znamená definovat ***konstruktor*** , která přiřadí tyto hodnoty. A ***konstruktor*** je člen, který má stejný název jako třída. Používá se třeba inicializovat objekty typu třídy. Přidejte následující konstruktor k `BankAccount` typu:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory jsou volány při vytváření objektu pomocí [ `new` ](../../language-reference/keywords/new.md). Nahraďte řádek `Console.WriteLine("Hello World!");` v ***program.cs*** tento řádek (nahradit `<name>` s vaším jménem):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Typ `dotnet run` chcete zobrazit, co se stane.  

Všimli jste si, že číslo účtu je prázdný? Čas potřebný k opravě, který je. Číslo účtu měla být přiřazena při vytvoření objektu. Ale neměl by být odpovědností volajícího k jeho vytvoření. `BankAccount` Kód třídy by měl vědět, jak přiřadit novou čísla účtů.  Jednoduchý způsob, jak to provést, je začít s 10 číslic. Zvýšte ji, když se vytvoří každý nový účet. Nakonec ukládání číslo aktuálního účtu, když je vytvořen objekt.

Přidejte následující deklaraci člena `BankAccount` třídy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Toto je datový člen. Má `private`, což znamená, že je přístupný pouze kódu uvnitř `BankAccount` třídy. Jedná se o způsob oddělení veřejného odpovědnosti (jako číslo účtu) z privátní implementace (jak čísla účtů jsou generovány.) Je také `static`, což znamená, že je sdílené všemi `BankAccount` objekty. Hodnota nestatické proměnné je jedinečné pro každé instance `BankAccount` objektu. Přidejte následující dva řádky konstruktoru přiřadit číslo účtu:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Typ `dotnet run` zobrazíte výsledky.

## <a name="create-deposits-and-withdrawals"></a>Vytvoření vkladů a stažení

Vaše třída bankovním účtu je potřeba přijmout vkladů a stažení fungovat správně. Můžeme implementovat vkladů a stažení vytvořením deníku o každé transakci pro účet. Který má několik výhod oproti aktualizací zůstatku na každou transakci. Historie je možné provádět audit všechny transakce a správu denní zůstatků. Výpočtem zůstatek z historie všechny transakce v případě potřeby všechny chyby v rámci jedné transakce, které jsou opraveny správně projeví v zůstatek na další výpočtu.

Začněme tím, že vytvoříte nový typ pro reprezentaci transakce. Toto je jednoduchý typ, který nemá žádné odpovědnosti. Rozpojuje několik vlastností. Vytvořte nový soubor s názvem ***Transaction.cs***. Přidejte do ní následující kód:

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Teď přidáme <xref:System.Collections.Generic.List%601> z `Transaction` objektů `BankAccount` třídy. Přidejte následující deklarace:

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Třídy, musíte k importu jiný obor názvů. Přidejte následující na začátku **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Teď Změníme způsob, jakým `Balance` se použije v hlášení.  Je možné najít sečtením hodnoty všechny transakce. Upravte deklaraci `Balance` v `BankAccount` třídy takto:

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Tento příklad ukazuje důležitou součástí ***vlastnosti***. Zůstatek na účtu už výpočtu nyní při jiné programátor vyzve k zadání hodnoty. Vaše výpočetní výkon vytvoří výčet všech transakcí a poskytuje součet jako aktuální zůstatek.

V dalším kroku implementovat `MakeDeposit` a `MakeWithdrawal` metody. Tyto metody se vynutit konečný dvě pravidla:, počáteční zůstatek, musí být kladné a, všechny stažení nesmí vytvořit záporný zůstatek. 

Zavádí koncepci ***výjimky***. Standardní způsob označující, zda metoda nelze dokončí svou práci úspěšně je vyvolání výjimky. Typ výjimky a zprávu s ním spojená popisující chybu. Tady `MakeDeposit` metoda vyvolá výjimku, pokud je množství uložení záporná. `MakeWithdrawal` Metoda vyvolá výjimku, pokud je záporná hodnota stažení nebo pokud použití stažení má za následek negativní zůstatek:

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../../language-reference/keywords/throw.md) Příkaz **vyvolá** výjimku. Provádění aktuálního bloku skončí a řízení přenosů na první odpovídající `catch` nalezen blok v zásobníku volání. Přidáte `catch` bloku k otestování tento kód o něco později.

Konstruktor by měl získat jednu změnu, tak, aby přidá počáteční transakce, nikoli přímo aktualizace zůstatek na účtu. Vzhledem k tomu, že už jste napsali `MakeDeposit` metody volat z vašeho konstruktoru. Dokončení konstruktor by měl vypadat nějak takto:

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> je vlastnost, která vrátí aktuální datum a čas. Otestovat tak, že přidáte několik vkladů a ke stažení v vaše `Main` metody:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

V dalším kroku otestujte, že jsou zachycení chybové podmínky pokusu o vytvoření účtu pomocí záporný zůstatek:

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

Můžete použít [ `try` a `catch` příkazy](../../language-reference/keywords/try-catch.md) jak označit bloku kódu, který může vyvolat výjimky a k zachytávání těchto chyb, které očekáváte. Stejný postup můžete použít k testování kódu, který vrací chybovou výjimku záporný zůstatek:

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

Uložení souboru a typu `dotnet run` vyzkoušejte si to.

## <a name="challenge---log-all-transactions"></a>Výzva – protokolovat všechny transakce

K dokončení tohoto kurzu, můžete psát `GetAccountHistory` metodu, která vytvoří `string` pro historie transakcí. Přidejte tuto metodu za účelem `BankAccount` typu:

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Tady se používá <xref:System.Text.StringBuilder> třídy formátovací řetězec, který obsahuje jeden řádek pro každou transakci. Už víte, řetězce formátování kódu výše v těchto kurzech. Jeden znak nové `\t`. Která vloží kartu můžete formátovat výstup.

Přidejte následující řádek a otestovat ho v **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Typ `dotnet run` zobrazíte výsledky.

## <a name="next-steps"></a>Další kroky

Pokud máte zablokuje, zobrazí se zdroj pro účely tohoto kurzu [v naše úložiště GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Blahopřejeme, jste dokončili všechny naše Úvod do C# kurzy. Pokud chcete získat další informace, zkuste některých našich [kurzy](../index.md)
