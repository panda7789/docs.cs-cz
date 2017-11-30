---
title: '&lt;wsdlImporters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c791ac53afa868bed2daee11eb787ed27efb731f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsdlimportersgt"></a><span data-ttu-id="b88d3-102">&lt;wsdlImporters&gt;</span><span class="sxs-lookup"><span data-stu-id="b88d3-102">&lt;wsdlImporters&gt;</span></span>
<span data-ttu-id="b88d3-103">Tento element konfigurace určuje všechny společnosti importers WSDL, která importuje metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.</span><span class="sxs-lookup"><span data-stu-id="b88d3-103">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="b88d3-104">Je každý podřízený element <`wsdlImporter`> určující způsob, jak můžete importovat metadata a také převést tyto informace do různých tříd, které představují informace kontraktu a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b88d3-104">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="b88d3-105">Selektivně ji můžete importovat informace o kontraktu a koncový bod a vlastnosti, které vystavit všechny chyby při importu a přijímat informace o typu relevantní pro proces importu a převod.</span><span class="sxs-lookup"><span data-stu-id="b88d3-105">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="b88d3-106">Také podporuje import informace o vazbě a vlastnosti, které poskytují přístup na všechny dokumenty zásad, WSDL dokumenty, rozšíření WSDL a dokumentech schémat XML.</span><span class="sxs-lookup"><span data-stu-id="b88d3-106">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88d3-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="b88d3-107">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="b88d3-108">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="b88d3-108">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="b88d3-109">Klienti</span><span class="sxs-lookup"><span data-stu-id="b88d3-109">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
