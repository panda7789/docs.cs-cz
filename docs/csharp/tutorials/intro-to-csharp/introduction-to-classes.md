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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="e8893-103">Prozkoumat objektově orientované programování pomocí tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="e8893-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="e8893-104">V tomto kurzu se očekává, že máte počítač, který můžete použít pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="e8893-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="e8893-105">Kurz rozhraní .NET [Hello World v 10 minutách](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) obsahuje pokyny pro nastavení místního vývojového prostředí v systému Windows, Linux nebo MacOS.</span><span class="sxs-lookup"><span data-stu-id="e8893-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e8893-106">Rychlý přehled příkazů, které budete používat, najdete v článku [seznámit se s vývojovými nástroji](local-environment.md) s odkazy na další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="e8893-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="e8893-107">Vytvořte si svoji aplikaci</span><span class="sxs-lookup"><span data-stu-id="e8893-107">Create your application</span></span>

<span data-ttu-id="e8893-108">Pomocí okna terminálu vytvořte adresář s názvem *Classes*.</span><span class="sxs-lookup"><span data-stu-id="e8893-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="e8893-109">V takovém případě sestavíte svou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e8893-109">You'll build your application there.</span></span> <span data-ttu-id="e8893-110">Přejděte do tohoto adresáře a zadejte `dotnet new console` v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e8893-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="e8893-111">Tento příkaz vytvoří vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e8893-111">This command creates your application.</span></span> <span data-ttu-id="e8893-112">Otevřete *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="e8893-112">Open *Program.cs*.</span></span> <span data-ttu-id="e8893-113">Mělo by to vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="e8893-113">It should look like this:</span></span>

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

<span data-ttu-id="e8893-114">V tomto kurzu budete vytvářet nové typy, které reprezentují bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="e8893-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="e8893-115">Vývojáři obvykle definují každou třídu v jiném textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="e8893-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="e8893-116">To usnadňuje správu v případě, že se velikost programu zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="e8893-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="e8893-117">V adresáři *třídy* vytvořte nový soubor s názvem *BankAccount.cs* .</span><span class="sxs-lookup"><span data-stu-id="e8893-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="e8893-118">Tento soubor bude obsahovat definici ***bankovního účtu***.</span><span class="sxs-lookup"><span data-stu-id="e8893-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="e8893-119">Objektově orientované programování organizuje kód vytvořením typů ve formě ***tříd***.</span><span class="sxs-lookup"><span data-stu-id="e8893-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="e8893-120">Tyto třídy obsahují kód, který představuje konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="e8893-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="e8893-121">`BankAccount`Třída představuje bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="e8893-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="e8893-122">Kód implementuje konkrétní operace prostřednictvím metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="e8893-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="e8893-123">V tomto kurzu bankovní účet podporuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="e8893-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="e8893-124">Má 10 číslic, které jedinečně identifikují bankovní účet.</span><span class="sxs-lookup"><span data-stu-id="e8893-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="e8893-125">Obsahuje řetězec, který ukládá název nebo názvy vlastníků.</span><span class="sxs-lookup"><span data-stu-id="e8893-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="e8893-126">Zůstatek lze načíst.</span><span class="sxs-lookup"><span data-stu-id="e8893-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="e8893-127">Přijímá vklady.</span><span class="sxs-lookup"><span data-stu-id="e8893-127">It accepts deposits.</span></span>
1. <span data-ttu-id="e8893-128">Přijímá stažení.</span><span class="sxs-lookup"><span data-stu-id="e8893-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="e8893-129">Počáteční zůstatek musí být kladný.</span><span class="sxs-lookup"><span data-stu-id="e8893-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="e8893-130">Vyčerpání nemůže vést k zápornému zůstatku.</span><span class="sxs-lookup"><span data-stu-id="e8893-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="e8893-131">Definování typu bankovního účtu</span><span class="sxs-lookup"><span data-stu-id="e8893-131">Define the bank account type</span></span>

<span data-ttu-id="e8893-132">Můžete začít vytvořením základních tříd, které definují toto chování.</span><span class="sxs-lookup"><span data-stu-id="e8893-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="e8893-133">Vytvořte nový soubor pomocí příkazu **soubor: nový** .</span><span class="sxs-lookup"><span data-stu-id="e8893-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="e8893-134">Pojmenujte ho *BankAccount.cs*.</span><span class="sxs-lookup"><span data-stu-id="e8893-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="e8893-135">Do souboru *BankAccount.cs* přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="e8893-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="e8893-136">Než začnete pracovat, Podívejme se na to, co jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="e8893-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="e8893-137">`namespace`Deklarace poskytuje způsob, jak logicky organizovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="e8893-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="e8893-138">Tento kurz je poměrně malý, takže veškerý kód se vloží do jednoho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e8893-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="e8893-139">`public class BankAccount`definuje třídu nebo typ, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="e8893-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="e8893-140">Vše uvnitř `{` a `}` , které následuje deklarace třídy, definuje stav a chování třídy.</span><span class="sxs-lookup"><span data-stu-id="e8893-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="e8893-141">Existuje pět ***členů*** `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="e8893-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="e8893-142">První tři jsou ***vlastnosti***.</span><span class="sxs-lookup"><span data-stu-id="e8893-142">The first three are ***properties***.</span></span> <span data-ttu-id="e8893-143">Vlastnosti jsou datové prvky a mohou mít kód, který vynutil ověřování nebo jiná pravidla.</span><span class="sxs-lookup"><span data-stu-id="e8893-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="e8893-144">Poslední dvě jsou ***metody***.</span><span class="sxs-lookup"><span data-stu-id="e8893-144">The last two are ***methods***.</span></span> <span data-ttu-id="e8893-145">Metody jsou bloky kódu, které provádějí jednu funkci.</span><span class="sxs-lookup"><span data-stu-id="e8893-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="e8893-146">Čtení názvů jednotlivých členů by mělo poskytnout dostatek informací pro vás nebo jiného vývojáře, aby bylo možné pochopit, co třída dělá.</span><span class="sxs-lookup"><span data-stu-id="e8893-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="e8893-147">Otevřít nový účet</span><span class="sxs-lookup"><span data-stu-id="e8893-147">Open a new account</span></span>

<span data-ttu-id="e8893-148">První funkcí, kterou je třeba implementovat, je otevření bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="e8893-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="e8893-149">Když zákazník otevře účet, musí dodat počáteční zůstatek a informace o vlastníkovi nebo vlastníkovi tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="e8893-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="e8893-150">Vytvoření nového objektu `BankAccount` typu znamená definování ***konstruktoru*** , který přiřazuje tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8893-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="e8893-151">***Konstruktor*** je člen, který má stejný název jako třída.</span><span class="sxs-lookup"><span data-stu-id="e8893-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="e8893-152">Slouží k inicializaci objektů tohoto typu třídy.</span><span class="sxs-lookup"><span data-stu-id="e8893-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="e8893-153">Přidejte k typu následující konstruktor `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="e8893-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="e8893-154">Vložte následující kód nad deklaraci `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="e8893-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="e8893-155">Konstruktory jsou volány při vytváření objektu pomocí [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="e8893-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="e8893-156">Nahraďte řádek `Console.WriteLine("Hello World!");` v *program.cs* následujícím kódem (nahraďte `<name>` svým jménem):</span><span class="sxs-lookup"><span data-stu-id="e8893-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="e8893-157">Pojďme spustit, co jste zatím vytvořili.</span><span class="sxs-lookup"><span data-stu-id="e8893-157">Let's run what you've built so far.</span></span> <span data-ttu-id="e8893-158">Pokud používáte aplikaci Visual Studio, vyberte možnost **Spustit bez ladění** z nabídky **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="e8893-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="e8893-159">Pokud používáte příkazový řádek, zadejte `dotnet run` do adresáře, kde jste vytvořili projekt.</span><span class="sxs-lookup"><span data-stu-id="e8893-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="e8893-160">Všimnete si, že číslo účtu je prázdné?</span><span class="sxs-lookup"><span data-stu-id="e8893-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="e8893-161">Je čas ji opravit.</span><span class="sxs-lookup"><span data-stu-id="e8893-161">It's time to fix that.</span></span> <span data-ttu-id="e8893-162">Číslo účtu by mělo být přiřazeno, když je objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="e8893-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="e8893-163">Ale nemělo by to být zodpovědností volajícího vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e8893-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="e8893-164">`BankAccount`Kód třídy by měl znát způsob přiřazení nových čísel účtů.</span><span class="sxs-lookup"><span data-stu-id="e8893-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="e8893-165">To lze provést jednoduše tak, že začnete s 10 číslicemi.</span><span class="sxs-lookup"><span data-stu-id="e8893-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="e8893-166">Při vytvoření každého nového účtu ho zvyšte.</span><span class="sxs-lookup"><span data-stu-id="e8893-166">Increment it when each new account is created.</span></span> <span data-ttu-id="e8893-167">Nakonec uložte aktuální číslo účtu, když je objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="e8893-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="e8893-168">Přidejte do třídy deklaraci člena `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="e8893-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="e8893-169">Vložte následující řádek kódu za levou složenou závorku `{` na začátku `BankAccount` třídy:</span><span class="sxs-lookup"><span data-stu-id="e8893-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="e8893-170">Toto je datový člen.</span><span class="sxs-lookup"><span data-stu-id="e8893-170">This is a data member.</span></span> <span data-ttu-id="e8893-171">Je to `private` , to znamená, že k němu lze přistupovat pouze pomocí kódu uvnitř `BankAccount` třídy.</span><span class="sxs-lookup"><span data-stu-id="e8893-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="e8893-172">Jedná se o způsob, jak oddělit veřejné zodpovědnosti (jako je třeba číslo účtu) od soukromé implementace (jak se generují čísla účtů).</span><span class="sxs-lookup"><span data-stu-id="e8893-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="e8893-173">Je to také to `static` , to znamená, že je sdílen všemi `BankAccount` objekty.</span><span class="sxs-lookup"><span data-stu-id="e8893-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="e8893-174">Hodnota proměnné, která není statická, je jedinečná pro každou instanci `BankAccount` objektu.</span><span class="sxs-lookup"><span data-stu-id="e8893-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="e8893-175">Přidejte následující dva řádky do konstruktoru, aby bylo možné přiřadit číslo účtu.</span><span class="sxs-lookup"><span data-stu-id="e8893-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="e8893-176">Umístěte je za řádek, který říká `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="e8893-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="e8893-177">`dotnet run`Pro zobrazení výsledků zadejte.</span><span class="sxs-lookup"><span data-stu-id="e8893-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="e8893-178">Vytváření vkladů a stažení</span><span class="sxs-lookup"><span data-stu-id="e8893-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="e8893-179">Třída bankovního účtu musí přijímat vklady a stažení, aby fungovaly správně.</span><span class="sxs-lookup"><span data-stu-id="e8893-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="e8893-180">Pojďme implementovat vklady a stažení, a to vytvořením deníku každé transakce pro účet.</span><span class="sxs-lookup"><span data-stu-id="e8893-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="e8893-181">Který má několik výhod v rámci jednoduché aktualizace zůstatku každé transakce.</span><span class="sxs-lookup"><span data-stu-id="e8893-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="e8893-182">Historii lze použít k auditování všech transakcí a ke správě každodenních zůstatků.</span><span class="sxs-lookup"><span data-stu-id="e8893-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="e8893-183">Vynásobením zůstatku z historie všech transakcí v případě potřeby budou všechny chyby v jedné transakci, které jsou opraveny, správně promítnuty do zůstatku následujícího výpočtu.</span><span class="sxs-lookup"><span data-stu-id="e8893-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="e8893-184">Pojďme začít vytvořením nového typu reprezentujícího transakci.</span><span class="sxs-lookup"><span data-stu-id="e8893-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="e8893-185">Toto je jednoduchý typ, který nemá žádné zodpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="e8893-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="e8893-186">Potřebuje několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="e8893-186">It needs a few properties.</span></span> <span data-ttu-id="e8893-187">Vytvořte nový soubor s názvem *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="e8893-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="e8893-188">Přidejte do ní následující kód:</span><span class="sxs-lookup"><span data-stu-id="e8893-188">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="e8893-189">Nyní přidáme do <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` třídy objekty.</span><span class="sxs-lookup"><span data-stu-id="e8893-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="e8893-190">Přidejte následující deklaraci za konstruktor v souboru *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="e8893-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="e8893-191"><xref:System.Collections.Generic.List%601>Třída vyžaduje, abyste naimportovali jiný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e8893-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="e8893-192">Na začátek *BankAccount.cs*přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="e8893-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="e8893-193">Teď změníme způsob, jakým `Balance` se nahlásí.</span><span class="sxs-lookup"><span data-stu-id="e8893-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="e8893-194">Dá se najít sečtením hodnot všech transakcí.</span><span class="sxs-lookup"><span data-stu-id="e8893-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="e8893-195">Upravte deklaraci `Balance` ve `BankAccount` třídě na následující:</span><span class="sxs-lookup"><span data-stu-id="e8893-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="e8893-196">Tento příklad ukazuje důležitý aspekt ***vlastností***.</span><span class="sxs-lookup"><span data-stu-id="e8893-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="e8893-197">Nyní počítáte rovnováhu, když další programátor žádá o hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8893-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="e8893-198">Vaše výpočty vyčísluje všechny transakce a jako aktuální zůstatek poskytuje součet.</span><span class="sxs-lookup"><span data-stu-id="e8893-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="e8893-199">Dále implementujte `MakeDeposit` metody a `MakeWithdrawal` .</span><span class="sxs-lookup"><span data-stu-id="e8893-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="e8893-200">Tyto metody vyplatí poslední dvě pravidla: počáteční zůstatek musí být kladný a že jakékoli stažení nesmí vytvořit záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="e8893-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="e8893-201">Tím se zavádí koncept ***výjimek***.</span><span class="sxs-lookup"><span data-stu-id="e8893-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="e8893-202">Standardní způsob, jak určit, že metoda nemůže dokončit svou práci, je vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="e8893-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="e8893-203">Typ výjimky a přidružená zpráva popisují chybu.</span><span class="sxs-lookup"><span data-stu-id="e8893-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="e8893-204">V tomto případě `MakeDeposit` metoda vyvolá výjimku, pokud je velikost depozita záporná.</span><span class="sxs-lookup"><span data-stu-id="e8893-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="e8893-205">`MakeWithdrawal`Metoda vyvolá výjimku, pokud je částka pro stažení záporná, nebo pokud se použije výsledek vyjmutí v záporném zůstatku.</span><span class="sxs-lookup"><span data-stu-id="e8893-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="e8893-206">Po deklaraci seznamu přidejte následující kód `allTransactions` :</span><span class="sxs-lookup"><span data-stu-id="e8893-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="e8893-207">[`throw`](../../language-reference/keywords/throw.md)Příkaz **vyvolá** výjimku.</span><span class="sxs-lookup"><span data-stu-id="e8893-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="e8893-208">Spuštění aktuálního bloku končí a řízení přenosů do prvního odpovídajícího `catch` bloku nalezeného v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="e8893-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="e8893-209">Přidáte `catch` blok pro otestování tohoto kódu trochu později.</span><span class="sxs-lookup"><span data-stu-id="e8893-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="e8893-210">Konstruktor by měl získat jednu změnu, aby přidal počáteční transakci místo přímé aktualizace zůstatku.</span><span class="sxs-lookup"><span data-stu-id="e8893-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="e8893-211">Vzhledem k tomu, že jste již zapsali `MakeDeposit` metodu, zavolejte ji z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e8893-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="e8893-212">Dokončený konstruktor by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="e8893-212">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="e8893-213"><xref:System.DateTime.Now?displayProperty=nameWithType>je vlastnost, která vrací aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="e8893-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="e8893-214">Otestujte to přidáním několika vkladů a výstupů v `Main` metodě za kód, který vytvoří novou `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="e8893-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="e8893-215">V dalším kroku otestujte chybové stavy tím, že se pokusíte vytvořit účet se záporným zůstatkem.</span><span class="sxs-lookup"><span data-stu-id="e8893-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="e8893-216">Za předchozí kód, který jste právě přidali, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="e8893-216">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="e8893-217">[ `try` `catch` Příkazy a](../../language-reference/keywords/try-catch.md) můžete použít k označení bloku kódu, který může vyvolat výjimky a zachytit tyto chyby, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="e8893-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="e8893-218">Stejný postup můžete použít k otestování kódu, který vyvolá výjimku pro záporný zůstatek.</span><span class="sxs-lookup"><span data-stu-id="e8893-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="e8893-219">Na konec metody přidejte následující kód `Main` :</span><span class="sxs-lookup"><span data-stu-id="e8893-219">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="e8893-220">Uložte soubor a zadejte `dotnet run` ho a zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="e8893-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="e8893-221">Výzva – protokoluje všechny transakce.</span><span class="sxs-lookup"><span data-stu-id="e8893-221">Challenge - log all transactions</span></span>

<span data-ttu-id="e8893-222">Pro dokončení tohoto kurzu můžete napsat `GetAccountHistory` metodu, která vytvoří `string` pro historii transakce.</span><span class="sxs-lookup"><span data-stu-id="e8893-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="e8893-223">Přidejte tuto metodu do `BankAccount` typu:</span><span class="sxs-lookup"><span data-stu-id="e8893-223">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="e8893-224">To používá <xref:System.Text.StringBuilder> třídu k formátování řetězce, který obsahuje jeden řádek pro každou transakci.</span><span class="sxs-lookup"><span data-stu-id="e8893-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="e8893-225">Kód pro formátování řetězců jste viděli dříve v těchto kurzech.</span><span class="sxs-lookup"><span data-stu-id="e8893-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="e8893-226">Jeden nový znak je `\t` .</span><span class="sxs-lookup"><span data-stu-id="e8893-226">One new character is `\t`.</span></span> <span data-ttu-id="e8893-227">Tím se vloží karta pro formátování výstupu.</span><span class="sxs-lookup"><span data-stu-id="e8893-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="e8893-228">Přidejte tento řádek k otestování v *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="e8893-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="e8893-229">Výsledky zobrazíte spuštěním programu.</span><span class="sxs-lookup"><span data-stu-id="e8893-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e8893-230">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e8893-230">Next steps</span></span>

<span data-ttu-id="e8893-231">Pokud jste se zablokovali, můžete se podívat na zdroj tohoto kurzu [v našem úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="e8893-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="e8893-232">Blahopřejeme, dokončili jste všechny naše Úvod do kurzů C#.</span><span class="sxs-lookup"><span data-stu-id="e8893-232">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="e8893-233">Pokud se Eager o další informace, vyzkoušejte si více našich [kurzů](../index.md).</span><span class="sxs-lookup"><span data-stu-id="e8893-233">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
