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
# <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat
Služby Windows Communication Foundation (WCF) publikují metadata publikováním jednoho nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata pomocí standardizovaných protokolů, jako jsou WS-MetadataExchange (MEX) a požadavky HTTP/GET. Koncové body metadat jsou podobné jiným koncovým bodům služby v tom, že mají adresu, vazbu a kontrakt a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu. Chcete-li povolit publikování koncových bodů metadat, musíte do služby Přidat chování služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat službu WCF pro publikování metadat, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo požadavku HTTP/GET pomocí řetězce dotazu `?wsdl`.  
  
 [Postupy: Publikování metadat služby promocí kódu](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat pro službu WCF v kódu tak, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo požadavku HTTP/GET pomocí řetězce dotazu `?wsdl`.  
  
## <a name="see-also"></a>Viz také:

- [Publikování metadat](./feature-details/publishing-metadata.md)
