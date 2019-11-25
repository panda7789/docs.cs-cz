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
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
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
 Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.  
  
 [Zabezpečení v síťovém programování](security-in-network-programming.md)  
 Popisuje, jak používat standardní techniky ověřování a zabezpečení v Internetu.  
  
 [Osvědčené postupy pro třídy System.Net](best-practices-for-system-net-classes.md)  
 Nabízí tipy a triky pro maximální využití internetových aplikací.  
  
 [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)  
 Popisuje postup konfigurace proxy serverů.  
  
 [Informace o síti](networkinformation.md)  
 Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.  
  
 [Změny v oboru názvů System.Uri ve verzi 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.  
  
 [Podpora mezinárodních identifikátorů prostředků v System.Uri](international-resource-identifier-support-in-system-uri.md)  
 Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.  
  
 [Vylepšení výkonu soketů ve verzi 3.5](socket-performance-enhancements-in-version-3-5.md)  
 Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.  
  
 [Protokol PNRP](peer-name-resolution-protocol.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu protokolu PNRP (Peer Name Resolution Protocol), registrace názvů bez použití serverů, dynamické registrace názvů a protokolu překladu IP adres. These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.  
  
 [Spolupráce partnerských uzlů](peer-to-peer-collaboration.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu spolupráce Peer-to-Peer založené na protokolu PNRP. These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.  
  
 [Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.  
  
 [Integrované ověřování systému Windows s rozšířenou ochranou](integrated-windows-authentication-with-extended-protection.md)  
 Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.  
  
 [Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo](nat-traversal-using-ipv6-and-teredo.md)  
 Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.  
  
 [Izolace sítě pro aplikace z obchodu Microsoft Store](network-isolation-for-windows-store-apps.md)  
 Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.  
  
 [Ukázky programování sítě](network-programming-samples.md)  
 Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Net?displayProperty=nameWithType>  
 Poskytuje jednoduché programovací rozhraní pro celou řadu protokolů, které se v současnosti v sítích používají. The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Třídy, pomocí nichž aplikace přistupují v kódu programu k nastavením konfigurace pro obory názvů System.Net a aktualizují tato nastavení  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Třídy, které poskytují programovací rozhraní pro moderní aplikace využívající protokol HTTP  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Třídy pro vytváření a odesílání e-mailů pomocí protokolu SMTP  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.  
  
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

- [Transport Layer Security (TLS) best practices with .NET Framework](tls.md)
- [Postupy: Témata programování vizuální vrstvy](network-programming-how-to-topics.md)
- [Ukázky programování sítě](network-programming-samples.md)
- [HttpClient Sample](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
