---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 017c5f959ed109ffe9b5e5c4bf2b9de9d04fdcdb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964942"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="49955-102">Překladač záložek pro WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="49955-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="49955-103">Tato ukázka předvádí, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49955-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="49955-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="49955-104">Demonstrates</span></span>  
 <span data-ttu-id="49955-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="49955-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="49955-106">Účely</span><span class="sxs-lookup"><span data-stu-id="49955-106">Discussion</span></span>  
 <span data-ttu-id="49955-107">Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instancí pracovního postupu hostovaných <xref:System.ServiceModel.Activities.WorkflowServiceHost>pomocí.</span><span class="sxs-lookup"><span data-stu-id="49955-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="49955-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který může být použit v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="49955-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="49955-109">Vytváření nových instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49955-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="49955-110">Obnovování záložek v instanci pracovního postupu hostované <xref:System.ServiceModel.Activities.WorkflowServiceHost>v.</span><span class="sxs-lookup"><span data-stu-id="49955-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="49955-111">Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID.</span><span class="sxs-lookup"><span data-stu-id="49955-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="49955-112">Ukázková Konzolová aplikace vytvoří <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí pracovního postupu a `CreationEndpoint` přidá ji do hostitele.</span><span class="sxs-lookup"><span data-stu-id="49955-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="49955-113">Pak zavolá `Create` operaci na koncovém bodu a vytvoří novou instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49955-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49955-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="49955-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="49955-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="49955-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="49955-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49955-116">Run the application.</span></span> <span data-ttu-id="49955-117">`CreationEndpoint` Konzola zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49955-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="49955-118">Zpráva "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="49955-118">The message "Hello World!"</span></span> <span data-ttu-id="49955-119">je vytištěna instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49955-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="49955-120">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="49955-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49955-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="49955-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49955-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="49955-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49955-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="49955-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
