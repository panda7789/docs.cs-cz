---
title: Rozšíření systému metadat
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7ccef0c2b908a8f78249742decd6c46a862e541e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991299"
---
# <a name="extending-the-metadata-system"></a>Rozšíření systému metadat
Metadata systému Windows Communication Foundation (WCF) je skupina třídy a rozhraní, které představují metadata jsou požadovaná k implementaci aplikací založené na službách. Upravit nebo rozšířit třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat – například rozšíření webové služby WSDL (Description Language) nebo vlastní WS-PolicyAttachments kontrolní výrazy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Export vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní pro vložení kontrolních výrazů vlastních zásad dokumenty WSDL.  
  
 [Import vlastních metadat pro rozšíření WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní pro čtení a reakce na kontrolních výrazů vlastních zásad v dokumenty WSDL.  
  
 [Publikování a načítání metadat prostřednictvím vlastní vazby](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Popisuje, jak k výměně metadat prostřednictvím vlastní vazby.
