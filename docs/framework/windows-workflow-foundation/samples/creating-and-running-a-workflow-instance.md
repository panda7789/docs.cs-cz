---
title: Vytvoření a spuštění instance pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715194"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="41ee8-102">Vytvoření a spuštění instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="41ee8-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="41ee8-103">V této ukázce se dozvíte, jak spustit instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="41ee8-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="41ee8-104">Ukazuje, jak ho spustit synchronně a asynchronně.</span><span class="sxs-lookup"><span data-stu-id="41ee8-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="41ee8-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="41ee8-105">Demonstrates</span></span>

<span data-ttu-id="41ee8-106"><xref:System.Activities.WorkflowInvoker><xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="41ee8-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="41ee8-107">Účely</span><span class="sxs-lookup"><span data-stu-id="41ee8-107">Discussion</span></span>

<span data-ttu-id="41ee8-108">První část ukázky používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="41ee8-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="41ee8-109">Toto je nejzákladnější způsob, jak spustit pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="41ee8-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="41ee8-110">Pracovní postupy spouštěné pomocí <xref:System.Activities.WorkflowInvoker.Invoke%2A> jsou spouštěny synchronně.</span><span class="sxs-lookup"><span data-stu-id="41ee8-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="41ee8-111">Druhá část ukázky používá třídu <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="41ee8-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="41ee8-112"><xref:System.Activities.WorkflowApplication> vám umožní mít větší kontrolu nad každou instancí, včetně možnosti pracovat se spuštěným pracovním postupem a spustit pracovní postup asynchronně.</span><span class="sxs-lookup"><span data-stu-id="41ee8-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41ee8-113">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="41ee8-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41ee8-114">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="41ee8-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="41ee8-115">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="41ee8-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41ee8-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="41ee8-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="41ee8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41ee8-117">See also</span></span>

- [<span data-ttu-id="41ee8-118">Použití WorkflowInvoker a WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="41ee8-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
