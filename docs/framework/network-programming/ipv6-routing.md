---
title: Směrování IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047790"
---
# <a name="ipv6-routing"></a>Směrování IPv6
Flexibilní mechanismus směrování je výhodou protokolu IPv6. Vzhledem ke způsobu, jakým byla a přidělována ID sítě IPv4, musí být velké směrovací tabulky udržovány směrovači, které jsou v páteřních sítích. Tyto směrovače musí znát všechny trasy, aby bylo možné předávat pakety, které jsou potenciálně směrovány do libovolného uzlu v Síti Internet. Díky schopnosti agregovat adresy umožňuje protokol IPv6 flexibilní adresování a výrazně zmenšuje velikost směrovacích tabulek. V této nové architektuře adresování musí zprostředkující směrovače sledovat pouze místní část své sítě, aby mohly zprávy odpovídajícím způsobem předat dál.  
  
## <a name="neighbor-discovery"></a>Zjišťování souseda  
 Některé z funkcí poskytovaných Neighbor Discovery jsou:  
  
- Zjišťování směrovače. To umožňuje hostitelům identifikovat místní směrovače.  
  
- Rozlišení adresy. To umožňuje uzlům vyřešit adresu linkové vrstvy pro odpovídající adresu dalšího směrování (náhrada za protokol Http Resolution Protocol [ARP]).  
  
- Automatická konfigurace adresy. To umožňuje hostitelům automaticky konfigurovat místní a globální adresy lokality.  
  
 Zjišťování souseda používá pro zprávy IPv6 (ICMPv6) protokol IPV6 (ICMPv6), které zahrnují:  
  
- Router reklama. Odesláno směrovačem pseudopravidelně nebo v reakci na oslovení směrovače. Směrovače IPv6 používají inzerování směrovačů k propagaci své dostupnosti, předpon adres a dalších parametrů.  
  
- Oslovení směrovače. Odesláno hostitelem s požadavkem, aby směrovače na propojení okamžitě odeslali reklamu směrovače.  
  
- Sousedské obtěžování. Odesláno uzly pro překlad adres, vyhledávání duplicitních adres nebo ověření, zda je soused stále dostupný.  
  
- Sousedská reklama. Odesláno uzly reagovat na souseda oslovení nebo upozornit sousedy na změnu adresy linkové vrstvy.  
  
- Přesměrování. Odeslané směrovači k označení lepší adresy dalšího směrování do určitého cíle pro odesílající uzel.  
  
## <a name="see-also"></a>Viz také

- [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)
- [Sokety](sockets.md)
