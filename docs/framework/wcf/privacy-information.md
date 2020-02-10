---
title: Windows Communication Foundation – informace o ochraně osobních údajů
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: b724ff1ce85442f64980fdc972188705992d5a4f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094979"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="44489-102">Windows Communication Foundation – informace o ochraně osobních údajů</span><span class="sxs-lookup"><span data-stu-id="44489-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="44489-103">Společnost Microsoft se zavazuje chránit ochranu osobních údajů koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="44489-103">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="44489-104">Při sestavování aplikace pomocí Windows Communication Foundation (WCF) verze 3,0 může vaše aplikace ovlivnit ochranu osobních údajů koncových uživatelů.</span><span class="sxs-lookup"><span data-stu-id="44489-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="44489-105">Vaše aplikace může například explicitně shromažďovat kontaktní údaje uživatele nebo může vyžádat nebo odeslat informace prostřednictvím internetu na web.</span><span class="sxs-lookup"><span data-stu-id="44489-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="44489-106">Pokud do své aplikace vložíte technologii Microsoftu, může mít tato technologie vlastní chování, které může mít vliv na ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="44489-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="44489-107">WCF nepošle žádné informace společnosti Microsoft z vaší aplikace, pokud vy nebo koncový uživatel nerozhodnete, že ji odešlete na nás.</span><span class="sxs-lookup"><span data-stu-id="44489-107">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="44489-108">WCF v krátkém</span><span class="sxs-lookup"><span data-stu-id="44489-108">WCF in Brief</span></span>  
 <span data-ttu-id="44489-109">Služba WCF je distribuovaná architektura pro zasílání zpráv pomocí .NET Framework Microsoftu, která vývojářům umožňuje vytvářet distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="44489-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="44489-110">Zprávy komunikující mezi dvěma aplikacemi obsahují záhlaví a informace o textu.</span><span class="sxs-lookup"><span data-stu-id="44489-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="44489-111">Záhlaví mohou obsahovat směrování zpráv, informace o zabezpečení, transakce a další informace v závislosti na službách, které aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="44489-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="44489-112">Zprávy jsou obvykle ve výchozím nastavení zašifrovány.</span><span class="sxs-lookup"><span data-stu-id="44489-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="44489-113">Jedinou výjimkou je použití `BasicHttpBinding`, které bylo navrženo pro použití s nezabezpečenými staršími webovými službami.</span><span class="sxs-lookup"><span data-stu-id="44489-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="44489-114">Jako návrhář aplikace zodpovídáte za finální návrh.</span><span class="sxs-lookup"><span data-stu-id="44489-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="44489-115">Zprávy v těle protokolu SOAP obsahují data specifická pro aplikaci; Tato data, jako jsou osobní údaje definované aplikací, je ale možné zabezpečit pomocí funkcí šifrování a utajení WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="44489-116">V následujících částech jsou popsány funkce, které mohou mít vliv na ochranu osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="44489-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="44489-117">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-117">Messaging</span></span>  
 <span data-ttu-id="44489-118">Každá zpráva WCF má hlavičku adresy, která určuje cíl zprávy a kam má odpověď jít.</span><span class="sxs-lookup"><span data-stu-id="44489-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="44489-119">Součást Address adresy koncového bodu je identifikátor URI (Uniform Resource Identifier), který identifikuje koncový bod.</span><span class="sxs-lookup"><span data-stu-id="44489-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="44489-120">Adresa může být síťová nebo logická adresa.</span><span class="sxs-lookup"><span data-stu-id="44489-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="44489-121">Adresa může obsahovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu.</span><span class="sxs-lookup"><span data-stu-id="44489-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="44489-122">Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID) nebo kolekci identifikátorů GUID pro dočasné adresování, které slouží k nerozlišujeí jednotlivých adres.</span><span class="sxs-lookup"><span data-stu-id="44489-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="44489-123">Každá zpráva obsahuje ID zprávy, která je identifikátorem GUID.</span><span class="sxs-lookup"><span data-stu-id="44489-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="44489-124">Tato funkce se řídí referenčním standardem WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="44489-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="44489-125">Vrstva zasílání zpráv WCF nepíše žádné osobní údaje do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="44489-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="44489-126">Může však šířit osobní údaje na úrovni sítě, pokud vývojář služby vytvořil službu, která tyto informace zpřístupňuje (například pomocí názvu osoby v názvu koncového bodu nebo včetně osobních údajů na webu koncového bodu). Služba Description Language, ale nevyžaduje, aby klienti k přístupu ke WSDL používali https.</span><span class="sxs-lookup"><span data-stu-id="44489-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="44489-127">Pokud vývojář spustí nástroj pro dodané [metadata (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) v rámci koncového bodu, který zveřejňuje osobní údaje, může také výstup tohoto nástroje obsahovat tyto informace a výstupní soubor je zapsán na místní pevný disk.</span><span class="sxs-lookup"><span data-stu-id="44489-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="44489-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="44489-128">Hosting</span></span>  
 <span data-ttu-id="44489-129">Funkce hostování v rámci WCF umožňuje aplikacím spouštět na vyžádání nebo povolit sdílení portů mezi několika aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="44489-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="44489-130">Aplikace WCF může být hostována ve službě Internetová informační služba (IIS), podobně jako ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="44489-130">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="44489-131">Hostování nezveřejňuje žádné konkrétní informace v síti a neuchovává data v počítači.</span><span class="sxs-lookup"><span data-stu-id="44489-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="44489-132">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-132">Message Security</span></span>  
 <span data-ttu-id="44489-133">Zabezpečení WCF poskytuje možnosti zabezpečení pro aplikace zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="44489-134">K dispozici jsou funkce zabezpečení zahrnující ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="44489-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="44489-135">Ověřování se provádí předáním přihlašovacích údajů mezi klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="44489-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="44489-136">Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu, nebo prostřednictvím zabezpečení na úrovni zpráv SOAP, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="44489-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="44489-137">V zabezpečení zpráv SOAP se ověřování provádí prostřednictvím přihlašovacích údajů, jako jsou uživatelské jméno a hesla, certifikáty X. 509, lístky protokolu Kerberos a tokeny SAML, z nichž všechny můžou obsahovat osobní informace v závislosti na vystaviteli.</span><span class="sxs-lookup"><span data-stu-id="44489-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="44489-138">Pomocí zabezpečení přenosu se ověřování provádí pomocí tradičních mechanismů ověřování přenosu, jako jsou schémata ověřování HTTP (Basic, Digest, Negotiate, integrovaná autorizace Windows, NTLM, None a Anonymous), a ověřování pomocí formuláře.</span><span class="sxs-lookup"><span data-stu-id="44489-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="44489-139">Ověřování může mít za následek zabezpečenou relaci vytvořenou mezi komunikujícími koncovými body.</span><span class="sxs-lookup"><span data-stu-id="44489-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="44489-140">Relace je identifikována identifikátorem GUID, který vydrží životnost relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44489-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="44489-141">Následující tabulka ukazuje, co se zachová a kde.</span><span class="sxs-lookup"><span data-stu-id="44489-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="44489-142">Data</span><span class="sxs-lookup"><span data-stu-id="44489-142">Data</span></span>|<span data-ttu-id="44489-143">Úložiště</span><span class="sxs-lookup"><span data-stu-id="44489-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="44489-144">Přihlašovací údaje pro prezentace, jako je uživatelské jméno, certifikáty X. 509, tokeny Kerberos a odkazy na přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="44489-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="44489-145">Standardní mechanismy správy přihlašovacích údajů systému Windows, jako je například úložiště certifikátů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="44489-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="44489-146">Informace o členství uživatele, například uživatelská jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="44489-146">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="44489-147">ASP.NET poskytovatelé členství.</span><span class="sxs-lookup"><span data-stu-id="44489-147">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="44489-148">Informace o identitě služby, která se používá k ověření služby pro klienty.</span><span class="sxs-lookup"><span data-stu-id="44489-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="44489-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="44489-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="44489-150">Informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="44489-150">Caller information.</span></span>|<span data-ttu-id="44489-151">Protokoly auditování.</span><span class="sxs-lookup"><span data-stu-id="44489-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="44489-152">Auditování</span><span class="sxs-lookup"><span data-stu-id="44489-152">Auditing</span></span>  
 <span data-ttu-id="44489-153">Auditování zaznamenává úspěšné a neúspěšné události ověřování a autorizace.</span><span class="sxs-lookup"><span data-stu-id="44489-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="44489-154">Záznamy auditu obsahují následující data: identifikátor URI služby, identifikátor URI akce a identifikaci volajícího.</span><span class="sxs-lookup"><span data-stu-id="44489-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="44489-155">Auditování také zaznamenává, když správce změní konfiguraci protokolování zpráv (zapnutí nebo vypnutí), protože protokolování zpráv může protokolovat data specifická pro aplikaci v záhlavích a subjektech.</span><span class="sxs-lookup"><span data-stu-id="44489-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="44489-156">V systému Windows XP se záznam zaznamená do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="44489-156">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="44489-157">V případě systémů Windows Vista a Windows Server 2003 se záznam zaznamená do protokolu událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="44489-157">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="44489-158">Transakce</span><span class="sxs-lookup"><span data-stu-id="44489-158">Transactions</span></span>  
 <span data-ttu-id="44489-159">Funkce transakcí poskytuje transakční služby pro aplikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="44489-160">Hlavičky transakce použité v šíření transakce mohou obsahovat ID transakce nebo ID zařazení, což jsou identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="44489-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="44489-161">Funkce Transactions používá správce transakcí služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) ke správě stavu transakce (součást systému Windows).</span><span class="sxs-lookup"><span data-stu-id="44489-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="44489-162">Ve výchozím nastavení jsou komunikace mezi správci transakcí zašifrována.</span><span class="sxs-lookup"><span data-stu-id="44489-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="44489-163">Správci transakcí mohou protokolovat odkazy koncových bodů, ID transakcí a ID zařazení v rámci jejich trvalého stavu.</span><span class="sxs-lookup"><span data-stu-id="44489-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="44489-164">Doba života tohoto stavu je určena životností souboru protokolu správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="44489-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="44489-165">Služba MSDTC vlastní a udržuje tento protokol.</span><span class="sxs-lookup"><span data-stu-id="44489-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="44489-166">Funkce transakcí implementuje standardy pro transakce WS-koordinační a WS-Atomic.</span><span class="sxs-lookup"><span data-stu-id="44489-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="44489-167">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="44489-167">Reliable Sessions</span></span>  
 <span data-ttu-id="44489-168">Spolehlivé relace v rámci WCF poskytují přenos zpráv, když dojde k selhání přenosu nebo zprostředkovatelských prostředků.</span><span class="sxs-lookup"><span data-stu-id="44489-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="44489-169">Poskytují právě jeden přenos zpráv, i když se podkladové přenosy odpojí (například připojení TCP v bezdrátové síti) nebo ztratí zprávu (proxy server HTTP, který vyřazuje odchozí nebo příchozí zpráva).</span><span class="sxs-lookup"><span data-stu-id="44489-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="44489-170">Spolehlivé relace také obnovují pořadí zpráv (k tomu může dojít v případě směrování s více uživateli) a zachovává pořadí, ve kterém se zprávy poslaly.</span><span class="sxs-lookup"><span data-stu-id="44489-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="44489-171">Spolehlivé relace se implementují pomocí protokolu WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="44489-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="44489-172">Přidávají hlavičky WS-RM, které obsahují informace o relacích, které slouží k identifikaci všech zpráv přidružených ke konkrétní spolehlivé relaci.</span><span class="sxs-lookup"><span data-stu-id="44489-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="44489-173">Každá relace WS-RM má identifikátor, který je identifikátorem GUID.</span><span class="sxs-lookup"><span data-stu-id="44489-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="44489-174">V počítači koncového uživatele nejsou zachovány žádné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="44489-174">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="44489-175">Kanály zařazené do fronty</span><span class="sxs-lookup"><span data-stu-id="44489-175">Queued Channels</span></span>  
 <span data-ttu-id="44489-176">Fronty ukládají zprávy z odesílající aplikace jménem přijímající aplikace a později tyto zprávy předají do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="44489-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="44489-177">Pomůžou zajistit přenos zpráv z odesílajících aplikací do přijímajících aplikací, když například přijímající aplikace je přechodný.</span><span class="sxs-lookup"><span data-stu-id="44489-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="44489-178">Služba WCF poskytuje podporu pro řazení do fronty pomocí služby Microsoft řízení front zpráv (MSMQ) jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="44489-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="44489-179">Funkce kanálů zařazených do fronty nepřidává do zprávy záhlaví.</span><span class="sxs-lookup"><span data-stu-id="44489-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="44489-180">Místo toho vytvoří zprávu služby Řízení front zpráv s příslušným nastavením vlastností zprávy služby Řízení front zpráv a vyvolá metody služby Řízení front zpráv pro vložení zprávy do fronty služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="44489-181">Služba Řízení front zpráv je volitelná součást, která se dodává se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="44489-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="44489-182">Funkce kanálů ve frontě neuchovává žádné informace v počítači koncového uživatele, protože používá službu Řízení front zpráv jako infrastrukturu služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-182">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="44489-183">Integrace COM+</span><span class="sxs-lookup"><span data-stu-id="44489-183">COM+ Integration</span></span>  
 <span data-ttu-id="44489-184">Tato funkce zalomí existující funkce COM a COM+ a vytvoří služby, které jsou kompatibilní se službami WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="44489-185">Tato funkce nepoužívá konkrétní záhlaví a neuchovává data v počítači koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="44489-185">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="44489-186">Moniker služby COM</span><span class="sxs-lookup"><span data-stu-id="44489-186">COM Service Moniker</span></span>  
 <span data-ttu-id="44489-187">To poskytuje nespravovaný obálku standardnímu klientovi WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="44489-188">Tato funkce nemá konkrétní záhlaví na lince ani neuchovává data v počítači.</span><span class="sxs-lookup"><span data-stu-id="44489-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="44489-189">Rovnocenný kanál</span><span class="sxs-lookup"><span data-stu-id="44489-189">Peer Channel</span></span>  
 <span data-ttu-id="44489-190">Partnerský kanál umožňuje vývoj aplikací s více částmi pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="44489-191">Zasílání zpráv s více částmi probíhá v kontextu sítě.</span><span class="sxs-lookup"><span data-stu-id="44489-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="44489-192">Sítě jsou označeny názvem, ke kterému se uzly můžou připojit.</span><span class="sxs-lookup"><span data-stu-id="44489-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="44489-193">Každý uzel v partnerském kanálu vytvoří naslouchací proces TCP na portu zadaného uživatelem a naváže připojení k ostatním uzlům v síti, aby se zajistila odolnost.</span><span class="sxs-lookup"><span data-stu-id="44489-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="44489-194">Pokud se chcete připojit k ostatním uzlům v síti, uzly také vyměňují data, včetně adresy naslouchacího procesu a IP adresy počítače, s dalšími uzly v síti.</span><span class="sxs-lookup"><span data-stu-id="44489-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="44489-195">Zprávy odesílané do sítě mohou obsahovat informace o zabezpečení, které se týkají odesilatele, aby se zabránilo falšování a falšování zprávy.</span><span class="sxs-lookup"><span data-stu-id="44489-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="44489-196">V počítači koncového uživatele nejsou uloženy žádné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="44489-196">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="44489-197">Uživatelské prostředí pro IT specialisty</span><span class="sxs-lookup"><span data-stu-id="44489-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="44489-198">Trasování</span><span class="sxs-lookup"><span data-stu-id="44489-198">Tracing</span></span>  
 <span data-ttu-id="44489-199">Funkce diagnostiky infrastruktury WCF protokoluje zprávy, které procházejí prostřednictvím vrstev přenosu a modelu služby, a aktivit a událostí přidružených k těmto zprávám.</span><span class="sxs-lookup"><span data-stu-id="44489-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="44489-200">Tato funkce je ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="44489-200">This feature is turned off by default.</span></span> <span data-ttu-id="44489-201">Je povolená pomocí konfiguračního souboru aplikace a chování trasování se dá v době běhu upravit pomocí zprostředkovatele WMI WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="44489-202">Pokud je tato možnost povolena, trasovací infrastruktura vygeneruje diagnostické trasování, které obsahuje zprávy, aktivity a zpracování událostí pro nakonfigurované naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="44489-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="44489-203">Formát a umístění výstupu jsou určeny volbami konfigurace naslouchacího procesu správce, ale obvykle se jedná o soubor ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="44489-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="44489-204">Správce zodpovídá za nastavení seznamu řízení přístupu (ACL) na trasovacích souborech.</span><span class="sxs-lookup"><span data-stu-id="44489-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="44489-205">Zejména pokud je hostovaný systémem Windows Activation System (WAS), správce by měl zajistit, aby soubory nebyly obsluhovány z veřejného virtuálního kořenového adresáře, pokud to není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="44489-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="44489-206">Existují dva typy trasování: protokolování zpráv a trasování diagnostiky modelu služby, které jsou popsány v následující části.</span><span class="sxs-lookup"><span data-stu-id="44489-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="44489-207">Každý typ je nakonfigurován prostřednictvím vlastního zdroje trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="44489-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="44489-208">Oba tyto zdroje trasování protokolování zachytí data, která jsou místní pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="44489-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="44489-209">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-209">Message Logging</span></span>  
 <span data-ttu-id="44489-210">Zdroj trasování protokolování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správci Protokolovat zprávy, které procházejí systémem.</span><span class="sxs-lookup"><span data-stu-id="44489-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="44489-211">Uživatel může prostřednictvím konfigurace zaprotokolovat pouze celé zprávy nebo hlavičky zpráv, zda se mají protokolovat na vrstvy přenosu nebo modelu služby a zda mají být zahrnuty poškozené zprávy.</span><span class="sxs-lookup"><span data-stu-id="44489-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="44489-212">Uživatel taky může nakonfigurovat filtrování, aby se omezilo protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="44489-213">Ve výchozím nastavení je protokolování zpráv zakázané.</span><span class="sxs-lookup"><span data-stu-id="44489-213">By default, message logging is disabled.</span></span> <span data-ttu-id="44489-214">Správce místního počítače může zabránit tomu, aby správce na úrovni aplikace zapnul protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="44489-215">Šifrované a dešifrované protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="44489-216">Zprávy jsou protokolovány, šifrovány nebo dešifrovány, jak je popsáno v následujících výrazech.</span><span class="sxs-lookup"><span data-stu-id="44489-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="44489-217">Protokolování přenosu</span><span class="sxs-lookup"><span data-stu-id="44489-217">Transport Logging</span></span>  
 <span data-ttu-id="44489-218">Protokoluje přijaté a odesílané zprávy na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="44489-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="44489-219">Tyto zprávy obsahují všechny hlavičky a můžou být před odesláním na kabel a při přijímání zašifrované.</span><span class="sxs-lookup"><span data-stu-id="44489-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="44489-220">Pokud jsou zprávy před odesláním na síťový kabel zašifrované a jsou přijímány, zašifrují se i do protokolu.</span><span class="sxs-lookup"><span data-stu-id="44489-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="44489-221">Výjimkou je případ, kdy se používá protokol zabezpečení (https): před odesláním a po přijetí, i když jsou zašifrovány na lince, se zaprotokolují dešifrování.</span><span class="sxs-lookup"><span data-stu-id="44489-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="44489-222">Protokolování služby</span><span class="sxs-lookup"><span data-stu-id="44489-222">Service Logging</span></span>  
 <span data-ttu-id="44489-223">Protokoluje zprávy přijaté nebo odeslané na úrovni modelu služby, poté, co došlo ke zpracování hlaviček kanálu, těsně před a po zadání uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="44489-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="44489-224">Zprávy, které jsou protokolovány na této úrovni, jsou dešifrovány, i když byly zabezpečeny a šifrovány na lince.</span><span class="sxs-lookup"><span data-stu-id="44489-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="44489-225">Poškozené protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="44489-226">Protokoluje zprávy, které infrastruktura WCF nedokáže pochopit nebo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="44489-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="44489-227">Zprávy jsou protokolovány tak, jak jsou, jsou zašifrovány nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="44489-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="44489-228">Pokud jsou zprávy protokolovány v dešifrovaném nebo nešifrovaném tvaru, služba WCF ve výchozím nastavení odstraní klíče zabezpečení a potenciálně osobní informace ze zpráv předtím, než je přihlásí.</span><span class="sxs-lookup"><span data-stu-id="44489-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="44489-229">V dalších oddílech jsou popsány informace, které jsou odebrány a kdy.</span><span class="sxs-lookup"><span data-stu-id="44489-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="44489-230">Správce počítače a nástroj pro nasazení aplikace musí provést určité konfigurační akce a změnit výchozí chování na klíče protokolu a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="44489-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="44489-231">Informace odebrané z hlaviček zpráv při protokolování dešifrovaných/nešifrovaných zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="44489-232">Pokud jsou zprávy protokolovány v dešifrovaném/nešifrovaném tvaru, jsou klíče zabezpečení a potenciálně osobní informace ve výchozím nastavení odebrány z záhlaví zpráv a těla zprávy před jejich zápisem do protokolu.</span><span class="sxs-lookup"><span data-stu-id="44489-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="44489-233">Následující seznam uvádí, co WCF považuje klíče a potenciálně osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="44489-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="44489-234">Odebrané klíče:</span><span class="sxs-lookup"><span data-stu-id="44489-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="44489-235">\- pro xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="44489-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="44489-236">wst: BinarySecret</span><span class="sxs-lookup"><span data-stu-id="44489-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="44489-237">wst: entropie</span><span class="sxs-lookup"><span data-stu-id="44489-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="44489-238">\- pro xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="44489-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="44489-239">wsse: heslo</span><span class="sxs-lookup"><span data-stu-id="44489-239">wsse:Password</span></span>  
  
 <span data-ttu-id="44489-240">wsse: nonce</span><span class="sxs-lookup"><span data-stu-id="44489-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="44489-241">Potenciálně odstraněné osobní informace:</span><span class="sxs-lookup"><span data-stu-id="44489-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="44489-242">\- pro xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="44489-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="44489-243">wsse: username</span><span class="sxs-lookup"><span data-stu-id="44489-243">wsse:Username</span></span>  
  
 <span data-ttu-id="44489-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="44489-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="44489-245">\- pro xmlns: SAML = "urn: Oasis: names: TC: SAML: 1.0: assertion" položky tučným písmem (níže) jsou odebrány:</span><span class="sxs-lookup"><span data-stu-id="44489-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="44489-246">Kontrolní výraz \<</span><span class="sxs-lookup"><span data-stu-id="44489-246">\<Assertion</span></span>  
  
 <span data-ttu-id="44489-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="44489-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="44489-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="44489-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="44489-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="44489-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="44489-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="44489-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="44489-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="44489-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="44489-252">Podmínky \<NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="44489-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="44489-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="44489-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="44489-254">\<cílovou skupinu > [URI]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="44489-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="44489-255">\</AudienceRestrictionCondition > \*</span><span class="sxs-lookup"><span data-stu-id="44489-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="44489-256">\<DoNotCacheCondition/> \*</span><span class="sxs-lookup"><span data-stu-id="44489-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="44489-257"><\!– abstraktní základní typ</span><span class="sxs-lookup"><span data-stu-id="44489-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="44489-258">Podmínka \</> \*</span><span class="sxs-lookup"><span data-stu-id="44489-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="44489-259">\</Conditions >?</span><span class="sxs-lookup"><span data-stu-id="44489-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="44489-260">\<rad ></span><span class="sxs-lookup"><span data-stu-id="44489-260">\<Advice></span></span>  
  
 <span data-ttu-id="44489-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="44489-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="44489-262">\<kontrolní výraz > [kontrolní výraz]\</assertion > \*</span><span class="sxs-lookup"><span data-stu-id="44489-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="44489-263">[any] \*</span><span class="sxs-lookup"><span data-stu-id="44489-263">[any]\*</span></span>  
  
 <span data-ttu-id="44489-264">\</Advice >?</span><span class="sxs-lookup"><span data-stu-id="44489-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="44489-265"><\!– abstraktní základní typy</span><span class="sxs-lookup"><span data-stu-id="44489-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="44489-266">Příkaz \</> \*</span><span class="sxs-lookup"><span data-stu-id="44489-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="44489-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="44489-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="44489-268">\<> předmětu</span><span class="sxs-lookup"><span data-stu-id="44489-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="44489-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="44489-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="44489-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="44489-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="44489-271">\<SubjectConfirmationData > [any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="44489-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="44489-272">\<DS: KeyInfo >...\</DS: KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="44489-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="44489-273">\</SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="44489-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="44489-274">\</Subject ></span><span class="sxs-lookup"><span data-stu-id="44489-274">\</Subject></span></span>  
  
 <span data-ttu-id="44489-275">\</SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="44489-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="44489-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="44489-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="44489-277">AuthenticationMethod = "[identifikátor URI]"</span><span class="sxs-lookup"><span data-stu-id="44489-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="44489-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="44489-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="44489-279">Závislosti</span><span class="sxs-lookup"><span data-stu-id="44489-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="44489-280">< elementů AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="44489-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="44489-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="44489-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="44489-282">Location = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="44489-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="44489-283">Binding = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="44489-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="44489-284">\</AuthenticationStatement > \*</span><span class="sxs-lookup"><span data-stu-id="44489-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="44489-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="44489-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="44489-286">Závislosti</span><span class="sxs-lookup"><span data-stu-id="44489-286">[Subject]</span></span>  
  
 <span data-ttu-id="44489-287">Atribut \<</span><span class="sxs-lookup"><span data-stu-id="44489-287">\<Attribute</span></span>  
  
 <span data-ttu-id="44489-288">AttributeName = "[řetězec]"</span><span class="sxs-lookup"><span data-stu-id="44489-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="44489-289">AttributeNamespace = "[identifikátor URI]"</span><span class="sxs-lookup"><span data-stu-id="44489-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="44489-290">\</Attribute > +</span><span class="sxs-lookup"><span data-stu-id="44489-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="44489-291">\</AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="44489-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="44489-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="44489-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="44489-293">Prostředek = "[identifikátor URI]"</span><span class="sxs-lookup"><span data-stu-id="44489-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="44489-294">Rozhodnutí = "[Povolit&#124;odmítnutí&#124;neurčitelné]"</span><span class="sxs-lookup"><span data-stu-id="44489-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="44489-295">Závislosti</span><span class="sxs-lookup"><span data-stu-id="44489-295">[Subject]</span></span>  
  
 <span data-ttu-id="44489-296">\<Action Namespace = "[URI]" > [String]\<za akci > +</span><span class="sxs-lookup"><span data-stu-id="44489-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="44489-297">\<legitimace ></span><span class="sxs-lookup"><span data-stu-id="44489-297">\<Evidence></span></span>  
  
 <span data-ttu-id="44489-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="44489-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="44489-299">\<kontrolní výraz > [kontrolní výraz]\</assertion > +</span><span class="sxs-lookup"><span data-stu-id="44489-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="44489-300">\</evidence >?</span><span class="sxs-lookup"><span data-stu-id="44489-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="44489-301">\</AuthorizationDecisionStatement > \*</span><span class="sxs-lookup"><span data-stu-id="44489-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="44489-302">\</assertion ></span><span class="sxs-lookup"><span data-stu-id="44489-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="44489-303">Informace odebrané z těla zprávy při protokolování dešifrovaných/nešifrovaných zpráv</span><span class="sxs-lookup"><span data-stu-id="44489-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="44489-304">Jak je popsáno výše, WCF odebere klíče a známé potenciálně osobní informace z hlaviček zpráv pro protokolované/nešifrované zprávy protokolu.</span><span class="sxs-lookup"><span data-stu-id="44489-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="44489-305">Kromě toho WCF odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zprávy o zabezpečení zapojené do výměny klíčů.</span><span class="sxs-lookup"><span data-stu-id="44489-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="44489-306">Pro následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="44489-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="44489-307">xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (například pokud není k dispozici žádná akce)</span><span class="sxs-lookup"><span data-stu-id="44489-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="44489-308">Odeberou se informace pro tyto prvky těla, které zahrnují výměnu klíčů:</span><span class="sxs-lookup"><span data-stu-id="44489-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="44489-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="44489-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="44489-310">wst: RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="44489-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="44489-311">wst: třída RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="44489-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="44489-312">Odeberou se taky informace pro každou z těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="44489-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="44489-313">Z hlaviček specifických pro aplikaci a dat těla nejsou odebrány žádné informace</span><span class="sxs-lookup"><span data-stu-id="44489-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="44489-314">WCF nesleduje osobní údaje v hlavičkách specifických pro aplikace (například řetězce dotazů) nebo data základního textu (například číslo platební karty).</span><span class="sxs-lookup"><span data-stu-id="44489-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="44489-315">Když je zapnuté protokolování zpráv, můžou se v protokolech zobrazovat osobní informace v záhlavích specifických pro jednotlivé aplikace a informace o textu.</span><span class="sxs-lookup"><span data-stu-id="44489-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="44489-316">Znovu, nástroj pro nasazení aplikace zodpovídá za nastavení seznamů ACL pro konfigurační soubory a soubory protokolů.</span><span class="sxs-lookup"><span data-stu-id="44489-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="44489-317">Můžou také vypnout protokolování, pokud nechtějí zobrazovat tyto informace, nebo tyto informace vyfiltrovat ze souborů protokolu po jejich zaprotokolování.</span><span class="sxs-lookup"><span data-stu-id="44489-317">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="44489-318">Trasování modelu služby</span><span class="sxs-lookup"><span data-stu-id="44489-318">Service Model Tracing</span></span>  
 <span data-ttu-id="44489-319">Zdroj trasování modelu služby (<xref:System.ServiceModel>) umožňuje sledovat aktivity a události související se zpracováním zprávy.</span><span class="sxs-lookup"><span data-stu-id="44489-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="44489-320">Tato funkce používá diagnostické funkce .NET Framework z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="44489-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="44489-321">Stejně jako u vlastnosti <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> je umístění a seznam ACL uživatelsky konfigurovatelné pomocí konfiguračních souborů aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44489-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="44489-322">Stejně jako u protokolování zpráv je umístění souboru vždy nakonfigurované, když správce povolí trasování; Proto správce řídí seznam ACL.</span><span class="sxs-lookup"><span data-stu-id="44489-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="44489-323">Pokud je zpráva v oboru, trasování obsahují záhlaví zpráv.</span><span class="sxs-lookup"><span data-stu-id="44489-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="44489-324">Stejná pravidla pro skrývání potenciálně osobních údajů v hlavičkách zpráv v předchozí části platí: osobní údaje, které byly dříve identifikovány, jsou ve výchozím nastavení odebrány z hlaviček v trasování.</span><span class="sxs-lookup"><span data-stu-id="44489-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="44489-325">Aby bylo možné protokolovat potenciálně osobní údaje, musí konfigurace správce počítače i nástroj pro nasazení aplikace upravit.</span><span class="sxs-lookup"><span data-stu-id="44489-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="44489-326">Osobní údaje obsažené v hlavičkách specifických pro aplikace jsou však zaznamenávány do trasování.</span><span class="sxs-lookup"><span data-stu-id="44489-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="44489-327">Nástroj pro nasazení aplikace zodpovídá za nastavení seznamů ACL pro konfigurační a trasovací soubory.</span><span class="sxs-lookup"><span data-stu-id="44489-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="44489-328">Mohou také vypnout trasování pro skrytí těchto informací nebo odfiltrovat tyto informace z trasovacích souborů po jejich zaprotokolování.</span><span class="sxs-lookup"><span data-stu-id="44489-328">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="44489-329">V rámci trasování ServiceModel (označované jako ID aktivit a obvykle identifikátor GUID) propojuje různé aktivity společně jako zprávu mezi různými částmi infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="44489-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="44489-330">Vlastní naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="44489-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="44489-331">Pro protokolování a trasování zpráv je možné nakonfigurovat vlastní naslouchací proces trasování, který může odesílat trasování a zprávy na lince (například do vzdálené databáze).</span><span class="sxs-lookup"><span data-stu-id="44489-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="44489-332">Nástroj pro nasazení aplikací zodpovídá za konfiguraci vlastních naslouchacího procesu nebo k tomu, aby je uživatelé mohli použít.</span><span class="sxs-lookup"><span data-stu-id="44489-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="44489-333">Zodpovídá taky za všechny osobní údaje vystavené ve vzdáleném umístění a pro správné použití seznamů ACL do tohoto umístění.</span><span class="sxs-lookup"><span data-stu-id="44489-333">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="44489-334">Další funkce pro odborníky v oblasti IT</span><span class="sxs-lookup"><span data-stu-id="44489-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="44489-335">WCF má poskytovatele rozhraní WMI, který zpřístupňuje informace o konfiguraci infrastruktury WCF prostřednictvím rozhraní WMI (dodávané se systémem Windows).</span><span class="sxs-lookup"><span data-stu-id="44489-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="44489-336">Ve výchozím nastavení je rozhraní WMI k dispozici správcům.</span><span class="sxs-lookup"><span data-stu-id="44489-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="44489-337">Konfigurace WCF používá mechanismus konfigurace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44489-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="44489-338">Konfigurační soubory jsou uloženy v počítači.</span><span class="sxs-lookup"><span data-stu-id="44489-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="44489-339">Vývojář aplikací a správce vytvoří konfigurační soubory a seznam řízení přístupu pro jednotlivé požadavky aplikace.</span><span class="sxs-lookup"><span data-stu-id="44489-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="44489-340">Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="44489-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="44489-341">Certifikáty lze použít k poskytnutí dat aplikací pro konfiguraci různých vlastností funkcí používaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="44489-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="44489-342">WCF také používá funkci výpisu paměti procesu .NET Framework voláním metody <xref:System.Environment.FailFast%2A>.</span><span class="sxs-lookup"><span data-stu-id="44489-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="44489-343">Nástroje pro IT specialisty</span><span class="sxs-lookup"><span data-stu-id="44489-343">IT Pro Tools</span></span>  
 <span data-ttu-id="44489-344">WCF nabízí také následující profesionální nástroje, které dodávají Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="44489-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="44489-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="44489-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="44489-346">Prohlížeč zobrazí trasovací soubory WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="44489-347">Prohlížeč zobrazuje všechny informace, které jsou obsaženy v trasováních.</span><span class="sxs-lookup"><span data-stu-id="44489-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="44489-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="44489-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="44489-349">Editor umožňuje uživateli vytvářet a upravovat konfigurační soubory služby WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="44489-350">Editor zobrazuje informace, které jsou obsaženy v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="44489-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="44489-351">Stejný úkol lze provést pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="44489-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="44489-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="44489-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="44489-353">Tento nástroj umožňuje uživateli spravovat na počítači instalaci ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="44489-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="44489-354">Nástroj zobrazí stavové zprávy v okně konzoly při spuštění a v procesu se může zobrazit informace o konfiguraci instalace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="44489-355">WSATConfig. exe a WSATUI. dll</span><span class="sxs-lookup"><span data-stu-id="44489-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="44489-356">Tyto nástroje umožňují odborníkům v oblasti IT konfigurovat interoperabilní podporu sítě WS-AtomicTransaction ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="44489-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="44489-357">Nástroje se zobrazí a umožní uživateli změnit hodnoty nejčastěji používaných nastavení WS-AtomicTransaction uložených v registru.</span><span class="sxs-lookup"><span data-stu-id="44489-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="44489-358">Funkce pro různé vyprůřezování</span><span class="sxs-lookup"><span data-stu-id="44489-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="44489-359">Následující funkce jsou křížově vykrájené.</span><span class="sxs-lookup"><span data-stu-id="44489-359">The following features are cross-cutting.</span></span> <span data-ttu-id="44489-360">To znamená, že mohou být tvořeny kteroukoli z výše uvedených funkcí.</span><span class="sxs-lookup"><span data-stu-id="44489-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="44489-361">Architektura služby</span><span class="sxs-lookup"><span data-stu-id="44489-361">Service Framework</span></span>  
 <span data-ttu-id="44489-362">Hlavičky mohou obsahovat ID instance, což je identifikátor GUID, který přidruží zprávu s instancí třídy CLR.</span><span class="sxs-lookup"><span data-stu-id="44489-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="44489-363">Jazyk WSDL (Web Services Description Language) obsahuje definici portu.</span><span class="sxs-lookup"><span data-stu-id="44489-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="44489-364">Každý port má adresu koncového bodu a vazbu, která představuje služby používané aplikací.</span><span class="sxs-lookup"><span data-stu-id="44489-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="44489-365">Vystavení kódu WSDL může být vypnuto pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="44489-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="44489-366">V počítači nejsou uchovány žádné informace.</span><span class="sxs-lookup"><span data-stu-id="44489-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44489-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="44489-367">See also</span></span>

- [<span data-ttu-id="44489-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="44489-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="44489-369">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44489-369">Security</span></span>](./feature-details/security.md)
