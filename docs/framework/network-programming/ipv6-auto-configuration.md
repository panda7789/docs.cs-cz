---
title: Automatická konfigurace protokolu IPv6
description: Přečtěte si, jak protokol IPv6 podporuje technologie Plug and Play uzlů, kde se uzel připojuje k síti IPv6 a je nakonfigurovaný bez zásahu člověka.
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 9d65bc453478ac4679556e931b1758c18cfedcf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502324"
---
# <a name="ipv6-auto-configuration"></a>Automatická konfigurace protokolu IPv6
Jedním z důležitých cílů pro protokol IPv6 je podpora technologie Plug and Play uzlů. To znamená, že by mělo být možné připojit uzel do sítě IPv6 a automaticky ho nakonfigurovat bez zásahu člověka.  
  
## <a name="type-of-auto-configuration"></a>Typ automatické konfigurace  
 Protokol IPv6 podporuje následující typy automatické konfigurace:  
  
- **Automatická konfigurace stavů**. Tento typ konfigurace vyžaduje určitou úroveň lidského zásahu, protože pro instalaci a správu uzlů potřebuje pro server IPv6 (DHCPv6) dynamický protokol konfigurace hostitele. Server DHCPv6 uchovává seznam uzlů, do kterých poskytuje informace o konfiguraci. Také uchovává informace o stavu, takže server ví, jak dlouho se každá adresa používá, a kdy může být k dispozici pro změnu přiřazení.  
  
- **Automatická konfigurace bez stavu**. Tento typ konfigurace je vhodný pro malé organizace a jednotlivce. V takovém případě každý hostitel určí své adresy z obsahu přijatých inzerování směrovače. Pomocí standardu IEEE EUI-64 definujte část adresy ID sítě, je vhodné předpokládat jedinečnost adresy hostitele na odkazu.  
  
 Bez ohledu na to, jak je adresa určena, musí uzel ověřit, zda je jeho potenciální adresa jedinečná pro místní odkaz. To se provádí odesláním zprávy o sousedi na potenciální adrese. Pokud uzel obdrží odpověď, ví, že se adresa už používá, a musí určit jinou adresu.  
  
## <a name="ipv6-mobility"></a>Mobilita IPv6  
 Šíření mobilních zařízení zavedlo nový požadavek: zařízení musí být schopné libovolně měnit umístění na internetu s protokolem IPv6 a nadále udržovat stávající připojení. Aby bylo možné tuto funkci poskytnout, je mobilnímu uzlu přiřazena domovská adresa, na které může být vždy dosažitelná. Když je mobilní uzel doma, připojí se k domovskému odkazu a použije jeho domovskou adresu. Když je mobilní uzel pryč z domova, od domovského agenta, který je obvykle směrovačem, přenáší zprávy mezi mobilním uzlem a uzly, se kterými komunikuje.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
