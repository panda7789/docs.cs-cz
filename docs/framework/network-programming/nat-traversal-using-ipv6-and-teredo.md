---
title: Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: f617dc8912091576727b90da1e9efb9ebd5f9bda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642168"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo
Byla provedena vylepšení, která poskytují podporu pro průchod překladu síťových adres (NAT). Tyto změny jsou určeny pro použití s IPv6 a Teredo, ale jsou také použitelné pro jiné technologie tunelového propojení IP. Tato vylepšení ovlivňují třídy v <xref:System.Net> a související obory názvů.  
  
 Tyto změny mohou ovlivnit klientské a serverové aplikace, které plánují používat technologie tunelového propojení IP.  
  
 Změny pro podporu průchodu NAT jsou k dispozici pouze pro aplikace používající rozhraní .NET Framework verze 4. Tyto funkce nejsou k dispozici v dřívějších verzích rozhraní .NET Framework.  
  
## <a name="overview"></a>Přehled  
 Internetový protokol verze 4 (IPv4) definoval adresu IPv4 jako 32 bitů dlouhou. V důsledku toho Protokol IPv4 podporuje přibližně 4 miliardy jedinečných IP adres (2^32). Jak se počet počítačů a síťových zařízení na Internetu v devadesátých letech rozšiřoval, začaly se projevovat limity adresního prostoru IPv4.  
  
 Jednou z několika technik používaných k prodloužení životnosti protokolu IPv4 bylo nasazení nat, aby jedna jedinečná veřejná IP adresa představovala velký počet privátních IP adres (privátní intranet). Privátní IP adresy za zařízením NAT sdílejí jednu veřejnou adresu IPv4. Zařízení NAT může být vyhrazené hardwarové zařízení (například levný bezdrátový přístupový bod a směrovač) nebo počítač se službou pro poskytování nat. Zařízení nebo služba pro tuto veřejnou IP adresu převádí síťové pakety IP mezi veřejným Internetem a privátním intranetu.  
  
 Toto schéma funguje dobře pro klientské aplikace spuštěné v privátním intranetu, které odesílají požadavky na jiné adresy IP (obvykle servery) v Síti Internet. Zařízení nebo server NAT může zachovat mapování požadavků klientů, takže když je vrácena odpověď, ví, kam odpověď odeslat. Toto schéma však představuje problémy pro aplikace spuštěné v privátním intranetu za zařízením NAT, které chtějí poskytovat služby, naslouchat paketům a reagovat. To platí zejména pro aplikace typu peer-to-peer.  
  
 Protokol IPv6 definoval adresu IPv4 jako 128 bitů. V důsledku toho protokol IPv6 podporuje velmi velký adresní prostor IP 3,2 x 10^38 jedinečných adres (2^128). S adresním prostorem této velikosti je možné, aby každé zařízení připojené k Internetu dostalo jedinečnou adresu. Ale jsou tu problémy. Velká část světa stále používá pouze IPv4. Zejména mnoho existujících směrovačů a bezdrátových přístupových bodů používaných malými společnostmi, organizacemi a domácnostmi nepodporuje protokolu IPv6. Také někteří poskytovatelé služeb Internetu, kteří slouží těmto zákazníkům, nepodporují nebo nenakonfigurovali podporu pro protokol IPv6.  
  
 Pro tunelování adres IPv6 v paketu IPv4 bylo vyvinuto několik technologií přechodu IPv6. Tyto technologie zahrnují tunely 6to4, ISATAP a Teredo, které poskytují přiřazení adres a automatické tunelové propojení host-hostitel pro přenos yPv6, když hostitelé IPv6 musí procházet sítěmi IP4, aby se dostali do jiných sítí IPv6. Pakety IPv6 jsou odesílány tunelové propojení jako pakety IPv4. Používá se několik technik tunelového propojení, které umožňují průchod NAT pro adresy IPv6 prostřednictvím zařízení NAT.  
  
 Teredo je jednou z přechodových technologií IPv6, která přináší připojení IPv6 k sítím IPv4. Teredo je dokumentováno v RFC 4380 vydané Internet Engineering Task Force (IETF). Systém Windows XP SP2 a novější poskytují podporu pro virtuální adaptér Teredo, který může poskytnout veřejnou adresu IPv6 v rozsahu 2001:0::/32. Tuto adresu IPv6 lze použít k naslouchání příchozím připojením z Internetu a může být poskytnuta klientům s podporou IPv6, kteří se chtějí připojit k poslechové službě. Tím se aplikace osvobozuje od starostí o to, jak řešit počítač za zařízením NAT, protože aplikace se k němu může připojit pomocí adresy IPv6 Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Vylepšení pro podporu NAT Traversal a Teredo  
 Vylepšení jsou přidány <xref:System.Net>do <xref:System.Net.NetworkInformation>, <xref:System.Net.Sockets> a obory názvů pro podporu průchodu NAT pomocí IPv6 a Teredo.  
  
 Do <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> třídy je přidáno několik metod, které mají získat seznam jednosměrových ADRES IP na hostiteli. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> spustí asynchronní požadavek na načtení stabilní tabulky adres IP jednosměrového vysílání v místním počítači. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> ukončí čekající asynchronní požadavek na načtení stabilní tabulky ip adres jednosměrového vysílání v místním počítači. Metoda <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> je synchronní požadavek na načtení stabilní tabulky adres IP jednosměrového vysílání v místním počítači a v případě potřeby čeká, až se tabulka adres stabilizuje.  
  
 Vlastnost <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> lze použít k určení, pokud <xref:System.Net.IPAddress> je Adresa Teredo IPv6.  
  
 Použití těchto <xref:System.Net.NetworkInformation.IPGlobalProperties> nových metod třídy v kombinaci s vlastností <xref:System.Net.IPAddress.IsIPv6Teredo%2A> umožňuje aplikaci snadno najít adresu Teredo. Aplikace obvykle potřebuje znát pouze místní adresu Teredo, pokud tyto informace sděluje vzdáleným aplikacím. Například aplikace peer-to-peer může odeslat všechny své adresy IPv6 na server tvorby dohazování, který je pak může předat ostatním partnerům a povolit přímou komunikaci.  
  
 Aplikace by měla obvykle nastavit svou <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> službu naslouchání poslouchat na spíše než na místní adresu Teredo. Pokud tedy vzdálený klient nebo partner má přímou trasu IPv6 k hostiteli odposlouchávací služby, může se klient nebo partner připojit přímo pomocí iPv6 a nemusí používat Teredo k tunelovým paketům.  
  
 Pro aplikace TCP <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> má <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> třída metodu, která umožňuje průchod NAT. Pro aplikace UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> má <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> třída metodu, která umožňuje průchod NAT.  
  
 Pro aplikace, <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> které používají a <xref:System.Net.Sockets.Socket.GetSocketOption%2A> <xref:System.Net.Sockets.Socket.SetSocketOption%2A> související třídy a <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> a metody lze použít s možností soketu k dotazování, povolení nebo zakázání průchodu NAT.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
