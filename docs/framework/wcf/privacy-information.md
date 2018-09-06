---
title: Windows Communication Foundation – informace o ochraně osobních údajů
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 9c2a8d89fc62f8e3e0ce17f13604a6ba05df1a6f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799197"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="4f5a6-102">Windows Communication Foundation – informace o ochraně osobních údajů</span><span class="sxs-lookup"><span data-stu-id="4f5a6-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="4f5a6-103">Společnost Microsoft se zavazuje chránit osobní údaje koncoví uživatelé.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="4f5a6-104">Při vytvoření aplikace využívající Windows Communication Foundation (WCF), verze 3.0, vaše aplikace může mít vliv na vaše koncové uživatele o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="4f5a6-105">Například vaše aplikace explicitně shromažďovat informace o uživateli, nebo může požádat o nebo odeslat informace přes Internet k vašemu webovému serveru.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="4f5a6-106">Pokud vložíte technologie společnosti Microsoft ve vaší aplikaci, tato technologie může mít svůj vlastní chování, které můžou ovlivnit ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="4f5a6-107">WCF neodešle žádné informace o společnosti Microsoft z vaší aplikace Pokud vy nebo koncový uživatel se rozhodnete odeslat na nás.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="4f5a6-108">Přehled WCF</span><span class="sxs-lookup"><span data-stu-id="4f5a6-108">WCF in Brief</span></span>  
 <span data-ttu-id="4f5a6-109">WCF je distribuovaná architektura zasílání zpráv pomocí rozhraní Microsoft .NET Framework, která umožňuje vývojářům vytvářet distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="4f5a6-110">Komunikace mezi dvěma aplikacemi zprávy obsahují informace záhlaví a text.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="4f5a6-111">Záhlaví může obsahovat směrování zpráv, informace o zabezpečení, transakce a déle v závislosti na služby používané aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="4f5a6-112">Ve výchozím nastavení jsou obvykle šifrované zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="4f5a6-113">Jedinou výjimkou je při použití `BasicHttpBinding`, která je navržená pro použití s nezabezpečené, starší verze webových služeb.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="4f5a6-114">Při návrhu aplikace zodpovídáte za konečný návrh.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="4f5a6-115">Zprávy v těle SOAP obsahují data specifická pro aplikaci; Tato data, jako je například osobní informace definované aplikací, ale můžete zabezpečit pomocí funkce šifrování nebo důvěrnosti WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="4f5a6-116">Následující části popisují funkce, které mohou mít vliv na ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="4f5a6-117">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="4f5a6-117">Messaging</span></span>  
 <span data-ttu-id="4f5a6-118">Hlavička adresy, která určuje cíl zprávy má každá zpráva WCF a kde by měly patřit odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="4f5a6-119">Součást adresy adresy koncového bodu je identifikátor URI (Uniform Resource), který identifikuje koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="4f5a6-120">Adresa může být síťové adresy nebo logické adresy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="4f5a6-121">Adresa může obsahovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="4f5a6-122">Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID), nebo kolekci identifikátorů GUID pro účely dočasné řešení umožňuje rozpoznat každou adresu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="4f5a6-123">Každá zpráva obsahuje ID zprávy, které je identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="4f5a6-124">Tato funkce se řídí standardu WS-Addressing odkaz.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="4f5a6-125">Vrstva zasílání zpráv WCF nezapisuje žádnými osobními údaji v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="4f5a6-126">Však to může-li vývojářem služeb vytvořil službu, která poskytuje tyto informace (například pomocí v názvu koncového bodu jméno uživatele, nebo se včetně osobních údajů na webu koncový bod šířit osobní informace na úrovni sítě Služby popis jazyka, ale nevyžaduje klientů na používání protokolu https pro přístup k rozhraní jazyka WSDL).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="4f5a6-127">Také pokud běží Vývojář [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro koncový bod, který zpřístupňuje osobní údaje, výstup nástroje můžou obsahovat tyto informace a je zapsaný do výstupního souboru místní disk.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="4f5a6-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-128">Hosting</span></span>  
 <span data-ttu-id="4f5a6-129">Hostování funkcí ve službě WCF umožňuje aplikacím spustit na vyžádání nebo povolit sdílení portů mezi více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="4f5a6-130">Aplikace WCF je možné hostovat v Internetové informační služby (IIS), podobně jako [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f5a6-130">An WCF application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="4f5a6-131">Hostování nevystavuje žádné konkrétní informace v síti a neudržuje data na počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="4f5a6-132">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="4f5a6-132">Message Security</span></span>  
 <span data-ttu-id="4f5a6-133">Zabezpečení WCF zajišťuje bezpečnostní funkce pro zasílání zpráv aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="4f5a6-134">Poskytuje funkce zabezpečení zahrnují ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="4f5a6-135">Ověřování se provádí pomocí přihlašovacích údajů mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="4f5a6-136">Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu nebo prostřednictvím protokolu SOAP zprávy zabezpečení na úrovni, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="4f5a6-137">V zabezpečení zpráv SOAP provádí se ověření pomocí přihlašovacích údajů, jako je uživatelské jméno a hesla, certifikáty X.509, lístky protokolu Kerberos a tokeny SAML, které mohou obsahovat osobní informace, podle toho, že vystavitel.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="4f5a6-138">Pomocí zabezpečení přenosu, ověření se provádí pomocí tradičního přenosu ověřovací mechanismy, jako jsou schémata HTTP ověřování (Basic, Digest, Negotiate, integrované ověřování Windows, protokolu NTLM, None a anonymní) a ověření formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="4f5a6-139">Ověřování může vést k zabezpečenou relaci mezi komunikujícími koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="4f5a6-140">Relace je identifikován identifikátor GUID, který trvá životnost relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="4f5a6-141">Následující tabulka uvádí, co se ukládají a kdekoli.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="4f5a6-142">Data</span><span class="sxs-lookup"><span data-stu-id="4f5a6-142">Data</span></span>|<span data-ttu-id="4f5a6-143">Úložiště</span><span class="sxs-lookup"><span data-stu-id="4f5a6-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="4f5a6-144">Prezentace pověření, jako je například uživatelské jméno, certifikáty X.509, tokenů Kerberos a odkazy na přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="4f5a6-145">Standardní Windows přihlašovacích údajů mechanismy správy, jako je úložiště certifikátů Windows.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="4f5a6-146">Členství informace o uživateli, jako jsou uživatelská jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="4f5a6-147"> zprostředkovateli členství.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-147"> membership providers.</span></span>|  
|<span data-ttu-id="4f5a6-148">Informace o identitě týkající se služby používá k ověření služby pro klienty.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="4f5a6-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="4f5a6-150">Informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-150">Caller information.</span></span>|<span data-ttu-id="4f5a6-151">Protokoly auditování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="4f5a6-152">Auditování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-152">Auditing</span></span>  
 <span data-ttu-id="4f5a6-153">Auditování zaznamenává úspěchy a chyby ověřování a autorizace událostí.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="4f5a6-154">Záznamy auditu obsahují následující data: identifikátor URI, identifikátor URI akce a identifikace volajícího.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="4f5a6-155">Auditování také záznamy, pokud správce změní konfiguraci protokolování zpráv (ho na zapnutí a vypnutí funkce), protože protokolování zpráv může protokolovat data specifická pro aplikaci v záhlaví a obsah.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="4f5a6-156">Pro [!INCLUDE[wxp](../../../includes/wxp-md.md)], záznam se zaznamenají do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="4f5a6-157">Pro [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], záznam se zaznamenají do protokolu událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="4f5a6-158">Transakce</span><span class="sxs-lookup"><span data-stu-id="4f5a6-158">Transactions</span></span>  
 <span data-ttu-id="4f5a6-159">Transakce funkce poskytuje transakční služeb k aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="4f5a6-160">Záhlaví transakce používat při šíření transakcí může obsahovat ID transakce nebo zařazení ID, které jsou identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="4f5a6-161">Transakce funkce používá správce transakcí Microsoft distribuované transakce koordinátor (MSDTC) (součást Windows) ke správě stavu transakce.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="4f5a6-162">Ve výchozím nastavení jsou zašifrovaná komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="4f5a6-163">Správci transakcí může protokolovat Reference koncového bodu, ID transakce a zařazení ID jako součást svých trvalého stavu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="4f5a6-164">Doba platnosti tohoto stavu se určuje podle doby života souboru protokolu správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="4f5a6-165">Služba MSDTC vlastní a spravuje tento protokol.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="4f5a6-166">Transakce funkce implementuje standardů WS-koordinaci a protokolu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="4f5a6-167">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="4f5a6-167">Reliable Sessions</span></span>  
 <span data-ttu-id="4f5a6-168">Spolehlivé relace ve službě WCF poskytují přenos zpráv při přenosu nebo zprostředkující selhání.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="4f5a6-169">Poskytují právě – jednou přenos zpráv, i v případě, že je základní přenos odpojí (například připojení protokolu TCP v bezdrátové síti) nebo ztratí zprávu (proxy server HTTP vyřadit odchozí nebo příchozí zprávy).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="4f5a6-170">Spolehlivé relace také obnovit zprávu změny pořadí (jak se může stát v případě více cest směrování), zachovávají pořadí, ve kterém byly odeslané zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="4f5a6-171">Spolehlivé relace jsou implementovány pomocí protokolu WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="4f5a6-172">Přidávají WS-RM hlavičky, které obsahují informace o relaci, která se používá k identifikaci všech zpráv přidružených k určité stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="4f5a6-173">Každá relace WS-RM má identifikátor, což je identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="4f5a6-174">Žádné osobní informace se uchovávají v počítači koncového uživatele společnosti.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="4f5a6-175">Ve frontě kanálů</span><span class="sxs-lookup"><span data-stu-id="4f5a6-175">Queued Channels</span></span>  
 <span data-ttu-id="4f5a6-176">Fronty ukládání zpráv od odeslání aplikace jménem přijímající aplikace a později předávání těchto zpráv do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="4f5a6-177">Pomáhají zajistit přenos zpráv z odeslání aplikace na přijímající aplikace po, například přijímající aplikace přechodné.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="4f5a6-178">WCF poskytuje podporu pro službu Řízení front s použitím Microsoft Message Queuing (MSMQ) jako přenosového mechanismu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="4f5a6-179">Funkce ve frontě kanálů nepřidá záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="4f5a6-180">Místo toho vytvoří zprávy služby Řízení front zpráv se příslušné služby Řízení front zpráv sady zpráv vlastnosti a volá metody služby Řízení front zpráv vložit zprávu do fronty služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="4f5a6-181">Služba Řízení front zpráv je volitelná součást, která se dodává s Windows.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="4f5a6-182">Žádné informace se uchovávají v počítači koncového uživatele na funkcí ve frontě kanálů, protože ho používá jako infrastruktura zařazování služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="4f5a6-183">Integrace COM+</span><span class="sxs-lookup"><span data-stu-id="4f5a6-183">COM+ Integration</span></span>  
 <span data-ttu-id="4f5a6-184">Tato funkce zabalí stávajících funkcí modelu COM a modelu COM + vytvářet služby, které jsou kompatibilní se službou WCF services.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="4f5a6-185">Tato funkce nebude používat konkrétní hlavičky a neuchovává data na koncového uživatele na počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="4f5a6-186">Moniker služby modelu COM</span><span class="sxs-lookup"><span data-stu-id="4f5a6-186">COM Service Moniker</span></span>  
 <span data-ttu-id="4f5a6-187">To poskytuje nespravované obálky standardní klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="4f5a6-188">Tato funkce nemá žádné konkrétní hlavičky na lince ani nemá zachovat data v počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="4f5a6-189">Rovnocenný kanál</span><span class="sxs-lookup"><span data-stu-id="4f5a6-189">Peer Channel</span></span>  
 <span data-ttu-id="4f5a6-190">Rovnocenný kanál umožňuje vývoj éře aplikací pomocí technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="4f5a6-191">Zasílání zpráv éře dochází v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="4f5a6-192">Mřížky jsou označeny název, který se můžete zapojit do uzlů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="4f5a6-193">Každý uzel v protokolu peer channel vytvoří naslouchací proces TCP na portu zadané uživatelem a naváže připojení k jiným uzlům v síti k zajištění odolnosti proti chybám.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="4f5a6-194">Připojení k ostatním uzlům v síti, uzly také exchange nějaká data, včetně adresy naslouchací proces a jeho IP adresy s jinými uzly síť.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="4f5a6-195">Zprávy odeslané kolem síť může obsahovat informace o zabezpečení, která se týkají odesílatele, aby se zabránilo falšování zprávu a manipulaci s.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="4f5a6-196">Na počítači koncového uživatele nebudou uloženy žádné osobní informace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="4f5a6-197">Profesionální IT prostředí</span><span class="sxs-lookup"><span data-stu-id="4f5a6-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="4f5a6-198">Trasování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-198">Tracing</span></span>  
 <span data-ttu-id="4f5a6-199">Funkce Diagnostika služby WCF infrastruktury protokoly zpráv, které procházejí přenos a modelu vrstvy služby a činnosti a události související se tyto zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="4f5a6-200">Tato funkce je ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-200">This feature is turned off by default.</span></span> <span data-ttu-id="4f5a6-201">Je povoleno, je používán konfigurační soubor aplikace a chování trasování může být upraveno pomocí poskytovatele služby WMI WCF v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="4f5a6-202">Při povolení trasování infrastruktury vysílá diagnostickém trasování, která obsahuje zprávy, aktivity a zpracování událostí do nakonfigurovaného naslouchacích procesů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="4f5a6-203">Formát a umístění výstupu se určují podle volby konfigurace naslouchacího procesu na správce, ale je obvykle formátovaného souboru XML.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="4f5a6-204">Správce zodpovídá za nastavení seznamu řízení přístupu (ACL) pro trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="4f5a6-205">Zejména když jsou hostované pomocí aktivace systému Windows (WAS), Správce by měl Ujistěte se, že soubory nejsou obsluhovány z veřejné virtuální kořenový adresář Pokud, který není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="4f5a6-206">Existují dva typy trasování: protokolování zpráv a Model služby diagnostické trasování, je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="4f5a6-207">Každý typ je nakonfigurovaná prostřednictvím vlastní zdroj trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="4f5a6-208">Obě tyto zdroje protokolování trasování zaznamenávat data, která je vůči aplikaci lokální.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="4f5a6-209">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="4f5a6-209">Message Logging</span></span>  
 <span data-ttu-id="4f5a6-210">Protokolování zdroj trasování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správci protokolování zprávy tohoto toku prostřednictvím systému.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="4f5a6-211">Prostřednictvím konfigurace uživatel může rozhodnout protokolovat celé zprávy nebo pouze hlavičky zpráv, zda chcete protokolovat v modelu vrstvy přenosu a/nebo služba a jestli se mají zahrnout špatně vytvořené zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="4f5a6-212">Uživatel také může konfigurovat filtrování omezit zprávy, které jsou zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="4f5a6-213">Protokolování zpráv je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-213">By default, message logging is disabled.</span></span> <span data-ttu-id="4f5a6-214">Správce místního počítače zabránit zapnutí protokolování úrovni aplikace správce.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="4f5a6-215">Protokolování zpráv zašifrovaně a je dešifrován</span><span class="sxs-lookup"><span data-stu-id="4f5a6-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="4f5a6-216">Zprávy jsou protokolovány, šifrované nebo dešifrovat, jak je popsáno v následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="4f5a6-217">Protokolování přenosu</span><span class="sxs-lookup"><span data-stu-id="4f5a6-217">Transport Logging</span></span>  
 <span data-ttu-id="4f5a6-218">Protokoly zpráv přijatých a odeslaných na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="4f5a6-219">Tyto zprávy obsahují všechny hlavičky a můžou šifrovat před odesláním na lince a při jejich obdržení.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="4f5a6-220">Pokud se šifrují zprávy před odesláním na lince a při jejich přijetí, kterému jsou přihlášeni šifrovaná i.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="4f5a6-221">Výjimkou je, když protokol zabezpečení se používá (https): potom se protokolují, dešifrují před odesláním a po jejich obdržení i v případě, že jsou šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="4f5a6-222">Služba protokolování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-222">Service Logging</span></span>  
 <span data-ttu-id="4f5a6-223">Zaznamenává zprávy příjem nebo odeslání na úrovni modelu služby po zpracování záhlaví kanálu, těsně před a po zadání uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="4f5a6-224">Zprávy zaprotokolované na této úrovni se dešifrují i v případě, že by byly zabezpečená a šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="4f5a6-225">Protokolování chybnou zprávu</span><span class="sxs-lookup"><span data-stu-id="4f5a6-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="4f5a6-226">Zaznamenává zprávy, které infrastruktura WCF nemůže pochopit a zpracovat.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="4f5a6-227">Zprávy se zaznamenávají jako-se, to znamená, šifrují nebo ne</span><span class="sxs-lookup"><span data-stu-id="4f5a6-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="4f5a6-228">Zprávy jsou zaznamenány dešifrovaný nebo nezašifrované podobě, ve výchozím nastavení WCF odebere zabezpečení klíčů a potenciálně osobní údaje z zprávy před jejich protokolování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="4f5a6-229">Tento oddíl popisuje, jaké informace se odebere a kdy.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="4f5a6-230">Správce počítače a nástroje pro nasazení aplikace musí provést určité akce konfigurace, chcete-li změnit výchozí chování pro přihlášení klíče a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="4f5a6-231">Informace, které jsou odebrány ze záhlaví zpráv při přihlašování bez dešifrovat/šifrování zprávy</span><span class="sxs-lookup"><span data-stu-id="4f5a6-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="4f5a6-232">Když zprávy se protokolují v dešifrovat/nešifrované podobě klíčů zabezpečení a potenciálně osobní údaje se odeberou ve výchozím nastavení ze záhlaví zpráv a zpráv předtím, než jsou protokolovány.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="4f5a6-233">Následující seznam uvádí, co WCF považuje za klíče a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="4f5a6-234">Klíče, které jsou odebrány:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="4f5a6-235">\- Xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="4f5a6-236">WSt:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="4f5a6-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="4f5a6-237">WSt:Entropy</span><span class="sxs-lookup"><span data-stu-id="4f5a6-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="4f5a6-238">\- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="4f5a6-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="4f5a6-239">wsse:Password</span></span>  
  
 <span data-ttu-id="4f5a6-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="4f5a6-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="4f5a6-241">Potenciálně osobní údaje, která byla odstraněna:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="4f5a6-242">\- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="4f5a6-243">wsse:username</span><span class="sxs-lookup"><span data-stu-id="4f5a6-243">wsse:Username</span></span>  
  
 <span data-ttu-id="4f5a6-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="4f5a6-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="4f5a6-245">\- Pro xmlns:saml = "urn: oasis: názvy: tc: SAML:1.0:assertion" jsou odebrány položky tučným písmem (níže):</span><span class="sxs-lookup"><span data-stu-id="4f5a6-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="4f5a6-246">\<kontrolní výraz</span><span class="sxs-lookup"><span data-stu-id="4f5a6-246">\<Assertion</span></span>  
  
 <span data-ttu-id="4f5a6-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="4f5a6-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="4f5a6-249">AssertionId = "[ID]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="4f5a6-250">Vystavitel = "[string]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="4f5a6-251">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="4f5a6-252">\<Podmínky NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="4f5a6-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="4f5a6-254">\<Audience>[uri]\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="4f5a6-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="4f5a6-255">\</ AudienceRestrictionCondition > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="4f5a6-256">\<DoNotCacheCondition / > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="4f5a6-257"><\!--abstraktní základní typ</span><span class="sxs-lookup"><span data-stu-id="4f5a6-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="4f5a6-258">\<Podmínka / > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="4f5a6-259">\</ Podmínky >?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="4f5a6-260">\<Rady ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-260">\<Advice></span></span>  
  
 <span data-ttu-id="4f5a6-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="4f5a6-262">\<Kontrolní výraz > [výrazu]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="4f5a6-263">[jakýkoli] \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-263">[any]\*</span></span>  
  
 <span data-ttu-id="4f5a6-264">\</ Rady >?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="4f5a6-265"><\!--Abstraktních základních typů</span><span class="sxs-lookup"><span data-stu-id="4f5a6-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="4f5a6-266">\<Příkaz / > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="4f5a6-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="4f5a6-268">\<Předmět ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="4f5a6-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="4f5a6-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="4f5a6-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="4f5a6-271">\<SubjectConfirmationData > [jakýkoli]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="4f5a6-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="4f5a6-273">\</ SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="4f5a6-274">\</ Předmět ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-274">\</Subject></span></span>  
  
 <span data-ttu-id="4f5a6-275">\</ SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="4f5a6-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="4f5a6-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="4f5a6-277">AuthenticationMethod = "[identifikátor uri]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="4f5a6-278">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="4f5a6-279">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="4f5a6-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="4f5a6-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="4f5a6-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="4f5a6-281">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="4f5a6-282">Umístění = "[identifikátor uri]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="4f5a6-283">Vytvoření vazby = "[identifikátor uri]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="4f5a6-284">\</ AuthenticationStatement > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="4f5a6-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="4f5a6-286">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="4f5a6-286">[Subject]</span></span>  
  
 <span data-ttu-id="4f5a6-287">\<Atribut</span><span class="sxs-lookup"><span data-stu-id="4f5a6-287">\<Attribute</span></span>  
  
 <span data-ttu-id="4f5a6-288">AttributeName = "[string]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="4f5a6-289">AttributeNamespace = "[identifikátor uri]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="4f5a6-290">\</ Atribut > +</span><span class="sxs-lookup"><span data-stu-id="4f5a6-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="4f5a6-291">\</ AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="4f5a6-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="4f5a6-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="4f5a6-293">Zdroj = "[identifikátor uri]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="4f5a6-294">Rozhodnutí = "[Povolit&#124;Odepřít&#124;neurčitý]"</span><span class="sxs-lookup"><span data-stu-id="4f5a6-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="4f5a6-295">[Subjektu]</span><span class="sxs-lookup"><span data-stu-id="4f5a6-295">[Subject]</span></span>  
  
 <span data-ttu-id="4f5a6-296">\<Akce Namespace = "[identifikátor uri]" > [string]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="4f5a6-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="4f5a6-297">\<Legitimace ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-297">\<Evidence></span></span>  
  
 <span data-ttu-id="4f5a6-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="4f5a6-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="4f5a6-299">\<Kontrolní výraz > [výrazu]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="4f5a6-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="4f5a6-300">\</ Důkazy >?</span><span class="sxs-lookup"><span data-stu-id="4f5a6-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="4f5a6-301">\</ AuthorizationDecisionStatement > \*</span><span class="sxs-lookup"><span data-stu-id="4f5a6-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="4f5a6-302">\</ Kontrolní výraz ></span><span class="sxs-lookup"><span data-stu-id="4f5a6-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="4f5a6-303">Informace, které jsou odebrány z těla zprávy při přihlašování bez dešifrovat/šifrování zprávy</span><span class="sxs-lookup"><span data-stu-id="4f5a6-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="4f5a6-304">Jak je uvedeno výše, WCF odebere klíče a známé potenciálně osobními údaji ze záhlaví zpráv pro zprávy zaznamenané dříve dešifrovat/nezašifrované.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="4f5a6-305">Kromě toho WCF odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zabezpečení zprávy, které jsou zahrnuté v výměny klíčů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="4f5a6-306">Pro následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="4f5a6-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (např. Pokud nejsou k dispozici žádná akce)</span><span class="sxs-lookup"><span data-stu-id="4f5a6-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="4f5a6-308">Pro tyto elementy textu, které zahrnují výměny klíčů odebraly informace:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="4f5a6-309">WSt:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="4f5a6-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="4f5a6-310">WSt:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="4f5a6-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="4f5a6-311">WSt:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="4f5a6-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="4f5a6-312">Informace o odebrán také pro každou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4f5a6-312">Information is also removed for each of the following Actions:</span></span>  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="4f5a6-313">Žádné informace se odebere z hlavičky specifické pro aplikace a Data těla</span><span class="sxs-lookup"><span data-stu-id="4f5a6-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="4f5a6-314">WCF nesleduje osobní údaje v záhlaví specifické pro aplikaci (například řetězce dotazu) a data subjektu (například číslo platební karty).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="4f5a6-315">Při protokolování zpráv je na, může být osobní údaje v hlavičkách specifické pro aplikaci a informace o subjektu viditelné v protokolech.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="4f5a6-316">Nástroje pro nasazení aplikace znovu, zodpovídá za nastavení seznamu ACL u souborů konfigurace a protokolu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="4f5a6-317">Si můžete také vypnout protokolování nechce uvidí tyto informace nebo mu může odfiltrovat tyto informace v souborech protokolů, až se protokoluje.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="4f5a6-318">Služby modelu trasování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-318">Service Model Tracing</span></span>  
 <span data-ttu-id="4f5a6-319">Zdroj trasování Service Model (<xref:System.ServiceModel>) umožňuje trasování aktivity a události související se zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="4f5a6-320">Tato funkce používá diagnostické funkce rozhraní .NET Framework z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="4f5a6-321">Stejně jako u <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> vlastnost, umístění a jeho seznamu ACL se uživatelem konfigurovatelné pomocí konfiguračních souborů aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="4f5a6-322">Stejně jako u protokolování zpráv umístění souboru vždy nakonfigurované, pokud správce povolí trasování; Proto správce ovládací prvky seznamu ACL.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="4f5a6-323">Trasování neobsahovala záhlaví zpráv, když je zpráva v oboru.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="4f5a6-324">Platí stejná pravidla pro skrytí potenciálně osobní údaje v záhlaví zpráv v předchozí části: Odebereme osobní údaje dříve identifikovat ve výchozím nastavení ze záhlaví ve trasování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="4f5a6-325">Správce počítače a nástroje pro nasazení aplikace, musíte změnit konfiguraci protokolování potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="4f5a6-326">Osobní informace obsažené v konkrétní aplikaci záhlaví je však přihlášen trasování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="4f5a6-327">Nástroje pro nasazení aplikace je zodpovědná za nastavení seznamu ACL u souborů konfigurace a trasování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="4f5a6-328">Má také vypnout trasování nechce uvidí tyto informace nebo mu můžete filtrovat tyto informace ze souborů trasování po je zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="4f5a6-329">Jako součást ServiceModel trasování, jedinečné identifikátory (označované jako ID aktivit a obvykle GUID) propojit různé aktivity jako zpráva prochází různých součástí infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="4f5a6-330">Naslouchací procesy vlastního trasování</span><span class="sxs-lookup"><span data-stu-id="4f5a6-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="4f5a6-331">Pro obě zprávy protokolování a trasování naslouchací proces vlastního trasování je možné nakonfigurovat, který můžete poslat trasování a zpráv na lince (například vzdálená databáze).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="4f5a6-332">Nástroje pro nasazení aplikace je zodpovědná za konfiguraci vlastní naslouchacích procesů nebo umožnění uživatelům Uděláte to tak.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="4f5a6-333">Je také zodpovídá za žádné osobní údaje, které jsou zveřejněné ve vzdáleném umístění a správně do tohoto umístění seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="4f5a6-334">Další funkce pro IT specialisty</span><span class="sxs-lookup"><span data-stu-id="4f5a6-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="4f5a6-335">WCF se zprostředkovatel rozhraní WMI, který poskytuje informace o konfiguraci infrastruktury WCF přes rozhraní WMI (dodávané s Windows).</span><span class="sxs-lookup"><span data-stu-id="4f5a6-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="4f5a6-336">Ve výchozím nastavení je k dispozici správcům rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="4f5a6-337">Konfigurace WCF používá mechanismus konfigurace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="4f5a6-338">Konfigurační soubory se ukládají na počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="4f5a6-339">Správce a vývojáře aplikací vytvořte konfigurační soubory a seznamu ACL pro každou podle požadavků vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="4f5a6-340">Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="4f5a6-341">Certifikáty slouží k poskytnutí dat aplikace nakonfigurovat různé vlastnosti objektu funkcí používaných v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="4f5a6-342">WCF také používá funkce rozhraní .NET Framework procesu s výpisem paměti pomocí volání <xref:System.Environment.FailFast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="4f5a6-343">IT profesionálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="4f5a6-343">IT Pro Tools</span></span>  
 <span data-ttu-id="4f5a6-344">WCF také obsahuje následující IT professional nástroje, které se dodávají v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="4f5a6-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="4f5a6-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="4f5a6-346">Prohlížeč zobrazí soubory trasování WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="4f5a6-347">Prohlížeč zobrazí libovolné informace je součástí trasování.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="4f5a6-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="4f5a6-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="4f5a6-349">Editor umožňuje uživateli vytvoření a úprava konfiguračních souborů WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="4f5a6-350">Editor hlásí libovolné informace je obsažen v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="4f5a6-351">Stejné úlohy můžete provést pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="4f5a6-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="4f5a6-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="4f5a6-353">Tento nástroj umožňuje uživateli spravovat ServiceModel nainstaluje na počítač.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="4f5a6-354">Nástroj zobrazí stavové zprávy v okně konzoly, když se spustí a v procesu, mohou zobrazit informace o konfiguraci instalace WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="4f5a6-355">WSATConfig.exe a WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="4f5a6-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="4f5a6-356">Tyto nástroje umožňují Odborníci v oblasti IT provést konfiguraci podpory sítě interoperabilní WS-AtomicTransaction ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="4f5a6-357">Nástroje pro zobrazení a povolit uživateli měnit hodnoty nejčastěji používaná nastavení WS-AtomicTransaction uložené v registru.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="4f5a6-358">Společné funkce</span><span class="sxs-lookup"><span data-stu-id="4f5a6-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="4f5a6-359">Společné spadají následující funkce.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-359">The following features are cross-cutting.</span></span> <span data-ttu-id="4f5a6-360">To znamená mohou být složené s některým z předchozích funkcí.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="4f5a6-361">Architektura služby</span><span class="sxs-lookup"><span data-stu-id="4f5a6-361">Service Framework</span></span>  
 <span data-ttu-id="4f5a6-362">Záhlaví může obsahovat ID instance, což je identifikátor GUID, která přidružuje zprávu instance třídy CLR.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="4f5a6-363">Na webové služby WSDL (Description Language) obsahuje definici portu.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="4f5a6-364">Každý z portů má adresu koncového bodu a vazbu, která představuje služby používané aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="4f5a6-365">Vystavení WSDL můžete vypnout pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="4f5a6-366">Žádné informace se uchovávají v počítači.</span><span class="sxs-lookup"><span data-stu-id="4f5a6-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5a6-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f5a6-367">See Also</span></span>  
 [<span data-ttu-id="4f5a6-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4f5a6-368">Windows Communication Foundation</span></span>](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="4f5a6-369">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4f5a6-369">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
