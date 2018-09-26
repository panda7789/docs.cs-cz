---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208427"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="75c21-102">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="75c21-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="75c21-103">Ke spuštění musí být hostovaný služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="75c21-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="75c21-104"><xref:System.ServiceModel.WorkflowServiceHost> Je hostitele pracovního postupu out-of-the-box, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou potřeba použít zasílání aby bylo možné hostovat pracovních postupů).</span><span class="sxs-lookup"><span data-stu-id="75c21-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="75c21-105">Je integrován se sadou trvalost, sledování a řízení instance prostřednictvím sady chování služby.</span><span class="sxs-lookup"><span data-stu-id="75c21-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="75c21-106">Stejně jako jeho WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete ve všech spravovaných aplikací .NET v místním prostředí nebo web hostované (jako soubor .xamlx) ve službě IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="75c21-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="75c21-107">Témata v této části popisují, jak k hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75c21-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75c21-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="75c21-108">In This Section</span></span>  
 [<span data-ttu-id="75c21-109">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="75c21-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="75c21-110">Popisuje hostování služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="75c21-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="75c21-111">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75c21-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="75c21-112">Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="75c21-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="75c21-113">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75c21-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="75c21-114">Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75c21-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="75c21-115">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75c21-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="75c21-116">Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75c21-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="75c21-117">Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="75c21-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="75c21-118">Ukazuje, jak hostovat existující služby pracovního postupu v systému Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="75c21-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="75c21-119">Konfigurace třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="75c21-119">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="75c21-120">Popisuje, jak řídit trvalost, sledování, nečinnosti a neošetřené výjimky chování.</span><span class="sxs-lookup"><span data-stu-id="75c21-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="75c21-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="75c21-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="75c21-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="75c21-122">Related Sections</span></span>  
 [<span data-ttu-id="75c21-123">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="75c21-123">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
