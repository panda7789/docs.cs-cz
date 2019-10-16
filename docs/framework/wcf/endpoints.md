---
title: Koncové body Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: f11a8198d38a01fe27a84a3e613e1ff066c25b9d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319915"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="9bf72-102">Koncové body Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9bf72-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="9bf72-103">Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím *koncových bodů* služby.</span><span class="sxs-lookup"><span data-stu-id="9bf72-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="9bf72-104">Koncové body poskytují klientům přístup k funkcím, které služba WCF nabízí.</span><span class="sxs-lookup"><span data-stu-id="9bf72-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="9bf72-105">Přehled o tom, jak vytvořit koncový bod, najdete v tématu [Přehled vytváření koncových bodů](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9bf72-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="9bf72-106">Každý koncový bod obsahuje:</span><span class="sxs-lookup"><span data-stu-id="9bf72-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="9bf72-107">Adresa, která indikuje, kde se má koncový bod najít.</span><span class="sxs-lookup"><span data-stu-id="9bf72-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="9bf72-108">Vazba, která určuje, jak klient může komunikovat s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="9bf72-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="9bf72-109">Kontrakt, který identifikuje dostupné metody.</span><span class="sxs-lookup"><span data-stu-id="9bf72-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="9bf72-110">Popisy, jak zadat tyto jednotlivé části koncového bodu, najdete v tématech:</span><span class="sxs-lookup"><span data-stu-id="9bf72-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="9bf72-111">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="9bf72-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="9bf72-112">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9bf72-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="9bf72-113">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="9bf72-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="9bf72-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9bf72-114">In This Section</span></span>  
 [<span data-ttu-id="9bf72-115">Přehled vytváření koncových bodů</span><span class="sxs-lookup"><span data-stu-id="9bf72-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="9bf72-116">Popisuje strukturu koncového bodu a popisuje, jak definovat koncový bod v konfiguraci a v kódu, a jak používat výchozí koncové body, vazby a chování poskytované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="9bf72-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="9bf72-117">Zadání adresy koncového bodu</span><span class="sxs-lookup"><span data-stu-id="9bf72-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="9bf72-118">Popisuje, jak probíhá komunikace se službou WCF prostřednictvím koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="9bf72-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="9bf72-119">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="9bf72-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="9bf72-120">Ukazuje, jak vytvořit koncový bod služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="9bf72-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="9bf72-121">Postupy: Vytvoření koncového bodu služby v kódu</span><span class="sxs-lookup"><span data-stu-id="9bf72-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="9bf72-122">Ukazuje, jak vytvořit koncový bod služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="9bf72-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="9bf72-123">Publikování koncových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="9bf72-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="9bf72-124">Ukazuje, jak publikovat metadata publikováním koncových bodů metadat v konfiguraci a v kódu.</span><span class="sxs-lookup"><span data-stu-id="9bf72-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9bf72-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9bf72-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="9bf72-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9bf72-126">Related Sections</span></span>  
 [<span data-ttu-id="9bf72-127">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="9bf72-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
