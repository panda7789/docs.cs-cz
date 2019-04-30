---
title: Koncové body Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923185"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="d493b-102">Koncové body Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d493b-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="d493b-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím *koncové body* služby.</span><span class="sxs-lookup"><span data-stu-id="d493b-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="d493b-104">Koncové body poskytují klientům přístup k funkci, která nabízí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d493b-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="d493b-105">Přehled o tom, jak vytvořit koncový bod, najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d493b-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="d493b-106">Každý koncový bod obsahuje:</span><span class="sxs-lookup"><span data-stu-id="d493b-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="d493b-107">Adresu, která označuje, kde najít koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d493b-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="d493b-108">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="d493b-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="d493b-109">Kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="d493b-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="d493b-110">Popisy o způsobech zadávání těchto jednotlivých částí koncový bod, naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="d493b-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="d493b-111">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="d493b-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="d493b-112">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d493b-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="d493b-113">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="d493b-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="d493b-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d493b-114">In This Section</span></span>  
 [<span data-ttu-id="d493b-115">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="d493b-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="d493b-116">Popisuje strukturu koncový bod a také ukazuje, jak definovat koncový bod v konfiguraci a v kódu, jak používat výchozí koncové body, vazby a chování poskytovaný modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d493b-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="d493b-117">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="d493b-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="d493b-118">Popisuje, jak probíhá komunikace se službou WCF prostřednictvím koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d493b-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="d493b-119">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="d493b-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="d493b-120">Popisuje způsob vytvoření koncového bodu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d493b-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="d493b-121">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="d493b-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="d493b-122">Popisuje způsob vytvoření koncového bodu služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="d493b-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="d493b-123">Publikování koncových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="d493b-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="d493b-124">Ukazuje, jak měla být zveřejněna metadata publikováním koncové body metadat v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="d493b-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d493b-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d493b-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="d493b-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d493b-126">Related Sections</span></span>  
 [<span data-ttu-id="d493b-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="d493b-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
