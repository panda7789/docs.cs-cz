---
title: Síťové programování v rozhraní .NET Framework
description: Pomocí těchto zdrojů můžete integrovat vrstvenou, rozšiřitelnou a spravovanou implementaci internetových služeb poskytovaných .NET Framework do vašich aplikací.
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 117fce887a04def7f9b3f7654a8e9e675ea462d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502402"
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
 Popisuje, jak používat ukládání do mezipaměti pro aplikace, které používají <xref:System.Net.WebClient?displayProperty=nameWithType> <xref:System.Net.WebRequest?displayProperty=nameWithType> třídy, a <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .  
  
 [Zabezpečení v síťovém programování](security-in-network-programming.md)  
 Popisuje, jak používat standardní techniky ověřování a zabezpečení v Internetu.  
  
 [Osvědčené postupy pro třídy System.Net](best-practices-for-system-net-classes.md)  
 Nabízí tipy a triky pro maximální využití internetových aplikací.  
  
 [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)  
 Popisuje postup konfigurace proxy serverů.  
  
 [Informace o síti](networkinformation.md)  
 Popisuje, jak získat informace o událostech sítě, změnách, statistikách a vlastnostech a také vysvětluje, jak určit, zda je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.  
  
 [Změny v oboru názvů System.Uri ve verzi 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Popisuje několik změn provedených <xref:System.Uri?displayProperty=nameWithType> ve třídě ve verzi 2,0 pro opravení nesprávného chování, vylepšení použitelnosti a vylepšení zabezpečení.  
  
 [Podpora mezinárodních identifikátorů prostředků v System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Popisuje vylepšení <xref:System.Uri?displayProperty=nameWithType> třídy ve verzi 3,5, 3,0 SP1 a 2,0 SP1 pro mezinárodní identifikátor prostředku (IRI) a podporu pro mezinárodní názvy domén (IDN).  
  
 [Vylepšení výkonu soketů ve verzi 3.5](socket-performance-enhancements-in-version-3-5.md)  
 Popisuje sadu vylepšení <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy ve verzi 3,5, 3,0 SP1 a 2,0 SP1, která poskytuje alternativní asynchronní vzor, který mohou být používány specializovanými vysoce výkonnými aplikacemi soketu.  
  
 [Protokol PNRP (Peer Name Resolution Protocol)](peer-name-resolution-protocol.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu protokolu PNRP (Peer Name Resolution Protocol), registrace názvů bez použití serverů, dynamické registrace názvů a protokolu překladu IP adres. Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer?displayProperty=nameWithType> oborem názvů.  
  
 [Spolupráce peer-to-peer](peer-to-peer-collaboration.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu spolupráce Peer-to-Peer založené na protokolu PNRP. Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> oborem názvů.  
  
 [Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Popisuje změny zabezpečení provedené ve verzi 3,5 SP1, které mají vliv na integrované ověřování systému Windows pomocí <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> tříd,, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> a souvisejících třídy v oboru názvů System.NET.  
  
 [Integrované ověřování systému Windows s rozšířenou ochranou](integrated-windows-authentication-with-extended-protection.md)  
 Popisuje vylepšení rozšířené ochrany, která mají vliv na to, jak se integrované ověřování systému Windows zpracovává pomocí <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> tříd,,, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> a souvisejících v <xref:System.Net?displayProperty=nameWithType> souvisejících oborech názvů a.  
  
 [Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Popisuje vylepšení přidaná do <xref:System.Net?displayProperty=nameWithType> <xref:System.Net.NetworkInformation?displayProperty=nameWithType> <xref:System.Net.Sockets?displayProperty=nameWithType> oborů názvů, a pro podporu procházení NAT pomocí protokolu IPv6 a Teredo.  
  
 [Izolace sítě pro aplikace z obchodu Microsoft Store](network-isolation-for-windows-store-apps.md)  
 Popisuje dopad izolace sítě, pokud se třídy v <xref:System.Net> , <xref:System.Net.Http> a <xref:System.Net.Http.Headers> obory názvů používají v aplikacích pro Windows 8. x Store.  
  
 [Ukázky programování sítě](network-programming-samples.md)  
 Odkazy na ukázky síťového programování ke stažení, které používají třídy <xref:System.Net> v <xref:System.Net.Cache> <xref:System.Net.Configuration> <xref:System.Net.Mail> oborech názvů,,,, <xref:System.Net.Mime> , <xref:System.Net.NetworkInformation> , <xref:System.Net.PeerToPeer> , <xref:System.Net.Security> a <xref:System.Net.Sockets> .  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Net?displayProperty=nameWithType>  
 Poskytuje jednoduché programovací rozhraní pro celou řadu protokolů, které se v současnosti v sítích používají. <xref:System.Net.WebRequest?displayProperty=nameWithType>Třídy a <xref:System.Net.WebResponse?displayProperty=nameWithType> v tomto oboru názvů jsou základem pro připojení protokolů.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Definuje typy a výčty používané k definování zásad mezipaměti pro prostředky získané pomocí <xref:System.Net.WebRequest?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> tříd a.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Třídy, pomocí nichž aplikace přistupují v kódu programu k nastavením konfigurace pro obory názvů System.Net a aktualizují tato nastavení  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Třídy, které poskytují programovací rozhraní pro moderní aplikace využívající protokol HTTP  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Poskytuje podporu pro kolekce hlaviček HTTP používané <xref:System.Net.Http?displayProperty=nameWithType> oborem názvů.  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Třídy pro vytváření a odesílání e-mailů pomocí protokolu SMTP  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Definuje typy, které se používají k vyjádření hlaviček Multipurpose Internet Mail Exchange (MIME) používaných třídami v <xref:System.Net.Mail?displayProperty=nameWithType> oboru názvů.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Osvědčené postupy TLS (Transport Layer Security) s .NET Framework](tls.md)
- [Témata s postupy: Programování vizuální vrstvy](network-programming-how-to-topics.md)
- [Ukázky programování sítě](network-programming-samples.md)
- [Ukázka HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
