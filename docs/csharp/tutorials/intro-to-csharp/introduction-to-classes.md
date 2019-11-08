---
title: Třídy a objekty – Úvod do C# kurzu
description: Vytvoření prvního C# programu a prozkoumání konceptů orientovaných na objekty
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: e4cf7912de69946289c0594944b8ac3a8c252ac2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736838"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Prozkoumat objektově orientované programování pomocí tříd a objektů

V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj. Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS. Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.

## <a name="create-your-application"></a>Vytvoření aplikace

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

Tento soubor bude obsahovat definici ***bankovního účtu***. Objektově orientované programování organizuje kód vytvořením typů ve formě ***tříd***. Tyto třídy obsahují kód, který představuje konkrétní entitu. Třída `BankAccount` představuje bankovní účet. Kód implementuje konkrétní operace prostřednictvím metod a vlastností. V tomto kurzu bankovní účet podporuje toto chování:

1. Má 10 číslic, které jedinečně identifikují bankovní účet.
1. Obsahuje řetězec, který ukládá název nebo názvy vlastníků.
1. Zůstatek lze načíst.
1. Přijímá vklady.
1. Přijímá stažení.
1. Počáteční zůstatek musí být kladný.
1. Vyčerpání nemůže vést k zápornému zůstatku.

## <a name="define-the-bank-account-type"></a>Definování typu bankovního účtu

Můžete začít vytvořením základních tříd, které definují toto chování. To by vypadalo takto:

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

Než začnete pracovat, Podívejme se na to, co jste vytvořili.  Deklarace `namespace` poskytuje způsob, jak logicky organizovat váš kód. Tento kurz je poměrně malý, takže veškerý kód se vloží do jednoho oboru názvů. 

`public class BankAccount` definuje třídu nebo typ, který vytváříte. Vše uvnitř `{` a `}`, které následuje deklarace třídy, definuje chování třídy. Existuje pět ***členů*** třídy `BankAccount`. První tři jsou ***vlastnosti***. Vlastnosti jsou datové prvky a mohou mít kód, který vynutil ověřování nebo jiná pravidla. Poslední dvě jsou ***metody***. Metody jsou bloky kódu, které provádějí jednu funkci. Čtení názvů jednotlivých členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře, aby bylo možné pochopit, co třída dělá.

## <a name="open-a-new-account"></a>Otevřít nový účet

První funkcí, kterou je třeba implementovat, je otevření bankovního účtu. Když zákazník otevře účet, musí dodat počáteční zůstatek a informace o vlastníkovi nebo vlastníkovi tohoto účtu. 

Vytvoření nového objektu `BankAccount`ho typu znamená definování ***konstruktoru*** , který přiřazuje tyto hodnoty. ***Konstruktor*** je člen, který má stejný název jako třída. Slouží k inicializaci objektů tohoto typu třídy. Přidejte následující konstruktor do typu `BankAccount`:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Konstruktory jsou volány při vytváření objektu pomocí [`new`](../../language-reference/operators/new-operator.md). Řádek `Console.WriteLine("Hello World!");` v *program.cs* nahraďte následujícím řádkem (nahraďte `<name>` názvem):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Zadejte `dotnet run` a zjistěte, co se stane.  

Všimnete si, že číslo účtu je prázdné? Je čas ji opravit. Číslo účtu by mělo být přiřazeno, když je objekt vytvořen. Ale nemělo by to být zodpovědností volajícího vytvořit. Kód třídy `BankAccount` by měl znát způsob přiřazení nových čísel účtů.  To lze provést jednoduše tak, že začnete s 10 číslicemi. Při vytvoření každého nového účtu ho zvyšte. Nakonec uložte aktuální číslo účtu, když je objekt vytvořen.

Přidejte následující deklaraci člena do třídy `BankAccount`:

```csharp
private static int accountNumberSeed = 1234567890;
```

Toto je datový člen. Je to `private`, což znamená, že k němu lze přistupovat pouze pomocí kódu v rámci `BankAccount` třídy. Jedná se o způsob, jak oddělit veřejné zodpovědnosti (jako je třeba číslo účtu) od soukromé implementace (způsob generování čísel účtů). Je také `static`, což znamená, že je sdílen všemi objekty `BankAccount`. Hodnota proměnné, která není statická, je jedinečná pro každou instanci objektu `BankAccount`. Přidejte následující dva řádky do konstruktoru pro přiřazení čísla účtu:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Výsledky zobrazíte zadáním `dotnet run`.

## <a name="create-deposits-and-withdrawals"></a>Vytváření vkladů a stažení

Třída bankovního účtu musí přijímat vklady a stažení, aby fungovaly správně. Pojďme implementovat vklady a stažení, a to vytvořením deníku každé transakce pro účet. Který má několik výhod v rámci jednoduché aktualizace zůstatku každé transakce. Historii lze použít k auditování všech transakcí a ke správě každodenních zůstatků. Vynásobením zůstatku z historie všech transakcí v případě potřeby budou všechny chyby v jedné transakci, které jsou opraveny, správně promítnuty do zůstatku následujícího výpočtu.

Pojďme začít vytvořením nového typu reprezentujícího transakci. Toto je jednoduchý typ, který nemá žádné zodpovědnosti. Potřebuje několik vlastností. Vytvořte nový soubor s názvem *Transaction.cs*. Přidejte do něj následující kód:

[!code-csharp[Transaction](~/samples/csharp/classes-quickstart/Transaction.cs)]

Nyní přidáme <xref:System.Collections.Generic.List%601> objektů `Transaction` do třídy `BankAccount`. Přidejte následující deklaraci:

[!code-csharp[TransactionDecl](~/samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

Třída <xref:System.Collections.Generic.List%601> vyžaduje, abyste naimportovali jiný obor názvů. Na začátek *BankAccount.cs*přidejte následující:

```csharp
using System.Collections.Generic;
```

Teď změníme způsob hlášení `Balance`.  Dá se najít sečtením hodnot všech transakcí. Upravte deklaraci `Balance` ve třídě `BankAccount` na následující:

[!code-csharp[BalanceComputation](~/samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Tento příklad ukazuje důležitý aspekt ***vlastností***. Nyní počítáte rovnováhu, když další programátor žádá o hodnotu. Vaše výpočty vyčísluje všechny transakce a jako aktuální zůstatek poskytuje součet.

Dále Implementujte metody `MakeDeposit` a `MakeWithdrawal`. Tyto metody vyplatí poslední dvě pravidla: počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvořit záporný zůstatek. 

Tím se zavádí koncept ***výjimek***. Standardní způsob, jak určit, že metoda nemůže dokončit svou práci, je vyvolat výjimku. Typ výjimky a přidružená zpráva popisují chybu. V tomto případě metoda `MakeDeposit` vyvolá výjimku, pokud je velikost depozita záporná. Metoda `MakeWithdrawal` vyvolá výjimku, pokud je částka pro stažení záporná, nebo pokud se použije výsledek vyjmutí v záporném zůstatku:

[!code-csharp[DepositAndWithdrawal](~/samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

Příkaz [`throw`](../../language-reference/keywords/throw.md) **vyvolá** výjimku. Spuštění aktuálního bloku končí a ovládací prvky se přenesou do prvního odpovídajícího `catch` bloku nalezeného v zásobníku volání. Přidáte `catch` blok pro otestování tohoto kódu trochu později.

Konstruktor by měl získat jednu změnu, aby přidal počáteční transakci místo přímé aktualizace zůstatku. Vzhledem k tomu, že jste už napsali metodu `MakeDeposit`, zavolejte ji z vašeho konstruktoru. Dokončený konstruktor by měl vypadat takto:

[!code-csharp[Constructor](~/samples/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType> je vlastnost, která vrátí aktuální datum a čas. Otestujte to přidáním několika vkladů a staženími v metodě `Main`:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

V dalším kroku otestujte chybové stavy tím, že se pokusíte vytvořit účet se záporným zůstatkem:

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

Pomocí [příkazů`try` a `catch`](../../language-reference/keywords/try-catch.md) označíte blok kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte. Stejný postup můžete použít k otestování kódu, který vyvolá výjimku pro záporný zůstatek:

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

Uložte soubor a zadejte `dotnet run`, abyste ho mohli vyzkoušet.

## <a name="challenge---log-all-transactions"></a>Výzva – protokoluje všechny transakce.

Pro dokončení tohoto kurzu můžete napsat metodu `GetAccountHistory`, která vytvoří `string` pro historii transakce. Přidejte tuto metodu do `BankAccount`ho typu:

[!code-csharp[History](~/samples/csharp/classes-quickstart/BankAccount.cs#History)]

Tato třída používá třídu <xref:System.Text.StringBuilder> k formátování řetězce, který obsahuje jeden řádek pro každou transakci. Kód pro formátování řetězců jste viděli dříve v těchto kurzech. Jeden nový znak je `\t`. Tím se vloží karta pro formátování výstupu.

Přidejte tento řádek k otestování v *program.cs*:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Výsledky zobrazíte zadáním `dotnet run`.

## <a name="next-steps"></a>Další kroky

Pokud jste se zablokovali, můžete se podívat na zdroj tohoto kurzu [v našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).

Blahopřejeme, dokončili jste všechny naše úvodní C# informace k kurzům. Pokud se Eager o další informace, vyzkoušejte si více našich [kurzů](../index.md).
