---
title: Automatické konfigurace protokolu IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 530d772f905937681a9d06625e1bcf0c1b78c922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ipv6-auto-configuration"></a>Automatické konfigurace protokolu IPv6
Jeden cíl důležité pro protokol IPv6 je podpora uzlu technologie Plug and Play. To znamená musí být možné připojit k síti IPv6 uzlu a automaticky konfigurace bez lidského zásahu.  
  
## <a name="type-of-auto-configuration"></a>Typ automatické konfigurace  
 IPv6 podporuje následující typy automatické konfigurace:  
  
-   **Stavová automatické konfigurace**. Tento typ konfigurace vyžaduje určitou úroveň lidského zásahu, protože je nutné Dynamic Host Configuration Protocol pro protokol IPv6 (DHCPv6) server pro instalaci a správu uzlů. DHCPv6 server udržuje seznam uzlů, na které poskytne informace o konfiguraci. Také udržuje informace o stavu, aby server věděli, jak dlouho každou adresu se používá, a když může být k dispozici pro změnu přiřazení.  
  
-   **Bezstavové automatické konfigurace**. Tento typ konfigurace je vhodná pro malé organizace a jednotlivci. V takovém případě každý hostitel Určuje jeho adresy z obsahu přijaté zprávy o trasách. Standard IEEE EUI-64 používá k definování části ID sítě adresy, je možné logicky předpokládat, že jedinečnost adresy hostitele na odkaz.  
  
 Bez ohledu na to, jakým způsobem je určován adresu musí uzel ověřte, zda je jedinečný místní odkaz na jeho potenciální adresa. K tomu je potřeba odesílání sousedním oslovení zprávu na adresu potenciální. Pokud uzel přijme všechny odpovědi, ví, že adresa je již používán a musí určit jinou adresu.  
  
## <a name="ipv6-mobility"></a>IPv6 Mobility  
 Jak narůstá počet mobilních zařízení, zavádí nový požadavek: zařízení musí být schopen libovolně změnit umístění na Internetu s protokolem IPv6 a přitom zachovat stávající připojení. Tuto funkčnost poskytovaly mobilní uzlu přiřazena domovské adresy, kde ji můžete vždy dostupný. Když mobilní uzlu v domácnostech, připojí k odkaz na domovskou a používá svůj domácí adresu. Po mimo domov uzlu Mobilní domácí agenta, který je obvykle směrovač, předává zprávy mezi mobilní uzlů a uzly, se kterými je komunikaci.  
  
## <a name="see-also"></a>Viz také  
 [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
