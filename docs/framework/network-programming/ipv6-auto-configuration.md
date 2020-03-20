---
title: Automatická konfigurace protokolu IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 95d9dce36c70b8f6c6b9f963c0842305a111d436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047811"
---
# <a name="ipv6-auto-configuration"></a>Automatická konfigurace protokolu IPv6
Jedním z důležitých cílů pro IPv6 je podpora uzlu Plug and Play. To znamená, že by mělo být možné připojit uzel do sítě IPv6 a mít jej automaticky nakonfigurován bez lidského zásahu.  
  
## <a name="type-of-auto-configuration"></a>Typ automatické konfigurace  
 Protokol IPv6 podporuje následující typy automatické konfigurace:  
  
- **Stavová automatická konfigurace**. Tento typ konfigurace vyžaduje určitou úroveň lidského zásahu, protože pro instalaci a správu uzlů potřebuje protokol DHCP pro server DHCPv6 (Dynamic Host Configuration Protocol). Server DHCPv6 uchovává seznam uzlů, do kterých poskytuje informace o konfiguraci. Také udržuje informace o stavu, takže server ví, jak dlouho jsou jednotlivé adresy používány a kdy může být k dispozici pro opětovné přiřazení.  
  
- **Bezstavová automatická konfigurace**. Tento typ konfigurace je vhodný pro malé organizace i jednotlivce. V tomto případě každý hostitel určuje své adresy z obsahu přijatých směrovačových reklam. Pomocí standardu IEEE EUI-64 k definování části id sítě adresy je rozumné předpokládat jedinečnost adresy hostitele na odkazu.  
  
 Bez ohledu na to, jak je určena adresa, uzel musí ověřit, že jeho potenciální adresa je jedinečná pro místní propojení. To se provádí odesláním sousední oslovení zprávu na potenciální adresu. Pokud uzel obdrží jakoukoli odpověď, ví, že adresa je již používán a musí určit jinou adresu.  
  
## <a name="ipv6-mobility"></a>Mobilita IPv6  
 Šíření mobilních zařízení zavedlo nový požadavek: Zařízení musí být schopno libovolně měnit umístění na Internetu IPv6 a stále udržovat stávající připojení. Chcete-li poskytnout tuto funkci, mobilní uzel je přiřazena domovská adresa, na které je vždy k zastižení. Když je mobilní uzel doma, připojí se k domovskému odkazu a použije jeho domovskou adresu. Když je mobilní uzel mimo domov, domácí agent, což je obvykle směrovač, přenáší zprávy mezi mobilním uzlem a uzly, se kterými komunikuje.  
  
## <a name="see-also"></a>Viz také

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
