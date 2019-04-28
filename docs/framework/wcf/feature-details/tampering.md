---
title: Falšování
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703384"
---
# <a name="tampering"></a>Falšování
*Manipulace* je změna zprávu nebo doručení zprávy a pomocí upravený zprávy pro účely, než jaké byla určená.  
  
## <a name="do-not-disable-ws-addressing"></a>Nezakazujte WS-Addressing  
 Specifikace WS-Addressing obsahuje záhlaví adres v každé zprávě, povolení příjemce zprávy ověření odesílatele zprávy. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Pokud režim zabezpečení je nastavený na zprávu a WS-Addressing je zakázaná, útočník by mohl přijmout žádost od klienta a odeslat do jiné služby, a druhý služby nemá možnost nijak zjistit, že zpráva pochází z původního klienta. V důsledku toho první služby můžete předstírat, že, že je klient upozorňovat druhý služby.  
  
 Chcete-li tento problém zmírnit, nikdy nastavte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>a vyhnout se použití <xref:System.ServiceModel.Channels.MessageVersion>, jako je například statické <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastavuje <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
