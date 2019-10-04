---
title: Třídy a objekty – Úvod do C# kurzu
description: Vytvoření prvního C# programu a prozkoumání konceptů orientovaných na objekty
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: f4199f709ee0011af9f00f6909193f08345bc49e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834109"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="37e87-103">Prozkoumat objektově orientované programování pomocí tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="37e87-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="37e87-104">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="37e87-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="37e87-105">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="37e87-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="37e87-106">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="37e87-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="37e87-107">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="37e87-107">Create your application</span></span>

<span data-ttu-id="37e87-108">Pomocí okna terminálu vytvořte adresář s názvem *Classes*.</span><span class="sxs-lookup"><span data-stu-id="37e87-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="37e87-109">V takovém případě sestavíte svou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37e87-109">You'll build your application there.</span></span> <span data-ttu-id="37e87-110">Přejděte do tohoto adresáře a v okně konzoly zadejte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="37e87-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="37e87-111">Tento příkaz vytvoří vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37e87-111">This command creates your application.</span></span> <span data-ttu-id="37e87-112">Otevřete *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="37e87-112">Open *Program.cs*.</span></span> <span data-ttu-id="37e87-113">Mělo by to vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="37e87-113">It should look like this:</span></span>

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

<span data-ttu-id="37e87-114">V tomto kurzu budete vytvářet nové typy, které reprezentují bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="37e87-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="37e87-115">Vývojáři obvykle definují každou třídu v jiném textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="37e87-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="37e87-116">To usnadňuje správu v případě, že se velikost programu zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="37e87-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="37e87-117">V adresáři *třídy* vytvořte nový soubor s názvem *BankAccount.cs* .</span><span class="sxs-lookup"><span data-stu-id="37e87-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span> 

<span data-ttu-id="37e87-118">Tento soubor bude obsahovat definici ***bankovního účtu***.</span><span class="sxs-lookup"><span data-stu-id="37e87-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="37e87-119">Objektově orientované programování organizuje kód vytvořením typů ve formě ***tříd***.</span><span class="sxs-lookup"><span data-stu-id="37e87-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="37e87-120">Tyto třídy obsahují kód, který představuje konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="37e87-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="37e87-121">Třída `BankAccount` představuje bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="37e87-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="37e87-122">Kód implementuje konkrétní operace prostřednictvím metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="37e87-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="37e87-123">V tomto kurzu bankovní účet podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="37e87-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="37e87-124">Má 10 číslic, které jedinečně identifikují bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="37e87-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="37e87-125">Obsahuje řetězec, který ukládá název nebo názvy vlastníků.</span><span class="sxs-lookup"><span data-stu-id="37e87-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="37e87-126">Zůstatek lze načíst.</span><span class="sxs-lookup"><span data-stu-id="37e87-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="37e87-127">Přijímá vklady.</span><span class="sxs-lookup"><span data-stu-id="37e87-127">It accepts deposits.</span></span>
1. <span data-ttu-id="37e87-128">Přijímá stažení.</span><span class="sxs-lookup"><span data-stu-id="37e87-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="37e87-129">Počáteční zůstatek musí být kladný.</span><span class="sxs-lookup"><span data-stu-id="37e87-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="37e87-130">Vyčerpání nemůže vést k zápornému zůstatku.</span><span class="sxs-lookup"><span data-stu-id="37e87-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="37e87-131">Definování typu bankovního účtu</span><span class="sxs-lookup"><span data-stu-id="37e87-131">Define the bank account type</span></span>

<span data-ttu-id="37e87-132">Můžete začít vytvořením základních tříd, které definují toto chování.</span><span class="sxs-lookup"><span data-stu-id="37e87-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="37e87-133">To by vypadalo takto:</span><span class="sxs-lookup"><span data-stu-id="37e87-133">It would look like this:</span></span>

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

<span data-ttu-id="37e87-134">Než začnete pracovat, Podívejme se na to, co jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="37e87-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="37e87-135">Deklarace `namespace` poskytuje způsob, jak logicky organizovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="37e87-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="37e87-136">Tento kurz je poměrně malý, takže veškerý kód se vloží do jednoho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="37e87-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="37e87-137">`public class BankAccount` definuje třídu nebo typ, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="37e87-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="37e87-138">Vše uvnitř `{` a `}`, které následuje deklarace třídy, definuje chování třídy.</span><span class="sxs-lookup"><span data-stu-id="37e87-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="37e87-139">Existuje pět ***členů*** třídy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="37e87-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="37e87-140">První tři jsou ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="37e87-140">The first three are ***properties***.</span></span> <span data-ttu-id="37e87-141">Vlastnosti jsou datové prvky a mohou mít kód, který vynutil ověřování nebo jiná pravidla.</span><span class="sxs-lookup"><span data-stu-id="37e87-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="37e87-142">Poslední dvě jsou ***metody***.</span><span class="sxs-lookup"><span data-stu-id="37e87-142">The last two are ***methods***.</span></span> <span data-ttu-id="37e87-143">Metody jsou bloky kódu, které provádějí jednu funkci.</span><span class="sxs-lookup"><span data-stu-id="37e87-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="37e87-144">Čtení názvů jednotlivých členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře, aby bylo možné pochopit, co třída dělá.</span><span class="sxs-lookup"><span data-stu-id="37e87-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="37e87-145">Otevřít nový účet</span><span class="sxs-lookup"><span data-stu-id="37e87-145">Open a new account</span></span>

<span data-ttu-id="37e87-146">První funkcí, kterou je třeba implementovat, je otevření bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="37e87-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="37e87-147">Když zákazník otevře účet, musí dodat počáteční zůstatek a informace o vlastníkovi nebo vlastníkovi tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="37e87-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="37e87-148">Vytvoření nového objektu typu `BankAccount` znamená definování ***konstruktoru*** , který přiřazuje tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37e87-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="37e87-149">***Konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="37e87-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="37e87-150">Slouží k inicializaci objektů tohoto typu třídy.</span><span class="sxs-lookup"><span data-stu-id="37e87-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="37e87-151">Přidejte následující konstruktor do typu `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="37e87-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="37e87-152">Konstruktory jsou volány při vytváření objektu pomocí [`new`](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="37e87-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="37e87-153">Nahraďte řádek `Console.WriteLine("Hello World!");` v *program.cs* následujícím řádkem (nahraďte `<name>` vaším jménem):</span><span class="sxs-lookup"><span data-stu-id="37e87-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="37e87-154">Pokud se chcete podívat, co se stane, zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="37e87-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="37e87-155">Všimnete si, že číslo účtu je prázdné?</span><span class="sxs-lookup"><span data-stu-id="37e87-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="37e87-156">Je čas ji opravit.</span><span class="sxs-lookup"><span data-stu-id="37e87-156">It's time to fix that.</span></span> <span data-ttu-id="37e87-157">Číslo účtu by mělo být přiřazeno, když je objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="37e87-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="37e87-158">Ale nemělo by to být zodpovědností volajícího vytvořit.</span><span class="sxs-lookup"><span data-stu-id="37e87-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="37e87-159">Kód třídy `BankAccount` by měl znát způsob přiřazení nových čísel účtů.</span><span class="sxs-lookup"><span data-stu-id="37e87-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="37e87-160">To lze provést jednoduše tak, že začnete s 10 číslicemi.</span><span class="sxs-lookup"><span data-stu-id="37e87-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="37e87-161">Při vytvoření každého nového účtu ho zvyšte.</span><span class="sxs-lookup"><span data-stu-id="37e87-161">Increment it when each new account is created.</span></span> <span data-ttu-id="37e87-162">Nakonec uložte aktuální číslo účtu, když je objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="37e87-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="37e87-163">Přidejte následující deklaraci člena do třídy `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="37e87-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="37e87-164">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="37e87-164">This is a data member.</span></span> <span data-ttu-id="37e87-165">Je `private`, což znamená, že k němu lze přistupovat pouze kód v rámci třídy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="37e87-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="37e87-166">Jedná se o způsob, jak oddělit veřejné zodpovědnosti (jako je třeba číslo účtu) od soukromé implementace (způsob generování čísel účtů). Také je `static`, což znamená, že je sdílen všemi objekty `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="37e87-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="37e87-167">Hodnota proměnné, která není statická, je jedinečná pro každou instanci objektu `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="37e87-167">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="37e87-168">Přidejte následující dva řádky do konstruktoru pro přiřazení čísla účtu:</span><span class="sxs-lookup"><span data-stu-id="37e87-168">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="37e87-169">Pokud chcete zobrazit výsledky, zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="37e87-169">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="37e87-170">Vytváření vkladů a stažení</span><span class="sxs-lookup"><span data-stu-id="37e87-170">Create deposits and withdrawals</span></span>

<span data-ttu-id="37e87-171">Třída bankovního účtu musí přijímat vklady a stažení, aby fungovaly správně.</span><span class="sxs-lookup"><span data-stu-id="37e87-171">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="37e87-172">Pojďme implementovat vklady a stažení, a to vytvořením deníku každé transakce pro účet.</span><span class="sxs-lookup"><span data-stu-id="37e87-172">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="37e87-173">Který má několik výhod v rámci jednoduché aktualizace zůstatku každé transakce.</span><span class="sxs-lookup"><span data-stu-id="37e87-173">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="37e87-174">Historii lze použít k auditování všech transakcí a ke správě každodenních zůstatků.</span><span class="sxs-lookup"><span data-stu-id="37e87-174">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="37e87-175">Vynásobením zůstatku z historie všech transakcí v případě potřeby budou všechny chyby v jedné transakci, které jsou opraveny, správně promítnuty do zůstatku následujícího výpočtu.</span><span class="sxs-lookup"><span data-stu-id="37e87-175">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="37e87-176">Pojďme začít vytvořením nového typu reprezentujícího transakci.</span><span class="sxs-lookup"><span data-stu-id="37e87-176">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="37e87-177">Toto je jednoduchý typ, který nemá žádné zodpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="37e87-177">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="37e87-178">Potřebuje několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="37e87-178">It needs a few properties.</span></span> <span data-ttu-id="37e87-179">Vytvořte nový soubor s názvem *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="37e87-179">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="37e87-180">Přidejte do něj následující kód:</span><span class="sxs-lookup"><span data-stu-id="37e87-180">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="37e87-181">Nyní přidáme <xref:System.Collections.Generic.List%601> objektů `Transaction` do třídy `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="37e87-181">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="37e87-182">Přidejte následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="37e87-182">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="37e87-183">Třída <xref:System.Collections.Generic.List%601> vyžaduje, abyste naimportovali jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="37e87-183">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="37e87-184">Na začátek *BankAccount.cs*přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="37e87-184">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="37e87-185">Teď změníme způsob, jakým se nahlásí `Balance`.</span><span class="sxs-lookup"><span data-stu-id="37e87-185">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="37e87-186">Dá se najít sečtením hodnot všech transakcí.</span><span class="sxs-lookup"><span data-stu-id="37e87-186">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="37e87-187">Upravte deklaraci `Balance` ve třídě `BankAccount` na následující:</span><span class="sxs-lookup"><span data-stu-id="37e87-187">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="37e87-188">Tento příklad ukazuje důležitý aspekt ***vlastností***.</span><span class="sxs-lookup"><span data-stu-id="37e87-188">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="37e87-189">Nyní počítáte rovnováhu, když další programátor žádá o hodnotu.</span><span class="sxs-lookup"><span data-stu-id="37e87-189">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="37e87-190">Vaše výpočty vyčísluje všechny transakce a jako aktuální zůstatek poskytuje součet.</span><span class="sxs-lookup"><span data-stu-id="37e87-190">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="37e87-191">Dále Implementujte metody `MakeDeposit` a `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="37e87-191">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="37e87-192">Tyto metody vyplatí poslední dvě pravidla: počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvořit záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="37e87-192">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="37e87-193">Tím se zavádí koncept ***výjimek***.</span><span class="sxs-lookup"><span data-stu-id="37e87-193">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="37e87-194">Standardní způsob, jak určit, že metoda nemůže dokončit svou práci, je vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="37e87-194">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="37e87-195">Typ výjimky a přidružená zpráva popisují chybu.</span><span class="sxs-lookup"><span data-stu-id="37e87-195">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="37e87-196">V tomto případě metoda `MakeDeposit` vyvolá výjimku, pokud je velikost vkladu záporná.</span><span class="sxs-lookup"><span data-stu-id="37e87-196">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="37e87-197">Metoda `MakeWithdrawal` vyvolá výjimku, pokud je částka pro stažení záporná, nebo pokud se použije výsledek odinstalace v záporném zůstatku:</span><span class="sxs-lookup"><span data-stu-id="37e87-197">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="37e87-198">Příkaz [`throw`](../../language-reference/keywords/throw.md) **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="37e87-198">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="37e87-199">Spuštění aktuálního bloku končí a řízení přenosů do prvního odpovídajícího bloku `catch` nalezeného v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="37e87-199">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="37e87-200">Přidáte blok `catch` pro otestování tohoto kódu trochu později.</span><span class="sxs-lookup"><span data-stu-id="37e87-200">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="37e87-201">Konstruktor by měl získat jednu změnu, aby přidal počáteční transakci místo přímé aktualizace zůstatku.</span><span class="sxs-lookup"><span data-stu-id="37e87-201">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="37e87-202">Vzhledem k tomu, že jste již zapsali metodu `MakeDeposit`, zavolejte ji z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="37e87-202">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="37e87-203">Dokončený konstruktor by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="37e87-203">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="37e87-204"><xref:System.DateTime.Now?displayProperty=nameWithType> je vlastnost, která vrací aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="37e87-204"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="37e87-205">Otestujte to přidáním několika vkladů a staženími v metodě `Main`:</span><span class="sxs-lookup"><span data-stu-id="37e87-205">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="37e87-206">V dalším kroku otestujte chybové stavy tím, že se pokusíte vytvořit účet se záporným zůstatkem:</span><span class="sxs-lookup"><span data-stu-id="37e87-206">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="37e87-207">Pomocí [příkazů `try` a `catch`](../../language-reference/keywords/try-catch.md) označíte blok kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="37e87-207">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="37e87-208">Stejný postup můžete použít k otestování kódu, který vyvolá výjimku pro záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="37e87-208">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

```csharp
// Test for a negative balance:
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

<span data-ttu-id="37e87-209">Uložte soubor a zadejte `dotnet run` a zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="37e87-209">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="37e87-210">Výzva – protokoluje všechny transakce.</span><span class="sxs-lookup"><span data-stu-id="37e87-210">Challenge - log all transactions</span></span>

<span data-ttu-id="37e87-211">Pro dokončení tohoto kurzu můžete napsat metodu `GetAccountHistory`, která pro historii transakcí vytvoří `string`.</span><span class="sxs-lookup"><span data-stu-id="37e87-211">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="37e87-212">Přidejte tuto metodu do typu `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="37e87-212">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="37e87-213">Používá třídu <xref:System.Text.StringBuilder> k formátování řetězce, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="37e87-213">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="37e87-214">Kód pro formátování řetězců jste viděli dříve v těchto kurzech.</span><span class="sxs-lookup"><span data-stu-id="37e87-214">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="37e87-215">Jeden nový znak je `\t`.</span><span class="sxs-lookup"><span data-stu-id="37e87-215">One new character is `\t`.</span></span> <span data-ttu-id="37e87-216">Tím se vloží karta pro formátování výstupu.</span><span class="sxs-lookup"><span data-stu-id="37e87-216">That inserts a tab to format the output.</span></span>

<span data-ttu-id="37e87-217">Přidejte tento řádek k otestování v *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="37e87-217">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="37e87-218">Pokud chcete zobrazit výsledky, zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="37e87-218">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="37e87-219">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37e87-219">Next Steps</span></span>

<span data-ttu-id="37e87-220">Pokud jste se zablokovali, můžete se podívat na zdroj tohoto kurzu [v našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/) .</span><span class="sxs-lookup"><span data-stu-id="37e87-220">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="37e87-221">Blahopřejeme, dokončili jste všechny naše úvodní C# informace k kurzům.</span><span class="sxs-lookup"><span data-stu-id="37e87-221">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="37e87-222">Pokud se Eager o další informace, vyzkoušejte si více našich [kurzů](../index.md) .</span><span class="sxs-lookup"><span data-stu-id="37e87-222">If you're eager to learn more, try more of our [tutorials](../index.md)</span></span>
