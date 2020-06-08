---
title: Protokol IP (Internet Protocol) verze 6
description: Přečtěte si o protokolu IPv6 a o tom, jak se liší od protokolu IPv4. .NET Framework aplikace podporují protokol IPv6, ale můžou vyžadovat konfiguraci.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502389"
---
# <a name="internet-protocol-version-6"></a>Protokol IP (Internet Protocol) verze 6
Internet Protocol verze 6 (IPv6) je nová sada standardních protokolů pro síťovou vrstvu Internetu. Protokol IPv6 je navržený tak, aby vyřešil mnohé z problémů aktuální verze Internet Protocol sady (označované jako IPv4) s ohledem na vyčerpání adres, zabezpečení, automatickou konfiguraci, rozšiřitelnost atd. Protokol IPv6 rozšiřuje možnosti Internetu, aby umožňoval nové typy aplikací, včetně peer-to-peer a mobilní aplikace. V následujícím seznamu jsou uvedené hlavní problémy s aktuálním protokolem IPv4:  
  
- Rychlá vyčerpání adresního prostoru.  
  
     To vedlo k použití překladatelů síťových adres (NAT), které mapují několik privátních adres na jednu veřejnou IP adresu. Hlavními problémy vytvořenými tímto mechanismem jsou režie zpracování a neexistují kompletní připojení.  
  
- Nedostatečná podpora hierarchie.  
  
     Vzhledem k předdefinované organizaci vaší organizace nemá protokol IPv4 true hierarchickou podporu. Není možné strukturovat IP adresy způsobem, který skutečně mapuje topologii sítě. Tato zásadní návrhová chyba vytvoří potřebu rozsáhlých směrovacích tabulek pro doručování paketů IPv4 do libovolného umístění v Internetu.  
  
- Složitá konfigurace sítě.  
  
     S protokolem IPv4 musí být adresy přiřazeny staticky nebo pomocí konfiguračního protokolu, jako je například DHCP. V ideálním případě by se hostitelé neměli spoléhat na správu infrastruktury DHCP. Místo toho by se daly nakonfigurovat na základě segmentu sítě, ve kterém se nacházejí.  
  
- Chybí integrované ověřování a důvěrnost.  
  
     Protokol IPv4 nevyžaduje podporu žádného mechanismu, který poskytuje ověřování nebo šifrování vyměňovaných dat. Tato změna se projeví v protokolu IPv6. Protokol IPSec (Internet Protocol Security) je požadavek na podporu IPv6.  
  
 Nová sada protokolů musí splňovat následující základní požadavky:  
  
- Velký rozsah směrování a adresování s nízkou režií.  
  
- Automatická konfigurace v různých situacích připojení.  
  
- Integrované ověřování a důvěrnost.  
  
 Další informace najdete v tématech [adresování IPv6](ipv6-addressing.md), [směrování IPv6](ipv6-routing.md), [Automatická konfigurace protokolu IPv6](ipv6-auto-configuration.md), [povolení a zakázání protokolu IPv6](enabling-and-disabling-ipv6.md)a [Postupy: Změna konfiguračního souboru počítače na povolení podpory protokolu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odkazy  
 V následující části jsou vybrané dokumenty RFC, které najdete na webu [IETF (Internet Engineering Task Force)](https://www.ietf.org/) :  
  
- RFC 1287, směrem k budoucí internetové architektuře.  
  
- RFC 1454, porovnání návrhů pro další verzi protokolu IP.  
  
- RFC 2373, Architektura adresování IP verze 6.  
  
- RFC 2374: globální formát adresy jednosměrového vysílání IPv6, který je agregován.  
  
 Informace související s protokolem IPv6 najdete také v protokolu [IP verze 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka soketů IPv6](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Ukázky programování sítě](network-programming-samples.md)
- [Sokety](sockets.md)
