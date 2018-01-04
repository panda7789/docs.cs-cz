---
title: "Přehled hostování služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06012da95660fb4dc20d034c2d1691afad12037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="fa96c-102">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fa96c-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="fa96c-103">K provedení musí být hostované služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fa96c-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="fa96c-104"><xref:System.ServiceModel.WorkflowServiceHost> Je hostitel pracovního postupu se na pole, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou vyžaduje použití zasílání zpráv aby bylo možné hostovat pracovních postupů).</span><span class="sxs-lookup"><span data-stu-id="fa96c-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="fa96c-105">Je integrován se sadou trvalost, sledování a řízení instance pomocí sady chování služby.</span><span class="sxs-lookup"><span data-stu-id="fa96c-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="fa96c-106">Stejně jako na WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete samoobslužně hostovaná v žádné spravované aplikace .NET nebo webové hostované (jako soubor .xamlx) ve službě IIS / byla.</span><span class="sxs-lookup"><span data-stu-id="fa96c-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="fa96c-107">Témata v této části popisují, jak k hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fa96c-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa96c-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fa96c-108">In This Section</span></span>  
 [<span data-ttu-id="fa96c-109">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fa96c-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="fa96c-110">Popisuje hostování služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fa96c-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="fa96c-111">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fa96c-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="fa96c-112">Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracuje příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa96c-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="fa96c-113">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fa96c-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="fa96c-114">Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fa96c-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="fa96c-115">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fa96c-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="fa96c-116">Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fa96c-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="fa96c-117">Postupy: Hostování pracovního postupu v IIS, který není součástí služby</span><span class="sxs-lookup"><span data-stu-id="fa96c-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="fa96c-118">Demonstruje hostování pracovní postup, který není služby pracovního postupu ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="fa96c-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="fa96c-119">Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="fa96c-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="fa96c-120">Ukazuje, jak k hostování služby pracovního postupu existující v systému Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="fa96c-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="fa96c-121">Konfigurace třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="fa96c-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="fa96c-122">Popisuje, jak řídit trvalost, sledování chování nečinnosti a neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="fa96c-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa96c-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fa96c-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="fa96c-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fa96c-124">Related Sections</span></span>  
 [<span data-ttu-id="fa96c-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fa96c-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
