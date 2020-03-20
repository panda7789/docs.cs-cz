---
title: Protokol IP (Internet Protocol) verze 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047881"
---
# <a name="internet-protocol-version-6"></a>Protokol IP (Internet Protocol) verze 6
Protokol IPv6 (Internet Protocol verze 6) je nová sada standardních protokolů pro síťovou vrstvu Internetu. Protokol IPv6 je určen k řešení mnoha problémů aktuální verze sady ip(ip(t) s ohledem na odstranění adres, zabezpečení, automatickou konfiguraci, rozšiřitelnost a tak dále. Protokol IPv6 rozšiřuje možnosti Internetu a umožňuje tak nové druhy aplikací, včetně aplikací typu peer-to-peer a mobilních aplikací. Následují hlavní problémy aktuálního protokolu IPv4:  
  
- Rychlé vyčerpání adresního prostoru.  
  
     To vedlo k použití překladačů síťových adres (NAT), které mapují více soukromých adres na jednu veřejnou IP adresu. Hlavní problémy vytvořené tímto mechanismem jsou zpracování režie a nedostatek připojení od konce do konce.  
  
- Nedostatečná podpora hierarchie.  
  
     Z důvodu vlastní předdefinované třídy organizace, IPv4 postrádá skutečnou hierarchickou podporu. Není možné strukturovat IP adresy způsobem, který skutečně mapuje topologii sítě. Tato zásadní chyba návrhu vytváří potřebu velkých směrovacích tabulek pro doručování paketů IPv4 do libovolného umístění v Internetu.  
  
- Komplexní konfigurace sítě.  
  
     U protokolu IPv4 musí být adresy přiřazeny staticky nebo pomocí konfiguračního protokolu, například DHCP. V ideální situaci by hostitelé nemuseli spoléhat na správu infrastruktury DHCP. Místo toho by mohli konfigurovat sami na základě segmentu sítě, ve kterém jsou umístěny.  
  
- Nedostatek vestavěné autentizace a důvěrnosti.  
  
     Protokol IPv4 nevyžaduje podporu pro žádný mechanismus, který poskytuje ověřování nebo šifrování vyměňovaných dat. To se změní s IPv6. Protokol IPSec (IPSec) je požadavek podpory protokolu IPv6.  
  
 Nová sada protokolů musí splňovat následující základní požadavky:  
  
- Rozsáhlé směrování a adresování s nízkou režií.  
  
- Automatická konfigurace pro různé spojovací situace.  
  
- Integrované ověřování a důvěrnost.  
  
 Další informace naleznete v [tématech Adresování Protokolu IPv6](ipv6-addressing.md), [Směrování Protokolu IPv6](ipv6-routing.md), [Automatická konfigurace Protokolu IPv6](ipv6-auto-configuration.md), [Povolení a zakázání protokolu IPv6](enabling-and-disabling-ipv6.md)a [Postup: Úprava konfiguračního souboru počítače za účelem povolení podpory protokolu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odkazy  
 Níže jsou vybrány dokumenty RFC, které najdete na webových stránkách [Skupiny iETF (Internet Engineering Task Force):](https://www.ietf.org/)  
  
- RFC 1287, Směrem k budoucí internetové architektuře.  
  
- RFC 1454, Porovnání návrhů pro další verzi IP.  
  
- RFC 2373, architektura adresování IP verze 6.  
  
- RFC 2374, Agregovatelný formát adresy IPv6 Global Unicast.  
  
 Informace týkající se protokolu IPv6 naleznete také v [protokolu IP verze 6 (IPv6).](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)  
  
## <a name="see-also"></a>Viz také

- [Ukázka soketů IPv6](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Ukázky programování sítě](network-programming-samples.md)
- [Sokety](sockets.md)
