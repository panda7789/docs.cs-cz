---
title: '&lt;wsdlImporters&gt;'
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: aa07bb2af0c448c08908902f1243d152d16daded
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705914"
---
# <a name="ltwsdlimportersgt"></a><span data-ttu-id="82e72-102">&lt;wsdlImporters&gt;</span><span class="sxs-lookup"><span data-stu-id="82e72-102">&lt;wsdlImporters&gt;</span></span>
<span data-ttu-id="82e72-103">Tento prvek konfigurace určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="82e72-103">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="82e72-104">Každý podřízený prvek je <`wsdlImporter`>, která určuje způsob, jak importovat metadata a také převést tyto informace do různých tříd, které představují informace o smlouvě a koncový bod.</span><span class="sxs-lookup"><span data-stu-id="82e72-104">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="82e72-105">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="82e72-105">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="82e72-106">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="82e72-106">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e72-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e72-107">See also</span></span>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="82e72-108">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="82e72-108">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="82e72-109">Klienti</span><span class="sxs-lookup"><span data-stu-id="82e72-109">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
