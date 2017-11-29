---
title: "Jednoduché zásady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a><span data-ttu-id="f4b0c-102">Jednoduché zásady</span><span class="sxs-lookup"><span data-stu-id="f4b0c-102">Simple Policy</span></span>
<span data-ttu-id="f4b0c-103">Tento příklad ukazuje způsob použití <xref:System.Workflow.Activities.PolicyActivity> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="f4b0c-104">Sekvenční pracovní postup v této ukázce je vytvořená pomocí <xref:System.Workflow.Activities.PolicyActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="f4b0c-105">Pracovní postup definuje `orderValue`, `customerType`, a `discount` pole, která slouží k určení produktu slevách pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="f4b0c-106">Pravidla definovaná v souboru pravidel nastavit slevu hodnotu, která je založena na `orderValue` a `customerType`.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="f4b0c-107">`orderValue` a `customerType` jsou nastavené `SimplePolicyWorkflow` definici třídy a ke změně chování lze změnit.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="f4b0c-108">Výsledný slevu je zapsán do konzoly v <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obslužné rutiny události, která je definována v `SimplePolicyWorkflow` třídy.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="f4b0c-109">Chcete-li sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="f4b0c-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="f4b0c-110">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4b0c-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f4b0c-111">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f4b0c-112">Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="f4b0c-113">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f4b0c-113">To run the sample</span></span>  
  
-   <span data-ttu-id="f4b0c-114">V okně Příkazový řádek SDK spusťte soubor .exe ve složce SimplePolicy\bin\debug (nebo ve složce SimplePolicy\bin pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4b0c-115">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f4b0c-116">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="f4b0c-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4b0c-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4b0c-118">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="f4b0c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4b0c-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="f4b0c-120">Rozšířené zásady</span><span class="sxs-lookup"><span data-stu-id="f4b0c-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
