---
title: Směrování IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047790"
---
# <a name="ipv6-routing"></a>Směrování IPv6
Flexibilní mechanizmus směrování je výhodou protokolu IPv6. Vzhledem k tomu, jak se přidělují identifikátory sítě IPv4 a jsou přidělené, musí být velké směrovací tabulky udržované směrovači, které se nacházejí v Internetu. Aby bylo možné přesměrování paketů, které jsou potenciálně směrovány na libovolný uzel na internetu, musí tyto směrovače znát všechny trasy. Díky schopnosti agregovat adresy podporuje IPv6 flexibilní adresování a významně snižuje velikost směrovacích tabulek. V této nové architektuře adres musí zprostředkující směrovače sledovat pouze místní část své sítě, aby bylo možné zprávy přeposílat správně.  
  
## <a name="neighbor-discovery"></a>Sousední zjišťování  
 Mezi funkce poskytované sousedním zjišťováním patří:  
  
- Zjišťování směrovače. To umožňuje hostitelům identifikovat místní směrovače.  
  
- Překlad adres. To umožňuje uzlům přeložit adresu linkové vrstvy pro odpovídající adresu dalšího směrování (náhradu za protokol ARP (Address Resolution Protocol)).  
  
- Automatická konfigurace adres. To umožňuje hostitelům automaticky konfigurovat místní a globální adresy lokality.  
  
 Sousední zjišťování používá protokol zpráv protokolu IPv6 (ICMPv6), který zahrnuje:  
  
- Inzerování směrovače. Odesílá se směrovačem na základě pseudo-periody nebo v reakci na oslovování směrovače. Směrovače IPv6 používají inzerování směrovače k inzerování jejich dostupnosti, předpon adres a dalších parametrů.  
  
- Oslovování směrovače. Odesílá se hostitelem, aby požádal o to, aby směrovače v odkazu odeslaly oznámení směrovače okamžitě.  
  
- Oslovování sousedů. Odesílá se uzly kvůli překladu adres, duplicitě zjišťování adres nebo k ověření, že je sousední uzel stále dosažitelný.  
  
- Inzerování sousedů. Odesílá se uzly, aby reagovaly na oslovování sousedů nebo upozornily sousedním uzlům na změnu v adrese linkové vrstvy.  
  
- Požadavek. Odesílá se směrovači k označení lepší adresy dalšího směrování na konkrétní cíl pro odesílající uzel.  
  
## <a name="see-also"></a>Viz také:

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
