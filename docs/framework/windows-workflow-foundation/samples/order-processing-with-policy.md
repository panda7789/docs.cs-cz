---
title: Zpracování objednávky pomocí zásad
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: b927d8e7090f96b22c0510f9651070ab999c91be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398367"
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="9fff1-102">Zpracování objednávky pomocí zásad</span><span class="sxs-lookup"><span data-stu-id="9fff1-102">Order Processing with Policy</span></span>
<span data-ttu-id="9fff1-103">Pořadí zpracování zásad příklad ukazuje některé klíčové funkce [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="9fff1-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="9fff1-104">Následující funkce jsou nové pro stroj pravidel pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="9fff1-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="9fff1-105">Podpora pro přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="9fff1-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="9fff1-106">Podpora `new` operátor umožňuje uživatelům vytvářet nové objekty a pole z pracovního postupu pravidla.</span><span class="sxs-lookup"><span data-stu-id="9fff1-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="9fff1-107">Podpora pro rozšiřující metody uživatelského prostředí ve volání metody rozšíření z pravidla WF kompatibilní s stylů kódování C#.</span><span class="sxs-lookup"><span data-stu-id="9fff1-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fff1-108">Tato ukázka vyžaduje, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] je nainstalovaná sestavení a spuštění.</span><span class="sxs-lookup"><span data-stu-id="9fff1-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="9fff1-109"> je potřeba otevřít soubory projektu a řešení.</span><span class="sxs-lookup"><span data-stu-id="9fff1-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="9fff1-110">Ukázce `OrderProcessingPolicy` objednávku zákazníka, který se skládá z číslovaný seznam dostupných položek a PSČ, je zadaný projekt.</span><span class="sxs-lookup"><span data-stu-id="9fff1-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="9fff1-111">Pořadí je úspěšně zpracovat, pokud obě položky jsou správná. jinak zásady vytvoří objekty chyba, využitím přetížený `+` operátor a předdefinované rozšiřující metoda uživatel informován o chybách.</span><span class="sxs-lookup"><span data-stu-id="9fff1-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fff1-112">Další informace o metodách rozšíření naleznete v tématu [3.0 specifikace verze jazyka C#](https://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="9fff1-112">For more information about extension methods, see [C# Version 3.0 Specification](https://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="9fff1-113">Ukázka se skládá z následující projekty:</span><span class="sxs-lookup"><span data-stu-id="9fff1-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="9fff1-114">`OrderErrorLibrary` Je knihovny tříd, který definuje `OrderError` a `OrderErrorCollection` třídy.</span><span class="sxs-lookup"><span data-stu-id="9fff1-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="9fff1-115">`OrderError` Je vytvořena instance, pokud je zadán neplatný vstup.</span><span class="sxs-lookup"><span data-stu-id="9fff1-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="9fff1-116">Knihovna také poskytuje metodu rozšíření na `OrderErrorCollection` třídy, jejichž výstupem jsou `ErrorText` vlastnost na všech `OrderError` objekty v `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="9fff1-117">`OrderProcessingPolicy` Projekt je konzolová aplikace pracovního postupu, který definuje jedinou `PolicyFromFile` aktivity.</span><span class="sxs-lookup"><span data-stu-id="9fff1-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="9fff1-118">Aktivita má následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="9fff1-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="9fff1-119">Toto pravidlo ověří, že je číslo mezi 1 a 6, včetně.</span><span class="sxs-lookup"><span data-stu-id="9fff1-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="9fff1-120">Pokud je položka číslo v platném rozsahu, pravidlo nemá žádný účinek, (jiné než tisk do konzoly).</span><span class="sxs-lookup"><span data-stu-id="9fff1-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="9fff1-121">Pokud není položka číslo mezi 1 a 6, `invalidItemNum` pravidlo provede následující:</span><span class="sxs-lookup"><span data-stu-id="9fff1-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9fff1-122">Vytvoří novou `OrderError` objektu, předají se jí číslo zadali a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="9fff1-123">Vytvoří `invalidItemNumErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="9fff1-124">Přidá nově vytvořené `OrderError` instance na `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="9fff1-125">Tento příklad ukazuje podporu `new` operátoru, pomocí kterého můžete vytvořit instanci objektů uvnitř pravidla.</span><span class="sxs-lookup"><span data-stu-id="9fff1-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="9fff1-126">Toto pravidlo ověří, že má 5 číslic PSČ a je v rozsahu 600 k 99998.</span><span class="sxs-lookup"><span data-stu-id="9fff1-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="9fff1-127">Pokud je kód zip v platném rozsahu, pravidlo nemá žádný účinek, (jiné než tisk do konzoly).</span><span class="sxs-lookup"><span data-stu-id="9fff1-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="9fff1-128">Pokud aplikace PSČ je menší než 5 nebo PSČ není mezi 00600 a 99998, `invalidZip` pravidlo provede následující:</span><span class="sxs-lookup"><span data-stu-id="9fff1-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9fff1-129">Vytvoří `OrderError` objektu, předají se jí zadán, PSČ a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="9fff1-130">Vytvoří `invalidZipCodeErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="9fff1-131">Přidá nově vytvořené `OrderError` instance do nově vytvořené `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="9fff1-132">Toto pravidlo znovu ukazuje podporu `new` operátor, který umožňuje vytvořit instanci objektů uvnitř pravidla.</span><span class="sxs-lookup"><span data-stu-id="9fff1-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="9fff1-133">Toto pravidlo zkontroluje, pokud byly nějaké chyby přidal předchozí dvě pravidla ve dvou `OrderErrorCollection` objekty `invalidItemNumErrorCollection` a `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="9fff1-134">Pokud došlo k chybám (buď `invalidItemNumErrorCollection` nebo `invalidZipCodeErrorCollection` není `null`), pravidla provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="9fff1-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9fff1-135">Volání přetížené `+` operátor zkopírujte obsah `invalidItemNumErrorCollection` a `invalidZipCodeErrorCollection` do `invalidOrdersCollection``OrderErrorCollection` instance.</span><span class="sxs-lookup"><span data-stu-id="9fff1-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="9fff1-136">Volání `PrintOrderErrors` rozšiřující metody na `invalidOrdersCollection` a vypíše `ErrorText` vlastnost na všech `orderError` objekty v `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="9fff1-137">Přetížený operátor `+` na `OrderErrorCollection` je definována v `OrderErrorCollection` třídy v `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="9fff1-138">Má dva `OrderErrorCollection` objekty a kombinuje je do jedné `OrderErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="9fff1-139">`PrintOrderErrors` – Metoda rozšíření je také definováno v `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="9fff1-140">Rozšiřující metody jsou novou C# funkci, která vývojářům umožňuje přidat nové metody do veřejného kontraktu existujícího typu CLR, aniž byste museli odvodit třídu z něj nebo znovu zkompilovat původního typu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="9fff1-141">Při spuštění ukázky budete vyzváni k zadání názvu, číslo položky položky, která se dá zakoupit a PSČ.</span><span class="sxs-lookup"><span data-stu-id="9fff1-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="9fff1-142">Tyto informace potom ověřují z pravidel definovaných v rámci aktivity zásad.</span><span class="sxs-lookup"><span data-stu-id="9fff1-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="9fff1-143">Tady je ukázkový výstup z programu.</span><span class="sxs-lookup"><span data-stu-id="9fff1-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9fff1-144">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9fff1-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9fff1-145">Otevřete soubor projektu OrderProcessingPolicy.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fff1-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9fff1-146">Existují dva různé projekty v řešení: `OrderErrorLibrary` a `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="9fff1-147">`OrderProcessingPolicy` Projekt používá třídy a metody definované v `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="9fff1-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="9fff1-148">Sestavte všechny projekty.</span><span class="sxs-lookup"><span data-stu-id="9fff1-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="9fff1-149">Klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="9fff1-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9fff1-150">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9fff1-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9fff1-151">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="9fff1-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9fff1-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9fff1-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9fff1-153">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="9fff1-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`