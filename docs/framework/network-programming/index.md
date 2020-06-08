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
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="e3514-103">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3514-103">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="e3514-104">Rozhraní Microsoft .NET Framework poskytuje vícevrstvou rozšiřitelnou a spravovatelnou implementaci internetových služeb, kterou můžete rychle a snadno integrovat do své aplikace.</span><span class="sxs-lookup"><span data-stu-id="e3514-104">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="e3514-105">Síťové aplikace mohou stavět na připojitelných protokolech a díky tomu automaticky využívat nové internetové protokoly nebo mohou používat spravovanou implementaci rozhraní soketů systému Windows pro práci se sítí na úrovni soketu.</span><span class="sxs-lookup"><span data-stu-id="e3514-105">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3514-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e3514-106">In This Section</span></span>  

 [<span data-ttu-id="e3514-107">Úvod k připojitelným protokolům</span><span class="sxs-lookup"><span data-stu-id="e3514-107">Introducing Pluggable Protocols</span></span>](introducing-pluggable-protocols.md)  
 <span data-ttu-id="e3514-108">Popisuje, jak získat přístup ke zdroji v Internetu bez ohledu na přístupový protokol, který vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e3514-108">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="e3514-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="e3514-109">Requesting Data</span></span>](requesting-data.md)  
 <span data-ttu-id="e3514-110">Vysvětluje, jak pomocí připojitelných protokolů odesílat a stahovat data ze zdrojů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="e3514-110">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="e3514-111">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="e3514-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)  
 <span data-ttu-id="e3514-112">Vysvětluje, jak odvodit třídy pro konkrétní protokoly za účelem implementace připojitelných protokolů.</span><span class="sxs-lookup"><span data-stu-id="e3514-112">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="e3514-113">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="e3514-113">Using Application Protocols</span></span>](using-application-protocols.md)  
 <span data-ttu-id="e3514-114">Popisuje programování aplikací, které využívají síťové protokoly, například TCP, UDP nebo HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3514-114">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="e3514-115">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="e3514-115">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)  
 <span data-ttu-id="e3514-116">Popisuje výhody verze 6 protokolu Internet Protocol (IPv6) oproti aktuální verzi sady protokolů Internet Protocol (IPv4). Dále popisuje adresování, směrování a automatickou konfiguraci protokolu IPv6 a postup, jak povolit nebo zakázat protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="e3514-116">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="e3514-117">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="e3514-117">Configuring Internet Applications</span></span>](configuring-internet-applications.md)  
 <span data-ttu-id="e3514-118">Vysvětluje, jak nakonfigurovat internetové aplikace pomocí konfiguračních souborů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3514-118">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="e3514-119">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3514-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)  
 <span data-ttu-id="e3514-120">Vysvětluje, jak pomocí trasování sítě získat informace o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací.</span><span class="sxs-lookup"><span data-stu-id="e3514-120">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="e3514-121">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="e3514-121">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)  
 <span data-ttu-id="e3514-122">Popisuje, jak používat ukládání do mezipaměti pro aplikace, které používají <xref:System.Net.WebClient?displayProperty=nameWithType> <xref:System.Net.WebRequest?displayProperty=nameWithType> třídy, a <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e3514-122">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="e3514-123">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="e3514-123">Security in Network Programming</span></span>](security-in-network-programming.md)  
 <span data-ttu-id="e3514-124">Popisuje, jak používat standardní techniky ověřování a zabezpečení v Internetu.</span><span class="sxs-lookup"><span data-stu-id="e3514-124">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="e3514-125">Osvědčené postupy pro třídy System.Net</span><span class="sxs-lookup"><span data-stu-id="e3514-125">Best Practices for System.Net Classes</span></span>](best-practices-for-system-net-classes.md)  
 <span data-ttu-id="e3514-126">Nabízí tipy a triky pro maximální využití internetových aplikací.</span><span class="sxs-lookup"><span data-stu-id="e3514-126">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="e3514-127">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="e3514-127">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="e3514-128">Popisuje postup konfigurace proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="e3514-128">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="e3514-129">Informace o síti</span><span class="sxs-lookup"><span data-stu-id="e3514-129">NetworkInformation</span></span>](networkinformation.md)  
 <span data-ttu-id="e3514-130">Popisuje, jak získat informace o událostech sítě, změnách, statistikách a vlastnostech a také vysvětluje, jak určit, zda je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="e3514-130">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="e3514-131">Změny v oboru názvů System.Uri ve verzi 2.0</span><span class="sxs-lookup"><span data-stu-id="e3514-131">Changes to the System.Uri namespace in Version 2.0</span></span>](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="e3514-132">Popisuje několik změn provedených <xref:System.Uri?displayProperty=nameWithType> ve třídě ve verzi 2,0 pro opravení nesprávného chování, vylepšení použitelnosti a vylepšení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e3514-132">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="e3514-133">Podpora mezinárodních identifikátorů prostředků v System.Uri</span><span class="sxs-lookup"><span data-stu-id="e3514-133">International Resource Identifier Support in System.Uri</span></span>](international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="e3514-134">Popisuje vylepšení <xref:System.Uri?displayProperty=nameWithType> třídy ve verzi 3,5, 3,0 SP1 a 2,0 SP1 pro mezinárodní identifikátor prostředku (IRI) a podporu pro mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="e3514-134">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="e3514-135">Vylepšení výkonu soketů ve verzi 3.5</span><span class="sxs-lookup"><span data-stu-id="e3514-135">Socket Performance Enhancements in Version 3.5</span></span>](socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="e3514-136">Popisuje sadu vylepšení <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy ve verzi 3,5, 3,0 SP1 a 2,0 SP1, která poskytuje alternativní asynchronní vzor, který mohou být používány specializovanými vysoce výkonnými aplikacemi soketu.</span><span class="sxs-lookup"><span data-stu-id="e3514-136">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="e3514-137">Protokol PNRP (Peer Name Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="e3514-137">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)  
 <span data-ttu-id="e3514-138">Popisuje funkce přidané ve verzi 3.5 pro podporu protokolu PNRP (Peer Name Resolution Protocol), registrace názvů bez použití serverů, dynamické registrace názvů a protokolu překladu IP adres.</span><span class="sxs-lookup"><span data-stu-id="e3514-138">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="e3514-139">Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer?displayProperty=nameWithType> oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="e3514-139">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="e3514-140">Spolupráce peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="e3514-140">Peer-to-Peer Collaboration</span></span>](peer-to-peer-collaboration.md)  
 <span data-ttu-id="e3514-141">Popisuje funkce přidané ve verzi 3.5 pro podporu spolupráce Peer-to-Peer založené na protokolu PNRP.</span><span class="sxs-lookup"><span data-stu-id="e3514-141">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="e3514-142">Tyto nové funkce jsou podporovány <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="e3514-142">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="e3514-143">Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e3514-143">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="e3514-144">Popisuje změny zabezpečení provedené ve verzi 3,5 SP1, které mají vliv na integrované ověřování systému Windows pomocí <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> tříd,, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> a souvisejících třídy v oboru názvů System.NET.</span><span class="sxs-lookup"><span data-stu-id="e3514-144">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="e3514-145">Integrované ověřování systému Windows s rozšířenou ochranou</span><span class="sxs-lookup"><span data-stu-id="e3514-145">Integrated Windows Authentication with Extended Protection</span></span>](integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="e3514-146">Popisuje vylepšení rozšířené ochrany, která mají vliv na to, jak se integrované ověřování systému Windows zpracovává pomocí <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.Net.HttpListener?displayProperty=nameWithType> tříd,,, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType> a souvisejících v <xref:System.Net?displayProperty=nameWithType> souvisejících oborech názvů a.</span><span class="sxs-lookup"><span data-stu-id="e3514-146">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="e3514-147">Přechod přes překlad síťových adres (NAT) využívající protokoly IPv6 a Teredo</span><span class="sxs-lookup"><span data-stu-id="e3514-147">NAT Traversal using IPv6 and Teredo</span></span>](nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="e3514-148">Popisuje vylepšení přidaná do <xref:System.Net?displayProperty=nameWithType> <xref:System.Net.NetworkInformation?displayProperty=nameWithType> <xref:System.Net.Sockets?displayProperty=nameWithType> oborů názvů, a pro podporu procházení NAT pomocí protokolu IPv6 a Teredo.</span><span class="sxs-lookup"><span data-stu-id="e3514-148">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="e3514-149">Izolace sítě pro aplikace z obchodu Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="e3514-149">Network Isolation for Windows Store Apps</span></span>](network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="e3514-150">Popisuje dopad izolace sítě, pokud se třídy v <xref:System.Net> , <xref:System.Net.Http> a <xref:System.Net.Http.Headers> obory názvů používají v aplikacích pro Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="e3514-150">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="e3514-151">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="e3514-151">Network Programming Samples</span></span>](network-programming-samples.md)  
 <span data-ttu-id="e3514-152">Odkazy na ukázky síťového programování ke stažení, které používají třídy <xref:System.Net> v <xref:System.Net.Cache> <xref:System.Net.Configuration> <xref:System.Net.Mail> oborech názvů,,,, <xref:System.Net.Mime> , <xref:System.Net.NetworkInformation> , <xref:System.Net.PeerToPeer> , <xref:System.Net.Security> a <xref:System.Net.Sockets> .</span><span class="sxs-lookup"><span data-stu-id="e3514-152">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e3514-153">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="e3514-153">Reference</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-154">Poskytuje jednoduché programovací rozhraní pro celou řadu protokolů, které se v současnosti v sítích používají.</span><span class="sxs-lookup"><span data-stu-id="e3514-154">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="e3514-155"><xref:System.Net.WebRequest?displayProperty=nameWithType>Třídy a <xref:System.Net.WebResponse?displayProperty=nameWithType> v tomto oboru názvů jsou základem pro připojení protokolů.</span><span class="sxs-lookup"><span data-stu-id="e3514-155">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-156">Definuje typy a výčty používané k definování zásad mezipaměti pro prostředky získané pomocí <xref:System.Net.WebRequest?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> tříd a.</span><span class="sxs-lookup"><span data-stu-id="e3514-156">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-157">Třídy, pomocí nichž aplikace přistupují v kódu programu k nastavením konfigurace pro obory názvů System.Net a aktualizují tato nastavení</span><span class="sxs-lookup"><span data-stu-id="e3514-157">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-158">Třídy, které poskytují programovací rozhraní pro moderní aplikace využívající protokol HTTP</span><span class="sxs-lookup"><span data-stu-id="e3514-158">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-159">Poskytuje podporu pro kolekce hlaviček HTTP používané <xref:System.Net.Http?displayProperty=nameWithType> oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="e3514-159">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-160">Třídy pro vytváření a odesílání e-mailů pomocí protokolu SMTP</span><span class="sxs-lookup"><span data-stu-id="e3514-160">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-161">Definuje typy, které se používají k vyjádření hlaviček Multipurpose Internet Mail Exchange (MIME) používaných třídami v <xref:System.Net.Mail?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3514-161">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-162">Třídy, které umožňují získávat v kódu programu informace o událostech sítě, změnách, statistických údajích a vlastnostech</span><span class="sxs-lookup"><span data-stu-id="e3514-162">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-163">Poskytuje spravovanou implementaci protokolu PNRP (Peer Name) pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="e3514-163">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-164">Poskytuje spravovanou implementaci rozhraní pro spolupráci Peer-to-Peer pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="e3514-164">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-165">Třídy, které poskytují síťové datové proudy pro zabezpečenou komunikaci mezi hostiteli</span><span class="sxs-lookup"><span data-stu-id="e3514-165">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-166">Poskytuje spravovatelnou implementaci rozhraní Windows Sockets (Winsock) pro vývojáře, kteří potřebují řídit přístup k síti.</span><span class="sxs-lookup"><span data-stu-id="e3514-166">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-167">Poskytuje spravovanou implementaci rozhraní WebSocket pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="e3514-167">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-168">Poskytuje reprezentaci identifikátoru URI ve formě objektu a snadný přístup k částem identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="e3514-168">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-169">Poskytuje podporu pro ověřování s použitím rozšířené ochrany pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="e3514-169">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="e3514-170">Poskytuje podporu pro konfiguraci ověřování s použitím rozšířené ochrany pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="e3514-170">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3514-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3514-171">See also</span></span>

- [<span data-ttu-id="e3514-172">Osvědčené postupy TLS (Transport Layer Security) s .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3514-172">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](tls.md)
- [<span data-ttu-id="e3514-173">Témata s postupy: Programování vizuální vrstvy</span><span class="sxs-lookup"><span data-stu-id="e3514-173">Network Programming How-to Topics</span></span>](network-programming-how-to-topics.md)
- [<span data-ttu-id="e3514-174">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="e3514-174">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="e3514-175">Ukázka HttpClient</span><span class="sxs-lookup"><span data-stu-id="e3514-175">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
