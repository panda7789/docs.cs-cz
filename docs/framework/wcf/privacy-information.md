---
title: "Windows Communication Foundation – informace o ochraně osobních údajů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53fc4be67fd3f6a7b2b8c914c11fb6540b28c199
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="f130c-102">Windows Communication Foundation – informace o ochraně osobních údajů</span><span class="sxs-lookup"><span data-stu-id="f130c-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="f130c-103">Společnost Microsoft se zavazuje chránit osobní údaje koncoví uživatelé.</span><span class="sxs-lookup"><span data-stu-id="f130c-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="f130c-104">Při vytváření aplikace pomocí [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], verze 3.0, vaše aplikace může mít vliv na vaši koncoví uživatelé o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="f130c-104">When you build an application using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="f130c-105">Například aplikace může shromažďovat explicitně kontaktní informace o uživateli, nebo může požádat nebo poslat informace přes Internet na webové stránky.</span><span class="sxs-lookup"><span data-stu-id="f130c-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="f130c-106">Pokud vložíte technologie společnosti Microsoft v aplikaci, že technologie může mít svůj vlastní chování, které by mohly ovlivnit ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="f130c-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-107">neodesílá žádné informace společnosti Microsoft z vaší aplikace Pokud jste nebo koncový uživatel se rozhodnete odeslat do us.</span><span class="sxs-lookup"><span data-stu-id="f130c-107"> does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="f130c-108">WCF v Brief</span><span class="sxs-lookup"><span data-stu-id="f130c-108">WCF in Brief</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-109">distribuované zasílání zpráv rozhraní používá rozhraní Microsoft .NET Framework, která umožňuje vývojářům vytvářet distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-109"> is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="f130c-110">Přenášená mezi dvěma aplikacemi zprávy obsahují informace hlavičky a text.</span><span class="sxs-lookup"><span data-stu-id="f130c-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="f130c-111">Záhlaví může obsahovat směrování zpráv, informace o zabezpečení, transakce a další v závislosti na služby, které aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="f130c-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="f130c-112">Ve výchozím nastavení jsou obvykle šifrované zprávy.</span><span class="sxs-lookup"><span data-stu-id="f130c-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="f130c-113">Jedinou výjimkou je při použití `BasicHttpBinding`, který byl navržený pro použití s webovými službami-zabezpečené, starší verze.</span><span class="sxs-lookup"><span data-stu-id="f130c-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="f130c-114">Jako návrháře aplikací jste zodpovědní za konečný návrh.</span><span class="sxs-lookup"><span data-stu-id="f130c-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="f130c-115">Zprávy v těle protokolu SOAP obsahovat data, specifické pro aplikaci; však tato data, jako je například osobní informace definované aplikací, může být zabezpečené pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] funkce šifrování nebo důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="f130c-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] encryption or confidentiality features.</span></span> <span data-ttu-id="f130c-116">Následující části popisují funkce, které mohou mít vliv na ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="f130c-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="f130c-117">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="f130c-117">Messaging</span></span>  
 <span data-ttu-id="f130c-118">Každý [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zpráva má hlavičku adresy, která určuje cíl zprávy a kde se má zobrazit odpověď.</span><span class="sxs-lookup"><span data-stu-id="f130c-118">Each [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="f130c-119">Komponenta adresy adresu koncového bodu je identifikátor URI (Uniform Resource) identifikující koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f130c-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="f130c-120">Adresa může být síťová adresa nebo logické adresy.</span><span class="sxs-lookup"><span data-stu-id="f130c-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="f130c-121">Adresa může zahrnovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu.</span><span class="sxs-lookup"><span data-stu-id="f130c-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="f130c-122">Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID), nebo kolekce identifikátory GUID pro dočasné adresování použít pro každou adresu rozpoznat.</span><span class="sxs-lookup"><span data-stu-id="f130c-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="f130c-123">Každá zpráva obsahuje ID zprávy, která je identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="f130c-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="f130c-124">Tato funkce se řídí odkaz standard adresování WS.</span><span class="sxs-lookup"><span data-stu-id="f130c-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="f130c-125">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Vrstva zasílání zpráv nelze zapsat žádné osobní údaje v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f130c-125">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="f130c-126">Však ho může pokud vývojář service vytvoří služba, která zveřejňuje informace (například pomocí v název koncového bodu jméno uživatele, nebo se včetně osobních údajů v Web pro koncový bod rozšířit osobní informace na úrovni sítě Služby s popisem jazyka, ale které nevyžadují klienti používat protokol https pro přístup k schématu WSDL).</span><span class="sxs-lookup"><span data-stu-id="f130c-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="f130c-127">Navíc pokud běží Vývojář [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro koncový bod, který zveřejňuje osobní údaje, výstup nástroje může obsahovat tyto informace a výstupní soubor je zapsán do místní pevný disk.</span><span class="sxs-lookup"><span data-stu-id="f130c-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="f130c-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="f130c-128">Hosting</span></span>  
 <span data-ttu-id="f130c-129">Hostování funkcí v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umožňuje aplikacím můžete spustit na vyžádání nebo povolit sdílení portů mezi různými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="f130c-129">The hosting feature in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="f130c-130">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Aplikace může být hostovaný v Internetové informační služby (IIS), podobně jako [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f130c-130">An [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="f130c-131">Hostování nevystavuje žádné konkrétní informace v síti a není jej ponechat data v počítači.</span><span class="sxs-lookup"><span data-stu-id="f130c-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="f130c-132">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="f130c-132">Message Security</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-133">funkce zabezpečení poskytuje funkce zabezpečení pro aplikace zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f130c-133"> security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="f130c-134">Funkce zabezpečení poskytuje zahrnují ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="f130c-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="f130c-135">Ověřování se provádí pomocí předání přihlašovacích údajů mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="f130c-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="f130c-136">Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu nebo prostřednictvím protokolu SOAP zprávy úroveň zabezpečení, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f130c-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="f130c-137">V zabezpečení zpráv protokolu SOAP provádí se ověření pomocí přihlašovacích údajů jako uživatelského jména a hesla, certifikáty X.509, lístky protokolu Kerberos a tokeny SAML, které mohou obsahovat osobní informace, v závislosti na vystavitele.</span><span class="sxs-lookup"><span data-stu-id="f130c-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="f130c-138">Pomocí zabezpečení přenosu, ověření se provádí pomocí tradičního přenosu ověřovací mechanismy, které jako schémat ověřování protokolu HTTP (Basic, ověřování algoritmem Digest, Negotiate, integrované ověřování systému Windows, protokol NTLM, None a anonymní) a ověření formuláře.</span><span class="sxs-lookup"><span data-stu-id="f130c-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="f130c-139">Ověřování může způsobit v zabezpečené relaci mezi komunikuje koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f130c-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="f130c-140">Relace je identifikována identifikátor GUID, který trvá po dobu životnosti relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f130c-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="f130c-141">Následující tabulka uvádí, co se ukládají a kde.</span><span class="sxs-lookup"><span data-stu-id="f130c-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="f130c-142">Data</span><span class="sxs-lookup"><span data-stu-id="f130c-142">Data</span></span>|<span data-ttu-id="f130c-143">Úložiště</span><span class="sxs-lookup"><span data-stu-id="f130c-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="f130c-144">Přihlašovací údaje prezentace, například uživatelské jméno, certifikáty X.509, tokeny pomocí protokolu Kerberos a odkazy na přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="f130c-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="f130c-145">Standardní Windows pověření správu mechanismy, jako je Windows úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f130c-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="f130c-146">Informace členství uživatele, například uživatelská jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="f130c-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="f130c-147">zprostředkovateli členství.</span><span class="sxs-lookup"><span data-stu-id="f130c-147"> membership providers.</span></span>|  
|<span data-ttu-id="f130c-148">Identity informace o službě, kterou používá k ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="f130c-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="f130c-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="f130c-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="f130c-150">Informace o subjektu volajícím.</span><span class="sxs-lookup"><span data-stu-id="f130c-150">Caller information.</span></span>|<span data-ttu-id="f130c-151">V protokolech auditování.</span><span class="sxs-lookup"><span data-stu-id="f130c-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="f130c-152">Auditování</span><span class="sxs-lookup"><span data-stu-id="f130c-152">Auditing</span></span>  
 <span data-ttu-id="f130c-153">Auditování zaznamenává úspěchy a chyby ověřování a autorizace událostí.</span><span class="sxs-lookup"><span data-stu-id="f130c-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="f130c-154">Auditování záznamy obsahují následující data: služby URI, identifikátor URI akce a identifikace volajícího.</span><span class="sxs-lookup"><span data-stu-id="f130c-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="f130c-155">Auditování také záznamy, když správce upraví konfiguraci protokolování zpráv (ho na zapnutí a vypnutí funkce), protože protokolování zpráv může protokolovat data specifické pro aplikaci v záhlaví a obsah.</span><span class="sxs-lookup"><span data-stu-id="f130c-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="f130c-156">Pro [!INCLUDE[wxp](../../../includes/wxp-md.md)], záznam se zaznamenají do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="f130c-157">Pro [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], záznam se zaznamenají do protokolu událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f130c-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="f130c-158">Transakce</span><span class="sxs-lookup"><span data-stu-id="f130c-158">Transactions</span></span>  
 <span data-ttu-id="f130c-159">Transakce funkce poskytuje transakční služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-159">The transactions feature provides transactional services to a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span>  
  
 <span data-ttu-id="f130c-160">Záhlaví transakce používá v transakci šíření může obsahovat ID transakce nebo zařazení ID, které jsou identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="f130c-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="f130c-161">Transakce funkce používá správce transakcí Microsoft Distributed Transaction Coordinator služba MSDTC () (součásti systému Windows) ke správě stav transakce.</span><span class="sxs-lookup"><span data-stu-id="f130c-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="f130c-162">Ve výchozím nastavení jsou zašifrovaná komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="f130c-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="f130c-163">Správci transakcí může odkazy na koncový bod, ID transakce a zařazení ID protokolu v rámci jejich trvalého stavu.</span><span class="sxs-lookup"><span data-stu-id="f130c-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="f130c-164">Životnost tento stav je určen podle životnost soubor protokolu správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="f130c-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="f130c-165">Služba koordinátoru MS DTC vlastní a spravuje tento protokol.</span><span class="sxs-lookup"><span data-stu-id="f130c-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="f130c-166">Transakce funkce implementuje WS-koordinace a WS-Atomic Transactions standardy.</span><span class="sxs-lookup"><span data-stu-id="f130c-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="f130c-167">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="f130c-167">Reliable Sessions</span></span>  
 <span data-ttu-id="f130c-168">Spolehlivé relace v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zadejte přenos zpráv, když dojde k selhání přenos nebo prostředník.</span><span class="sxs-lookup"><span data-stu-id="f130c-168">Reliable sessions in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="f130c-169">Poskytují přesně-jednou přenosu zpráv i v případě, že základní přenos odpojí (například připojení protokolu TCP v bezdrátové síti) nebo zruší zprávu (proxy serveru HTTP vyřadit zprávu příchozí nebo odchozí).</span><span class="sxs-lookup"><span data-stu-id="f130c-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="f130c-170">Spolehlivé relace také obnovit zprávy změna (jak může dojít v případě více cest směrování), zachování pořadí, ve které byly odeslány zprávy.</span><span class="sxs-lookup"><span data-stu-id="f130c-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="f130c-171">Spolehlivé relace se implementují pomocí protokolu WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="f130c-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="f130c-172">Zvyšují WS-RM hlavičky, které obsahují informace o relace, které slouží k identifikaci všechny zprávy, které jsou spojené s konkrétní spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="f130c-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="f130c-173">Každá relace WS-RM má identifikátor, který je identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="f130c-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="f130c-174">Žádné osobní informace se uchovávají v počítači uživatele end.</span><span class="sxs-lookup"><span data-stu-id="f130c-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="f130c-175">Kanály zařazených do fronty</span><span class="sxs-lookup"><span data-stu-id="f130c-175">Queued Channels</span></span>  
 <span data-ttu-id="f130c-176">Fronty ukládat zprávy z odesílající aplikací jménem přijímající aplikace a později předávat tyto zprávy do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="f130c-177">Mohou pomoci při má přijímající aplikace je třeba přechodný zajišťování přenos zpráv z odesílání na přijímací aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-178">poskytuje podporu pro službu Řízení front pomocí Microsoft služby Řízení front zpráv (MSMQ) jako přenosového mechanismu.</span><span class="sxs-lookup"><span data-stu-id="f130c-178"> provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="f130c-179">Funkci ve frontě kanály nepřidá záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="f130c-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="f130c-180">Místo toho se vytvoří zprávy služby Řízení front zpráv s příslušné služby Řízení front zpráv sady zpráv vlastnosti a volá metody služby Řízení front zpráv se umístí zprávy ve frontě služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="f130c-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="f130c-181">Služba Řízení front zpráv je volitelná součást, která se dodává s verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f130c-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="f130c-182">Žádné informace se uchovávají na počítači koncového uživatele na funkcí ve frontě kanály, protože používá služby Řízení front zpráv jako front infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f130c-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="f130c-183">Integrace COM+</span><span class="sxs-lookup"><span data-stu-id="f130c-183">COM+ Integration</span></span>  
 <span data-ttu-id="f130c-184">Tato funkce zabalí stávající funkce COM a modelu COM + k vytvoření služby, které jsou kompatibilní s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="f130c-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="f130c-185">Tato funkce nepoužívá konkrétní hlavičky a neuchovává data na počítači koncového uživatele je.</span><span class="sxs-lookup"><span data-stu-id="f130c-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="f130c-186">Monikeru služby COM</span><span class="sxs-lookup"><span data-stu-id="f130c-186">COM Service Moniker</span></span>  
 <span data-ttu-id="f130c-187">To poskytuje nespravované obálka pro standardní [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="f130c-187">This provides an unmanaged wrapper to a standard [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="f130c-188">Tato funkce nemá konkrétní hlavičky v drátové síti ani nemá zachovat data na počítači.</span><span class="sxs-lookup"><span data-stu-id="f130c-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="f130c-189">Rovnocenný kanál</span><span class="sxs-lookup"><span data-stu-id="f130c-189">Peer Channel</span></span>  
 <span data-ttu-id="f130c-190">Rovnocenného kanálu umožňuje vývoj více stran aplikací pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f130c-190">A peer channel enables development of multiparty applications using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f130c-191">Více stran zasílání zpráv dojde v kontextu mřížku.</span><span class="sxs-lookup"><span data-stu-id="f130c-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="f130c-192">Mřížek jsou identifikovány názvem, který se můžete zapojit do uzlů.</span><span class="sxs-lookup"><span data-stu-id="f130c-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="f130c-193">Každý uzel v rovnocenného kanálu vytvoří naslouchací proces TCP na portu zadán uživatel a navázat připojení s ostatními uzly v mřížce zajistit odolnost proti chybám.</span><span class="sxs-lookup"><span data-stu-id="f130c-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="f130c-194">Pokud chcete připojit k jiné uzly v mřížce, uzly také exchange některá data, včetně adres naslouchací proces a IP adres je počítač, se jiné uzly v mřížce.</span><span class="sxs-lookup"><span data-stu-id="f130c-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="f130c-195">Zprávy odeslané kolem v mřížce může obsahovat informace o zabezpečení, která se týkají odesílatele, aby se zabránilo falšování identity zprávu a manipulaci.</span><span class="sxs-lookup"><span data-stu-id="f130c-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="f130c-196">Žádné osobní informace jsou uloženy na počítači uživatele end.</span><span class="sxs-lookup"><span data-stu-id="f130c-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="f130c-197">Prostředí pro odborníky v oblasti IT</span><span class="sxs-lookup"><span data-stu-id="f130c-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="f130c-198">Trasování</span><span class="sxs-lookup"><span data-stu-id="f130c-198">Tracing</span></span>  
 <span data-ttu-id="f130c-199">Diagnostika funkci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastruktury protokoly zprávy, které předání modelu vrstev přenosu a služby a aktivit a událostí související se tyto zprávy.</span><span class="sxs-lookup"><span data-stu-id="f130c-199">The diagnostics feature of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="f130c-200">Tato funkce je ve výchozím nastavení vypnutý.</span><span class="sxs-lookup"><span data-stu-id="f130c-200">This feature is turned off by default.</span></span> <span data-ttu-id="f130c-201">Je povolena, pomocí konfiguračního souboru aplikace a chování trasování může být změněna pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zprostředkovatele rozhraní WMI v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f130c-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WMI provider at run time.</span></span> <span data-ttu-id="f130c-202">Když je povolené, vysílá infrastruktury trasování diagnostické trasování, která obsahuje zprávy, aktivity a zpracování události nakonfigurované naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="f130c-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="f130c-203">Formát a umístění výstupu určuje možnostmi konfigurace naslouchací proces správce, ale je obvykle formátovaný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="f130c-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="f130c-204">Správce je zodpovědný za nastavení seznamu řízení přístupu (ACL) pro trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="f130c-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="f130c-205">Zejména při hostování podle aktivace systému Windows (WAS), správce Ujistěte se, že soubory nejsou zpracovat z veřejné virtuálního kořenového adresáře, pokud je, není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="f130c-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="f130c-206">Existují dva typy trasování: protokolování zpráv a Model služby diagnostické trasování, popsané v následující části.</span><span class="sxs-lookup"><span data-stu-id="f130c-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="f130c-207">Každý typ je konfigurovaný pomocí vlastní zdroj trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="f130c-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="f130c-208">Obě tyto zdroje protokolování trasování zachytit data, která je lokální vzhledem k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f130c-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="f130c-209">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="f130c-209">Message Logging</span></span>  
 <span data-ttu-id="f130c-210">Protokolování zdroj trasování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správcům zprávy protokolu s tokem prostřednictvím systému.</span><span class="sxs-lookup"><span data-stu-id="f130c-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="f130c-211">Prostřednictvím konfigurace může uživatel rozhodnout protokolu celé zprávy nebo pouze hlavičky zpráv, zda se mají protokolovat v modelu vrstev přenosu nebo služby a zda mají být zahrnuty poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f130c-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="f130c-212">Tento uživatel také může nakonfigurovat filtrování a omezit, které zprávy se zaznamenávají.</span><span class="sxs-lookup"><span data-stu-id="f130c-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="f130c-213">Ve výchozím nastavení je protokolování zpráv zakázaná.</span><span class="sxs-lookup"><span data-stu-id="f130c-213">By default, message logging is disabled.</span></span> <span data-ttu-id="f130c-214">Zapnutí protokolování zpráv na úrovni aplikace správce můžete zabránit správce místního počítače.</span><span class="sxs-lookup"><span data-stu-id="f130c-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="f130c-215">Protokolování zpráv šifrovaná a dešifrovaným</span><span class="sxs-lookup"><span data-stu-id="f130c-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="f130c-216">Zprávy se protokolují, zašifrovaná nebo dešifrovat, jak je popsáno v následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="f130c-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="f130c-217">Protokolování přenosu</span><span class="sxs-lookup"><span data-stu-id="f130c-217">Transport Logging</span></span>  
 <span data-ttu-id="f130c-218">Zaznamenává zprávy přijatých a odeslaných na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="f130c-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="f130c-219">Tyto zprávy obsahují všechny hlavičky a může být šifrována před odesláním v drátové síti a pokud se přijímají.</span><span class="sxs-lookup"><span data-stu-id="f130c-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="f130c-220">Pokud jsou šifrované zprávy před odesláním v drátové síti a při příjmu, jsou zaznamenány šifrovaná i.</span><span class="sxs-lookup"><span data-stu-id="f130c-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="f130c-221">Výjimkou je, pokud protokol zabezpečení používané (https): pak jsou zaznamenány dešifrovat před odesláním a po přijímání i v případě, že se šifrují v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="f130c-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="f130c-222">Protokolování služby</span><span class="sxs-lookup"><span data-stu-id="f130c-222">Service Logging</span></span>  
 <span data-ttu-id="f130c-223">Zaznamenává zprávy přijatých nebo odeslaných na úrovni modelu služby, po zpracování záhlaví kanálu došlo k, těsně před a po zadání uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="f130c-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="f130c-224">Zprávy zaznamenané na této úrovni jsou dešifrovat i v případě, že by byly zabezpečená a šifrovaná v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="f130c-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="f130c-225">Protokolování poškozených zpráv</span><span class="sxs-lookup"><span data-stu-id="f130c-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="f130c-226">Protokoly zpráv, který [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastruktury nemůže pochopit nebo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f130c-226">Logs messages that the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="f130c-227">Zprávy se zaznamenávají jako-je, který je šifrovaná, nebo není</span><span class="sxs-lookup"><span data-stu-id="f130c-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="f130c-228">Když jsou přihlášení zprávy dešifrovat nebo nezašifrované podobě, ve výchozím nastavení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] odebere klíče zabezpečení a potenciálně osobní informace ze zprávy před jejich protokolování.</span><span class="sxs-lookup"><span data-stu-id="f130c-228">When messages are logged in decrypted or unencrypted form, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="f130c-229">Další části popisují, jaké informace se odebere a kdy.</span><span class="sxs-lookup"><span data-stu-id="f130c-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="f130c-230">Správce počítače a nástroje pro nasazení aplikace musí provést určité akce konfigurace, chcete-li změnit výchozí chování do protokolu klíče a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="f130c-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="f130c-231">Informace o odebrat z hlavičky zpráv, pokud protokolování dešifrovat nebo bez šifrování zprávy</span><span class="sxs-lookup"><span data-stu-id="f130c-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="f130c-232">Když zprávy se protokolují v dešifrovat nezašifrované podobě zabezpečení klíčů a potenciálně osobní údaje jsou odebrány ve výchozím nastavení z hlavičky zpráv a obsah zpráv předtím, než jsou zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="f130c-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="f130c-233">V následujícím seznamu jsou co [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zvažuje klíče a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="f130c-233">The following list shows what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="f130c-234">Klíče, které jsou odebrány:</span><span class="sxs-lookup"><span data-stu-id="f130c-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="f130c-235">\-Pro xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="f130c-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="f130c-236">WSt:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="f130c-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="f130c-237">WSt:Entropy</span><span class="sxs-lookup"><span data-stu-id="f130c-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="f130c-238">\-Pro xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="f130c-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="f130c-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="f130c-239">wsse:Password</span></span>  
  
 <span data-ttu-id="f130c-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="f130c-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="f130c-241">Potenciálně osobní údaje, které byly odstraněny:</span><span class="sxs-lookup"><span data-stu-id="f130c-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="f130c-242">\-Pro xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="f130c-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="f130c-243">wsse:username</span><span class="sxs-lookup"><span data-stu-id="f130c-243">wsse:Username</span></span>  
  
 <span data-ttu-id="f130c-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="f130c-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="f130c-245">\-Pro xmlns:saml = "urn: oasis: názvy: tc: SAML:1.0:assertion" položky tučným písmem (dole) jsou odebrány:</span><span class="sxs-lookup"><span data-stu-id="f130c-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="f130c-246">\<Kontrolní výraz</span><span class="sxs-lookup"><span data-stu-id="f130c-246">\<Assertion</span></span>  
  
 <span data-ttu-id="f130c-247">MajorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="f130c-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="f130c-248">MinorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="f130c-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="f130c-249">AssertionId = "[ID]"</span><span class="sxs-lookup"><span data-stu-id="f130c-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="f130c-250">Vystavitel = "[řetězec]"</span><span class="sxs-lookup"><span data-stu-id="f130c-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="f130c-251">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="f130c-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="f130c-252">\<Podmínky neplatí před = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="f130c-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="f130c-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="f130c-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="f130c-254">\<Cílová skupina > [uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="f130c-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="f130c-255">\</ AudienceRestrictionCondition > *</span><span class="sxs-lookup"><span data-stu-id="f130c-255">\</AudienceRestrictionCondition>*</span></span>  
  
 <span data-ttu-id="f130c-256">\<DoNotCacheCondition / > *</span><span class="sxs-lookup"><span data-stu-id="f130c-256">\<DoNotCacheCondition />*</span></span>  
  
 <span data-ttu-id="f130c-257"><\!--abstraktní základní typ</span><span class="sxs-lookup"><span data-stu-id="f130c-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="f130c-258">\<Podmínka / > *</span><span class="sxs-lookup"><span data-stu-id="f130c-258">\<Condition />*</span></span>  
  
 -->  
  
 <span data-ttu-id="f130c-259">\</ Podmínky >?</span><span class="sxs-lookup"><span data-stu-id="f130c-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="f130c-260">\<Rady, jak ></span><span class="sxs-lookup"><span data-stu-id="f130c-260">\<Advice></span></span>  
  
 <span data-ttu-id="f130c-261">\<AssertionIDReference > [ID]\</AssertionIDReference > *</span><span class="sxs-lookup"><span data-stu-id="f130c-261">\<AssertionIDReference>[ID]\</AssertionIDReference>*</span></span>  
  
 <span data-ttu-id="f130c-262">\<Kontrolní výraz > [assertion]\</Assertion > *</span><span class="sxs-lookup"><span data-stu-id="f130c-262">\<Assertion>[assertion]\</Assertion>*</span></span>  
  
 <span data-ttu-id="f130c-263">[žádné] *</span><span class="sxs-lookup"><span data-stu-id="f130c-263">[any]*</span></span>  
  
 <span data-ttu-id="f130c-264">\</ Poradenství >?</span><span class="sxs-lookup"><span data-stu-id="f130c-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="f130c-265"><\!--Abstraktní základní typy</span><span class="sxs-lookup"><span data-stu-id="f130c-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="f130c-266">\<Příkaz / > *</span><span class="sxs-lookup"><span data-stu-id="f130c-266">\<Statement />*</span></span>  
  
 <span data-ttu-id="f130c-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="f130c-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="f130c-268">\<Předmět ></span><span class="sxs-lookup"><span data-stu-id="f130c-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="f130c-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="f130c-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="f130c-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="f130c-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="f130c-271">\<SubjectConfirmationData > [žádné]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="f130c-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="f130c-272">\<DS:KeyInfo >... \</ds:KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="f130c-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="f130c-273">\</ SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="f130c-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="f130c-274">\</ Předmět ></span><span class="sxs-lookup"><span data-stu-id="f130c-274">\</Subject></span></span>  
  
 <span data-ttu-id="f130c-275">\</ SubjectStatement > *</span><span class="sxs-lookup"><span data-stu-id="f130c-275">\</SubjectStatement>*</span></span>  
  
 -->  
  
 <span data-ttu-id="f130c-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="f130c-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="f130c-277">AuthenticationMethod = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="f130c-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="f130c-278">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="f130c-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="f130c-279">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="f130c-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="f130c-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="f130c-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="f130c-281">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="f130c-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="f130c-282">Umístění = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="f130c-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="f130c-283">Vazba = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="f130c-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="f130c-284">\</ AuthenticationStatement > *</span><span class="sxs-lookup"><span data-stu-id="f130c-284">\</AuthenticationStatement>*</span></span>  
  
 <span data-ttu-id="f130c-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="f130c-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="f130c-286">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="f130c-286">[Subject]</span></span>  
  
 <span data-ttu-id="f130c-287">\<Atribut</span><span class="sxs-lookup"><span data-stu-id="f130c-287">\<Attribute</span></span>  
  
 <span data-ttu-id="f130c-288">AttributeName = "[řetězec]"</span><span class="sxs-lookup"><span data-stu-id="f130c-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="f130c-289">AttributeNamespace = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="f130c-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="f130c-290">\</ Atribut > +</span><span class="sxs-lookup"><span data-stu-id="f130c-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="f130c-291">\</ AttributeStatement > *</span><span class="sxs-lookup"><span data-stu-id="f130c-291">\</AttributeStatement>*</span></span>  
  
 <span data-ttu-id="f130c-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="f130c-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="f130c-293">Prostředek = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="f130c-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="f130c-294">Rozhodnutí = "[povolení &#124; odepřít &#124; neurčitém]"</span><span class="sxs-lookup"><span data-stu-id="f130c-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="f130c-295">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="f130c-295">[Subject]</span></span>  
  
 <span data-ttu-id="f130c-296">\<Akce Namespace = "[uri]" > [řetězec]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="f130c-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="f130c-297">\<Důkaz ></span><span class="sxs-lookup"><span data-stu-id="f130c-297">\<Evidence></span></span>  
  
 <span data-ttu-id="f130c-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="f130c-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="f130c-299">\<Kontrolní výraz > [assertion]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="f130c-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="f130c-300">\</ Důkazy >?</span><span class="sxs-lookup"><span data-stu-id="f130c-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="f130c-301">\</ AuthorizationDecisionStatement > *</span><span class="sxs-lookup"><span data-stu-id="f130c-301">\</AuthorizationDecisionStatement>*</span></span>  
  
 <span data-ttu-id="f130c-302">\</ Kontrolní výraz ></span><span class="sxs-lookup"><span data-stu-id="f130c-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="f130c-303">Informace z těla zprávy odstraněny, až protokolování dešifrovat nebo bez šifrování zprávy</span><span class="sxs-lookup"><span data-stu-id="f130c-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="f130c-304">Jak už bylo popsáno, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] odebere klíče a známé potenciálně osobní informace ze záhlaví zprávy zprávy zaznamenané dešifrovat nebo bez šifrování.</span><span class="sxs-lookup"><span data-stu-id="f130c-304">As previously described, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="f130c-305">Kromě toho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zabezpečení zprávy, které jsou zahrnuté v výměny klíčů.</span><span class="sxs-lookup"><span data-stu-id="f130c-305">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="f130c-306">Pro následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="f130c-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="f130c-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (například pokud není k dispozici žádná akce)</span><span class="sxs-lookup"><span data-stu-id="f130c-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="f130c-308">Pro tyto elementy textu, které zahrnují výměny klíčů jsou odebrány informace:</span><span class="sxs-lookup"><span data-stu-id="f130c-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="f130c-309">WSt:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="f130c-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="f130c-310">WSt:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="f130c-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="f130c-311">WSt:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="f130c-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="f130c-312">Informace o odebrán také pro každou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f130c-312">Information is also removed for each of the following Actions:</span></span>  
  
 <span data-ttu-id="f130c-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span><span class="sxs-lookup"><span data-stu-id="f130c-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span></span>  
  
 <span data-ttu-id="f130c-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span><span class="sxs-lookup"><span data-stu-id="f130c-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span></span>  
  
 <span data-ttu-id="f130c-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/renew</span><span class="sxs-lookup"><span data-stu-id="f130c-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew</span></span>  
  
 <span data-ttu-id="f130c-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/renew</span><span class="sxs-lookup"><span data-stu-id="f130c-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew</span></span>  
  
 <span data-ttu-id="f130c-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span><span class="sxs-lookup"><span data-stu-id="f130c-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span></span>  
  
 <span data-ttu-id="f130c-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span><span class="sxs-lookup"><span data-stu-id="f130c-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span></span>  
  
 <span data-ttu-id="f130c-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span><span class="sxs-lookup"><span data-stu-id="f130c-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span></span>  
  
 <span data-ttu-id="f130c-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span><span class="sxs-lookup"><span data-stu-id="f130c-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span></span>  
  
 <span data-ttu-id="f130c-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="f130c-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="f130c-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="f130c-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="f130c-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="f130c-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span></span>  
  
 <span data-ttu-id="f130c-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="f130c-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span></span>  
  
 <span data-ttu-id="f130c-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/renew</span><span class="sxs-lookup"><span data-stu-id="f130c-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew</span></span>  
  
 <span data-ttu-id="f130c-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/renew</span><span class="sxs-lookup"><span data-stu-id="f130c-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew</span></span>  
  
 <span data-ttu-id="f130c-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="f130c-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span></span>  
  
 <span data-ttu-id="f130c-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="f130c-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span></span>  
  
 <span data-ttu-id="f130c-329">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="f130c-329">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="f130c-330">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="f130c-330">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="f130c-331">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="f130c-331">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend</span></span>  
  
 <span data-ttu-id="f130c-332">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="f130c-332">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend</span></span>  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="f130c-333">Žádné informace se odebere z hlavičky specifické pro aplikace a Data textu</span><span class="sxs-lookup"><span data-stu-id="f130c-333">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-334">nesleduje osobní informace hlavičky specifické pro aplikaci (například řetězce dotazu) nebo text data (například číslo platební karty).</span><span class="sxs-lookup"><span data-stu-id="f130c-334"> does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="f130c-335">Pokud protokolování zpráv je zapnutý, může být osobní údaje v hlavičkách konkrétní aplikace a tělo informace viditelné v protokolech.</span><span class="sxs-lookup"><span data-stu-id="f130c-335">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="f130c-336">Nástroje pro nasazení aplikace znovu, zodpovídá za nastavení seznamy ACL v souborech konfigurace a protokolu.</span><span class="sxs-lookup"><span data-stu-id="f130c-336">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="f130c-337">Si můžete také vypnout protokolování Pokud nechce tyto informace mají být zobrazeny, nebo mu může vyfiltrovat tyto informace ze souborů protokolu, po je protokolována.</span><span class="sxs-lookup"><span data-stu-id="f130c-337">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="f130c-338">Služby modelu trasování</span><span class="sxs-lookup"><span data-stu-id="f130c-338">Service Model Tracing</span></span>  
 <span data-ttu-id="f130c-339">Zdroj trasování Model služby (<xref:System.ServiceModel>) umožňuje trasování aktivit a události související se zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="f130c-339">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="f130c-340">Tato funkce používá diagnostické funkce rozhraní .NET Framework z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="f130c-340">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="f130c-341">Stejně jako u <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> vlastnost, umístění a jeho seznamu ACL jsou uživatelsky konfigurovatelného pomocí konfigurační soubory aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f130c-341">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="f130c-342">Stejně jako u protokolování zpráv umístění souboru vždy nakonfigurované, pokud správce povolí trasování; Proto může správce nastavit seznam řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="f130c-342">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="f130c-343">Trasování obsahovat hlavičky zpráv, pokud zpráva je v oboru.</span><span class="sxs-lookup"><span data-stu-id="f130c-343">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="f130c-344">Použít stejná pravidla pro skrytí potenciálně osobní údaje v záhlaví zpráv v předchozí části: odeberou se osobní informace, které už identifikované ve výchozím nastavení z hlavičky v trasování.</span><span class="sxs-lookup"><span data-stu-id="f130c-344">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="f130c-345">Správce počítače a nástroje pro nasazení aplikace, musíte změnit konfiguraci chcete-li protokolu potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="f130c-345">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="f130c-346">Osobní informace obsažené v hlavičkách specifické pro aplikaci je ale přihlášení trasování.</span><span class="sxs-lookup"><span data-stu-id="f130c-346">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="f130c-347">Nástroje pro nasazení aplikace je zodpovědná za nastavení seznamy ACL v souborech konfigurace a trasování.</span><span class="sxs-lookup"><span data-stu-id="f130c-347">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="f130c-348">Mu taky můžete vypnout trasování Pokud nechce tyto informace mají být zobrazeny, nebo mu můžete filtrovat tyto informace z trasování souborů po je protokolována.</span><span class="sxs-lookup"><span data-stu-id="f130c-348">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="f130c-349">Jako součást ServiceModel trasování, jedinečné ID (nazývané ID aktivit a obvykle identifikátor GUID) propojit různé aktivity společně jako zprávu prochází různých částí infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f130c-349">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="f130c-350">Vlastní trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="f130c-350">Custom Trace Listeners</span></span>  
 <span data-ttu-id="f130c-351">Pro obě zprávy protokolování a trasování naslouchací proces vlastního trasování je možné nakonfigurovat, které může poslat trasování a zprávy v drátové síti (například ke vzdálené databázi).</span><span class="sxs-lookup"><span data-stu-id="f130c-351">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="f130c-352">Nástroje pro nasazení aplikace je zodpovědná za konfiguraci vlastní naslouchací procesy nebo uživatelům umožníte tak.</span><span class="sxs-lookup"><span data-stu-id="f130c-352">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="f130c-353">Také je odpovědný žádné osobní údaje, které jsou zveřejněné ve vzdáleném umístění a správně použití seznamů řízení přístupu do tohoto umístění.</span><span class="sxs-lookup"><span data-stu-id="f130c-353">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="f130c-354">Další funkce pro IT specialisty</span><span class="sxs-lookup"><span data-stu-id="f130c-354">Other features for IT Professionals</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-355">má poskytovatel rozhraní WMI, který zveřejňuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] informace o konfiguraci infrastruktury prostřednictvím rozhraní WMI (dodávané se systémem Windows).</span><span class="sxs-lookup"><span data-stu-id="f130c-355"> has a WMI provider that exposes the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="f130c-356">Ve výchozím nastavení je k dispozici správcům rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="f130c-356">By default, the WMI interface is available to administrators.</span></span>  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-357">konfigurace používá mechanismus konfigurace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f130c-357"> configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="f130c-358">Konfigurační soubory, které jsou uložené na počítači.</span><span class="sxs-lookup"><span data-stu-id="f130c-358">The configuration files are stored on the machine.</span></span> <span data-ttu-id="f130c-359">Vývojář aplikace a správce vytvořit konfigurační soubory a seznamu ACL pro všechny požadavky na aplikace.</span><span class="sxs-lookup"><span data-stu-id="f130c-359">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="f130c-360">Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f130c-360">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="f130c-361">Certifikáty slouží k poskytování data aplikací můžete nakonfigurovat různé vlastnosti funkce, které používá aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f130c-361">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-362">také používá funkci rozhraní .NET Framework proces výpisu voláním <xref:System.Environment.FailFast%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f130c-362"> also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="f130c-363">IT specialista nástroje</span><span class="sxs-lookup"><span data-stu-id="f130c-363">IT Pro Tools</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="f130c-364">také poskytuje následující IT odborníky v oblasti nástroje, které se dodávají v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="f130c-364"> also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="f130c-365">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="f130c-365">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="f130c-366">Prohlížeč zobrazí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="f130c-366">The viewer displays [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trace files.</span></span> <span data-ttu-id="f130c-367">Prohlížeč zobrazí, ať informací obsažených v trasování.</span><span class="sxs-lookup"><span data-stu-id="f130c-367">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="f130c-368">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="f130c-368">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="f130c-369">Editor umožňuje uživatelům vytvářet a upravovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="f130c-369">The editor allows the user to create and edit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration files.</span></span> <span data-ttu-id="f130c-370">Editor zobrazuje, ať informace je obsažena v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="f130c-370">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="f130c-371">Pro stejnou úlohu můžete provést pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="f130c-371">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="f130c-372">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="f130c-372">ServiceModel_Reg</span></span>  
 <span data-ttu-id="f130c-373">Tento nástroj umožňuje uživatelům spravovat ServiceModel nainstaluje na počítač.</span><span class="sxs-lookup"><span data-stu-id="f130c-373">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="f130c-374">Nástroj zobrazí stavové zprávy v okně konzoly, když běží a v procesu, se může zobrazovat informace o konfiguraci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] instalace.</span><span class="sxs-lookup"><span data-stu-id="f130c-374">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="f130c-375">WSATConfig.exe a WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="f130c-375">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="f130c-376">Tyto nástroje povolit Odborníci v oblasti IT konfigurace umožňuje vzájemnou spolupráci podpory protokolu WS-AtomicTransaction sítě v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f130c-376">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f130c-377">Nástroje pro zobrazení a povolit uživatelům změnit hodnoty nejčastěji používané WS-AtomicTransaction nastavení uložená v registru.</span><span class="sxs-lookup"><span data-stu-id="f130c-377">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="f130c-378">Mezi vyjímání funkce</span><span class="sxs-lookup"><span data-stu-id="f130c-378">Cross-cutting Features</span></span>  
 <span data-ttu-id="f130c-379">Následující funkce jsou mezi vyjímání.</span><span class="sxs-lookup"><span data-stu-id="f130c-379">The following features are cross-cutting.</span></span> <span data-ttu-id="f130c-380">To znamená mohou být komponovaná s žádným z předchozích funkcí.</span><span class="sxs-lookup"><span data-stu-id="f130c-380">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="f130c-381">Architektura služby</span><span class="sxs-lookup"><span data-stu-id="f130c-381">Service Framework</span></span>  
 <span data-ttu-id="f130c-382">Záhlaví může obsahovat ID instance, což je identifikátor GUID, který přidruží zprávu instance třídy CLR.</span><span class="sxs-lookup"><span data-stu-id="f130c-382">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="f130c-383">Webové služby popis Language (WSDL) obsahuje definici portu.</span><span class="sxs-lookup"><span data-stu-id="f130c-383">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="f130c-384">Každý z portů má adresu koncového bodu a vazbu, která představuje služby, které aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="f130c-384">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="f130c-385">Vystavení WSDL může být vypnuto pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f130c-385">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="f130c-386">Žádné informace se uchovávají v počítači.</span><span class="sxs-lookup"><span data-stu-id="f130c-386">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f130c-387">Viz také</span><span class="sxs-lookup"><span data-stu-id="f130c-387">See Also</span></span>  
 [<span data-ttu-id="f130c-388">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f130c-388">Windows Communication Foundation</span></span>](http://msdn.microsoft.com/en-us/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="f130c-389">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f130c-389">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
