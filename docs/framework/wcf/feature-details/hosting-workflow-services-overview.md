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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c38cd352eb860982b9b1e3aa32daa7aeeee9ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="56dae-102">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="56dae-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="56dae-103">K provedení musí být hostované služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="56dae-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="56dae-104"><xref:System.ServiceModel.WorkflowServiceHost> Je hostitel pracovního postupu se na pole, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou vyžaduje použití zasílání zpráv aby bylo možné hostovat pracovních postupů).</span><span class="sxs-lookup"><span data-stu-id="56dae-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="56dae-105">Je integrován se sadou trvalost, sledování a řízení instance pomocí sady chování služby.</span><span class="sxs-lookup"><span data-stu-id="56dae-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="56dae-106">Stejně jako na WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete samoobslužně hostovaná v žádné spravované aplikace .NET nebo webové hostované (jako soubor .xamlx) ve službě IIS / byla.</span><span class="sxs-lookup"><span data-stu-id="56dae-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="56dae-107">Témata v této části popisují, jak k hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56dae-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56dae-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="56dae-108">In This Section</span></span>  
 [<span data-ttu-id="56dae-109">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="56dae-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="56dae-110">Popisuje hostování služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="56dae-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="56dae-111">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="56dae-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="56dae-112">Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracuje příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="56dae-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="56dae-113">Rozšíření hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="56dae-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="56dae-114">Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56dae-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="56dae-115">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="56dae-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="56dae-116">Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="56dae-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="56dae-117">Postupy: hostování bez služby pracovního postupu ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="56dae-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="56dae-118">Demonstruje hostování pracovní postup, který není služby pracovního postupu ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="56dae-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="56dae-119">Postupy: hostování služby pracovního postupu pomocí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="56dae-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="56dae-120">Ukazuje, jak k hostování služby pracovního postupu existující v systému Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="56dae-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="56dae-121">Konfigurace třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="56dae-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="56dae-122">Popisuje, jak řídit trvalost, sledování chování nečinnosti a neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="56dae-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="56dae-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="56dae-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="56dae-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="56dae-124">Related Sections</span></span>  
 [<span data-ttu-id="56dae-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="56dae-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
