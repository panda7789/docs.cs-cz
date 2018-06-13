---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 7b5de31b5931af13b41b11af6e48a52b5628e27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489557"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="df8e4-102">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="df8e4-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="df8e4-103">K provedení musí být hostované služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="df8e4-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="df8e4-104"><xref:System.ServiceModel.WorkflowServiceHost> Je hostitel pracovního postupu se na pole, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou vyžaduje použití zasílání zpráv aby bylo možné hostovat pracovních postupů).</span><span class="sxs-lookup"><span data-stu-id="df8e4-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="df8e4-105">Je integrován se sadou trvalost, sledování a řízení instance pomocí sady chování služby.</span><span class="sxs-lookup"><span data-stu-id="df8e4-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="df8e4-106">Stejně jako na WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete samoobslužně hostovaná v žádné spravované aplikace .NET nebo webové hostované (jako soubor .xamlx) ve službě IIS / byla.</span><span class="sxs-lookup"><span data-stu-id="df8e4-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="df8e4-107">Témata v této části popisují, jak k hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df8e4-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df8e4-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="df8e4-108">In This Section</span></span>  
 [<span data-ttu-id="df8e4-109">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="df8e4-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="df8e4-110">Popisuje hostování služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="df8e4-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="df8e4-111">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df8e4-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="df8e4-112">Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracuje příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="df8e4-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="df8e4-113">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df8e4-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="df8e4-114">Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df8e4-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="df8e4-115">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df8e4-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="df8e4-116">Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df8e4-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="df8e4-117">Postupy: Hostování pracovního postupu v IIS, který není součástí služby</span><span class="sxs-lookup"><span data-stu-id="df8e4-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="df8e4-118">Demonstruje hostování pracovní postup, který není služby pracovního postupu ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="df8e4-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="df8e4-119">Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="df8e4-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="df8e4-120">Ukazuje, jak k hostování služby pracovního postupu existující v systému Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="df8e4-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="df8e4-121">Konfigurace třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="df8e4-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="df8e4-122">Popisuje, jak řídit trvalost, sledování chování nečinnosti a neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="df8e4-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="df8e4-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="df8e4-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="df8e4-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="df8e4-124">Related Sections</span></span>  
 [<span data-ttu-id="df8e4-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="df8e4-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
