---
title: Použití třídy WorkflowInvoker
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: d6525dbbd30aae95be4c4ee1de267736e557a541
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748701"
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="8a440-102">Použití třídy WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="8a440-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="8a440-103">Tato ukázka předvádí, jak používat <xref:System.Activities.WorkflowInvoker> třídy k vyvolání aktivity, jako by šlo metodu.</span><span class="sxs-lookup"><span data-stu-id="8a440-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="8a440-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8a440-104">Sample Details</span></span>  
 <span data-ttu-id="8a440-105">Použití <xref:System.Activities.WorkflowInvoker> třída je nejjednodušší způsob, jak provést aktivitu.</span><span class="sxs-lookup"><span data-stu-id="8a440-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="8a440-106">Je určená pro přímo spouštět aktivity, jako by šlo volání metody.</span><span class="sxs-lookup"><span data-stu-id="8a440-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="8a440-107">Je odlehčený, vysoce výkonné, snadno použitelná rozhraní API v situacích, kde aktivity spuštění nevyžaduje infrastrukturu řízení další varianty konfigurací hostování.</span><span class="sxs-lookup"><span data-stu-id="8a440-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="8a440-108">Ukázka používá vlastní aktivitu, která je odvozena z <xref:System.Activities.CodeActivity%601>< Int32\> s názvem `Add` , který přidá dvě <xref:System.Activities.InArgument%601>, `X` a `Y`a vrátí `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="8a440-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="8a440-109">(<xref:System.Activities.CodeActivity%601>\<T > je odvozena z <xref:System.Activities.Activity%601>< T\>, který má <xref:System.Activities.OutArgument%601> \<T > s názvem `Result`.) A `Dictionary` \<řetězec, objekt > slouží k předávání argumentů do aktivity vyvolání prostřednictvím <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="8a440-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="8a440-110">Klíč slovníku odpovídá názvu argumentu na vyvolaná aktivita.</span><span class="sxs-lookup"><span data-stu-id="8a440-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="8a440-111">Hodnota přidružená k určité klíče je vázán na argument identifikované klíčem.</span><span class="sxs-lookup"><span data-stu-id="8a440-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="8a440-112">Ukázka volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> a předává slovník, který obsahuje hodnoty pro `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="8a440-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="8a440-113"><xref:System.Activities.WorkflowInvoker> Třídy váže tyto hodnoty `Add` aktivity argumenty, spustí aktivity a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="8a440-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8a440-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="8a440-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="8a440-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Invoker.sln.</span><span class="sxs-lookup"><span data-stu-id="8a440-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="8a440-116">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8a440-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="8a440-117">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="8a440-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a440-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8a440-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a440-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8a440-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a440-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8a440-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a440-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8a440-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`