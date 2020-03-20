---
title: Síťové programování v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204685"
---
# <a name="network-programming-in-the-net-framework"></a>Síťové programování v rozhraní .NET Framework
Rozhraní Microsoft .NET Framework poskytuje vícevrstvou rozšiřitelnou a spravovatelnou implementaci internetových služeb, kterou můžete rychle a snadno integrovat do své aplikace. Síťové aplikace mohou stavět na připojitelných protokolech a díky tomu automaticky využívat nové internetové protokoly nebo mohou používat spravovanou implementaci rozhraní soketů systému Windows pro práci se sítí na úrovni soketu.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Úvod k připojitelným protokolům](introducing-pluggable-protocols.md)  
 Popisuje, jak získat přístup ke zdroji v Internetu bez ohledu na přístupový protokol, který vyžaduje.  
  
 [Žádosti o data](requesting-data.md)  
 Vysvětluje, jak pomocí připojitelných protokolů odesílat a stahovat data ze zdrojů v Internetu.  
  
 [Programování připojitelných protokolů](programming-pluggable-protocols.md)  
 Vysvětluje, jak odvodit třídy pro konkrétní protokoly za účelem implementace připojitelných protokolů.  
  
 [Použití aplikačních protokolů](using-application-protocols.md)  
 Popisuje programování aplikací, které využívají síťové protokoly, například TCP, UDP nebo HTTP.  
  
 [Protokol IP (Internet Protocol) verze 6](internet-protocol-version-6.md)  
 Popisuje výhody verze 6 protokolu Internet Protocol (IPv6) oproti aktuální verzi sady protokolů Internet Protocol (IPv4). Dále popisuje adresování, směrování a automatickou konfiguraci protokolu IPv6 a postup, jak povolit nebo zakázat protokol IPv6.  
  
 [Konfigurace internetových aplikací](configuring-internet-applications.md)  
 Vysvětluje, jak nakonfigurovat internetové aplikace pomocí konfiguračních souborů rozhraní .NET Framework.  
  
 [Trasování sítě v rozhraní .NET Framework](network-tracing.md)  
 Vysvětluje, jak pomocí trasování sítě získat informace o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací.  
  
 [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)  
 Popisuje způsob použití ukládání do mezipaměti <xref:System.Net.WebClient?displayProperty=nameWithType>pro <xref:System.Net.WebRequest?displayProperty=nameWithType>aplikace, které používají , a <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> třídy.  
  
 [Zabezpečení v síťovém programování](security-in-network-programming.md)  
 Popisuje, jak používat standardní techniky ověřování a zabezpečení v Internetu.  
  
 [Osvědčené postupy pro třídy System.Net](best-practices-for-system-net-classes.md)  
 Nabízí tipy a triky pro maximální využití internetových aplikací.  
  
 [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)  
 Popisuje postup konfigurace proxy serverů.  
  
 [Informace o síti](networkinformation.md)  
 Popisuje, jak shromažďovat informace o síťových událostech, změnách, statistikách a vlastnostech a také <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> vysvětluje, jak zjistit, zda je vzdálený hostitel dostupný pomocí třídy.  
  
 [Změny v oboru názvů System.Uri ve verzi 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Popisuje několik změn provedených <xref:System.Uri?displayProperty=nameWithType> ve třídě ve verzi 2.0 opravit nesprávné chování, zlepšit použitelnost a zvýšit zabezpečení.  
  
 [Podpora mezinárodních identifikátorů prostředků v System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Popisuje vylepšení <xref:System.Uri?displayProperty=nameWithType> třídy v podpoře verze 3.5, 3.0 SP1 a 2.0 SP1 pro mezinárodní identifikátor prostředků (IRI) a mezinárodní název domény (IDN).  
  
 [Vylepšení výkonu soketů ve verzi 3.5](socket-performance-enhancements-in-version-3-5.md)  
 Popisuje sadu vylepšení třídy <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> ve verzích 3.5, 3.0 SP1 a 2.0 SP1, které poskytují alternativní asynchronní vzor, který lze použít specializované vysoce výkonné aplikace soketu.  
  
 [Protokol PNRP (Peer Name Resolution Protocol)](peer-name-resolution-protocol.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu protokolu PNRP (Peer Name Resolution Protocol), registrace názvů bez použití serverů, dynamické registrace názvů a protokolu překladu IP adres. Tyto nové funkce jsou <xref:System.Net.PeerToPeer?displayProperty=nameWithType> podporovány oborem názvů.  
  
 [Spolupráce peer-to-peer](peer-to-peer-collaboration.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu spolupráce Peer-to-Peer založené na protokolu PNRP. Tyto nové funkce jsou <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> podporovány oborem názvů.  
  
 [Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Popisuje změny zabezpečení provedené ve verzi 3.5 SP1, které <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>ovlivňují <xref:System.Net.HttpListener?displayProperty=nameWithType> <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>způsob, jakým je integrované ověřování systému Windows zpracováváno třídami , , a souvisejícími v System.Net oboru názvů.  
  
 [Integrované ověřování systému Windows s rozšířenou ochranou](integrated-windows-authentication-with-extended-protection.md)  
 Popisuje vylepšení rozšířené ochrany, která ovlivňují způsob, jakým <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType>je <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType>integrované <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>ověřování systému <xref:System.Net?displayProperty=nameWithType> Windows zpracováváno třídami , , , a souvisejícími v oborech názvů a souvisejících s nimi.  
  
 [Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Popisuje vylepšení přidaná <xref:System.Net?displayProperty=nameWithType>do <xref:System.Net.NetworkInformation?displayProperty=nameWithType>aplikace <xref:System.Net.Sockets?displayProperty=nameWithType> , a obory názvů pro podporu průchodu NAT pomocí iPv6 a Teredo.  
  
 [Izolace sítě pro aplikace z obchodu Microsoft Store](network-isolation-for-windows-store-apps.md)  
 Popisuje dopad izolace sítě při <xref:System.Net>použití <xref:System.Net.Http>tříd <xref:System.Net.Http.Headers> v aplikacích pro Windows 8.x Store v aplikaci pro windows 8.x Store.  
  
 [Ukázky programování sítě](network-programming-samples.md)  
 Odkazy na ukázky programování sítě ke stažení, <xref:System.Net.Mail> <xref:System.Net.Mime>které <xref:System.Net.NetworkInformation> <xref:System.Net.PeerToPeer>používají třídy v oborech názvů <xref:System.Net.Security> <xref:System.Net>, <xref:System.Net.Cache> <xref:System.Net.Configuration>, , . <xref:System.Net.Sockets>  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Net?displayProperty=nameWithType>  
 Poskytuje jednoduché programovací rozhraní pro celou řadu protokolů, které se v současnosti v sítích používají. <xref:System.Net.WebRequest?displayProperty=nameWithType> Třídy <xref:System.Net.WebResponse?displayProperty=nameWithType> a v tomto oboru názvů jsou základem pro připojitelné protokoly.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Definuje typy a výčty používané k definování zásad mezipaměti pro prostředky získané pomocí <xref:System.Net.WebRequest?displayProperty=nameWithType> tříd a. <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Třídy, pomocí nichž aplikace přistupují v kódu programu k nastavením konfigurace pro obory názvů System.Net a aktualizují tato nastavení  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Třídy, které poskytují programovací rozhraní pro moderní aplikace využívající protokol HTTP  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Poskytuje podporu pro kolekce hlaviček <xref:System.Net.Http?displayProperty=nameWithType> PROTOKOLU HTTP používaných oborem názvů.  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Třídy pro vytváření a odesílání e-mailů pomocí protokolu SMTP  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Definuje typy, které se používají k reprezentaci víceúčelových hlaviček <xref:System.Net.Mail?displayProperty=nameWithType> MIME (Internet Mail Exchange), které používají třídy v oboru názvů.  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 Třídy, které umožňují získávat v kódu programu informace o událostech sítě, změnách, statistických údajích a vlastnostech  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 Poskytuje spravovanou implementaci protokolu PNRP (Peer Name) pro vývojáře.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 Poskytuje spravovanou implementaci rozhraní pro spolupráci Peer-to-Peer pro vývojáře.  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 Třídy, které poskytují síťové datové proudy pro zabezpečenou komunikaci mezi hostiteli  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 Poskytuje spravovatelnou implementaci rozhraní Windows Sockets (Winsock) pro vývojáře, kteří potřebují řídit přístup k síti.  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 Poskytuje spravovanou implementaci rozhraní WebSocket pro vývojáře.  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 Poskytuje reprezentaci identifikátoru URI ve formě objektu a snadný přístup k částem identifikátoru URI.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 Poskytuje podporu pro ověřování s použitím rozšířené ochrany pro aplikace.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 Poskytuje podporu pro konfiguraci ověřování s použitím rozšířené ochrany pro aplikace.  
  
## <a name="see-also"></a>Viz také

- [Osvědčené postupy zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](tls.md)
- [Témata s postupy: Programování vizuální vrstvy](network-programming-how-to-topics.md)
- [Ukázky programování sítě](network-programming-samples.md)
- [Ukázka httpklienta](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
