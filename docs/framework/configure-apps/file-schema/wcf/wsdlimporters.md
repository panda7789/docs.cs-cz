---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: 75f88219ab73d321b3e04c140bbfe964aed0b83a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785473"
---
# <a name="wsdlimporters"></a><span data-ttu-id="9d036-101">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="9d036-101">\<wsdlImporters></span></span>
<span data-ttu-id="9d036-102">Tento prvek konfigurace určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="9d036-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="9d036-103">Každý podřízený prvek je <`wsdlImporter`>, která určuje způsob, jak importovat metadata a také převést tyto informace do různých tříd, které představují informace o smlouvě a koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9d036-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="9d036-104">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="9d036-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="9d036-105">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="9d036-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d036-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d036-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="9d036-107">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9d036-107">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9d036-108">Klienti</span><span class="sxs-lookup"><span data-stu-id="9d036-108">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
