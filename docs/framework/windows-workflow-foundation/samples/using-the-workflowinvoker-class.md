---
title: "Používání třídy WorkflowInvoker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8bb6c4049b56702c8fad226c20884ff581ec6203
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="a45cf-102">Používání třídy WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="a45cf-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="a45cf-103">Tento příklad znázorňuje způsob použití <xref:System.Activities.WorkflowInvoker> třída má být vyvolán aktivity, jako by šlo metodu.</span><span class="sxs-lookup"><span data-stu-id="a45cf-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a45cf-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a45cf-104">Sample Details</span></span>  
 <span data-ttu-id="a45cf-105">Pomocí <xref:System.Activities.WorkflowInvoker> třída je nejjednodušší způsob, jak provést aktivitu.</span><span class="sxs-lookup"><span data-stu-id="a45cf-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="a45cf-106">Je určený pro přímo spouštět aktivitu, jako by šlo volání metody.</span><span class="sxs-lookup"><span data-stu-id="a45cf-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="a45cf-107">Je jednoduché, vysoce výkonné, snadno použitelné rozhraní API v situacích, kde provádění aktivity nevyžaduje infrastrukturu řízení jiných hostitelských variace.</span><span class="sxs-lookup"><span data-stu-id="a45cf-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="a45cf-108">Ukázka používá vlastní aktivity, která je odvozena z <xref:System.Activities.CodeActivity%601>< Int32\> s názvem `Add` , přidá dva <xref:System.Activities.InArgument%601>, `X` a `Y`a vrátí `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="a45cf-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="a45cf-109">(<xref:System.Activities.CodeActivity%601>\<T > je odvozena z <xref:System.Activities.Activity%601>< T\>, který má <xref:System.Activities.OutArgument%601> \<T > s názvem `Result`.) A `Dictionary` \<řetězec, objekt > slouží k předání argumentů do aktivity vyvolání prostřednictvím <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="a45cf-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="a45cf-110">Klíče slovníku odpovídá názvu argument vyvolaná aktivita.</span><span class="sxs-lookup"><span data-stu-id="a45cf-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="a45cf-111">Hodnoty přidružené k určité klíči je vázána k argumentu identifikovat pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="a45cf-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="a45cf-112">Ukázka volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> a předá slovník, který obsahuje hodnoty pro `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="a45cf-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="a45cf-113"><xref:System.Activities.WorkflowInvoker> Třída váže tyto hodnoty `Add` aktivity je argumenty, provádí aktivity a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="a45cf-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a45cf-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a45cf-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a45cf-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Invoker.sln.</span><span class="sxs-lookup"><span data-stu-id="a45cf-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a45cf-116">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a45cf-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a45cf-117">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="a45cf-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a45cf-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a45cf-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a45cf-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a45cf-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a45cf-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a45cf-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a45cf-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a45cf-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`