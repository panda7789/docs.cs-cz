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
ms.openlocfilehash: ad6e83d427b55482f9615e0083682bdca6c56704
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-classes"></a><span data-ttu-id="fd032-103">Úvod do třídy</span><span class="sxs-lookup"><span data-stu-id="fd032-103">Introduction to classes</span></span>

<span data-ttu-id="fd032-104">Tato lekce předpokládá, že jste nainstalovali [.NET Core SDK](http://dot.net/core)a editoru podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="fd032-104">This lesson assumes that you've installed [.NET Core SDK](http://dot.net/core), and an editor of your choice.</span></span> <span data-ttu-id="fd032-105">Pokud nemáte, zkuste [Visual Studio Code](https://code.visualstudio.com/), nebo [Visual Studio](https://www.visualstudio.com/) na Mac nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="fd032-105">If you don't have one, try [Visual Studio Code](https://code.visualstudio.com/), or [Visual Studio](https://www.visualstudio.com/) on Mac or Windows.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="fd032-106">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="fd032-106">Create your application</span></span>

<span data-ttu-id="fd032-107">Pomocí okna terminálu, vytvořte adresář s názvem **třídy**.</span><span class="sxs-lookup"><span data-stu-id="fd032-107">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="fd032-108">Budete sestavit aplikaci existuje.</span><span class="sxs-lookup"><span data-stu-id="fd032-108">You'll build your application there.</span></span> <span data-ttu-id="fd032-109">Tento adresář a zadejte `dotnet new console` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="fd032-109">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="fd032-110">Tento příkaz vytvoří vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd032-110">This command creates your application.</span></span> <span data-ttu-id="fd032-111">Otevřete **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="fd032-111">Open **Program.cs**.</span></span> <span data-ttu-id="fd032-112">Ho by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fd032-112">It should look like this:</span></span>

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

<span data-ttu-id="fd032-113">V této úvodní se chystáte vytvořit nové typy, které představují účet bank.</span><span class="sxs-lookup"><span data-stu-id="fd032-113">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="fd032-114">Vývojáři obvykle definujte každá třída v různých textového souboru.</span><span class="sxs-lookup"><span data-stu-id="fd032-114">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="fd032-115">Tím je snazší správa růstem program velikost.</span><span class="sxs-lookup"><span data-stu-id="fd032-115">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="fd032-116">Vytvořte nový soubor s názvem **BankAccount.cs** v **třídy** adresáře.</span><span class="sxs-lookup"><span data-stu-id="fd032-116">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="fd032-117">Tento soubor bude obsahovat deefinition z ***bankovní účet***.</span><span class="sxs-lookup"><span data-stu-id="fd032-117">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="fd032-118">Objekt Oriented programování organizuje kód tak, že vytvoříte typy ve formě ***třídy***.</span><span class="sxs-lookup"><span data-stu-id="fd032-118">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="fd032-119">Tyto třídy obsahovat kód, který představuje konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="fd032-119">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="fd032-120">`BankAccount` Třída reprezentuje účet bank.</span><span class="sxs-lookup"><span data-stu-id="fd032-120">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="fd032-121">Kód implementuje konkrétní operací prostřednictvím metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fd032-121">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="fd032-122">V této úvodní bankovní účet podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="fd032-122">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="fd032-123">Má 10 číslice, která jednoznačně identifikuje účet bank.</span><span class="sxs-lookup"><span data-stu-id="fd032-123">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="fd032-124">Obsahuje řetězec, který ukládá název nebo názvy vlastníky.</span><span class="sxs-lookup"><span data-stu-id="fd032-124">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="fd032-125">Zůstatek je možné načíst.</span><span class="sxs-lookup"><span data-stu-id="fd032-125">The balance can be retrieved.</span></span>
1. <span data-ttu-id="fd032-126">Přijímá vkladů.</span><span class="sxs-lookup"><span data-stu-id="fd032-126">It accepts deposits.</span></span>
1. <span data-ttu-id="fd032-127">Přijímá stažení.</span><span class="sxs-lookup"><span data-stu-id="fd032-127">It accepts withdrawals.</span></span>
1. <span data-ttu-id="fd032-128">Počáteční zůstatek musí být kladná.</span><span class="sxs-lookup"><span data-stu-id="fd032-128">The initial balance must be positive.</span></span>
1. <span data-ttu-id="fd032-129">Stažení nesmí mít záporný zůstatek výsledek.</span><span class="sxs-lookup"><span data-stu-id="fd032-129">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="fd032-130">Zadejte typ účtu bank</span><span class="sxs-lookup"><span data-stu-id="fd032-130">Define the bank account type</span></span>

<span data-ttu-id="fd032-131">Můžete spustit tak, že vytvoříte základní informace o třídu, která definuje tento chování.</span><span class="sxs-lookup"><span data-stu-id="fd032-131">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="fd032-132">Ho bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fd032-132">It would look like this:</span></span>

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

<span data-ttu-id="fd032-133">Před přechodem, Podívejme se na co jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="fd032-133">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="fd032-134">`namespace` Deklarace poskytuje způsob, jak logicky uspořádat vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="fd032-134">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="fd032-135">Tento rychlý start je poměrně malý, takže všechny kód budete chápat jeden obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fd032-135">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="fd032-136">`public class BankAccount`definuje třídu, nebo typu, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="fd032-136">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="fd032-137">Všechno uvnitř `{` a `}` třídy, které následuje deklarace definuje chování třídy.</span><span class="sxs-lookup"><span data-stu-id="fd032-137">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="fd032-138">Existují pět ***členy*** z `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="fd032-138">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="fd032-139">První tři ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="fd032-139">The first three are ***properties***.</span></span> <span data-ttu-id="fd032-140">Vlastnosti jsou datové prvky a může mít kód, který vynucuje ověřování nebo jinými pravidly.</span><span class="sxs-lookup"><span data-stu-id="fd032-140">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="fd032-141">Poslední dva jsou ***metody***.</span><span class="sxs-lookup"><span data-stu-id="fd032-141">The last two are ***methods***.</span></span> <span data-ttu-id="fd032-142">Metody jsou bloky kódu, že či jedné funkce.</span><span class="sxs-lookup"><span data-stu-id="fd032-142">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="fd032-143">Čtení názvy všech členů, měl by poskytnout dostatek informací pro vás nebo jiné vývojář zjistit, jaké jsou třídy.</span><span class="sxs-lookup"><span data-stu-id="fd032-143">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="fd032-144">Otevřete nový účet</span><span class="sxs-lookup"><span data-stu-id="fd032-144">Open a new account</span></span>

<span data-ttu-id="fd032-145">První funkce pro implementaci je otevřete účet bank.</span><span class="sxs-lookup"><span data-stu-id="fd032-145">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="fd032-146">Když zákazník otevře účet, musíte zadat v příslušné počáteční zůstatek a informace o vlastníkovi nebo vlastníky tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="fd032-146">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="fd032-147">Vytvoření nového objektu `BankAccount` typ znamená definovat ***konstruktor*** , přiřadí tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fd032-147">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="fd032-148">A ***konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="fd032-148">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="fd032-149">Slouží k chybě při inicializaci objekty daného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="fd032-149">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="fd032-150">Přidejte následující konstruktor `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="fd032-150">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="fd032-151">Konstruktory jsou volány při vytvoření objektu pomocí [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="fd032-151">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="fd032-152">Nahraďte řádku `Console.WriteLine("Hello World!");` v ***program.cs*** tento řádek (Nahraďte `<name>` nahraďte názvem):</span><span class="sxs-lookup"><span data-stu-id="fd032-152">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="fd032-153">Typ `dotnet run` chcete zobrazit, co se stane.</span><span class="sxs-lookup"><span data-stu-id="fd032-153">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="fd032-154">Všimli jste, že číslo účtu je prázdné?</span><span class="sxs-lookup"><span data-stu-id="fd032-154">Did you notice that the account number is blank?</span></span> <span data-ttu-id="fd032-155">Je třeba to opravíme.</span><span class="sxs-lookup"><span data-stu-id="fd032-155">It's time to fix that.</span></span> <span data-ttu-id="fd032-156">Číslo účtu měli přiřazen, když se objekt.</span><span class="sxs-lookup"><span data-stu-id="fd032-156">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="fd032-157">Ale by neměl být odpovědnost volajícího k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="fd032-157">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="fd032-158">`BankAccount` Kód třídy měli vědět, jak přiřadit nový účet čísla.</span><span class="sxs-lookup"><span data-stu-id="fd032-158">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="fd032-159">Jednoduchý způsob, jak to udělat se dá začít s číslem 10 číslic.</span><span class="sxs-lookup"><span data-stu-id="fd032-159">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="fd032-160">Zvýší ho, když se vytvoří každý nový účet.</span><span class="sxs-lookup"><span data-stu-id="fd032-160">Increment it when each new account is created.</span></span> <span data-ttu-id="fd032-161">Nakonec uložte aktuální číslo účtu, když se objekt.</span><span class="sxs-lookup"><span data-stu-id="fd032-161">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="fd032-162">Přidejte následující deklarace členů k `BankAccount` třídy:</span><span class="sxs-lookup"><span data-stu-id="fd032-162">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="fd032-163">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="fd032-163">This is a data member.</span></span> <span data-ttu-id="fd032-164">Má `private`, což znamená, že můžete přistupovat pouze kód `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="fd032-164">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="fd032-165">Jedná se o způsob oddělení veřejné odpovědnosti (např. nutnosti číslo účtu) od implementace rozhraní privátní (čísla účtů generování.) Přidejte následující dva řádky konstruktoru přiřadit číslo účtu:</span><span class="sxs-lookup"><span data-stu-id="fd032-165">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="fd032-166">Typ `dotnet run` a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="fd032-166">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="fd032-167">Vytvoření vkladů a stažení z</span><span class="sxs-lookup"><span data-stu-id="fd032-167">Create deposits and withdrawals</span></span>

<span data-ttu-id="fd032-168">Třídě bankovní účet je potřeba přijmout vkladů a stažení z fungovala správně.</span><span class="sxs-lookup"><span data-stu-id="fd032-168">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="fd032-169">Umožňuje implementovat vkladů a stažení z vytvořením deník každé transakci pro účet.</span><span class="sxs-lookup"><span data-stu-id="fd032-169">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="fd032-170">Který má několik výhod oproti jednoduše aktualizace zůstatku na každou transakci.</span><span class="sxs-lookup"><span data-stu-id="fd032-170">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="fd032-171">Historie lze provádět audit všechny transakce a správu denní zůstatky.</span><span class="sxs-lookup"><span data-stu-id="fd032-171">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="fd032-172">Podle computing vyrovnávání z historie všech transakcí v případě potřeby, všechny chyby v rámci jedné transakce opravené správně projeví v rovnováhu mezi na další výpočet.</span><span class="sxs-lookup"><span data-stu-id="fd032-172">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="fd032-173">Začněme vytvořením nového typu představují transakce.</span><span class="sxs-lookup"><span data-stu-id="fd032-173">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="fd032-174">Toto je jednoduchý typ, který nemá žádné odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="fd032-174">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="fd032-175">Je několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="fd032-175">It needs a few properties.</span></span> <span data-ttu-id="fd032-176">Vytvořte nový soubor s názvem ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="fd032-176">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="fd032-177">Přidejte do ní následující kód:</span><span class="sxs-lookup"><span data-stu-id="fd032-177">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="fd032-178">Nyní Pojďme přidat <xref:System.Collections.Generic.List%601> z `Transaction` objekty ke `BankAccount` – třída.</span><span class="sxs-lookup"><span data-stu-id="fd032-178">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="fd032-179">Přidejte následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="fd032-179">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="fd032-180"><xref:System.Collections.Generic.List%601> Třídy, musíte k importu jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fd032-180">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="fd032-181">Přidejte následující na začátku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="fd032-181">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="fd032-182">Nyní změníme jak `Balance` se použije v hlášení.</span><span class="sxs-lookup"><span data-stu-id="fd032-182">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="fd032-183">Je možné najít jako součet hodnot všech transakcí.</span><span class="sxs-lookup"><span data-stu-id="fd032-183">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="fd032-184">Upravit deklaraci `Balance` v `BankAccount` třídy pro následující:</span><span class="sxs-lookup"><span data-stu-id="fd032-184">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="fd032-185">Tento příklad ukazuje důležitým aspektem ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="fd032-185">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="fd032-186">Jste nyní computing rovnováhu mezi, když jiné programátory požádá o hodnotě.</span><span class="sxs-lookup"><span data-stu-id="fd032-186">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="fd032-187">Vaše výpočetní vytvoří výčet všech transakcí a poskytuje součet jako aktuální zůstatek.</span><span class="sxs-lookup"><span data-stu-id="fd032-187">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="fd032-188">V dalším kroku implementovat `MakeDeposit` a `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="fd032-188">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="fd032-189">Tyto metody vynutí poslední dvě pravidla: že počáteční zůstatek, musí být kladné a že každé odstoupení nesmí vytvořit záporné rovnováhu.</span><span class="sxs-lookup"><span data-stu-id="fd032-189">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="fd032-190">To zavádí koncepci ***výjimky***.</span><span class="sxs-lookup"><span data-stu-id="fd032-190">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="fd032-191">Standardní způsob vyjadřuje, že nelze úspěšně dokončit metodu svou práci je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fd032-191">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="fd032-192">Typ výjimky a zprávy s ním spojená popisují chybu.</span><span class="sxs-lookup"><span data-stu-id="fd032-192">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="fd032-193">Zde `MakeDeposit` metoda vyvolá výjimku, pokud množství uložení je záporná.</span><span class="sxs-lookup"><span data-stu-id="fd032-193">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="fd032-194">`MakeWithdrawal` Metoda vyvolá výjimku, pokud částka stažení je záporná, nebo pokud použití stažení výsledkem záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="fd032-194">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="fd032-195">[ `throw` ](../language-reference/keywords/throw.md) Příkaz **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="fd032-195">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="fd032-196">Spouštění aktuální metody skončí a bude pokračovat, až odpovídající `catch` bloku se nachází.</span><span class="sxs-lookup"><span data-stu-id="fd032-196">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="fd032-197">Přidáte `catch` bloku k testování této kódu trochu později.</span><span class="sxs-lookup"><span data-stu-id="fd032-197">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="fd032-198">Konstruktor měli získat jeden změnit tak, aby ho přidá počáteční transakce, nikoli přímo aktualizace zůstatku.</span><span class="sxs-lookup"><span data-stu-id="fd032-198">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="fd032-199">Vzhledem k tomu, že jste již napsali `MakeDeposit` metody volat z vašeho konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fd032-199">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="fd032-200">Dokončení konstruktoru by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="fd032-200">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="fd032-201"><xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrátí aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="fd032-201"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="fd032-202">Otestování tohoto přidáním několik vkladů a ke stažení v vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="fd032-202">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="fd032-203">V dalším kroku testovací, že jsou zachytávání chybové stavy tak, že zkusíte vytvořte účet s záporné vyrovnávání:</span><span class="sxs-lookup"><span data-stu-id="fd032-203">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="fd032-204">Můžete použít [ `try` a `catch` příkazy](../language-reference/keywords/try-catch.md) označit blok kódu, který může vyvolat výjimky a k zachycení tyto chyby, které byste očekávali.</span><span class="sxs-lookup"><span data-stu-id="fd032-204">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="fd032-205">Stejný postup můžete použít k testování kódu, který vyvolá záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="fd032-205">You can use the same technique to test the code that throws for a negative balance:</span></span>

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

<span data-ttu-id="fd032-206">Uložte soubor a typ `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="fd032-206">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="fd032-207">Challenge - protokolovat všechny transakce</span><span class="sxs-lookup"><span data-stu-id="fd032-207">Challenge - log all transactions</span></span>

<span data-ttu-id="fd032-208">Chcete-li dokončit tento rychlý start, můžete napsat `GetAccountHistory` metodu, která vytvoří `string` pro historii transakce.</span><span class="sxs-lookup"><span data-stu-id="fd032-208">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="fd032-209">Přidejte tuto metodu za účelem `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="fd032-209">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="fd032-210">Se používá <xref:System.Text.StringBuilder> třídy se naformátovat řetězec, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="fd032-210">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="fd032-211">Seznámili jste se řetězec formátování kódu dříve v těchto rychlé zahájení.</span><span class="sxs-lookup"><span data-stu-id="fd032-211">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="fd032-212">Je jeden znak nového `\t`.</span><span class="sxs-lookup"><span data-stu-id="fd032-212">One new character is `\t`.</span></span> <span data-ttu-id="fd032-213">Která vloží na kartě k formátování výstupu.</span><span class="sxs-lookup"><span data-stu-id="fd032-213">That inserts a tab to format the output.</span></span>

<span data-ttu-id="fd032-214">Přidejte tento řádek k testování v **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="fd032-214">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="fd032-215">Typ `dotnet run` a zobrazte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="fd032-215">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fd032-216">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fd032-216">Next Steps</span></span>

<span data-ttu-id="fd032-217">Pokud jste získali zablokuje, zobrazí se zdroji pro tento rychlý start [v našem úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="fd032-217">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="fd032-218">Blahopřejeme, jste dokončili všechny naše rychlý start.</span><span class="sxs-lookup"><span data-stu-id="fd032-218">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="fd032-219">Pokud jste přes další, zkuste naši [kurzy](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="fd032-219">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
