---
title: Vytvoření a spuštění instance pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016051"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="b86f4-102">Vytvoření a spuštění instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b86f4-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="b86f4-103">V této ukázce se dozvíte, jak spustit instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b86f4-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="b86f4-104">Ukazuje, jak ho spustit synchronně a asynchronně.</span><span class="sxs-lookup"><span data-stu-id="b86f4-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b86f4-105">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="b86f4-105">Demonstrates</span></span>

<span data-ttu-id="b86f4-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b86f4-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="b86f4-107">Účely</span><span class="sxs-lookup"><span data-stu-id="b86f4-107">Discussion</span></span>

<span data-ttu-id="b86f4-108">První část ukázkového použití <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="b86f4-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="b86f4-109">Toto je nejzákladnější způsob, jak spustit pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="b86f4-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="b86f4-110">Spuštěné pracovní postupy jsou spouštěny synchronně. <xref:System.Activities.WorkflowInvoker.Invoke%2A></span><span class="sxs-lookup"><span data-stu-id="b86f4-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="b86f4-111">Druhá část ukázky používá <xref:System.Activities.WorkflowApplication> třídu.</span><span class="sxs-lookup"><span data-stu-id="b86f4-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b86f4-112"><xref:System.Activities.WorkflowApplication>umožňuje mít větší kontrolu nad každou instancí, včetně možnosti pracovat se spuštěným pracovním postupem a asynchronním spuštěním pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b86f4-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b86f4-113">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b86f4-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b86f4-114">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b86f4-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b86f4-115">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b86f4-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b86f4-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b86f4-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="b86f4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b86f4-117">See also</span></span>

- [<span data-ttu-id="b86f4-118">Použití WorkflowInvoker a WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="b86f4-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
