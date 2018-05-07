---
title: NAT Traversal používající protokoly IPv6 a Teredo
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d2e503bedd908bff18f3c1a8d626d056f22d3f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>NAT Traversal používající protokoly IPv6 a Teredo
Byly provedeny vylepšení, která poskytuje podporu pro překlad adres (NAT) traversal. Tyto změny jsou navrženy pro použití s IPv6 a Teredo, ale jsou i pro jiné IP tunelování technologie. Tato vylepšení ovlivnit třídy v <xref:System.Net> a související obory názvů.  
  
 Tyto změny mohou ovlivnit klientské a serverové aplikace, které plánujete používat IP tunelování technologie.  
  
 K podpoře NAT traversal změny jsou k dispozici pouze pro aplikace pomocí rozhraní .NET Framework verze 4. Tyto funkce nejsou k dispozici v dřívějších verzích rozhraní .NET Framework.  
  
## <a name="overview"></a>Přehled  
 Internet Protocol verze 4 (IPv4) definován jako 32 bitů adresu IPv4. V důsledku toho IPv4 podporuje přibližně 4 miliardy jedinečných adres IP (2 ^ 32). Jako počet počítačů a síťových zařízení na Internetu rozšířit 1990s se objevily omezení prostoru IPv4 adres.  
  
 Jedním z několika technik, které slouží k rozšíření životnost IPv4 bylo nasazení NAT, abyste umožnili jeden jedinečný veřejnou IP adresu představují velký počet privátní IP adresy (privátní Intranet). Soukromé IP adresy za zařízením NAT sdílet jednu veřejnou adresu IPv4. Vyhrazené hardwarové zařízení (levné bezdrátové přístupové body a směrovač, např.) nebo počítači je spuštěna služba k poskytování adres (NAT) může být zařízení NAT Zařízení nebo službu, aby tato veřejná IP adresa překládá síťových paketů IP mezi veřejného Internetu a privátní sítě Intranet.  
  
 Toto schéma funguje dobře pro klientské aplikace spuštěné v soukromé síti Intranet, které odesílat požadavky na jiné adresy IP (obvykle servery) na Internetu. Zařízení NAT nebo serveru můžete ponechat mapování požadavků od klientů, pokud odpověď se vrátí, bude vědět, kam má posílat odpovědi. Ale toto schéma činí problémy pro aplikace spuštěné v privátním intranetu za zařízením NAT, které mají poskytovat služby, přijímat pakety a reagovat. Jde zejména v případě aplikací peer-to-peer.  
  
 Protokol IPv6 adresu IPv4 definován jako 128 bitů. V důsledku toho podporuje protokol IPv6 a velmi velký adresní prostor IP adres 3.2 × 10 ^ 38 jedinečných adres (2 ^ 128 znaků). S adresním prostorem této velikosti je možné pro každé zařízení připojené k Internetu, aby bylo možné přidělit jedinečnou adresu. Ale dochází k problémům. Velká část světě pořád používá pouze protokol IPv4. Konkrétně řadu existující směrovače a bezdrátové přístupové body, které používá malé společností, organizací a domácnostech nepodporují IPv6. Také některé poskytovatelům internetových služeb, které slouží těchto zákazníků buď nepodporují nebo nenakonfigurovali podpora adres IPv6.  
  
 Tunelové propojení IPv6 adresy v paketu IPv4 bylo vyvinuto několik přechodové technologie IPv6. K těmto technologiím patří 6to4, ISATAP, a Teredo tunelových propojení, které poskytují přiřazení adresy a automatické tunelové propojení typu hostitel hostitel pro přenosy protokolu IPv6 jednosměrového vysílání když hostitele IPv6 musí procházejí sítí IP4 k dosažení další sítě IPv6. Pakety IPv6 odesílají tunelových jako paketů IPv4. Několik tunelu techniky jsou používány umožňujících prostřednictvím zařízení NAT traversal NAT pro adresy IPv6.  
  
 Teredo je jedním z přechodové technologie IPv6, které přináší připojení IPv6 do sítě IPv4. Teredo je popsané v dokumentu RFC 4380 publikovaná Internet Engineering Task Force (IETF). Windows XP SP2 a novější poskytovat podporu pro virtuální adaptér Teredo, které můžou poskytovat veřejnou adresu IPv6 v rozsahu 2001:0:: / 32. Tato adresa IPv6 lze přijímat příchozí připojení z Internetu a může být poskytnut klientům pro protokol IPv6, které chcete připojit ke službě naslouchání. Tím se uvolní aplikace z starostí o tom, jak vyřešit počítači za zařízením NAT, protože aplikace můžete jednoduše připojte se pomocí adresy IPv6 Teredo.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Vylepšení podpory NAT Traversal a Teredo  
 Vylepšení jsou přidány do <xref:System.Net>, <xref:System.Net.NetworkInformation>, a <xref:System.Net.Sockets> obory názvů pro podporu NAT traversal používající protokoly IPv6 a Teredo.  
  
 Existuje několik metod, které jsou přidány do <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> třídy pro získání seznamu jednosměrového vysílání IP adresy na hostiteli. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Metoda zahájí Asynchronní požadavek k načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Metoda končí čekající asynchronní požadavek na načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Metoda je synchronní požadavek na načtení tabulky stabilní jednosměrového vysílání IP adres v místním počítači, počkejte, až tabulky adres nestabilizuje v případě potřeby.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Vlastnost lze použít k určení, zda <xref:System.Net.IPAddress> je adresa IPv6 Teredo.  
  
 Použití těchto nových <xref:System.Net.NetworkInformation.IPGlobalProperties> metody v kombinaci s třídy <xref:System.Net.IPAddress.IsIPv6Teredo%2A> vlastnost umožňuje aplikaci snadno najít adresu Teredo. Aplikace obvykle pouze musí znát místní adresu Teredo, pokud komunikuje tyto informace do vzdálené aplikace. Například peer-to-peer aplikace může odesílat všech adres IPv6 k serveru matchmaking, který pak je předat dál ostatním partnerský vztah k povolení přímé komunikaci.  
  
 Aplikace by měl obvykle nastavit jeho naslouchání služby tak, aby naslouchala na <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> ne na místní adresu Teredo. Takže pokud vzdáleného klienta nebo sdílené má přímé trasy IPv6 na hostitele naslouchání služby, můžete připojit se přímo pomocí protokolu IPv6 a není nutné používat Teredo pro tunelové propojení paketů klienta nebo partnera.  
  
 U aplikací, TCP <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> třída má <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> způsob povolení NAT traversal. U aplikací, UDP <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> třída má <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> způsob povolení NAT traversal.  
  
 Pro aplikace, které používají <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> a souvisejících tříd <xref:System.Net.Sockets.Socket.GetSocketOption%2A> a <xref:System.Net.Sockets.Socket.SetSocketOption%2A> metody lze použít s <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> soketu možnost dotazu, povolit nebo zakázat NAT traversal.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
