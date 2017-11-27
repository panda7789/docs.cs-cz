---
title: "Koncové body Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ac3d1f16d860ea01217d0d1d35d0588da0c8d87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="6ab76-102">Koncové body Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6ab76-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="6ab76-103">Veškerá komunikace s [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="6ab76-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="6ab76-104">Koncové body poskytují klientům přístup k funkcím, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nabídky služeb.</span><span class="sxs-lookup"><span data-stu-id="6ab76-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="6ab76-105">Přehled o tom, jak vytvořit koncový bod, najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6ab76-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="6ab76-106">Každý koncový bod obsahuje:</span><span class="sxs-lookup"><span data-stu-id="6ab76-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="6ab76-107">Adresa, která určuje, kde najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6ab76-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="6ab76-108">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="6ab76-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="6ab76-109">Kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="6ab76-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="6ab76-110">Popis o tom, jak určit tyto jednotlivé části koncový bod najdete v tématu:</span><span class="sxs-lookup"><span data-stu-id="6ab76-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="6ab76-111">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="6ab76-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="6ab76-112">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6ab76-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="6ab76-113">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="6ab76-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="6ab76-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6ab76-114">In This Section</span></span>  
 [<span data-ttu-id="6ab76-115">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="6ab76-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="6ab76-116">Popisuje strukturu koncový bod a také ukazuje, jak definovat koncový bod v konfiguraci a v kódu, jak používat výchozí koncové body, vazby a chování poskytované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="6ab76-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="6ab76-117">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="6ab76-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="6ab76-118">Popisuje, jak komunikaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby dojde k prostřednictvím koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="6ab76-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="6ab76-119">Postupy: vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6ab76-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="6ab76-120">Demonstruje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6ab76-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="6ab76-121">Postupy: vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="6ab76-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="6ab76-122">Demonstruje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="6ab76-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="6ab76-123">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="6ab76-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="6ab76-124">Demonstruje postup publikování metadat pomocí publikování kocových bodů metadat v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="6ab76-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ab76-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="6ab76-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="6ab76-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6ab76-126">Related Sections</span></span>  
 [<span data-ttu-id="6ab76-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="6ab76-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
