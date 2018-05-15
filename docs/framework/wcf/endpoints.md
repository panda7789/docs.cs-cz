---
title: Koncové body Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="d92f8-102">Koncové body Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d92f8-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="d92f8-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) dojde k prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="d92f8-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="d92f8-104">Koncové body poskytují klientům přístup k funkci, která nabízí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d92f8-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="d92f8-105">Přehled o tom, jak vytvořit koncový bod, najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d92f8-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="d92f8-106">Každý koncový bod obsahuje:</span><span class="sxs-lookup"><span data-stu-id="d92f8-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="d92f8-107">Adresa, která určuje, kde najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d92f8-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="d92f8-108">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="d92f8-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="d92f8-109">Kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="d92f8-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="d92f8-110">Popis o tom, jak určit tyto jednotlivé části koncový bod najdete v tématu:</span><span class="sxs-lookup"><span data-stu-id="d92f8-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="d92f8-111">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="d92f8-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="d92f8-112">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d92f8-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="d92f8-113">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="d92f8-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="d92f8-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d92f8-114">In This Section</span></span>  
 [<span data-ttu-id="d92f8-115">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="d92f8-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="d92f8-116">Popisuje strukturu koncový bod a také ukazuje, jak definovat koncový bod v konfiguraci a v kódu, jak používat výchozí koncové body, vazby a chování poskytované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d92f8-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="d92f8-117">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="d92f8-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="d92f8-118">Popisuje, jak probíhá komunikace se službou WCF pomocí koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d92f8-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="d92f8-119">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="d92f8-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="d92f8-120">Demonstruje postup vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d92f8-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="d92f8-121">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="d92f8-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="d92f8-122">Demonstruje postup vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="d92f8-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="d92f8-123">Publikování koncových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="d92f8-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="d92f8-124">Demonstruje postup publikování metadat pomocí publikování kocových bodů metadat v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="d92f8-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d92f8-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d92f8-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="d92f8-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d92f8-126">Related Sections</span></span>  
 [<span data-ttu-id="d92f8-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="d92f8-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
