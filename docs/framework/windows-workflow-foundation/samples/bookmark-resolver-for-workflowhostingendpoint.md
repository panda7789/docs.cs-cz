---
title: BOOKMARK překladač pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: f8afb804525ecf36127e32441c92f43af70f5099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514941"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="eac11-102">BOOKMARK překladač pro WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="eac11-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="eac11-103">Tento příklad ukazuje, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eac11-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="eac11-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="eac11-104">Demonstrates</span></span>  
 <span data-ttu-id="eac11-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="eac11-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="eac11-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="eac11-106">Discussion</span></span>  
 <span data-ttu-id="eac11-107">V tomto příkladu <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovních postupů, které jsou hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="eac11-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="eac11-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšiřitelnosti pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> které lze použít v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="eac11-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="eac11-109">Vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eac11-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="eac11-110">Záložky na instanci pracovního postupu obnovení hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="eac11-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="eac11-111">Ukázka koncového bodu, který je součástí zpřístupní kontrakt, který obsahuje operace vytvoření pracovního postupu a vrátí instance ID nebo vytvoří instanci s konkrétním ID.</span><span class="sxs-lookup"><span data-stu-id="eac11-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="eac11-112">Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí pracovního postupu a přidá `CreationEndpoint` na hostitele.</span><span class="sxs-lookup"><span data-stu-id="eac11-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="eac11-113">Potom zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eac11-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eac11-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="eac11-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eac11-115">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="eac11-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="eac11-116">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eac11-116">Run the application.</span></span> <span data-ttu-id="eac11-117">`CreationEndpoint` Konzola zobrazí zprávu, která zahrnuje instance ID při vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eac11-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="eac11-118">Zpráva "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="eac11-118">The message "Hello World!"</span></span> <span data-ttu-id="eac11-119">je tištěné k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eac11-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eac11-120">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="eac11-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eac11-121">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="eac11-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eac11-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="eac11-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eac11-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="eac11-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
