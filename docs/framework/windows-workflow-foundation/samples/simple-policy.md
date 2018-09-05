---
title: Jednoduché zásady
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743743"
---
# <a name="simple-policy"></a><span data-ttu-id="b0e88-102">Jednoduché zásady</span><span class="sxs-lookup"><span data-stu-id="b0e88-102">Simple Policy</span></span>
<span data-ttu-id="b0e88-103">Tento příklad ukazuje způsob použití <xref:System.Workflow.Activities.PolicyActivity> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b0e88-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="b0e88-104">Sekvenční pracovní postup v této ukázce se vytvoří pomocí <xref:System.Workflow.Activities.PolicyActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b0e88-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="b0e88-105">Pracovní postup definuje `orderValue`, `customerType`, a `discount` pole, která se používají k definování produktu slevy pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b0e88-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="b0e88-106">Z pravidel definovaných v souboru pravidel nastavení, která je založena na hodnoty slevy `orderValue` a `customerType`.</span><span class="sxs-lookup"><span data-stu-id="b0e88-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="b0e88-107">`orderValue` a `customerType` jsou nastaveny `SimplePolicyWorkflow` definici třídy a změnit chování lze změnit.</span><span class="sxs-lookup"><span data-stu-id="b0e88-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="b0e88-108">Výsledný slevy je zapsán v konzole <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obslužná rutina události, která je definována v `SimplePolicyWorkflow` třídy.</span><span class="sxs-lookup"><span data-stu-id="b0e88-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="b0e88-109">K vytvoření vzorku</span><span class="sxs-lookup"><span data-stu-id="b0e88-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="b0e88-110">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0e88-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0e88-111">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b0e88-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b0e88-112">Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b0e88-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="b0e88-113">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b0e88-113">To run the sample</span></span>  
  
-   <span data-ttu-id="b0e88-114">V okně příkazového řádku sady SDK spusťte soubor .exe ve složce SimplePolicy\bin\debug (nebo ve složce SimplePolicy\bin pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="b0e88-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0e88-115">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b0e88-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b0e88-116">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="b0e88-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0e88-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b0e88-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0e88-118">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="b0e88-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="b0e88-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0e88-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="b0e88-120">Pokročilé zásady</span><span class="sxs-lookup"><span data-stu-id="b0e88-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
