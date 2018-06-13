---
title: Protokol IP verze 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 995bc2075a7df5c9a37cc68e812f62c9de2e53c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397114"
---
# <a name="internet-protocol-version-6"></a>Protokol IP verze 6
Internet Protocol version 6 (IPv6) je nová sada standardních protokolů pro síťovou vrstvou sítě Internet. Protokol IPv6 je proto, aby vyřešila mnohé z problémů aktuální verze sady Internet Protocol (známé jako IPv4) s ohledem na adrese spotřebovávat, zabezpečení, automatická konfigurace, rozšíření a tak dále. IPv6 rozšíří možnosti Internetu povolit nové typy aplikací, včetně peer-to-peer a mobilních aplikací. Tady jsou hlavní problémy aktuální protokolu IPv4:  
  
-   Rychlé spotřebovávat adresního prostoru.  
  
     To vedlo k použití síťových adres (NAT), mapovat více soukromých adres na jednu veřejnou IP adresu. Hlavní problémy, které tento mechanismus jsou zpracování režii a nedostatku možností připojení klient server.  
  
-   Nedostatečná podpora hierarchie.  
  
     Z důvodu jeho organizaci vyplývajících předdefinované třída chybí IPv4 true hierarchické podpory. Není možné struktury IP adresy způsobem, který skutečně mapuje síťové topologie. Tato chyba zásadní návrh vytvoří potřebu rozsáhlé směrovací tabulky pro doručování paketů IPv4 do libovolného umístění na Internetu.  
  
-   Konfigurace nejsložitějších sítí.  
  
     S IPv4, musí staticky přiřazené adresy nebo protokol konfigurace například DHCP. V ideálním případě hostitelů neměli spoléhat na správu infrastruktury DHCP. Místo toho se bude moct konfigurovat sami podle segmentu sítě, ve které se nacházejí.  
  
-   Chybí integrované ověřování a důvěrnost.  
  
     IPv4 nevyžaduje pro všechny mechanismus, který poskytuje ověřování nebo šifrování výměně dat na technickou podporu. Tato operace změní s IPv6. Internet Protocol security (IPSec) je požadavek na podporu IPv6.  
  
 Nová sada protokolů musí splňovat základní požadavky na následující:  
  
-   Ve velkém měřítku směrování a adresování s nízkou režii.  
  
-   Automatická konfigurace pro různé situace připojování.  
  
-   Integrované ověřování a důvěrnost.  
  
 Další informace najdete v tématu [adresách IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [směrování IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [automatické konfigurace protokolu IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [povolení a zakázání IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), a [Postup: Upravte konfigurační soubor počítače. Chcete-li povolit podporu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odkazy  
 Následují vybrané dokumenty RFC, které můžete najít na webu Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)):  
  
-   RFC. 1287, směrem k architektuře budoucí Internetu.  
  
-   RFC 1454 porovnání návrhy na další verzi protokolu IP.  
  
-   RFC 2373, Architektura adresování IP verze 6.  
  
-   RFC 2374, formátu agregovatelné globální adresy jednosměrového vysílání IPv6.  
  
 Můžete také najít informace týkající se IPv6 na [IPv6 oblast na webu Technet](http://go.microsoft.com/fwlink/?LinkID=179658).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka Sockets IPv6](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
