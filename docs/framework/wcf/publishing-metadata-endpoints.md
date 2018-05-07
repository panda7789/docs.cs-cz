---
title: Publikování kocových bodů metadat
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 6060850b78c890e043dfaf6f242460bc6e0ef627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat
Služby Windows Communication Foundation (WCF) publikování metadat tím, že publikujete jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o služby WS-MetadataExchange (MEX) a protokolu HTTP nebo získat. Koncové body metadat jsou podobná další koncové body služby, že mají adresy, vazby a kontraktu a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu. Chcete-li povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby publikovat metadata, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v kódu tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Publikování metadat](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
