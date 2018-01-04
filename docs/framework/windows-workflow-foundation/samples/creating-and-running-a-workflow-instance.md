---
title: "Vytváření a spouštění instanci pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d6dd2f27a6db9770231a5c947c98614d4f6f175
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="c7761-102">Vytváření a spouštění instanci pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c7761-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="c7761-103">Tento příklad ukazuje, jak spustit instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7761-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="c7761-104">Ukazuje, jak provést synchronně a asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c7761-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c7761-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="c7761-105">Demonstrates</span></span>  
 <span data-ttu-id="c7761-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="c7761-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c7761-107">Diskusní</span><span class="sxs-lookup"><span data-stu-id="c7761-107">Discussion</span></span>  
 <span data-ttu-id="c7761-108">První část vzorku používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7761-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="c7761-109">To je nejzákladnější způsob k provedení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7761-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="c7761-110">Pracovní postupy provést s <xref:System.Activities.WorkflowInvoker.Invoke%2A> jsou spouštěny synchronně.</span><span class="sxs-lookup"><span data-stu-id="c7761-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="c7761-111">Druhá část vzorku používá <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="c7761-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="c7761-112"><xref:System.Activities.WorkflowApplication>umožňuje mít větší kontrolu nad každou instanci, včetně možnosti pro interakci s běžícím workflowem a asynchronně spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7761-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7761-113">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c7761-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7761-114">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c7761-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7761-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7761-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7761-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c7761-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="c7761-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7761-117">See Also</span></span>  
 [<span data-ttu-id="c7761-118">Použití WorkflowInvoker a WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="c7761-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
