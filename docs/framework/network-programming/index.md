---
title: Síťové programování v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f4ed8fa218e97f4a6b06bd1c8a06d9b300b16119
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529376"
---
# <a name="network-programming-in-the-net-framework"></a>Síťové programování v rozhraní .NET Framework
Rozhraní Microsoft .NET Framework poskytuje vícevrstvou rozšiřitelnou a spravovatelnou implementaci internetových služeb, kterou můžete rychle a snadno integrovat do své aplikace. Síťové aplikace mohou stavět na připojitelných protokolech a díky tomu automaticky využívat nové internetové protokoly nebo mohou používat spravovanou implementaci rozhraní soketů systému Windows pro práci se sítí na úrovni soketu.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Úvod k připojitelným protokolům](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 Popisuje, jak získat přístup ke zdroji v Internetu bez ohledu na přístupový protokol, který vyžaduje.  
  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)  
 Vysvětluje, jak pomocí připojitelných protokolů odesílat a stahovat data ze zdrojů v Internetu.  
  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 Vysvětluje, jak odvodit třídy pro konkrétní protokoly za účelem implementace připojitelných protokolů.  
  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)  
 Popisuje programování aplikací, které využívají síťové protokoly, například TCP, UDP nebo HTTP.  
  
 [Protokol IP (Internet Protocol) verze 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 Popisuje výhody verze 6 protokolu Internet Protocol (IPv6) oproti aktuální verzi sady protokolů Internet Protocol (IPv4). Dále popisuje adresování, směrování a automatickou konfiguraci protokolu IPv6 a postup, jak povolit nebo zakázat protokol IPv6.  
  
 [Konfigurace internetových aplikací](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 Vysvětluje, jak nakonfigurovat internetové aplikace pomocí konfiguračních souborů rozhraní .NET Framework.  
  
 [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 Vysvětluje, jak pomocí trasování sítě získat informace o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací.  
  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 Popisuje, jak používat ukládání do mezipaměti pro aplikace, které používají <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, a <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> třídy.  
  
 [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)  
 Popisuje, jak používat standardní techniky ověřování a zabezpečení v Internetu.  
  
 [Osvědčené postupy pro třídy System.Net](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 Nabízí tipy a triky pro maximální využití internetových aplikací.  
  
 [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 Popisuje postup konfigurace proxy serverů.  
  
 [Informace o síti](../../../docs/framework/network-programming/networkinformation.md)  
 Popisuje, jak získat informace o událostech sítě, změnách, statistiky a vlastnosti a také vysvětluje, jak zjistit, jestli je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.  
  
 [Změny v oboru názvů System.Uri ve verzi 2.0](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Popisuje několik změn provedených <xref:System.Uri?displayProperty=nameWithType> třídy ve verzi 2.0, opravují nesprávné chování, zlepšují použitelnost a zvyšují zabezpečení.  
  
 [Podpora mezinárodních identifikátorů prostředků v System.Uri](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 Popisuje vylepšení <xref:System.Uri?displayProperty=nameWithType> podporovat třídu ve verzi 3.5, 3.0 SP1 a 2.0 SP1 pro International Resource Identifier (IRI) a mezinárodních názvů domén (IDN).  
  
 [Vylepšení výkonu soketů ve verzi 3.5](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 Popisuje sadu rozšíření <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy ve verzi 3.5, 3.0 SP1 a 2.0 SP1 umožňující alternativní asynchronní zpracování, které mohou využívat specializované vysoce výkonné soketu aplikací.  
  
 [Protokol PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu protokolu PNRP (Peer Name Resolution Protocol), registrace názvů bez použití serverů, dynamické registrace názvů a protokolu překladu IP adres. Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer?displayProperty=nameWithType> oboru názvů.  
  
 [Spolupráce partnerských uzlů](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 Popisuje funkce přidané ve verzi 3.5 pro podporu spolupráce Peer-to-Peer založené na protokolu PNRP. Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> oboru názvů.  
  
 [Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Popisuje změny zabezpečení provedené ve verzi 3.5 SP1, které ovlivňují způsob integrované ověřování zařizuje služba Windows <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, a související třídy v oboru názvů System.Net.  
  
 [Integrované ověřování systému Windows s rozšířenou ochranou](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 Popisuje vylepšení pro rozšíření ochrany, které ovlivňují způsob integrované ověřování Windows se zpracovává souborem <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, a související třídy v <xref:System.Net?displayProperty=nameWithType> a související obory názvů.  
  
 [Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 Popisuje vylepšení přidaná do <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, a <xref:System.Net.Sockets?displayProperty=nameWithType> obory názvů podporující přecházení NAT používající protokoly IPv6 a Teredo.  
  
 [Izolace sítě pro aplikace z obchodu Microsoft Store](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 Popisuje dopad má izolace sítě při tříd v <xref:System.Net>, <xref:System.Net.Http>, a <xref:System.Net.Http.Headers> oborů názvů se používají v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 Odkazy na stažení síťové programování ukázky, které používají třídy v <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> obory názvů.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Net?displayProperty=nameWithType>  
 Poskytuje jednoduché programovací rozhraní pro celou řadu protokolů, které se v současnosti v sítích používají. <xref:System.Net.WebRequest?displayProperty=nameWithType> a <xref:System.Net.WebResponse?displayProperty=nameWithType> třídy v tomto oboru názvů jsou základem pro připojitelné protokoly.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Definuje typy a výčty, které slouží k definování zásad mezipaměti pro prostředky získané s použitím <xref:System.Net.WebRequest?displayProperty=nameWithType> a <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> třídy.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Třídy, pomocí nichž aplikace přistupují v kódu programu k nastavením konfigurace pro obory názvů System.Net a aktualizují tato nastavení  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Třídy, které poskytují programovací rozhraní pro moderní aplikace využívající protokol HTTP  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Poskytuje podporu pro kolekce hlaviček HTTP používané oborem <xref:System.Net.Http?displayProperty=nameWithType> obor názvů  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 Třídy pro vytváření a odesílání e-mailů pomocí protokolu SMTP  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Definuje typy, které představují hlavičky Multipurpose Internet Mail Exchange (MIME) používané třídami oboru <xref:System.Net.Mail?displayProperty=nameWithType> oboru názvů.  
  
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

 [Zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework](../../../docs/framework/network-programming/tls.md)  
 [Postupy: Témata programování vizuální vrstvy](../../../docs/framework/network-programming/network-programming-how-to-topics.md)  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázky práce se sítí pro .NET v Galerie kódu na webu MSDN](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)  
 [Ukázka třídy HttpClient](https://go.microsoft.com/fwlink/?LinkId=242550)
