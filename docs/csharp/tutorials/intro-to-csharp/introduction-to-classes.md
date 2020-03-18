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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="1057d-103">Prozkoumejte objektově orientované programování pomocí tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="1057d-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="1057d-104">Tento kurz očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="1057d-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="1057d-105">Kurz .NET [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="1057d-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="1057d-106">Rychlý přehled příkazů, které budete používat, najdete v části [Seznamte se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="1057d-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="1057d-107">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="1057d-107">Create your application</span></span>

<span data-ttu-id="1057d-108">Pomocí okna terminálu vytvořte adresář s názvem *classes*.</span><span class="sxs-lookup"><span data-stu-id="1057d-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="1057d-109">Budete stavět svou aplikaci tam.</span><span class="sxs-lookup"><span data-stu-id="1057d-109">You'll build your application there.</span></span> <span data-ttu-id="1057d-110">Změňte na tento `dotnet new console` adresář a zadejte do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="1057d-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="1057d-111">Tento příkaz vytvoří aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1057d-111">This command creates your application.</span></span> <span data-ttu-id="1057d-112">Otevřít *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="1057d-112">Open *Program.cs*.</span></span> <span data-ttu-id="1057d-113">Mělo by to vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1057d-113">It should look like this:</span></span>

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

<span data-ttu-id="1057d-114">V tomto kurzu budete vytvářet nové typy, které představují bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="1057d-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="1057d-115">Vývojáři obvykle definují každou třídu v jiném textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="1057d-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="1057d-116">To usnadňuje správu, protože se velikost programu zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="1057d-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="1057d-117">Vytvořte nový soubor s názvem *BankAccount.cs* v adresáři *tříd.*</span><span class="sxs-lookup"><span data-stu-id="1057d-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="1057d-118">Tento soubor bude obsahovat definici ***bankovního účtu***.</span><span class="sxs-lookup"><span data-stu-id="1057d-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="1057d-119">Objektově orientované programování uspořádá kód vytvořením typů ve formě ***tříd***.</span><span class="sxs-lookup"><span data-stu-id="1057d-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="1057d-120">Tyto třídy obsahují kód, který představuje konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="1057d-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="1057d-121">Třída `BankAccount` představuje bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="1057d-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="1057d-122">Kód implementuje konkrétní operace prostřednictvím metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="1057d-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="1057d-123">V tomto kurzu bankovní účet podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="1057d-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="1057d-124">Má desetimístné číslo, které jednoznačně identifikuje bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="1057d-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="1057d-125">Má řetězec, který ukládá název nebo názvy vlastníků.</span><span class="sxs-lookup"><span data-stu-id="1057d-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="1057d-126">Zůstatek lze načíst.</span><span class="sxs-lookup"><span data-stu-id="1057d-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="1057d-127">Přijímá vklady.</span><span class="sxs-lookup"><span data-stu-id="1057d-127">It accepts deposits.</span></span>
1. <span data-ttu-id="1057d-128">Přijímá výběry.</span><span class="sxs-lookup"><span data-stu-id="1057d-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="1057d-129">Počáteční zůstatek musí být kladný.</span><span class="sxs-lookup"><span data-stu-id="1057d-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="1057d-130">Výběry nemohou mít za následek záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="1057d-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="1057d-131">Definování typu bankovního účtu</span><span class="sxs-lookup"><span data-stu-id="1057d-131">Define the bank account type</span></span>

<span data-ttu-id="1057d-132">Můžete začít vytvořením základů třídy, která definuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="1057d-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="1057d-133">Vypadalo by to takto:</span><span class="sxs-lookup"><span data-stu-id="1057d-133">It would look like this:</span></span>

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

<span data-ttu-id="1057d-134">Než půjdete dál, podívejme se na to, co jste vybudovali.</span><span class="sxs-lookup"><span data-stu-id="1057d-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="1057d-135">Deklarace `namespace` poskytuje způsob, jak logicky uspořádat kód.</span><span class="sxs-lookup"><span data-stu-id="1057d-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="1057d-136">Tento kurz je relativně malý, takže veškerý kód vložíte do jednoho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1057d-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="1057d-137">`public class BankAccount`definuje třídu nebo typ, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="1057d-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="1057d-138">Vše uvnitř `{` `}` a které následuje deklarace třídy definuje stav a chování třídy.</span><span class="sxs-lookup"><span data-stu-id="1057d-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="1057d-139">Ve `BankAccount` třídě je pět ***členů.***</span><span class="sxs-lookup"><span data-stu-id="1057d-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="1057d-140">První tři jsou ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="1057d-140">The first three are ***properties***.</span></span> <span data-ttu-id="1057d-141">Vlastnosti jsou datové prvky a může mít kód, který vynucuje ověření nebo jiná pravidla.</span><span class="sxs-lookup"><span data-stu-id="1057d-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="1057d-142">Poslední dvě jsou ***metody***.</span><span class="sxs-lookup"><span data-stu-id="1057d-142">The last two are ***methods***.</span></span> <span data-ttu-id="1057d-143">Metody jsou bloky kódu, které provádějí jednu funkci.</span><span class="sxs-lookup"><span data-stu-id="1057d-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="1057d-144">Čtení názvů každého z členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře pochopit, co třída dělá.</span><span class="sxs-lookup"><span data-stu-id="1057d-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="1057d-145">Otevření nového účtu</span><span class="sxs-lookup"><span data-stu-id="1057d-145">Open a new account</span></span>

<span data-ttu-id="1057d-146">První funkcí, kterou je třeba implementovat, je otevření bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="1057d-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="1057d-147">Když si zákazník otevře účet, musí zadat počáteční zůstatek a informace o vlastníkovi nebo vlastnících tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="1057d-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="1057d-148">Vytvoření nového objektu `BankAccount` typu znamená definování ***konstruktoru,*** který přiřadí tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1057d-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="1057d-149">***Konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="1057d-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="1057d-150">Používá se k inicializaci objektů tohoto typu třídy.</span><span class="sxs-lookup"><span data-stu-id="1057d-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="1057d-151">Přidejte do `BankAccount` typu následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="1057d-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="1057d-152">Konstruktory jsou volány při [`new`](../../language-reference/operators/new-operator.md)vytváření objektu pomocí .</span><span class="sxs-lookup"><span data-stu-id="1057d-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="1057d-153">Nahraďte `Console.WriteLine("Hello World!");` řádek v *Program.cs* následujícím `<name>` kódem (nahraďte se svým jménem):</span><span class="sxs-lookup"><span data-stu-id="1057d-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="1057d-154">Zadejte, `dotnet run` abyste viděli, co se stane.</span><span class="sxs-lookup"><span data-stu-id="1057d-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="1057d-155">Všimli jste si, že číslo účtu je prázdné?</span><span class="sxs-lookup"><span data-stu-id="1057d-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="1057d-156">Je čas to napravit.</span><span class="sxs-lookup"><span data-stu-id="1057d-156">It's time to fix that.</span></span> <span data-ttu-id="1057d-157">Číslo účtu by mělo být přiřazeno při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="1057d-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="1057d-158">Ale to by nemělo být odpovědností volajícího k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="1057d-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="1057d-159">Kód `BankAccount` třídy by měl vědět, jak přiřadit nová čísla účtů.</span><span class="sxs-lookup"><span data-stu-id="1057d-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="1057d-160">Jednoduchý způsob, jak to udělat, je začít s 10-místné číslo.</span><span class="sxs-lookup"><span data-stu-id="1057d-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="1057d-161">Při každém vytvoření nového účtu jej směřuje.</span><span class="sxs-lookup"><span data-stu-id="1057d-161">Increment it when each new account is created.</span></span> <span data-ttu-id="1057d-162">Nakonec uložte číslo aktuálního účtu při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="1057d-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="1057d-163">Do třídy přidejte `BankAccount` následující deklaraci člena:</span><span class="sxs-lookup"><span data-stu-id="1057d-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="1057d-164">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="1057d-164">This is a data member.</span></span> <span data-ttu-id="1057d-165">Je to `private`, což znamená, že lze přistupovat pouze kód uvnitř třídy. `BankAccount`</span><span class="sxs-lookup"><span data-stu-id="1057d-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="1057d-166">Je to způsob, jak oddělit veřejné odpovědnosti (jako je číslo účtu) od soukromé implementace (způsob generování čísel účtů).</span><span class="sxs-lookup"><span data-stu-id="1057d-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="1057d-167">Je také `static`, což znamená, že `BankAccount` je sdílena všemi objekty.</span><span class="sxs-lookup"><span data-stu-id="1057d-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="1057d-168">Hodnota nestatické proměnné je jedinečná pro každou `BankAccount` instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="1057d-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="1057d-169">Přidejte k konstruktoru následující dva řádky a přiřaďte číslo účtu:</span><span class="sxs-lookup"><span data-stu-id="1057d-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="1057d-170">Zadáním `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1057d-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="1057d-171">Vytváření vkladů a výběrů</span><span class="sxs-lookup"><span data-stu-id="1057d-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="1057d-172">Vaše třída bankovního účtu musí přijímat vklady a výběry, aby fungovaly správně.</span><span class="sxs-lookup"><span data-stu-id="1057d-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="1057d-173">Pojďme implementovat vklady a výběry vytvořením deníku každé transakce pro účet.</span><span class="sxs-lookup"><span data-stu-id="1057d-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="1057d-174">To má několik výhod oproti pouhé aktualizaci zůstatku na každé transakci.</span><span class="sxs-lookup"><span data-stu-id="1057d-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="1057d-175">Historii lze použít k auditu všech transakcí a správě denních zůstatků.</span><span class="sxs-lookup"><span data-stu-id="1057d-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="1057d-176">Výpočtem zůstatku z historie všech transakcí v případě potřeby se všechny chyby v jedné transakci, které jsou opraveny, správně projeví v zůstatku při dalším výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1057d-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="1057d-177">Začněme vytvořením nového typu představujícího transakci.</span><span class="sxs-lookup"><span data-stu-id="1057d-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="1057d-178">Jedná se o jednoduchý typ, který nemá žádné povinnosti.</span><span class="sxs-lookup"><span data-stu-id="1057d-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="1057d-179">Potřebuje pár nemovitostí.</span><span class="sxs-lookup"><span data-stu-id="1057d-179">It needs a few properties.</span></span> <span data-ttu-id="1057d-180">Vytvořte nový soubor s názvem *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="1057d-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="1057d-181">Přidejte do ní následující kód:</span><span class="sxs-lookup"><span data-stu-id="1057d-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="1057d-182">Nyní přidáme do <xref:System.Collections.Generic.List%601> třídy `Transaction` objekty. `BankAccount`</span><span class="sxs-lookup"><span data-stu-id="1057d-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="1057d-183">Přidejte následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="1057d-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="1057d-184">Třída <xref:System.Collections.Generic.List%601> vyžaduje import ovat jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1057d-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="1057d-185">Na začátku BankAccount.cs se přidejte k *nejtento*:</span><span class="sxs-lookup"><span data-stu-id="1057d-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="1057d-186">Nyní změníme způsob, `Balance` jakým je hlášen.</span><span class="sxs-lookup"><span data-stu-id="1057d-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="1057d-187">Lze jej nalézt sečtením hodnot všech transakcí.</span><span class="sxs-lookup"><span data-stu-id="1057d-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="1057d-188">Upravte deklaraci `Balance` `BankAccount` ve třídě takto:</span><span class="sxs-lookup"><span data-stu-id="1057d-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="1057d-189">Tento příklad ukazuje důležitý aspekt ***vlastností***.</span><span class="sxs-lookup"><span data-stu-id="1057d-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="1057d-190">Nyní počítačjete zůstatek, když jiný programátor požádá o hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1057d-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="1057d-191">Výpočty počadnou všechny transakce a poskytuje součet jako aktuální zůstatek.</span><span class="sxs-lookup"><span data-stu-id="1057d-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="1057d-192">Dále implementujte `MakeDeposit` `MakeWithdrawal` metody a.</span><span class="sxs-lookup"><span data-stu-id="1057d-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="1057d-193">Tyto metody budou prosazovat poslední dvě pravidla: že počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvářet záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="1057d-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="1057d-194">Tím se zavádí pojem ***výjimky***.</span><span class="sxs-lookup"><span data-stu-id="1057d-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="1057d-195">Standardní způsob označení, že metoda nemůže úspěšně dokončit svou práci, je vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="1057d-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="1057d-196">Typ výjimky a zprávy s ním spojené popisují chybu.</span><span class="sxs-lookup"><span data-stu-id="1057d-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="1057d-197">Zde `MakeDeposit` metoda vyvolá výjimku, pokud je částka vkladu záporná.</span><span class="sxs-lookup"><span data-stu-id="1057d-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="1057d-198">`MakeWithdrawal` Metoda vyvolá výjimku, pokud je částka výběru záporná nebo pokud použití výběru vede k zápornému zůstatku:</span><span class="sxs-lookup"><span data-stu-id="1057d-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="1057d-199">Příkaz [`throw`](../../language-reference/keywords/throw.md) **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="1057d-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="1057d-200">Spuštění aktuálního bloku končí a řízení se `catch` přenese do prvního odpovídajícího bloku nalezeného v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="1057d-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="1057d-201">Přidáte `catch` blok pro testování tohoto kódu o něco později.</span><span class="sxs-lookup"><span data-stu-id="1057d-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="1057d-202">Konstruktor by měl získat jednu změnu tak, aby přidá počáteční transakce, spíše než aktualizovat zůstatek přímo.</span><span class="sxs-lookup"><span data-stu-id="1057d-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="1057d-203">Vzhledem k `MakeDeposit` tomu, že jste již napsali metodu, zavolejte ji z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1057d-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="1057d-204">Hotový konstruktor by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1057d-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="1057d-205"><xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrací aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="1057d-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="1057d-206">Otestujte to přidáním několika vkladů a výběrů ve vaší `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="1057d-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="1057d-207">Dále otestujte, že zachycujete chybové stavy, a to pokusem o vytvoření účtu se záporným zůstatkem:</span><span class="sxs-lookup"><span data-stu-id="1057d-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="1057d-208">Pomocí [ `try` příkazy `catch` a](../../language-reference/keywords/try-catch.md) označit blok kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="1057d-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="1057d-209">Stejnou techniku můžete použít k testování kódu, který vyvolá výjimku pro záporné saldo:</span><span class="sxs-lookup"><span data-stu-id="1057d-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="1057d-210">Uložte soubor `dotnet run` a zadejte jej vyzkoušejte.</span><span class="sxs-lookup"><span data-stu-id="1057d-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="1057d-211">Výzva - protokolovat všechny transakce</span><span class="sxs-lookup"><span data-stu-id="1057d-211">Challenge - log all transactions</span></span>

<span data-ttu-id="1057d-212">Chcete-li dokončit tento kurz, můžete napsat metodu, `GetAccountHistory` která vytvoří `string` pro historii transakcí.</span><span class="sxs-lookup"><span data-stu-id="1057d-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="1057d-213">Přidejte tuto `BankAccount` metodu do typu:</span><span class="sxs-lookup"><span data-stu-id="1057d-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="1057d-214">To používá <xref:System.Text.StringBuilder> třídu k formátování řetězce, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="1057d-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="1057d-215">Viděli jste kód formátování řetězce dříve v těchto kurzech.</span><span class="sxs-lookup"><span data-stu-id="1057d-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="1057d-216">Jeden nový `\t`znak je .</span><span class="sxs-lookup"><span data-stu-id="1057d-216">One new character is `\t`.</span></span> <span data-ttu-id="1057d-217">To vloží kartu pro formátování výstupu.</span><span class="sxs-lookup"><span data-stu-id="1057d-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="1057d-218">Přidejte tento řádek a otestujte jej v *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="1057d-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="1057d-219">Zadáním `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1057d-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1057d-220">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1057d-220">Next steps</span></span>

<span data-ttu-id="1057d-221">Pokud jste uvízli, můžete vidět zdroj pro tento výukový program [v našem úložišti GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="1057d-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="1057d-222">Gratulujeme, jste dokončili všechny naše úvod do c# kurzy.</span><span class="sxs-lookup"><span data-stu-id="1057d-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="1057d-223">Pokud se chcete dozvědět více, vyzkoušejte více našich [výukových programů](../index.md).</span><span class="sxs-lookup"><span data-stu-id="1057d-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
