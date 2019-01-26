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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="40106-103">Prozkoumejte objektově orientované programování pomocí třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="40106-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="40106-104">V tomto kurzu očekává, že máte počítač, který používáte pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="40106-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="40106-105">Téma .NET [zahájení práce během 10 minut](https://www.microsoft.com/net/core) obsahuje pokyny pro nastavení místního vývojového prostředí v Mac, PC nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="40106-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="40106-106">Je rychlý přehled toho, příkazy, které použijete v [seznámit se s nástroje pro vývoj](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="40106-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="40106-107">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="40106-107">Create your application</span></span>

<span data-ttu-id="40106-108">Pomocí okna terminálu vytvořte adresář s názvem **třídy**.</span><span class="sxs-lookup"><span data-stu-id="40106-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="40106-109">Vytvoříte aplikaci existuje.</span><span class="sxs-lookup"><span data-stu-id="40106-109">You'll build your application there.</span></span> <span data-ttu-id="40106-110">Tento adresář a zadejte `dotnet new console` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="40106-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="40106-111">Tento příkaz vytvoří vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="40106-111">This command creates your application.</span></span> <span data-ttu-id="40106-112">Otevřít **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="40106-112">Open **Program.cs**.</span></span> <span data-ttu-id="40106-113">Mělo by to vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="40106-113">It should look like this:</span></span>

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

<span data-ttu-id="40106-114">V tomto kurzu budete vytvářet nové typy, které představují bankovním účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="40106-115">Vývojáři obvykle definovat každá třída v různých textového souboru.</span><span class="sxs-lookup"><span data-stu-id="40106-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="40106-116">Který usnadňuje spravovat stejným způsobem jako program roste velikost.</span><span class="sxs-lookup"><span data-stu-id="40106-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="40106-117">Vytvořte nový soubor s názvem **BankAccount.cs** v **třídy** adresáře.</span><span class="sxs-lookup"><span data-stu-id="40106-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="40106-118">Tento soubor bude obsahovat definici ***bankovním účtu***.</span><span class="sxs-lookup"><span data-stu-id="40106-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="40106-119">Objekt Oriented programování slouží k uspořádání kódu tak, že vytvoříte typů ve formě ***třídy***.</span><span class="sxs-lookup"><span data-stu-id="40106-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="40106-120">Tyto třídy obsahovat kód, který představuje konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="40106-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="40106-121">`BankAccount` Třída reprezentuje bankovním účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="40106-122">Kód implementuje konkrétní operace, ať už metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="40106-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="40106-123">V tomto kurzu bankovním účtu podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="40106-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="40106-124">Obsahuje číslo 10 číslic, které jednoznačně identifikuje bankovním účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="40106-125">Obsahuje řetězec, který ukládá název nebo názvy vlastníků.</span><span class="sxs-lookup"><span data-stu-id="40106-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="40106-126">Je možné načíst zůstatek na účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="40106-127">Přijímá vkladů.</span><span class="sxs-lookup"><span data-stu-id="40106-127">It accepts deposits.</span></span>
1. <span data-ttu-id="40106-128">Přijímá stažení.</span><span class="sxs-lookup"><span data-stu-id="40106-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="40106-129">Počáteční zůstatek musí být kladná.</span><span class="sxs-lookup"><span data-stu-id="40106-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="40106-130">Výsledkem stažení nesmí být záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="40106-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="40106-131">Definování typu bankovním účtu</span><span class="sxs-lookup"><span data-stu-id="40106-131">Define the bank account type</span></span>

<span data-ttu-id="40106-132">Můžete spustit tak, že vytvoříte základní třídu, která definuje chování.</span><span class="sxs-lookup"><span data-stu-id="40106-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="40106-133">To bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="40106-133">It would look like this:</span></span>

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

<span data-ttu-id="40106-134">Před přechodem na, Pojďme se podívat, co jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="40106-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="40106-135">`namespace` Deklarace poskytuje způsob, jak logické uspořádání vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="40106-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="40106-136">Tento kurz je poměrně malý, takže umístění vyberu veškerý kód v jednom oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="40106-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="40106-137">`public class BankAccount` Definuje třídy nebo typu, kterou vytváříte.</span><span class="sxs-lookup"><span data-stu-id="40106-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="40106-138">Všechno, co je uvnitř `{` a `}` , který sleduje třídy prohlášení definuje chování třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="40106-139">Existuje pět ***členy*** z `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="40106-140">První tři ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="40106-140">The first three are ***properties***.</span></span> <span data-ttu-id="40106-141">Vlastnosti jsou prvky dat a může mít kód, který vynucuje ověření nebo jiná pravidla.</span><span class="sxs-lookup"><span data-stu-id="40106-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="40106-142">Poslední dvě ***metody***.</span><span class="sxs-lookup"><span data-stu-id="40106-142">The last two are ***methods***.</span></span> <span data-ttu-id="40106-143">Metody jsou bloky kódu, které provádějí jednu funkci.</span><span class="sxs-lookup"><span data-stu-id="40106-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="40106-144">Názvy jednotlivých členů pro čtení by měly poskytnout dostatek informací pro vás nebo jiný vývojář zjistit, co dělá třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="40106-145">Otevřete nový účet</span><span class="sxs-lookup"><span data-stu-id="40106-145">Open a new account</span></span>

<span data-ttu-id="40106-146">První funkce k implementaci je otevřete bankovním účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="40106-147">Po otevření účtu zákazníka, musíte zadat počáteční zůstatek a informace o vlastník nebo vlastníci tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="40106-148">Vytvoření nového objektu `BankAccount` typ znamená definovat ***konstruktor*** , která přiřadí tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="40106-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="40106-149">A ***konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="40106-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="40106-150">Používá se třeba inicializovat objekty typu třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="40106-151">Přidejte následující konstruktor k `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="40106-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="40106-152">Konstruktory jsou volány při vytváření objektu pomocí [ `new` ](../../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="40106-152">Constructors are called when you create an object using [`new`](../../language-reference/keywords/new.md).</span></span> <span data-ttu-id="40106-153">Nahraďte řádek `Console.WriteLine("Hello World!");` v ***program.cs*** tento řádek (nahradit `<name>` s vaším jménem):</span><span class="sxs-lookup"><span data-stu-id="40106-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="40106-154">Typ `dotnet run` chcete zobrazit, co se stane.</span><span class="sxs-lookup"><span data-stu-id="40106-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="40106-155">Všimli jste si, že číslo účtu je prázdný?</span><span class="sxs-lookup"><span data-stu-id="40106-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="40106-156">Čas potřebný k opravě, který je.</span><span class="sxs-lookup"><span data-stu-id="40106-156">It's time to fix that.</span></span> <span data-ttu-id="40106-157">Číslo účtu měla být přiřazena při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="40106-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="40106-158">Ale neměl by být odpovědností volajícího k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="40106-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="40106-159">`BankAccount` Kód třídy by měl vědět, jak přiřadit novou čísla účtů.</span><span class="sxs-lookup"><span data-stu-id="40106-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="40106-160">Jednoduchý způsob, jak to provést, je začít s 10 číslic.</span><span class="sxs-lookup"><span data-stu-id="40106-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="40106-161">Zvýšte ji, když se vytvoří každý nový účet.</span><span class="sxs-lookup"><span data-stu-id="40106-161">Increment it when each new account is created.</span></span> <span data-ttu-id="40106-162">Nakonec ukládání číslo aktuálního účtu, když je vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="40106-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="40106-163">Přidejte následující deklaraci člena `BankAccount` třídy:</span><span class="sxs-lookup"><span data-stu-id="40106-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="40106-164">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="40106-164">This is a data member.</span></span> <span data-ttu-id="40106-165">Má `private`, což znamená, že je přístupný pouze kódu uvnitř `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="40106-166">Jedná se o způsob oddělení veřejného odpovědnosti (jako číslo účtu) z privátní implementace (jak čísla účtů jsou generovány.) Je také `static`, což znamená, že je sdílené všemi `BankAccount` objekty.</span><span class="sxs-lookup"><span data-stu-id="40106-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="40106-167">Hodnota nestatické proměnné je jedinečné pro každé instance `BankAccount` objektu.</span><span class="sxs-lookup"><span data-stu-id="40106-167">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="40106-168">Přidejte následující dva řádky konstruktoru přiřadit číslo účtu:</span><span class="sxs-lookup"><span data-stu-id="40106-168">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="40106-169">Typ `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="40106-169">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="40106-170">Vytvoření vkladů a stažení</span><span class="sxs-lookup"><span data-stu-id="40106-170">Create deposits and withdrawals</span></span>

<span data-ttu-id="40106-171">Vaše třída bankovním účtu je potřeba přijmout vkladů a stažení fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="40106-171">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="40106-172">Můžeme implementovat vkladů a stažení vytvořením deníku o každé transakci pro účet.</span><span class="sxs-lookup"><span data-stu-id="40106-172">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="40106-173">Který má několik výhod oproti aktualizací zůstatku na každou transakci.</span><span class="sxs-lookup"><span data-stu-id="40106-173">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="40106-174">Historie je možné provádět audit všechny transakce a správu denní zůstatků.</span><span class="sxs-lookup"><span data-stu-id="40106-174">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="40106-175">Výpočtem zůstatek z historie všechny transakce v případě potřeby všechny chyby v rámci jedné transakce, které jsou opraveny správně projeví v zůstatek na další výpočtu.</span><span class="sxs-lookup"><span data-stu-id="40106-175">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="40106-176">Začněme tím, že vytvoříte nový typ pro reprezentaci transakce.</span><span class="sxs-lookup"><span data-stu-id="40106-176">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="40106-177">Toto je jednoduchý typ, který nemá žádné odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="40106-177">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="40106-178">Rozpojuje několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="40106-178">It needs a few properties.</span></span> <span data-ttu-id="40106-179">Vytvořte nový soubor s názvem ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="40106-179">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="40106-180">Přidejte do ní následující kód:</span><span class="sxs-lookup"><span data-stu-id="40106-180">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="40106-181">Teď přidáme <xref:System.Collections.Generic.List%601> z `Transaction` objektů `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="40106-181">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="40106-182">Přidejte následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="40106-182">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="40106-183"><xref:System.Collections.Generic.List%601> Třídy, musíte k importu jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="40106-183">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="40106-184">Přidejte následující na začátku **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="40106-184">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="40106-185">Teď Změníme způsob, jakým `Balance` se použije v hlášení.</span><span class="sxs-lookup"><span data-stu-id="40106-185">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="40106-186">Je možné najít sečtením hodnoty všechny transakce.</span><span class="sxs-lookup"><span data-stu-id="40106-186">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="40106-187">Upravte deklaraci `Balance` v `BankAccount` třídy takto:</span><span class="sxs-lookup"><span data-stu-id="40106-187">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="40106-188">Tento příklad ukazuje důležitou součástí ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="40106-188">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="40106-189">Zůstatek na účtu už výpočtu nyní při jiné programátor vyzve k zadání hodnoty.</span><span class="sxs-lookup"><span data-stu-id="40106-189">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="40106-190">Vaše výpočetní výkon vytvoří výčet všech transakcí a poskytuje součet jako aktuální zůstatek.</span><span class="sxs-lookup"><span data-stu-id="40106-190">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="40106-191">V dalším kroku implementovat `MakeDeposit` a `MakeWithdrawal` metody.</span><span class="sxs-lookup"><span data-stu-id="40106-191">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="40106-192">Tyto metody se vynutit konečný dvě pravidla:, počáteční zůstatek, musí být kladné a, všechny stažení nesmí vytvořit záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="40106-192">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="40106-193">Zavádí koncepci ***výjimky***.</span><span class="sxs-lookup"><span data-stu-id="40106-193">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="40106-194">Standardní způsob označující, zda metoda nelze dokončí svou práci úspěšně je vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="40106-194">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="40106-195">Typ výjimky a zprávu s ním spojená popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="40106-195">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="40106-196">Tady `MakeDeposit` metoda vyvolá výjimku, pokud je množství uložení záporná.</span><span class="sxs-lookup"><span data-stu-id="40106-196">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="40106-197">`MakeWithdrawal` Metoda vyvolá výjimku, pokud je záporná hodnota stažení nebo pokud použití stažení má za následek negativní zůstatek:</span><span class="sxs-lookup"><span data-stu-id="40106-197">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="40106-198">[ `throw` ](../../language-reference/keywords/throw.md) Příkaz **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="40106-198">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="40106-199">Provádění aktuálního bloku skončí a řízení přenosů na první odpovídající `catch` nalezen blok v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="40106-199">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="40106-200">Přidáte `catch` bloku k otestování tento kód o něco později.</span><span class="sxs-lookup"><span data-stu-id="40106-200">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="40106-201">Konstruktor by měl získat jednu změnu, tak, aby přidá počáteční transakce, nikoli přímo aktualizace zůstatek na účtu.</span><span class="sxs-lookup"><span data-stu-id="40106-201">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="40106-202">Vzhledem k tomu, že už jste napsali `MakeDeposit` metody volat z vašeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="40106-202">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="40106-203">Dokončení konstruktor by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="40106-203">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="40106-204"><xref:System.DateTime.Now?displayProperty=nameWithType> je vlastnost, která vrátí aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="40106-204"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="40106-205">Otestovat tak, že přidáte několik vkladů a ke stažení v vaše `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="40106-205">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="40106-206">V dalším kroku otestujte, že jsou zachycení chybové podmínky pokusu o vytvoření účtu pomocí záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="40106-206">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="40106-207">Můžete použít [ `try` a `catch` příkazy](../../language-reference/keywords/try-catch.md) jak označit bloku kódu, který může vyvolat výjimky a k zachytávání těchto chyb, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="40106-207">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="40106-208">Stejný postup můžete použít k testování kódu, který vrací chybovou výjimku záporný zůstatek:</span><span class="sxs-lookup"><span data-stu-id="40106-208">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="40106-209">Uložení souboru a typu `dotnet run` vyzkoušejte si to.</span><span class="sxs-lookup"><span data-stu-id="40106-209">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="40106-210">Výzva – protokolovat všechny transakce</span><span class="sxs-lookup"><span data-stu-id="40106-210">Challenge - log all transactions</span></span>

<span data-ttu-id="40106-211">K dokončení tohoto kurzu, můžete psát `GetAccountHistory` metodu, která vytvoří `string` pro historie transakcí.</span><span class="sxs-lookup"><span data-stu-id="40106-211">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="40106-212">Přidejte tuto metodu za účelem `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="40106-212">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="40106-213">Tady se používá <xref:System.Text.StringBuilder> třídy formátovací řetězec, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="40106-213">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="40106-214">Už víte, řetězce formátování kódu výše v těchto kurzech.</span><span class="sxs-lookup"><span data-stu-id="40106-214">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="40106-215">Jeden znak nové `\t`.</span><span class="sxs-lookup"><span data-stu-id="40106-215">One new character is `\t`.</span></span> <span data-ttu-id="40106-216">Která vloží kartu můžete formátovat výstup.</span><span class="sxs-lookup"><span data-stu-id="40106-216">That inserts a tab to format the output.</span></span>

<span data-ttu-id="40106-217">Přidejte následující řádek a otestovat ho v **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="40106-217">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="40106-218">Typ `dotnet run` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="40106-218">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="40106-219">Další kroky</span><span class="sxs-lookup"><span data-stu-id="40106-219">Next Steps</span></span>

<span data-ttu-id="40106-220">Pokud máte zablokuje, zobrazí se zdroj pro účely tohoto kurzu [v naše úložiště GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="40106-220">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="40106-221">Blahopřejeme, jste dokončili všechny naše Úvod do C# kurzy.</span><span class="sxs-lookup"><span data-stu-id="40106-221">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="40106-222">Pokud chcete získat další informace, zkuste některých našich [kurzy](../index.md)</span><span class="sxs-lookup"><span data-stu-id="40106-222">If you're eager to learn more, try more of our [tutorials](../index.md)</span></span>
