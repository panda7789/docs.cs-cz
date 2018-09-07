---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047708"
---
# <a name="invokemethod"></a><span data-ttu-id="e5743-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e5743-102">InvokeMethod</span></span>
<span data-ttu-id="e5743-103">Tento příklad ukazuje různé způsoby použití <xref:System.Activities.Statements.InvokeMethod> aktivity k vyvolání metody dané třídy.</span><span class="sxs-lookup"><span data-stu-id="e5743-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="e5743-104">Metoda patří do třídy a představuje omezením sadu operací.</span><span class="sxs-lookup"><span data-stu-id="e5743-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="e5743-105"><xref:System.Activities.Statements.InvokeMethod> Aktivity vám dává možnost volání metod na objekty nebo typy, předat parametry a načtení návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e5743-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="e5743-106">Metody lze vyvolat synchronně nebo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="e5743-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e5743-107">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e5743-107">Sample Details</span></span>  
 <span data-ttu-id="e5743-108">Tento příklad používá <xref:System.Activities.Statements.InvokeMethod> aktivita k provedení následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="e5743-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="e5743-109">Vyvolejte metodu instance bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="e5743-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="e5743-110">Vyvolat metodu instance se dvěma parametry (<xref:System.String> a <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="e5743-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="e5743-111">Vyvolat metodu instance se dvěma parametry (<xref:System.String> a <xref:System.Int32>) a pole parametrů typu <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="e5743-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="e5743-112">Vyvolat metodu instance se dvěma parametry typu <xref:System.Int32> a výsledek typu <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="e5743-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="e5743-113">V tomto scénáři je výsledná hodnota vázán na proměnnou a použít v jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="e5743-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="e5743-114">Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="e5743-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="e5743-115">Volání statické metody se dvěma parametry typu <xref:System.String> a <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="e5743-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="e5743-116">Vyvolat metodu instance s jeden parametr obecného typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e5743-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="e5743-117">Volání statické metody se dvěma parametry obecného typu <xref:System.String> a <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="e5743-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="e5743-118">Vyvolat metodu instance, která má jeden parametr předaný prostřednictvím odkazu typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e5743-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="e5743-119">V tomto scénáři vazbu parametru odkazu na proměnnou (`outParam`) a použít v jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="e5743-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="e5743-120">Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="e5743-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="e5743-121">Vyvolejte metodu asynchronní instance.</span><span class="sxs-lookup"><span data-stu-id="e5743-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="e5743-122">Vyvolání dva různé způsoby ve stejné instanci objektu pomocí dvou <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="e5743-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="e5743-123">Store hodnotu v instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="e5743-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="e5743-124">Načtení hodnoty z instance objektu.</span><span class="sxs-lookup"><span data-stu-id="e5743-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e5743-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="e5743-125">To use this sample</span></span>  
 <span data-ttu-id="e5743-126">Tato ukázka je k dispozici ve dvou verzích.</span><span class="sxs-lookup"><span data-stu-id="e5743-126">This sample is provided in two versions.</span></span> <span data-ttu-id="e5743-127">První verzi tento příklad ukazuje použití <xref:System.Activities.Statements.InvokeMethod> prostřednictvím kódu C# kód, pomocí programovacího modelu Windows Workflow Foundation (WF) a nachází se ve složce CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="e5743-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="e5743-128">Druhá verze ukazuje použití <xref:System.Activities.Statements.InvokeMethod> pomocí XAML a nachází se ve složce DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="e5743-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="e5743-129">Ke spuštění ukázky programové pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e5743-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="e5743-130">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="e5743-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="e5743-131">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e5743-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e5743-132">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e5743-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="e5743-133">Ke spuštění ukázky Návrháře pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e5743-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="e5743-134">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="e5743-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="e5743-135">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e5743-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e5743-136">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e5743-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5743-137">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e5743-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e5743-138">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e5743-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e5743-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e5743-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5743-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e5743-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`