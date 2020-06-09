---
title: Služby pracovních postupů
ms.date: 03/30/2017
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
ms.openlocfilehash: c7a5c6245702497fcd75341b3ff7ba08dc190fa5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600124"
---
# <a name="workflow-services"></a><span data-ttu-id="2b0cf-102">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2b0cf-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="2b0cf-103">umožňuje plně popsat službu založenou na pracovních postupech deklarativně v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-103">allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="2b0cf-104">Můžete definovat pracovní postup, který implementuje vaši službu, a popsat koncové body, které služba zpřístupňuje, zcela v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="2b0cf-105">Témata v této části podrobně popisují programovací model, který podporuje deklarativní zápis služeb.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b0cf-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2b0cf-106">In This Section</span></span>  
 [<span data-ttu-id="2b0cf-107">Služby pracovních postupů – přehled</span><span class="sxs-lookup"><span data-stu-id="2b0cf-107">Workflow Services Overview</span></span>](workflow-services-overview.md)  
 <span data-ttu-id="2b0cf-108">Popisuje komponenty, které jsou součástí vytváření a hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="2b0cf-109">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="2b0cf-109">Messaging Activities</span></span>](messaging-activities.md)  
 <span data-ttu-id="2b0cf-110">Popisuje aktivity, které umožňují pracovním postupům odesílat a přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="2b0cf-111">Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="2b0cf-111">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="2b0cf-112">Popisuje, jak používat aktivity zasílání zpráv k vytvoření služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="2b0cf-113">Postupy: Přístup ke službě z aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2b0cf-113">How To: Access a Service From a Workflow Application</span></span>](how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="2b0cf-114">Popisuje, jak volat službu z aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="2b0cf-115">Korelace</span><span class="sxs-lookup"><span data-stu-id="2b0cf-115">Correlation</span></span>](correlation.md)  
 <span data-ttu-id="2b0cf-116">Popisuje, jak korelace mapuje zprávy mezi sebou a instancemi.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="2b0cf-117">Zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="2b0cf-117">Out-of-Order Message Processing</span></span>](out-of-order-message-processing.md)  
 <span data-ttu-id="2b0cf-118">V této části najdete popis konfigurace služby pro přijímání zpráv mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="2b0cf-119">Nasazení služby pracovního postupu s upřednostněním kontraktu</span><span class="sxs-lookup"><span data-stu-id="2b0cf-119">Contract First Workflow Service Development</span></span>](../../windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="2b0cf-120">Popisuje vytvoření služby pracovního postupu založeného na stávající kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-120">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="2b0cf-121">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="2b0cf-121">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="2b0cf-122">V této části najdete podrobný příklad vytvoření služby pracovního postupu pomocí existující smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-122">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="2b0cf-123">Přehled hostování služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2b0cf-123">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)  
 <span data-ttu-id="2b0cf-124">Popisuje různé aspekty hostování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-124">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="2b0cf-125">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="2b0cf-125">Using Contracts in Workflow</span></span>](using-contracts-in-workflow.md)  
 <span data-ttu-id="2b0cf-126">Popisuje různé typy kontraktů a odvození smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2b0cf-126">Describes the different types of contracts and contract inference.</span></span>
