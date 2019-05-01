---
title: Vytvoření a spuštění instance pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: f2bdfce0b311da6dd20aac5e0fe4f5fbcd14f68a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005300"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="43c35-102">Vytvoření a spuštění instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="43c35-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="43c35-103">Tento příklad ukazuje, jak spustit instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="43c35-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="43c35-104">Ukazuje, jak k jeho provedení synchronního a asynchronního.</span><span class="sxs-lookup"><span data-stu-id="43c35-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="43c35-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="43c35-105">Demonstrates</span></span>  
 <span data-ttu-id="43c35-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="43c35-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="43c35-107">Diskuse</span><span class="sxs-lookup"><span data-stu-id="43c35-107">Discussion</span></span>  
 <span data-ttu-id="43c35-108">První část Ukázka používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="43c35-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="43c35-109">Toto je nejzákladnější možnost pro spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="43c35-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="43c35-110">Pracovní postupy provést s <xref:System.Activities.WorkflowInvoker.Invoke%2A> provádějí synchronně.</span><span class="sxs-lookup"><span data-stu-id="43c35-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="43c35-111">Druhá část Ukázka používá <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="43c35-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="43c35-112"><xref:System.Activities.WorkflowApplication> umožňuje mít větší kontrolu nad každou instanci, včetně možnosti pro interakci s běžícím workflowem a pracovní postup spouští asynchronně.</span><span class="sxs-lookup"><span data-stu-id="43c35-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43c35-113">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="43c35-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43c35-114">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="43c35-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43c35-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="43c35-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43c35-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="43c35-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="43c35-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43c35-117">See also</span></span>

- [<span data-ttu-id="43c35-118">Použití WorkflowInvoker a WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="43c35-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
