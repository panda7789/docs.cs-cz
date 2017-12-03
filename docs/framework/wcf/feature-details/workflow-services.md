---
title: "Služby pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043aa541e32077faf8141701a5ec7e8c0e711959
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-services"></a><span data-ttu-id="bd665-102">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bd665-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="bd665-103">umožňuje plně popisují služby založené na pracovním postupu deklarativně v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="bd665-103"> allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="bd665-104">Můžete definovat pracovní postup, který implementuje služby a popisují koncové body služby zpřístupní všechny zcela v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="bd665-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="bd665-105">Témata v této části popisují podrobně, programovací model, který podporuje psaní služby deklarativně.</span><span class="sxs-lookup"><span data-stu-id="bd665-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd665-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bd665-106">In This Section</span></span>  
 [<span data-ttu-id="bd665-107">Přehled služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bd665-107">Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services-overview.md)  
 <span data-ttu-id="bd665-108">Popisuje vytvoření a hostování služby pracovního postupu součásti.</span><span class="sxs-lookup"><span data-stu-id="bd665-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="bd665-109">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="bd665-109">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 <span data-ttu-id="bd665-110">Popisuje aktivity, které umožňují pracovní postupy a odesílat a přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="bd665-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="bd665-111">Postupy: vytvoření služby pracovního postupu se aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="bd665-111">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="bd665-112">Popisuje, jak zasílání zpráv aktivity použít k vytvoření služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bd665-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="bd665-113">Postupy: Přístup ke službě z aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bd665-113">How To: Access a Service From a Workflow Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="bd665-114">Popisuje, jak volat službu z aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bd665-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="bd665-115">Korelace</span><span class="sxs-lookup"><span data-stu-id="bd665-115">Correlation</span></span>](../../../../docs/framework/wcf/feature-details/correlation.md)  
 <span data-ttu-id="bd665-116">Popisuje, jak mapuje korelace zprávy mezi sebou a instancí.</span><span class="sxs-lookup"><span data-stu-id="bd665-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="bd665-117">Zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="bd665-117">Out-of-Order Message Processing</span></span>](../../../../docs/framework/wcf/feature-details/out-of-order-message-processing.md)  
 <span data-ttu-id="bd665-118">Popisuje konfiguraci služby pro příjem zpráv mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="bd665-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="bd665-119">Postupy: vytvoření služby pracovního postupu, který volá jinou službu pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bd665-119">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 <span data-ttu-id="bd665-120">Popisuje, jak synchronně volání služby pracovního postupu z v rámci jiného pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="bd665-120">Describes how to synchronously call a workflow service from within another workflow service.</span></span>  
  
 [<span data-ttu-id="bd665-121">Vývoj kontrakt první pracovní postup služby</span><span class="sxs-lookup"><span data-stu-id="bd665-121">Contract First Workflow Service Development</span></span>](../../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="bd665-122">Popisuje vytvoření pracovního postupu služby založené na existující službu smlouvy.</span><span class="sxs-lookup"><span data-stu-id="bd665-122">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="bd665-123">Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby</span><span class="sxs-lookup"><span data-stu-id="bd665-123">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="bd665-124">Poskytuje podrobný příklad vytvoření pracovního postupu služby pomocí existující smlouvy služby.</span><span class="sxs-lookup"><span data-stu-id="bd665-124">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="bd665-125">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bd665-125">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 <span data-ttu-id="bd665-126">Popisuje různé aspekty hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bd665-126">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="bd665-127">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="bd665-127">Using Contracts in Workflow</span></span>](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  
 <span data-ttu-id="bd665-128">Popisuje různé typy smluv a odvození kontrakt.</span><span class="sxs-lookup"><span data-stu-id="bd665-128">Describes the different types of contracts and contract inference.</span></span>
