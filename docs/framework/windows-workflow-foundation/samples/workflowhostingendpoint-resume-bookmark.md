---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3c1a3421c87d18e695790cfb3a1f066600748ce9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619510"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="97800-102">Záložka pro obnovení WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="97800-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="97800-103">Tato ukázka předvádí, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jde použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="97800-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="97800-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="97800-104">Demonstrates</span></span>  
 <span data-ttu-id="97800-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="97800-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="97800-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="97800-106">Discussion</span></span>  
 <span data-ttu-id="97800-107">Tento příklad používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="97800-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="97800-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> představuje rozšíření bod pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> , který lze použít v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="97800-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="97800-109">Vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="97800-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="97800-110">Obnovení záložky pro instanci pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="97800-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="97800-111">Ukázka koncového bodu, který je součástí zpřístupňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vracet ID instance, nebo vytvořit instanci s konkrétním ID.</span><span class="sxs-lookup"><span data-stu-id="97800-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="97800-112">Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance s definicí základní pracovní postup a přidá `CreationEndpoint` k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="97800-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="97800-113">Poté zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="97800-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="97800-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="97800-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="97800-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="97800-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="97800-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="97800-116">Run the application.</span></span> <span data-ttu-id="97800-117">`CreationEndpoint` Konzoly zobrazuje zprávu, která obsahuje instance ID, když je vytvořena instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="97800-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="97800-118">Zprávu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="97800-118">The message "Hello World!"</span></span> <span data-ttu-id="97800-119">je vytištěna v pracovním postupu na úspěšné obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="97800-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97800-120">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="97800-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="97800-121">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="97800-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="97800-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="97800-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97800-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="97800-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
