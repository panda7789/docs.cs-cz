---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 12d028515c34c0e3593c90b81a5589fb05f36b82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517735"
---
# <a name="invokemethod"></a><span data-ttu-id="da5d5-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="da5d5-102">InvokeMethod</span></span>
<span data-ttu-id="da5d5-103">Tento příklad ukazuje různé způsoby použití <xref:System.Activities.Statements.InvokeMethod> aktivity k vyvolání metody třídy.</span><span class="sxs-lookup"><span data-stu-id="da5d5-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="da5d5-104">Metoda patří do třídy, představuje sadu operací obsažené.</span><span class="sxs-lookup"><span data-stu-id="da5d5-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="da5d5-105"><xref:System.Activities.Statements.InvokeMethod> Aktivity vám dává možnost volání metod s objekty nebo typů, předat parametry a získat návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="da5d5-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="da5d5-106">Metody mohou být vyvolány synchronně nebo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="da5d5-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="da5d5-107">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="da5d5-107">Sample Details</span></span>  
 <span data-ttu-id="da5d5-108">V tomto příkladu <xref:System.Activities.Statements.InvokeMethod> aktivita k provedení následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="da5d5-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="da5d5-109">Vyvolání metody instance bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="da5d5-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="da5d5-110">Vyvolání metody instance s dva parametry (<xref:System.String> a <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="da5d5-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="da5d5-111">Vyvolání metody instance s dva parametry (<xref:System.String> a <xref:System.Int32>) a parametr pole typu <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="da5d5-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="da5d5-112">Vyvolání metody instance s dva parametry typu <xref:System.Int32> a výsledek typu <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="da5d5-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="da5d5-113">V tomto scénáři je výsledkem hodnota vázaná na proměnnou a použít v jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="da5d5-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="da5d5-114">Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="da5d5-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="da5d5-115">Vyvolání statickou metodu s dva parametry typu <xref:System.String> a <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="da5d5-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="da5d5-116">Vyvolání metody instance s jeden obecný parametr typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="da5d5-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="da5d5-117">Vyvolání statickou metodu s dvě obecné parametry typu <xref:System.String> a <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="da5d5-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="da5d5-118">Vyvolání metody instance, který má jeden parametr předaná odkaz na typ <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="da5d5-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="da5d5-119">V tomto scénáři vazbu parametru odkazu na proměnnou (`outParam`) a použít v jiné aktivitě.</span><span class="sxs-lookup"><span data-stu-id="da5d5-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="da5d5-120">Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="da5d5-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="da5d5-121">Vyvolání metody asynchronní instance.</span><span class="sxs-lookup"><span data-stu-id="da5d5-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="da5d5-122">Vyvolání dvě různé metody na stejnou instanci objekt, který používá dva <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="da5d5-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="da5d5-123">Hodnotu uložte instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="da5d5-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="da5d5-124">Načtení hodnoty z instance objektu.</span><span class="sxs-lookup"><span data-stu-id="da5d5-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="da5d5-125">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="da5d5-125">To use this sample</span></span>  
 <span data-ttu-id="da5d5-126">Tato ukázka je součástí dvě verze.</span><span class="sxs-lookup"><span data-stu-id="da5d5-126">This sample is provided in two versions.</span></span> <span data-ttu-id="da5d5-127">První verzi této ukázce ukazuje použití <xref:System.Activities.Statements.InvokeMethod> prostřednictvím jazyka C# kódu, pomocí programovacího modelu Windows Workflow Foundation (WF) a nachází se ve složce CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="da5d5-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="da5d5-128">Druhá verze ukazuje použití <xref:System.Activities.Statements.InvokeMethod> pomocí XAML a nachází se ve složce DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="da5d5-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="da5d5-129">Ke spuštění ukázky programové pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="da5d5-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="da5d5-130">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="da5d5-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="da5d5-131">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="da5d5-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="da5d5-132">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="da5d5-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="da5d5-133">Ke spuštění ukázky Návrháře pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="da5d5-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="da5d5-134">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="da5d5-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="da5d5-135">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="da5d5-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="da5d5-136">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="da5d5-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da5d5-137">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="da5d5-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da5d5-138">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="da5d5-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da5d5-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="da5d5-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da5d5-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="da5d5-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`