---
title: "Pořadí zpracování pomocí zásad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aaab8fca4693f6b253d48f066e644cc76637241
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="7b039-102">Pořadí zpracování pomocí zásad</span><span class="sxs-lookup"><span data-stu-id="7b039-102">Order Processing with Policy</span></span>
<span data-ttu-id="7b039-103">Příklad pořadí zpracování zásad ukazuje některé klíčové funkce byla zavedená v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="7b039-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="7b039-104">Následující funkce jsou nové pro modul pravidla pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="7b039-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="7b039-105">Podpora pro přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="7b039-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="7b039-106">Podpora pro `new` operátor, což umožňuje uživatelům vytvářet nové objekty a pole z pravidel WF.</span><span class="sxs-lookup"><span data-stu-id="7b039-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="7b039-107">Podpora pro rozšíření metod, jak se uživateli při volání metody rozšíření z pravidel WF kompatibilní s kódování styly C#.</span><span class="sxs-lookup"><span data-stu-id="7b039-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b039-108">Tato ukázka vyžaduje, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] je nainstalovaná pro sestavení a spuštění.</span><span class="sxs-lookup"><span data-stu-id="7b039-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="7b039-109">je potřeba otevřít soubory projektu a řešení.</span><span class="sxs-lookup"><span data-stu-id="7b039-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="7b039-110">Ukázka ukazuje `OrderProcessingPolicy` projektu v pořadí zákazníka, které se skládá z číslovaný seznam dostupné položky a PSČ, je zadána.</span><span class="sxs-lookup"><span data-stu-id="7b039-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="7b039-111">Pořadí je úspěšně zpracovat, pokud jsou obě položky správné; jinak zásady vytvoří objekty chyby, využívá přetížené `+` operátor a metoda předdefinované rozšíření informovat uživatele chyby.</span><span class="sxs-lookup"><span data-stu-id="7b039-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7b039-112">rozšiřující metody, najdete v části [C# verze 3.0 specifikace](http://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="7b039-112"> extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="7b039-113">Ukázka se skládá z následujících projektech:</span><span class="sxs-lookup"><span data-stu-id="7b039-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="7b039-114">`OrderErrorLibrary` Třída knihovnu, která definuje `OrderError` a `OrderErrorCollection` třídy.</span><span class="sxs-lookup"><span data-stu-id="7b039-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="7b039-115">`OrderError` Instance se vytvoří, když je zadaný neplatný vstup.</span><span class="sxs-lookup"><span data-stu-id="7b039-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="7b039-116">Knihovna také poskytuje metody rozšíření na `OrderErrorCollection` třídu, která výstupy `ErrorText` vlastnost na všech `OrderError` objekty v `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="7b039-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="7b039-117">`OrderProcessingPolicy` Projekt je konzolová aplikace pracovního postupu, která definuje jeden `PolicyFromFile` aktivity.</span><span class="sxs-lookup"><span data-stu-id="7b039-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="7b039-118">Aktivita má následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="7b039-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="7b039-119">Toto pravidlo ověří, zda číslo položky je mezi 1 a 6 (včetně).</span><span class="sxs-lookup"><span data-stu-id="7b039-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="7b039-120">Pokud je číslo položky v platném rozsahu, pravidlo se nic nestane. (jiné než tisk do konzoly).</span><span class="sxs-lookup"><span data-stu-id="7b039-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="7b039-121">Pokud není číslo mezi 1 a 6, `invalidItemNum` pravidlo provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="7b039-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="7b039-122">Vytvoří novou `OrderError` objektu předání číslo zadali a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="7b039-123">Vytvoří `invalidItemNumErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="7b039-124">Přidá nově vytvořené `OrderError` instance na `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="7b039-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="7b039-125">Tento příklad ukazuje, podpora `new` operátor, pomocí kterého můžete vytvořit instanci objekty uvnitř pravidla.</span><span class="sxs-lookup"><span data-stu-id="7b039-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="7b039-126">Toto pravidlo ověří, zda kód zip 5 číslic a je v rozsahu 600 k 99998.</span><span class="sxs-lookup"><span data-stu-id="7b039-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="7b039-127">Pokud je kód zip v platném rozsahu, pravidlo se nic nestane. (jiné než tisk do konzoly).</span><span class="sxs-lookup"><span data-stu-id="7b039-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="7b039-128">Pokud délka zadané PSČ je menší než 5 nebo kód zip není mezi 00600 a 99998, `invalidZip` pravidlo provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="7b039-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="7b039-129">Vytvoří `OrderError` objektu předání PSČ zadán a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="7b039-130">Vytvoří `invalidZipCodeErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="7b039-131">Přidá nově vytvořené `OrderError` instance nově vytvořené `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="7b039-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="7b039-132">Toto pravidlo znovu ukazuje podpora `new` operátor, který slouží k vytváření instancí objektů uvnitř pravidla.</span><span class="sxs-lookup"><span data-stu-id="7b039-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="7b039-133">Toto pravidlo zkontroluje, pokud došlo k chybám žádné přidal předchozí dvě pravidla ve dvou `OrderErrorCollection` objekty `invalidItemNumErrorCollection` a `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="7b039-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="7b039-134">Pokud došlo k chybám (buď `invalidItemNumErrorCollection` nebo `invalidZipCodeErrorCollection` není `null`), pravidlo provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="7b039-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="7b039-135">Volání přetížené `+` operátor a zkopírujte obsah `invalidItemNumErrorCollection` a `invalidZipCodeErrorCollection` k `invalidOrdersCollection``OrderErrorCollection` instance.</span><span class="sxs-lookup"><span data-stu-id="7b039-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="7b039-136">Volání `PrintOrderErrors` rozšiřující metody na `invalidOrdersCollection` a výstupy `ErrorText` vlastnost na všech `orderError` objekty v `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="7b039-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="7b039-137">Přetížené operátor `+` na `OrderErrorCollection` je definována v `OrderErrorCollection` třídy v `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="7b039-138">Dva trvá `OrderErrorCollection` objekty a sloučí je do jedné `OrderErrorCollection` objektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="7b039-139">`PrintOrderErrors` Metoda rozšíření je také definován ve `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="7b039-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="7b039-140">Rozšiřující metody jsou nová C# funkce, která vývojářům umožňuje přidat nové metody do veřejného kontraktu existujícího typu CLR, aniž by museli odvození třídy z něj nebo znovu zkompiluje původní typ.</span><span class="sxs-lookup"><span data-stu-id="7b039-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="7b039-141">Při spuštěním ukázky budete vyzváni k zadání názvu, číslo položky je možné zakoupit a kód zip.</span><span class="sxs-lookup"><span data-stu-id="7b039-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="7b039-142">Tyto informace pak ověří pravidla definovaná v aktivity zásad.</span><span class="sxs-lookup"><span data-stu-id="7b039-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="7b039-143">Zde je ukázkový výstup z programu.</span><span class="sxs-lookup"><span data-stu-id="7b039-143">The following is sample output from the program.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b039-144">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7b039-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7b039-145">Otevřete soubor projektu OrderProcessingPolicy.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b039-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b039-146">Existují dva různé projekty v řešení: `OrderErrorLibrary` a `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="7b039-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="7b039-147">`OrderProcessingPolicy` Projektu používá třídy a metody definované v `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="7b039-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="7b039-148">Všechny projekty sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b039-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="7b039-149">Klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="7b039-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b039-150">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="7b039-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7b039-151">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="7b039-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b039-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7b039-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b039-153">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="7b039-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`