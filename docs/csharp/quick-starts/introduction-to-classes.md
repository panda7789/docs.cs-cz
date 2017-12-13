---
title: "Průvodce rychlé zahájení – Úvod do třídy - C#"
description: "Vytvoření vaší první programu C# a prozkoumat objektově orientované koncepty"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: b7598309f48cbccf2d270be53a4b40dae11e8df8
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2017
---
# <a name="introduction-to-classes"></a><span data-ttu-id="b6177-103">Úvod do třídy</span><span class="sxs-lookup"><span data-stu-id="b6177-103">Introduction to classes</span></span>

<span data-ttu-id="b6177-104">Tento úvodní očekává, že máte počítače, které můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="b6177-104">This quick start expects that you have a machine you can use for development.</span></span> <span data-ttu-id="b6177-105">Téma .NET [Začínáme za 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, počítače nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="b6177-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="b6177-106">Rychlý přehled o příkazy, které budete používat je ve [Úvod do místní rychlé zahájení](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="b6177-106">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="b6177-107">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="b6177-107">Create your application</span></span>

<span data-ttu-id="b6177-108">Pomocí okna terminálu, vytvořte adresář s názvem **třídy**.</span><span class="sxs-lookup"><span data-stu-id="b6177-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="b6177-109">Budete sestavit aplikaci existuje.</span><span class="sxs-lookup"><span data-stu-id="b6177-109">You'll build your application there.</span></span> <span data-ttu-id="b6177-110">Tento adresář a zadejte `dotnet new console` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="b6177-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="b6177-111">Tento příkaz vytvoří vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6177-111">This command creates your application.</span></span> <span data-ttu-id="b6177-112">Otevřete **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="b6177-112">Open **Program.cs**.</span></span> <span data-ttu-id="b6177-113">Ho by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="b6177-113">It should look like this:</span></span>

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

<span data-ttu-id="b6177-114">V této úvodní se chystáte vytvořit nové typy, které představují účet bank.</span><span class="sxs-lookup"><span data-stu-id="b6177-114">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="b6177-115">Vývojáři obvykle definujte každá třída v různých textového souboru.</span><span class="sxs-lookup"><span data-stu-id="b6177-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="b6177-116">Tím je snazší správa růstem program velikost.</span><span class="sxs-lookup"><span data-stu-id="b6177-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="b6177-117">Vytvořte nový soubor s názvem **BankAccount.cs** v **třídy** adresáře.</span><span class="sxs-lookup"><span data-stu-id="b6177-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="b6177-118">Tento soubor bude obsahovat deefinition z ***bankovní účet***.</span><span class="sxs-lookup"><span data-stu-id="b6177-118">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="b6177-119">Objekt Oriented programování organizuje kód tak, že vytvoříte typy ve formě ***třídy***.</span><span class="sxs-lookup"><span data-stu-id="b6177-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="b6177-120">Tyto třídy obsahovat kód, který představuje konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="b6177-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="b6177-121">`BankAccount` Třída reprezentuje účet bank.</span><span class="sxs-lookup"><span data-stu-id="b6177-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="b6177-122">Kód implementuje konkrétní operací prostřednictvím metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6177-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="b6177-123">V této úvodní bankovní účet podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="b6177-123">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="b6177-124">Má 10 číslice, která jednoznačně identifikuje účet bank.</span><span class="sxs-lookup"><span data-stu-id="b6177-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="b6177-125">Obsahuje řetězec, který ukládá název nebo názvy vlastníky.</span><span class="sxs-lookup"><span data-stu-id="b6177-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="b6177-126">Zůstatek je možné načíst.</span><span class="sxs-lookup"><span data-stu-id="b6177-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="b6177-127">Přijímá vkladů.</span><span class="sxs-lookup"><span data-stu-id="b6177-127">It accepts deposits.</span></span>
1. <span data-ttu-id="b6177-128">Přijímá stažení.</span><span class="sxs-lookup"><span data-stu-id="b6177-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="b6177-129">Počáteční zůstatek musí být kladná.</span><span class="sxs-lookup"><span data-stu-id="b6177-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="b6177-130">Stažení nesmí mít záporný zůstatek výsledek.</span><span class="sxs-lookup"><span data-stu-id="b6177-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="b6177-131">Zadejte typ účtu bank</span><span class="sxs-lookup"><span data-stu-id="b6177-131">Define the bank account type</span></span>

<span data-ttu-id="b6177-132">Můžete spustit tak, že vytvoříte základní informace o třídu, která definuje tento chování.</span><span class="sxs-lookup"><span data-stu-id="b6177-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="b6177-133">Ho bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="b6177-133">It would look like this:</span></span>

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

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

<span data-ttu-id="b6177-134">Před přechodem, Podívejme se na co jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="b6177-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="b6177-135">`namespace` Deklarace poskytuje způsob, jak logicky uspořádat vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="b6177-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="b6177-136">Tento rychlý start je poměrně malý, takže všechny kód budete chápat jeden obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b6177-136">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="b6177-137">`public class BankAccount`definuje třídu, nebo typu, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="b6177-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="b6177-138">Všechno uvnitř `{` a `}` třídy, které následuje deklarace definuje chování třídy.</span><span class="sxs-lookup"><span data-stu-id="b6177-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="b6177-139">Existují pět ***členy*** z `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="b6177-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="b6177-140">První tři ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="b6177-140">The first three are ***properties***.</span></span> <span data-ttu-id="b6177-141">Vlastnosti jsou datové prvky a může mít kód, který vynucuje ověřování nebo jinými pravidly.</span><span class="sxs-lookup"><span data-stu-id="b6177-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="b6177-142">Poslední dva jsou ***metody***.</span><span class="sxs-lookup"><span data-stu-id="b6177-142">The last two are ***methods***.</span></span> <span data-ttu-id="b6177-143">Metody jsou bloky kódu, že či jedné funkce.</span><span class="sxs-lookup"><span data-stu-id="b6177-143">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="b6177-144">Čtení názvy všech členů, měl by poskytnout dostatek informací pro vás nebo jiné vývojář zjistit, jaké jsou třídy.</span><span class="sxs-lookup"><span data-stu-id="b6177-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="b6177-145">Otevřete nový účet</span><span class="sxs-lookup"><span data-stu-id="b6177-145">Open a new account</span></span>

<span data-ttu-id="b6177-146">První funkce pro implementaci je otevřete účet bank.</span><span class="sxs-lookup"><span data-stu-id="b6177-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="b6177-147">Když zákazník otevře účet, musíte zadat v příslušné počáteční zůstatek a informace o vlastníkovi nebo vlastníky tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="b6177-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="b6177-148">Vytvoření nového objektu `BankAccount` typ znamená definovat ***konstruktor*** , přiřadí tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b6177-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="b6177-149">A ***konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="b6177-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="b6177-150">Slouží k chybě při inicializaci objekty daného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="b6177-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="b6177-151">Přidejte následující konstruktor `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="b6177-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="b6177-152">Konstruktory jsou volány při vytvoření objektu pomocí [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="b6177-152">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="b6177-153">Nahraďte řádku `Console.WriteLine("Hello World!");` v ***program.cs*** tento řádek (Nahraďte `<name>` nahraďte názvem):</span><span class="sxs-lookup"><span data-stu-id="b6177-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="b6177-154">Typ `dotnet run` chcete zobrazit, co se stane.</span><span class="sxs-lookup"><span data-stu-id="b6177-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="b6177-155">Všimli jste, že číslo účtu je prázdné?</span><span class="sxs-lookup"><span data-stu-id="b6177-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="b6177-156">Je třeba to opravíme.</span><span class="sxs-lookup"><span data-stu-id="b6177-156">It's time to fix that.</span></span> <span data-ttu-id="b6177-157">Číslo účtu měli přiřazen, když se objekt.</span><span class="sxs-lookup"><span data-stu-id="b6177-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="b6177-158">Ale by neměl být odpovědnost volajícího k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b6177-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="b6177-159">`BankAccount` Kód třídy měli vědět, jak přiřadit nový účet čísla.</span><span class="sxs-lookup"><span data-stu-id="b6177-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="b6177-160">Jednoduchý způsob, jak to udělat se dá začít s číslem 10 číslic.</span><span class="sxs-lookup"><span data-stu-id="b6177-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="b6177-161">Zvýší ho, když se vytvoří každý nový účet.</span><span class="sxs-lookup"><span data-stu-id="b6177-161">Increment it when each new account is created.</span></span> <span data-ttu-id="b6177-162">Nakonec uložte aktuální číslo účtu, když se objekt.</span><span class="sxs-lookup"><span data-stu-id="b6177-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="b6177-163">Přidejte následující deklarace členů k `BankAccount` třídy:</span><span class="sxs-lookup"><span data-stu-id="b6177-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="b6177-164">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="b6177-164">This is a data member.</span></span> <span data-ttu-id="b6177-165">Má `private`, což znamená, že můžete přistupovat pouze kód `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="b6177-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="b6177-166">Jedná se o způsob oddělení veřejné odpovědnosti (např. nutnosti číslo účtu) od implementace rozhraní privátní (čísla účtů generování.) Přidejte následující dva řádky konstruktoru přiřadit číslo účtu:</span><span class="sxs-lookup"><span data-stu-id="b6177-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="b6177-167">Typ `dotnet run` a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="b6177-167">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="b6177-168">Vytvoření vkladů a stažení z</span><span class="sxs-lookup"><span data-stu-id="b6177-168">Create deposits and withdrawals</span></span>

<span data-ttu-id="b6177-169">Třídě bankovní účet je potřeba přijmout vkladů a stažení z fungovala správně.</span><span class="sxs-lookup"><span data-stu-id="b6177-169">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="b6177-170">Umožňuje implementovat vkladů a stažení z vytvořením deník každé transakci pro účet.</span><span class="sxs-lookup"><span data-stu-id="b6177-170">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="b6177-171">Který má několik výhod oproti jednoduše aktualizace zůstatku na každou transakci.</span><span class="sxs-lookup"><span data-stu-id="b6177-171">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="b6177-172">Historie lze provádět audit všechny transakce a správu denní zůstatky.</span><span class="sxs-lookup"><span data-stu-id="b6177-172">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="b6177-173">Podle computing vyrovnávání z historie všech transakcí v případě potřeby, všechny chyby v rámci jedné transakce opravené správně projeví v rovnováhu mezi na další výpočet.</span><span class="sxs-lookup"><span data-stu-id="b6177-173">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="b6177-174">Začněme vytvořením nového typu představují transakce.</span><span class="sxs-lookup"><span data-stu-id="b6177-174">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="b6177-175">Toto je jednoduchý typ, který nemá žádné odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="b6177-175">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="b6177-176">Je několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="b6177-176">It needs a few properties.</span></span> <span data-ttu-id="b6177-177">Vytvořte nový soubor s názvem ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="b6177-177">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="b6177-178">Přidejte do ní následující kód:</span><span class="sxs-lookup"><span data-stu-id="b6177-178">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="b6177-179">Nyní Pojďme přidat <xref:System.Collections.Generic.List%601> z `Transaction` objekty ke `BankAccount` – třída.</span><span class="sxs-lookup"><span data-stu-id="b6177-179">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="b6177-180">Přidejte následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="b6177-180">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="b6177-181"><xref:System.Collections.Generic.List%601> Třídy, musíte k importu jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b6177-181">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="b6177-182">Přidejte následující na začátku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="b6177-182">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="b6177-183">Nyní změníme jak `Balance` se použije v hlášení.</span><span class="sxs-lookup"><span data-stu-id="b6177-183">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="b6177-184">Je možné najít jako součet hodnot všech transakcí.</span><span class="sxs-lookup"><span data-stu-id="b6177-184">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="b6177-185">Upravit deklaraci `Balance` v `BankAccount` třídy pro následující:</span><span class="sxs-lookup"><span data-stu-id="b6177-185">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="b6177-186">Tento příklad ukazuje důležitým aspektem ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="b6177-186">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="b6177-187">Jste nyní computing rovnováhu mezi, když jiné programátory požádá o hodnotě.</span><span class="sxs-lookup"><span data-stu-id="b6177-187">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="b6177-188">Vaše výpočetní vytvoří výčet všech transakcí a poskytuje součet jako aktuální zůstatek.</span><span class="sxs-lookup"><span data-stu-id="b6177-188">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="b6177-189">V dalším kroku implementovat `MakeDeposit` a `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="b6177-189">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="b6177-190">Tyto metody vynutí poslední dvě pravidla: že počáteční zůstatek, musí být kladné a že každé odstoupení nesmí vytvořit záporné rovnováhu.</span><span class="sxs-lookup"><span data-stu-id="b6177-190">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="b6177-191">To zavádí koncepci ***výjimky***.</span><span class="sxs-lookup"><span data-stu-id="b6177-191">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="b6177-192">Standardní způsob vyjadřuje, že nelze úspěšně dokončit metodu svou práci je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b6177-192">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="b6177-193">Typ výjimky a zprávy s ním spojená popisují chybu.</span><span class="sxs-lookup"><span data-stu-id="b6177-193">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="b6177-194">Zde `MakeDeposit` metoda vyvolá výjimku, pokud množství uložení je záporná.</span><span class="sxs-lookup"><span data-stu-id="b6177-194">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="b6177-195">`MakeWithdrawal` Metoda vyvolá výjimku, pokud částka stažení je záporná, nebo pokud použití stažení výsledkem záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="b6177-195">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="b6177-196">[ `throw` ](../language-reference/keywords/throw.md) Příkaz **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="b6177-196">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="b6177-197">Spouštění aktuální metody skončí a bude pokračovat, až odpovídající `catch` bloku se nachází.</span><span class="sxs-lookup"><span data-stu-id="b6177-197">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="b6177-198">Přidáte `catch` bloku k testování této kódu trochu později.</span><span class="sxs-lookup"><span data-stu-id="b6177-198">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="b6177-199">Konstruktor měli získat jeden změnit tak, aby ho přidá počáteční transakce, nikoli přímo aktualizace zůstatku.</span><span class="sxs-lookup"><span data-stu-id="b6177-199">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="b6177-200">Vzhledem k tomu, že jste již napsali `MakeDeposit` metody volat z vašeho konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b6177-200">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="b6177-201">Dokončení konstruktoru by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="b6177-201">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="b6177-202"><xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrátí aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="b6177-202"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="b6177-203">Otestování tohoto přidáním několik vkladů a ke stažení v vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="b6177-203">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="b6177-204">V dalším kroku testovací, že jsou zachytávání chybové stavy tak, že zkusíte vytvořte účet s záporné vyrovnávání:</span><span class="sxs-lookup"><span data-stu-id="b6177-204">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="b6177-205">Můžete použít [ `try` a `catch` příkazy](../language-reference/keywords/try-catch.md) označit blok kódu, který může vyvolat výjimky a k zachycení tyto chyby, které byste očekávali.</span><span class="sxs-lookup"><span data-stu-id="b6177-205">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="b6177-206">Stejný postup můžete použít k testování kódu, který vyvolá záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="b6177-206">You can use the same technique to test the code that throws for a negative balance:</span></span>

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="b6177-207">Uložte soubor a typ `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="b6177-207">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="b6177-208">Challenge - protokolovat všechny transakce</span><span class="sxs-lookup"><span data-stu-id="b6177-208">Challenge - log all transactions</span></span>

<span data-ttu-id="b6177-209">Chcete-li dokončit tento rychlý start, můžete napsat `GetAccountHistory` metodu, která vytvoří `string` pro historii transakce.</span><span class="sxs-lookup"><span data-stu-id="b6177-209">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="b6177-210">Přidejte tuto metodu za účelem `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="b6177-210">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="b6177-211">Se používá <xref:System.Text.StringBuilder> třídy se naformátovat řetězec, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="b6177-211">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="b6177-212">Seznámili jste se řetězec formátování kódu dříve v těchto rychlé zahájení.</span><span class="sxs-lookup"><span data-stu-id="b6177-212">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="b6177-213">Je jeden znak nového `\t`.</span><span class="sxs-lookup"><span data-stu-id="b6177-213">One new character is `\t`.</span></span> <span data-ttu-id="b6177-214">Která vloží na kartě k formátování výstupu.</span><span class="sxs-lookup"><span data-stu-id="b6177-214">That inserts a tab to format the output.</span></span>

<span data-ttu-id="b6177-215">Přidejte tento řádek k testování v **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="b6177-215">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="b6177-216">Typ `dotnet run` a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="b6177-216">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6177-217">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b6177-217">Next Steps</span></span>

<span data-ttu-id="b6177-218">Pokud jste získali zablokuje, zobrazí se zdroji pro tento rychlý start [v našem úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="b6177-218">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="b6177-219">Blahopřejeme, jste dokončili všechny naše rychlý start.</span><span class="sxs-lookup"><span data-stu-id="b6177-219">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="b6177-220">Pokud jste přes další, zkuste naši [kurzy](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="b6177-220">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
