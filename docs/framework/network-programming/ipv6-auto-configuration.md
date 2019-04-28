---
title: Automatická konfigurace protokolu IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 4dc7a148364c9f96a0f6c68c8af71f7668e797b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642331"
---
# <a name="ipv6-auto-configuration"></a>Automatická konfigurace protokolu IPv6
Jedním z cílů důležité pro protokol IPv6 je podpora uzlu technologie Plug and Play. To znamená by měl být možné připojte uzel do sítě IPv6 a konfigurace automaticky bez zásahu člověka.  
  
## <a name="type-of-auto-configuration"></a>Typ Auto konfigurace  
 IPv6 podporuje následující typy automatické konfigurace:  
  
- **Stavové automatickou konfiguraci**. Tento typ konfigurace vyžaduje určitou úroveň zásahu člověka, protože potřebuje Dynamic Host Configuration Protocol pro protokol IPv6 serveru (DHCPv6) pro instalaci a správu uzlů. DHCPv6 server udržuje seznam uzlů, ke kterým poskytne informace o konfiguraci. Také udržuje informace o stavu, aby server věděli, jak dlouho každý adresa se používá a kdy může být dostupnou k opětovnému přiřazení.  
  
- **Bezstavové automatické konfigurace**. Tento typ konfigurace je vhodná pro malé organizace a jednotlivci. V takovém případě každého hostitele určuje jeho adresy z obsahu přijatý směrovače oznámení o inzerovaných programech. Použití standardu IEEE EUI-64 k definování část ID síťové adresy, je možné logicky předpokládat jedinečnost adresa hostitele na odkaz.  
  
 Bez ohledu na to, jak se určuje adresu musí uzel ověřte, zda je jeho potenciální adresa jedinečný odkaz na místní. Uděláte to pomocí odesílání žádostí sousední zprávy na potenciální adresu. Pokud uzel přijme odpověď, ví, že adresa se už používá a musíte určit jinou adresu.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobility  
 Růst počtu mobilních zařízení přináší nový požadavek: Zařízení musí být libovolně změnit umístění na Internetu s protokolem IPv6 a přitom zachovává existující připojení. Tuto funkci zajistí mobilní uzlu přiřazena adresa domů jakou můžou vždycky dostupný. Když se během chvilky mobilní uzlu, se připojí k odkaz na domovskou a používá jeho adresa domů. Když se mobilní uzlu mimo Domovská stránka, domácí agenta, který je obvykle směrovač, přenáší zprávy mezi mobilní uzlů a uzly, se kterými je komunikace.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Sokety](../../../docs/framework/network-programming/sockets.md)
