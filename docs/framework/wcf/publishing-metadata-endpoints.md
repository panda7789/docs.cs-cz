---
title: Publikování kocových bodů metadat
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319897"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="62e41-102">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="62e41-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="62e41-103">Služby Windows Communication Foundation (WCF) publikují metadata publikováním jednoho nebo více koncových bodů metadat.</span><span class="sxs-lookup"><span data-stu-id="62e41-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="62e41-104">Publikování metadat služby zpřístupňuje metadata pomocí standardizovaných protokolů, jako jsou WS-MetadataExchange (MEX) a požadavky HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="62e41-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="62e41-105">Koncové body metadat jsou podobné jiným koncovým bodům služby v tom, že mají adresu, vazbu a kontrakt a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="62e41-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="62e41-106">Chcete-li povolit publikování koncových bodů metadat, musíte do služby Přidat chování služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="62e41-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62e41-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="62e41-107">In This Section</span></span>  
 [<span data-ttu-id="62e41-108">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="62e41-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="62e41-109">Ukazuje, jak nakonfigurovat službu WCF pro publikování metadat, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo požadavku HTTP/GET pomocí řetězce dotazu `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="62e41-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="62e41-110">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="62e41-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="62e41-111">Ukazuje, jak povolit publikování metadat pro službu WCF v kódu tak, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo požadavku HTTP/GET pomocí řetězce dotazu `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="62e41-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e41-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62e41-112">See also</span></span>

- [<span data-ttu-id="62e41-113">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="62e41-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
