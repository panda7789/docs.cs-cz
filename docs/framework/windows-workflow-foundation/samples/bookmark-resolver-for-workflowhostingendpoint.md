---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142807"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="c7994-102">Překladač záložek pro WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="c7994-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="c7994-103">Tato ukázka ukazuje, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak <xref:System.ServiceModel.Activities.WorkflowServiceHost> lze použít s k vytvoření instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7994-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c7994-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="c7994-104">Demonstrates</span></span>  
 <span data-ttu-id="c7994-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="c7994-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c7994-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="c7994-106">Discussion</span></span>  
 <span data-ttu-id="c7994-107">Tato ukázka <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> používá k vytvoření instancí pracovního postupu hostovaných pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>aplikace .</span><span class="sxs-lookup"><span data-stu-id="c7994-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="c7994-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který lze použít v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="c7994-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="c7994-109">Vytváření nových instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7994-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="c7994-110">Obnovení záložek v instanci pracovního postupu hostované v aplikaci <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c7994-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="c7994-111">Ukázkový koncový bod, který je součástí zpřístupňuje smlouvu, která poskytuje operace k vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID.</span><span class="sxs-lookup"><span data-stu-id="c7994-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="c7994-112">Ukázková konzolová <xref:System.ServiceModel.Activities.WorkflowServiceHost> aplikace vytvoří instanci `CreationEndpoint` s definicí pracovního postupu a přidá a k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c7994-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="c7994-113">Potom volá `Create` operaci v koncovém bodě k vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7994-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7994-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c7994-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c7994-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="c7994-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="c7994-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c7994-116">Run the application.</span></span> <span data-ttu-id="c7994-117">Konzola `CreationEndpoint` zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7994-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="c7994-118">Zpráva "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c7994-118">The message "Hello World!"</span></span> <span data-ttu-id="c7994-119">je vytištěna instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c7994-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7994-120">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c7994-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7994-121">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c7994-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c7994-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7994-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7994-123">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c7994-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
