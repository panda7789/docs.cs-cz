---
title: Třídy a objekty – Úvod do kurzu jazyka C#
description: Vytvoření prvního programu v jazyce C# a prozkoumání konceptů orientovaných na objekty
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5edb2d7b11caace2d794b7958dfeb75ef502ee2b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396868"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Prozkoumat objektově orientované programování pomocí tříd a objektů

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="create-your-application"></a>Vytvořte si svoji aplikaci

Pomocí okna terminálu vytvořte adresář s názvem *Classes*. V takovém případě sestavíte svou aplikaci. Přejděte do tohoto adresáře a zadejte `dotnet new console` v okně konzoly. Tento příkaz vytvoří vaši aplikaci. Otevřete *program.cs*. Mělo by to vypadat takto:

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

V tomto kurzu budete vytvářet nové typy, které reprezentují bankovní účet. Vývojáři obvykle definují každou třídu v jiném textovém souboru. To usnadňuje správu v případě, že se velikost programu zvětšuje. V adresáři *třídy* vytvořte nový soubor s názvem *BankAccount.cs* .

Tento soubor bude obsahovat definici ***bankovního účtu***. Objektově orientované programování organizuje kód vytvořením typů ve formě ***tříd***. Tyto třídy obsahují kód, který představuje konkrétní entitu. `BankAccount`Třída představuje bankovní účet. Kód implementuje konkrétní operace prostřednictvím metod a vlastností. V tomto kurzu bankovní účet podporuje toto chování:

1. Má 10 číslic, které jedinečně identifikují bankovní účet.
1. Obsahuje řetězec, který ukládá název nebo názvy vlastníků.
1. Zůstatek lze načíst.
1. Přijímá vklady.
1. Přijímá stažení.
1. Počáteční zůstatek musí být kladný.
1. Vyčerpání nemůže vést k zápornému zůstatku.

## <a name="define-the-bank-account-type"></a>Definování typu bankovního účtu

Můžete začít vytvořením základních tříd, které definují toto chování. Vytvořte nový soubor pomocí příkazu **soubor: nový** . Pojmenujte ho *BankAccount.cs*. Do souboru *BankAccount.cs* přidejte následující kód:

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

Než začnete pracovat, Podívejme se na to, co jste vytvořili.  `namespace`Deklarace poskytuje způsob, jak logicky organizovat váš kód. Tento kurz je poměrně malý, takže veškerý kód se vloží do jednoho oboru názvů.

`public class BankAccount`definuje třídu nebo typ, který vytváříte. Vše uvnitř `{` a `}` , které následuje deklarace třídy, definuje stav a chování třídy. Existuje pět ***členů*** `BankAccount` třídy. První tři jsou ***vlastnosti***. Vlastnosti jsou datové prvky a mohou mít kód, který vynutil ověřování nebo jiná pravidla. Poslední dvě jsou ***metody***. Metody jsou bloky kódu, které provádějí jednu funkci. Čtení názvů jednotlivých členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře, aby bylo možné pochopit, co třída dělá.

## <a name="open-a-new-account"></a>Otevřít nový účet

První funkcí, kterou je třeba implementovat, je otevření bankovního účtu. Když zákazník otevře účet, musí dodat počáteční zůstatek a informace o vlastníkovi nebo vlastníkovi tohoto účtu.

Vytvoření nového objektu `BankAccount` typu znamená definování ***konstruktoru*** , který přiřazuje tyto hodnoty. ***Konstruktor*** je člen, který má stejný název jako třída. Slouží k inicializaci objektů tohoto typu třídy. Přidejte k typu následující konstruktor `BankAccount` . Vložte následující kód nad deklaraci `MakeDeposit` :

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory jsou volány při vytváření objektu pomocí [`new`](../../language-reference/operators/new-operator.md) . Nahraďte řádek `Console.WriteLine("Hello World!");` v *program.cs* následujícím kódem (nahraďte `<name>` svým jménem):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Pojďme spustit, co jste zatím vytvořili. Pokud používáte aplikaci Visual Studio, vyberte možnost **Spustit bez ladění** z nabídky **Spustit** . Pokud používáte příkazový řádek, zadejte `dotnet run` do adresáře, kde jste vytvořili projekt.

Všimnete si, že číslo účtu je prázdné? Je čas ji opravit. Číslo účtu by mělo být přiřazeno, když je objekt vytvořen. Ale nemělo by to být zodpovědností volajícího vytvořit. `BankAccount`Kód třídy by měl znát způsob přiřazení nových čísel účtů.  To lze provést jednoduše tak, že začnete s 10 číslicemi. Při vytvoření každého nového účtu ho zvyšte. Nakonec uložte aktuální číslo účtu, když je objekt vytvořen.

Přidejte do třídy deklaraci člena `BankAccount` . Vložte následující řádek kódu za levou složenou závorku `{` na začátku `BankAccount` třídy:

```csharp
private static int accountNumberSeed = 1234567890;
```

Toto je datový člen. Je to `private` , to znamená, že k němu lze přistupovat pouze pomocí kódu uvnitř `BankAccount` třídy. Jedná se o způsob, jak oddělit veřejné zodpovědnosti (jako je třeba číslo účtu) od soukromé implementace (jak se generují čísla účtů). Je to také to `static` , to znamená, že je sdílen všemi `BankAccount` objekty. Hodnota proměnné, která není statická, je jedinečná pro každou instanci `BankAccount` objektu. Přidejte následující dva řádky do konstruktoru, aby bylo možné přiřadit číslo účtu. Umístěte je za řádek, který říká `this.Balance = initialBalance` :

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

`dotnet run`Pro zobrazení výsledků zadejte.

## <a name="create-deposits-and-withdrawals"></a>Vytváření vkladů a stažení

Třída bankovního účtu musí přijímat vklady a stažení, aby fungovaly správně. Pojďme implementovat vklady a stažení, a to vytvořením deníku každé transakce pro účet. Který má několik výhod v rámci jednoduché aktualizace zůstatku každé transakce. Historii lze použít k auditování všech transakcí a ke správě každodenních zůstatků. Vynásobením zůstatku z historie všech transakcí v případě potřeby budou všechny chyby v jedné transakci, které jsou opraveny, správně promítnuty do zůstatku následujícího výpočtu.

Pojďme začít vytvořením nového typu reprezentujícího transakci. Toto je jednoduchý typ, který nemá žádné zodpovědnosti. Potřebuje několik vlastností. Vytvořte nový soubor s názvem *Transaction.cs*. Přidejte do ní následující kód:

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

Nyní přidáme do <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` třídy objekty. Přidejte následující deklaraci za konstruktor v souboru *BankAccount.cs* :

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<xref:System.Collections.Generic.List%601>Třída vyžaduje, abyste naimportovali jiný obor názvů. Na začátek *BankAccount.cs*přidejte následující:

```csharp
using System.Collections.Generic;
```

Teď změníme způsob, jakým `Balance` se nahlásí.  Dá se najít sečtením hodnot všech transakcí. Upravte deklaraci `Balance` ve `BankAccount` třídě na následující:

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Tento příklad ukazuje důležitý aspekt ***vlastností***. Nyní počítáte rovnováhu, když další programátor žádá o hodnotu. Vaše výpočty vyčísluje všechny transakce a jako aktuální zůstatek poskytuje součet.

Dále implementujte `MakeDeposit` metody a `MakeWithdrawal` . Tyto metody vyplatí poslední dvě pravidla: počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvořit záporný zůstatek.

Tím se zavádí koncept ***výjimek***. Standardní způsob, jak určit, že metoda nemůže dokončit svou práci, je vyvolat výjimku. Typ výjimky a přidružená zpráva popisují chybu. V tomto případě `MakeDeposit` metoda vyvolá výjimku, pokud je velikost depozita záporná. `MakeWithdrawal`Metoda vyvolá výjimku, pokud je částka pro stažení záporná, nebo pokud se použije výsledek vyjmutí v záporném zůstatku. Po deklaraci seznamu přidejte následující kód `allTransactions` :

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

[`throw`](../../language-reference/keywords/throw.md)Příkaz **vyvolá** výjimku. Spuštění aktuálního bloku končí a řízení přenosů do prvního odpovídajícího `catch` bloku nalezeného v zásobníku volání. Přidáte `catch` blok pro otestování tohoto kódu trochu později.

Konstruktor by měl získat jednu změnu, aby přidal počáteční transakci místo přímé aktualizace zůstatku. Vzhledem k tomu, že jste již zapsali `MakeDeposit` metodu, zavolejte ji z konstruktoru. Dokončený konstruktor by měl vypadat takto:

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrací aktuální datum a čas. Otestujte to přidáním několika vkladů a výstupů v `Main` metodě za kód, který vytvoří novou `BankAccount` :

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

V dalším kroku otestujte chybové stavy tím, že se pokusíte vytvořit účet se záporným zůstatkem. Za předchozí kód, který jste právě přidali, přidejte následující kód:

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

[ `try` `catch` Příkazy a](../../language-reference/keywords/try-catch.md) můžete použít k označení bloku kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte. Stejný postup můžete použít k otestování kódu, který vyvolá výjimku pro záporný zůstatek. Na konec metody přidejte následující kód `Main` :

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

Uložte soubor a zadejte `dotnet run` ho a zkuste to znovu.

## <a name="challenge---log-all-transactions"></a>Výzva – protokoluje všechny transakce.

Pro dokončení tohoto kurzu můžete napsat `GetAccountHistory` metodu, která vytvoří `string` pro historii transakce. Přidejte tuto metodu do `BankAccount` typu:

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

To používá <xref:System.Text.StringBuilder> třídu k formátování řetězce, který obsahuje jeden řádek pro každou transakci. Kód pro formátování řetězců jste viděli dříve v těchto kurzech. Jeden nový znak je `\t` . Tím se vloží karta pro formátování výstupu.

Přidejte tento řádek k otestování v *program.cs*:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Výsledky zobrazíte spuštěním programu.

## <a name="next-steps"></a>Další kroky

Pokud jste se zablokovali, můžete se podívat na zdroj tohoto kurzu [v našem úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).

Blahopřejeme, dokončili jste všechny naše Úvod do kurzů C#. Pokud se Eager o další informace, vyzkoušejte si více našich [kurzů](../index.md).
