---
title: Publikování kocových bodů metadat
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121729"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="d0e1a-102">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="d0e1a-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="d0e1a-103">Služby Windows Communication Foundation (WCF) měla být zveřejněna metadata a publikovat jednu nebo víc koncových bodů metadat.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="d0e1a-104">Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o WS-MetadataExchange (MEX) a protokolu HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="d0e1a-105">Koncové body metadat se podobně jako ostatní koncové body služby mají adresa, vazba a kontrakt a je možné je přidat k hostiteli služby prostřednictvím konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="d0e1a-106">Pokud chcete povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služeb chování ve službě.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0e1a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d0e1a-107">In This Section</span></span>  
 [<span data-ttu-id="d0e1a-108">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d0e1a-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="d0e1a-109">Ukazuje, jak nakonfigurovat tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET být zveřejněna metadata služby WCF `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="d0e1a-110">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="d0e1a-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="d0e1a-111">Ukazuje, jak povolit publikování metadat služby WCF v kódu tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="d0e1a-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e1a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0e1a-112">See also</span></span>

- [<span data-ttu-id="d0e1a-113">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="d0e1a-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
