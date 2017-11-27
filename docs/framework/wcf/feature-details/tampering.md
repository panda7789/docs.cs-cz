---
title: "Falšování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8852c4d19c48af2beee598f4ddfae7b775a025f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tampering"></a>Falšování
*Manipulaci* je operace změna zpráva nebo doručení zpráv a pomocí změněna zprávy pro účel, než jaké byla určená.  
  
## <a name="do-not-disable-ws-addressing"></a>Nezakazujte adresování WS  
 Specifikace WS-Addressing poskytuje hlavičky adresy na každou zprávu, povolení příjemce zprávy ověření odesílatele zprávy. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Režim zabezpečení je nastavena na zprávu, a adresování WS je zakázáno, útočník může trvat žádost od klienta a odeslat ho do jiné služby, a druhá služby nemá možnost nijak detekci, zda zpráva byla přijata z původního klienta. Ve skutečnosti první služby můžete předstírají, že ho je klient při posuzování druhý službě.  
  
 Toto riziko lze snížit nikdy nastavit <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>a vyhnout se použití <xref:System.ServiceModel.Channels.MessageVersion>, například statické <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastavuje <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Zvýšení úrovně oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmítnutí služby](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
