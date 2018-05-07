---
title: Rozšíření systému metadat
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7ccef0c2b908a8f78249742decd6c46a862e541e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="extending-the-metadata-system"></a>Rozšíření systému metadat
Systém Windows Communication Foundation (WCF) metadat je skupina třídy a rozhraní, které představují metadata potřebnou k implementaci aplikace založené na služby. Upravit nebo rozšíření třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat, jako je například rozšíření webové služby popis Language (WSDL) nebo vlastní WS-PolicyAttachments kontrolní výrazy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní pro vložení kontrolních výrazů vlastních zásad v dokumentech WSDL.  
  
 [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní ke čtení a reagovat na kontrolních výrazů vlastních zásad v dokumentech WSDL.  
  
 [Publikování a načítání metadat prostřednictvím vlastní vazby](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Popisuje, jak k výměně metadat prostřednictvím vlastní vazby.
