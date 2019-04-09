---
title: Publikování kocových bodů metadat
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121729"
---
# <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat
Služby Windows Communication Foundation (WCF) měla být zveřejněna metadata a publikovat jednu nebo víc koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o WS-MetadataExchange (MEX) a protokolu HTTP/GET. Koncové body metadat se podobně jako ostatní koncové body služby mají adresa, vazba a kontrakt a je možné je přidat k hostiteli služby prostřednictvím konfigurace nebo v kódu. Pokud chcete povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služeb chování ve službě.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET být zveřejněna metadata služby WCF `?wsdl` řetězec dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat služby WCF v kódu tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu.  
  
## <a name="see-also"></a>Viz také:

- [Publikování metadat](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
