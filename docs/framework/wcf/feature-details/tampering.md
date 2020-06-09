---
title: Falšování
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600708"
---
# <a name="tampering"></a>Falšování
*Manipulace* je způsob změny zprávy nebo doručení zprávy a použití změněné zprávy pro jiný účel, než k čemu bylo určeno.  
  
## <a name="do-not-disable-ws-addressing"></a>Nepovolujte WS-Addressing  
 Specifikace WS-Addressing poskytuje záhlaví adres pro každou zprávu a umožňuje příjemci zprávy ověřit odesílatele zprávy. Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnosti na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
 Pokud je režim zabezpečení nastavený na stav zpráva a služba WS-Addressing je zakázaná, může útočník přijmout požadavek od klienta a odeslat ho do jiné služby a druhá služba nijak nedokázala zjistit, jestli zpráva pochází z původního klienta. V důsledku toho může první služba předstírat, že se jedná o klienta při komunikaci s druhou službou.  
  
 Chcete-li tuto skutečnost zmírnit, nenastavte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost na hodnotu <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> a vyhněte se použití <xref:System.ServiceModel.Channels.MessageVersion> , jako je například statická <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> vlastnost, která nastaví <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> vlastnost na hodnotu <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
## <a name="see-also"></a>Viz také

- [Otázky zabezpečení](security-considerations-in-wcf.md)
- [Zpřístupnění informací](information-disclosure.md)
- [Zvýšení oprávnění](elevation-of-privilege.md)
- [Útok DoS](denial-of-service.md)
- [Nepodporované scénáře](unsupported-scenarios.md)
- [Útoky opakováním](replay-attacks.md)
