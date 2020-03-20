---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182746"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="b53ac-102">Záložka pro obnovení WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="b53ac-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="b53ac-103">Tato ukázka ukazuje, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak <xref:System.ServiceModel.Activities.WorkflowServiceHost> lze použít s k vytvoření instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b53ac-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b53ac-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="b53ac-104">Demonstrates</span></span>  
 <span data-ttu-id="b53ac-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="b53ac-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b53ac-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="b53ac-106">Discussion</span></span>  
 <span data-ttu-id="b53ac-107">Tato ukázka <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> používá k vytvoření instance <xref:System.ServiceModel.Activities.WorkflowServiceHost>pracovního postupu hostované pomocí .</span><span class="sxs-lookup"><span data-stu-id="b53ac-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b53ac-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který lze použít v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="b53ac-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="b53ac-109">Vytváření nových instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b53ac-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="b53ac-110">Obnovení záložek na instanci pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu hostované v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="b53ac-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b53ac-111">Ukázkový koncový bod, který je součástí zpřístupňuje smlouvu, která poskytuje operace k vytvoření pracovního postupu a vrácení ID instance nebo k vytvoření instance s určitým ID.</span><span class="sxs-lookup"><span data-stu-id="b53ac-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="b53ac-112">Ukázková konzolová <xref:System.ServiceModel.Activities.WorkflowServiceHost> aplikace vytvoří instanci se `CreationEndpoint` základní definicí pracovního postupu a přidá k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="b53ac-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="b53ac-113">Potom volá `Create` operaci v koncovém bodě k vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b53ac-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b53ac-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b53ac-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b53ac-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="b53ac-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="b53ac-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b53ac-116">Run the application.</span></span> <span data-ttu-id="b53ac-117">Konzola `CreationEndpoint` zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b53ac-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="b53ac-118">Zpráva "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="b53ac-118">The message "Hello World!"</span></span> <span data-ttu-id="b53ac-119">je vytištěn pracovním postupem při úspěšném obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="b53ac-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b53ac-120">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="b53ac-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b53ac-121">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b53ac-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b53ac-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b53ac-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b53ac-123">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b53ac-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
