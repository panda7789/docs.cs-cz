---
title: Publikování kocových bodů metadat
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 42e0f82ca2c669bbde444cf6aac9ce8f0266f783
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807076"
---
# <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat
Služby Windows Communication Foundation (WCF) publikování metadat tím, že publikujete jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o služby WS-MetadataExchange (MEX) a protokolu HTTP nebo získat. Koncové body metadat jsou podobná další koncové body služby, že mají adresy, vazby a kontraktu a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu. Chcete-li povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí publikování metadat služby WCF `?wsdl` řetězec dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat služby WCF v kódu tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Publikování metadat](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
