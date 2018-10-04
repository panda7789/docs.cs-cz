---
title: Přecházení NAT používající protokoly IPv6 a Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7ee219f8ecb3103e5f9676498b09f290d6e7be8d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581937"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Přecházení NAT používající protokoly IPv6 a Teredo
Vylepšení byly provedeny, který zajišťuje podporu pro procházení překladu adres (NAT). Tyto změny jsou určeny k použití s IPv6 a Teredo, ale navíc se vztahuje na jiné IP tunelování technologie. Tato vylepšení ovlivnit třídy v <xref:System.Net> a souvisejících oborech názvů.  
  
 Tyto změny mohou ovlivnit klientské a serverové aplikace, které plánujete používat IP tunelování technologie.  
  
 Změny pro podporu přecházení NAT jsou k dispozici pouze pro aplikace využívající rozhraní .NET Framework verze 4. Tyto funkce nejsou k dispozici v dřívějších verzích rozhraní .NET Framework.  
  
## <a name="overview"></a>Přehled  
 Internet Protocol verze 4 (IPv4) definované jako 32 bitů adresu IPv4. V důsledku toho IPv4 podporuje přibližně 4 miliardy jedinečných adres IP (2 ^ 32). Jako počet počítačů a síťových zařízení na Internetu rozbalení v 1990s se objevily omezení prostoru IPv4 adres.  
  
 Jeden z několika postupů použít k prodloužení doby života IPv4 bylo nasazení překladu adres umožňující jednu jedinečnou veřejnou IP adresu pro reprezentaci velký počet privátních IP adres (privátní Intranet). Privátní IP adresy za zařízením NAT sdílet jednu veřejnou IPv4 adresu. Může být zařízení NAT zařízení vyhrazený hardware (levné bezdrátový přístupový bod a směrovač, například) nebo počítač se spuštěnou službou poskytnout NAT. Zařízení nebo služby pro tuto veřejnou IP adresu přeloží síťových paketů IP mezi veřejného Internetu a privátních intranetech.  
  
 Toto schéma dobře funguje pro klientské aplikace spuštěné v soukromé síti Intranet, které odesílají požadavky na jiné IP adresy (obvykle servery) v síti Internet. Zařízení NAT nebo server můžete ponechat mapování požadavků od klientů, při vracení odpovědi věděl, kam má odesílat odpovědi. Ale toto schéma představuje potíží pro aplikace běžící v privátních intranetech za zařízením NAT, které mají poskytovat služby, poslechněte paketů a reagovat. To platí hlavně pro aplikace peer-to-peer.  
  
 Protokol IPv6 adresu IPv4 přístupnou definován jako délku 128 bitů. V důsledku toho podporuje protokol IPv6 s velmi velký adresní prostor IP adres 3.2 x 10 ^ 38 jedinečných adres (2 ^ 128). S adresním prostorem v tomto rozsahu je možné pro každé zařízení připojené k Internetu, abychom mohli zadat jedinečnou adresu. Ale dochází k problémům. Velká část na světě se pořád používá jenom protokol IPv4. Zejména mnoho existujících směrovače a bezdrátové přístupové body používají malé společnosti, organizace a domácností nepodporuje IPv6. Také někteří poskytovatelé Internetu, které slouží tyto zákazníky buď nepodporuje, nebo nenakonfigurovali podpory pro IPv6.  
  
 Bylo vyvinuto více přechodové technologie IPv6 adresy tunelového propojení IPv6 v paketu IPv4. K těmto technologiím patří 6to4, ISATAP, a Teredo tunelů, které poskytují přiřazování adres a hostitele na automatické tunelování jednosměrového vysílání IPv6 provoz při hostitele IPv6 musí procházet IP4 sítí k dosažení jiných sítí protokol IPv6. Pakety IPv6 se posílají tunelového propojení jako pakety protokolu IPv4. Několik technik tunelového propojení jsou použity, které umožňují přecházení NAT pro adresy IPv6 přes zařízení NAT.  
  
 Teredo je jedním z přechodové technologie IPv6, které přináší připojení IPv6 pro sítě IPv4. Teredo je popsané v dokumentu RFC 4380 publikovaná pomocí Engineering Task Force IETF (Internet). Windows XP SP2 a novější podporují virtuálního adaptéru Teredo, které můžou poskytovat veřejnou IPv6 adresu v rozsahu 2001:0:: / 32. Tato adresa IPv6 můžete použít k naslouchání pro příchozí připojení z Internetu a je možné poskytnout podporuje protokol IPv6 klientů, které se chcete připojit ke službě naslouchání. Tím se uvolní aplikaci byste se museli starat o tom, jak vyřešit počítač za zařízením NAT, protože aplikace můžete připojit jenom pomocí adresy IPv6 Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Vylepšení podpory přecházení NAT a Teredo  
 Vylepšení jsou přidány do <xref:System.Net>, <xref:System.Net.NetworkInformation>, a <xref:System.Net.Sockets> obory názvů pro podporu přecházení NAT používající protokoly IPv6 a Teredo.  
  
 Několik metod, které jsou přidány do <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> třídy zobrazíte seznam jednosměrového vysílání IP adresy na hostiteli. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Metoda začíná Asynchronní požadavek na načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Metoda byla ukončena čekající asynchronní požadavek na načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Metoda je synchronní požadavek na načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači, počkejte, až tabulky adres níže v případě potřeby.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Vlastnost lze použít k určení, zda <xref:System.Net.IPAddress> je adresa IPv6 Teredo.  
  
 Použití těchto nových <xref:System.Net.NetworkInformation.IPGlobalProperties> metody v kombinaci s třídy <xref:System.Net.IPAddress.IsIPv6Teredo%2A> vlastnost umožňuje aplikaci snadno najdete adrese Teredo. Aplikace obvykle jenom je potřeba vědět místní adresa Teredo, pokud komunikuje tyto informace ke vzdáleným aplikacím. Třeba aplikace peer-to-peer odesílat všechny jeho adresy IPv6 k matchmaking serveru, který lze potom je předejte ostatním uživatelům partnerský vztah k umožnění komunikace s přímým přístupem.  
  
 Aplikace by měl obvykle nastavit jeho naslouchací služby tak, aby naslouchala na <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> , nikoli na místní adrese Teredo. Pokud klient služby Vzdálená nebo partnerským má přímé trasy IPv6 do hostitele naslouchací služby, klienta nebo partnerským umožní připojit se přímo pomocí protokolu IPv6 a není nutné používat Teredo pakety tunelového propojení.  
  
 Pro aplikace TCP <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> třída má <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> způsob povolení přecházení NAT. U aplikací, UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> třída má <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> způsob povolení přecházení NAT.  
  
 Pro aplikace, které používají <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> a související třídy <xref:System.Net.Sockets.Socket.GetSocketOption%2A> a <xref:System.Net.Sockets.Socket.SetSocketOption%2A> můžete použít u metody <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> možnost k dotazování, povolení nebo zakázání procházení překladu adres soketu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
