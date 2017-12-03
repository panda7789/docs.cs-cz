---
title: "Publikování kocových bodů metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64032fbc675e30e9f01a5db4d56ecc36574e08de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]služby publikování metadat tím, že publikujete jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o služby WS-MetadataExchange (MEX) a protokolu HTTP nebo získat. Koncové body metadat jsou podobná další koncové body služby, že mají adresy, vazby a kontraktu a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu. Chcete-li povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby publikovat metadata, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
 [Postupy: publikování metadat služby promocí kódu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v kódu tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Publikování metadat](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
