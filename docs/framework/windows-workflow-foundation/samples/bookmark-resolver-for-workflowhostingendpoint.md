---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: e5a8adc73ba08007802eeb3b66de27098c688d84
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044331"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="fc5da-102">Překladač záložek pro WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="fc5da-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="fc5da-103">Tato ukázka předvádí, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fc5da-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fc5da-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="fc5da-104">Demonstrates</span></span>  
 <span data-ttu-id="fc5da-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="fc5da-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="fc5da-106">Účely</span><span class="sxs-lookup"><span data-stu-id="fc5da-106">Discussion</span></span>  
 <span data-ttu-id="fc5da-107">Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instancí pracovního postupu hostovaných <xref:System.ServiceModel.Activities.WorkflowServiceHost>pomocí.</span><span class="sxs-lookup"><span data-stu-id="fc5da-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="fc5da-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který může být použit v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="fc5da-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="fc5da-109">Vytváření nových instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fc5da-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="fc5da-110">Obnovování záložek v instanci pracovního postupu hostované <xref:System.ServiceModel.Activities.WorkflowServiceHost>v.</span><span class="sxs-lookup"><span data-stu-id="fc5da-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="fc5da-111">Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID.</span><span class="sxs-lookup"><span data-stu-id="fc5da-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="fc5da-112">Ukázková Konzolová aplikace vytvoří <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí pracovního postupu a `CreationEndpoint` přidá ji do hostitele.</span><span class="sxs-lookup"><span data-stu-id="fc5da-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="fc5da-113">Pak zavolá `Create` operaci na koncovém bodu a vytvoří novou instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fc5da-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc5da-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="fc5da-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc5da-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="fc5da-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="fc5da-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc5da-116">Run the application.</span></span> <span data-ttu-id="fc5da-117">`CreationEndpoint` Konzola zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fc5da-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="fc5da-118">Zpráva "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="fc5da-118">The message "Hello World!"</span></span> <span data-ttu-id="fc5da-119">je vytištěna instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fc5da-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc5da-120">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="fc5da-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc5da-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="fc5da-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fc5da-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="fc5da-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc5da-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fc5da-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
