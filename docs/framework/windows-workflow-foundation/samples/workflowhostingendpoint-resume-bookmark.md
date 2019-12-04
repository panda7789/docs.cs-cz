---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3b3c7d40a70e797960837c82e2f5a08b2814e17f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710964"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="9942f-102">Záložka pro obnovení WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="9942f-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="9942f-103">Tato ukázka předvádí, jak lze <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytváření instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9942f-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9942f-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="9942f-104">Demonstrates</span></span>  
 <span data-ttu-id="9942f-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint><xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="9942f-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9942f-106">Účely</span><span class="sxs-lookup"><span data-stu-id="9942f-106">Discussion</span></span>  
 <span data-ttu-id="9942f-107">Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostovaného pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9942f-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="9942f-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšíření pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>, který se dá použít v těchto scénářích:</span><span class="sxs-lookup"><span data-stu-id="9942f-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="9942f-109">Vytváření nových instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9942f-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="9942f-110">Obnovování záložek v instanci pracovního postupu hostované ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9942f-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="9942f-111">Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrácení ID instance nebo vytvoření instance s určitým ID.</span><span class="sxs-lookup"><span data-stu-id="9942f-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="9942f-112">Ukázková Konzolová aplikace vytvoří instanci <xref:System.ServiceModel.Activities.WorkflowServiceHost> se základní definicí pracovního postupu a přidá `CreationEndpoint` k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="9942f-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="9942f-113">Pak na koncovém bodu zavolá operaci `Create` a vytvoří novou instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9942f-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9942f-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9942f-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9942f-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="9942f-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="9942f-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9942f-116">Run the application.</span></span> <span data-ttu-id="9942f-117">Konzola `CreationEndpoint` zobrazuje zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9942f-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="9942f-118">Zpráva "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9942f-118">The message "Hello World!"</span></span> <span data-ttu-id="9942f-119">je vytištěn pracovním postupem po úspěšném obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="9942f-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9942f-120">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9942f-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9942f-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9942f-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9942f-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="9942f-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9942f-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9942f-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
