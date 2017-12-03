---
title: "Pomocí aktivity InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="a308c-102">Pomocí aktivity InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a308c-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="a308c-103">Tento příklad znázorňuje způsob použití <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) aktivity k vyvolání veřejné metody ve veřejné třídy.</span><span class="sxs-lookup"><span data-stu-id="a308c-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="a308c-104"><!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) Aktivita povoluje pracovního postupu k volání metody u objektů, předat parametry, získat návratovou hodnotu, určit typy pro obecné metody a určete, zda je metoda synchronní nebo asynchronní.</span><span class="sxs-lookup"><span data-stu-id="a308c-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
<span data-ttu-id="a308c-105">Je neobecnou verzi <xref:System.Activities.Statements.InvokeMethod> aktivity, kde je návratovou hodnotu nastaven na <xref:System.Activities.Statements.InvokeMethod.Result%2A> vlastnost a obecná verze <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) aktivity, kde se vrátí návratová hodnota prostřednictvím <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) vlastnost typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="a308c-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span> 
  
 <span data-ttu-id="a308c-106">Tento příklad ukazuje způsob volání různé typy metoda.</span><span class="sxs-lookup"><span data-stu-id="a308c-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="a308c-107">Následující podrobnosti seznam typů metoda předvedená v této ukázce:</span><span class="sxs-lookup"><span data-stu-id="a308c-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="a308c-108">Vyvolání metody instance bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="a308c-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="a308c-109">Vyvolání metody instance s dva parametry (System.String a System.Int32).</span><span class="sxs-lookup"><span data-stu-id="a308c-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a308c-110">Vyvolání metody instance s dva parametry (System.String a System.Int32) a parametr pole typu System.String [].</span><span class="sxs-lookup"><span data-stu-id="a308c-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="a308c-111">Vyvolání metody instance s dva parametry (dvou čísel System.Int32) a výsledek typu System.Int32.</span><span class="sxs-lookup"><span data-stu-id="a308c-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="a308c-112">Návratová hodnota je vázán k proměnné a vytisknout pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a308c-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="a308c-113">Vyvolání statickou metodu s dva parametry (System.String a System.Int32).</span><span class="sxs-lookup"><span data-stu-id="a308c-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a308c-114">Vyvolání metody instance s jeden obecný parametr (System.String).</span><span class="sxs-lookup"><span data-stu-id="a308c-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="a308c-115">Vyvolání statickou metodu s dvě obecné parametry (System.String a System.Int32).</span><span class="sxs-lookup"><span data-stu-id="a308c-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="a308c-116">Vyvolání metody instance, který má jeden parametr předaný odkazem (System.String).</span><span class="sxs-lookup"><span data-stu-id="a308c-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="a308c-117">Parametr odkazované je vázán k proměnné a vytisknout pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a308c-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="a308c-118">Vyvolání metody asynchronní instance.</span><span class="sxs-lookup"><span data-stu-id="a308c-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="a308c-119">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a308c-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="a308c-120">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln.</span><span class="sxs-lookup"><span data-stu-id="a308c-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a308c-121">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a308c-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a308c-122">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="a308c-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a308c-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a308c-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a308c-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a308c-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a308c-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a308c-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a308c-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a308c-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`