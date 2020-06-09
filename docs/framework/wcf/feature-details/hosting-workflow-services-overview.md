---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 10ea35fc1988e1b3e6ceb44aca098e63bfc7d7e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597290"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="b14e5-102">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b14e5-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="b14e5-103">Aby bylo možné spustit službu pracovního postupu, je nutné ji hostovat.</span><span class="sxs-lookup"><span data-stu-id="b14e5-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="b14e5-104">Je předem připravený <xref:System.ServiceModel.WorkflowServiceHost> hostitel pracovního postupu, který podporuje více instancí, konfigurací a zasílání zpráv WCF (i když pracovní postupy nevyžadují, aby používaly zasílání zpráv, aby bylo možné je hostovat).</span><span class="sxs-lookup"><span data-stu-id="b14e5-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="b14e5-105">Integruje se taky se zachováním, sledováním a instancí prostřednictvím sady chování služby.</span><span class="sxs-lookup"><span data-stu-id="b14e5-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="b14e5-106">Stejně jako v případě WCF se může v rámci <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> služby IIS/was hostovat v jakékoli spravované aplikaci .NET nebo v hostovaném webovém prostředí (jako soubor. xamlx).</span><span class="sxs-lookup"><span data-stu-id="b14e5-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="b14e5-107">Témata v této části popisují, jak hostovat službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b14e5-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b14e5-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b14e5-108">In This Section</span></span>  
 [<span data-ttu-id="b14e5-109">Hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b14e5-109">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="b14e5-110">Popisuje služby hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b14e5-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="b14e5-111">Interní informace o hostiteli služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b14e5-111">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="b14e5-112">Popisuje způsob <xref:System.ServiceModel.WorkflowServiceHost> zpracování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="b14e5-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="b14e5-113">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b14e5-113">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="b14e5-114">V této části najdete popis postupu rozšiřování funkcí hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b14e5-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="b14e5-115">Kontrolní koncový bod pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b14e5-115">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="b14e5-116">Popisuje, jak definovat koncový bod, který umožňuje vytvářet instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b14e5-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="b14e5-117">Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b14e5-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="b14e5-118">Ukazuje, jak hostovat existující službu pracovního postupu ve Windows Server App Fabric.</span><span class="sxs-lookup"><span data-stu-id="b14e5-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="b14e5-119">Konfigurace třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="b14e5-119">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="b14e5-120">Popisuje, jak řídit chování při persistenci, sledování, nečinnosti a neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b14e5-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b14e5-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="b14e5-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="b14e5-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b14e5-122">Related Sections</span></span>  
 [<span data-ttu-id="b14e5-123">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b14e5-123">Workflow Services</span></span>](workflow-services.md)
