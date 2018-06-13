---
title: Vytváření a spouštění instanci pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 3bfcde3dd635820fa66d639134a43e5e43186c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513683"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="a794b-102">Vytváření a spouštění instanci pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a794b-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="a794b-103">Tento příklad ukazuje, jak spustit instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a794b-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="a794b-104">Ukazuje, jak provést synchronně a asynchronně.</span><span class="sxs-lookup"><span data-stu-id="a794b-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a794b-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="a794b-105">Demonstrates</span></span>  
 <span data-ttu-id="a794b-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="a794b-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a794b-107">Diskusní</span><span class="sxs-lookup"><span data-stu-id="a794b-107">Discussion</span></span>  
 <span data-ttu-id="a794b-108">První část vzorku používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="a794b-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="a794b-109">To je nejzákladnější způsob k provedení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a794b-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="a794b-110">Pracovní postupy provést s <xref:System.Activities.WorkflowInvoker.Invoke%2A> jsou spouštěny synchronně.</span><span class="sxs-lookup"><span data-stu-id="a794b-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="a794b-111">Druhá část vzorku používá <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="a794b-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="a794b-112"><xref:System.Activities.WorkflowApplication> umožňuje mít větší kontrolu nad každou instanci, včetně možnosti pro interakci s běžícím workflowem a asynchronně spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a794b-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a794b-113">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a794b-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a794b-114">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a794b-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a794b-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a794b-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a794b-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a794b-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="a794b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a794b-117">See Also</span></span>  
 [<span data-ttu-id="a794b-118">Použití WorkflowInvoker a WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="a794b-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
