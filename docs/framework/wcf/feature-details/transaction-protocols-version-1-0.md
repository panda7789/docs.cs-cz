---
title: Protokoly transakce verze 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: d2a50e798af47dd4f80f149362f2afffbab007f6
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066360"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="5df4f-102">Protokoly transakce verze 1.0</span><span class="sxs-lookup"><span data-stu-id="5df4f-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="5df4f-103">Windows Communication Foundation (WCF) verze 1 implementuje protokol WS-koordinaci a WS-Atomic Transactions verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="5df4f-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="5df4f-104">Další informace o verzi 1.1 naleznete v tématu [protokoly transakcí](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="5df4f-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="5df4f-105">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="5df4f-105">Specification/Document</span></span>|<span data-ttu-id="5df4f-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5df4f-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="5df4f-107">Koordinace WS</span><span class="sxs-lookup"><span data-stu-id="5df4f-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="5df4f-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="5df4f-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="5df4f-109">Vzájemná funkční spolupráce na této specifikaci protokolu vyžádáním ve dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek).</span><span class="sxs-lookup"><span data-stu-id="5df4f-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="5df4f-110">Specifikace podrobnému popisu, skvělé formáty zpráv a zpráv exchange pro obě úrovně interoperability.</span><span class="sxs-lookup"><span data-stu-id="5df4f-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="5df4f-111">Některé zabezpečení, spolehlivost a kódování aplikace aplikace exchange platí, jako je tomu u aplikace regulární systému exchange.</span><span class="sxs-lookup"><span data-stu-id="5df4f-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="5df4f-112">Úspěšné vzájemná funkční spolupráce mezi správci transakcí však vyžaduje smlouvou pro konkrétní vazbu, protože není obvykle nakonfigurovaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5df4f-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="5df4f-113">Toto téma popisuje složení specifikaci WS-Atomic Transactions (WS-AT) se zabezpečením a popisuje zabezpečené vazby používaný ke komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="5df4f-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="5df4f-114">Postup popsaný v tomto dokumentu se úspěšně testoval se systémem jiným implementacím WS-AT a WS-koordinace včetně IBM, IONA, Sun Microsystems a dalších.</span><span class="sxs-lookup"><span data-stu-id="5df4f-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="5df4f-115">Následující obrázek znázorňuje interoperabilitu mezi dvěma vedoucími transakce, transakce Manager 1 a 2 správce transakcí a dvě aplikace, aplikace 1 a 2 aplikace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="5df4f-116">![Protokoly transakcí](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="5df4f-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="5df4f-117">Vezměte v úvahu Typický scénář WS-koordinace/WS-Atomic Transactions jednoho iniciátoru (I) a jeden účastník (P).</span><span class="sxs-lookup"><span data-stu-id="5df4f-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="5df4f-118">Iniciátor i účastníka mají správci transakcí (ITM a druh, v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="5df4f-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="5df4f-119">Dvoufázového potvrzení se označuje jako 2PC v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5df4f-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5df4f-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="5df4f-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="5df4f-121">12. Zpráva odpovědi aplikace</span><span class="sxs-lookup"><span data-stu-id="5df4f-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="5df4f-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="5df4f-123">13. Potvrzení změn (dokončení)</span><span class="sxs-lookup"><span data-stu-id="5df4f-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="5df4f-124">3. Registr (dokončení)</span><span class="sxs-lookup"><span data-stu-id="5df4f-124">3. Register (Completion)</span></span>|<span data-ttu-id="5df4f-125">14. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="5df4f-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-126">4. RegisterResponse</span></span>|<span data-ttu-id="5df4f-127">15. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="5df4f-128">5. Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-128">5. Application Message</span></span>|<span data-ttu-id="5df4f-129">16. Připravené (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="5df4f-130">6. CreateCoordinationContext s kontextem</span><span class="sxs-lookup"><span data-stu-id="5df4f-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="5df4f-131">17. Připravené (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="5df4f-132">7. Registr (trvale)</span><span class="sxs-lookup"><span data-stu-id="5df4f-132">7. Register (Durable)</span></span>|<span data-ttu-id="5df4f-133">18. Potvrdit (dokončení)</span><span class="sxs-lookup"><span data-stu-id="5df4f-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="5df4f-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-134">8. RegisterResponse</span></span>|<span data-ttu-id="5df4f-135">19. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="5df4f-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="5df4f-137">20. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="5df4f-138">10. Registr (trvale)</span><span class="sxs-lookup"><span data-stu-id="5df4f-138">10. Register (Durable)</span></span>|<span data-ttu-id="5df4f-139">21. Potvrdit (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="5df4f-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-140">11. RegisterResponse</span></span>|<span data-ttu-id="5df4f-141">22. Potvrdit (2PC)</span><span class="sxs-lookup"><span data-stu-id="5df4f-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="5df4f-142">Tento dokument popisuje složení specifikaci WS-AtomicTransaction se zabezpečením a zabezpečené vazby používaný ke komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="5df4f-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="5df4f-143">Postup popsaný v tomto dokumentu bylo úspěšně otestovat s jinými implementacemi WS-AT a WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="5df4f-144">Obrázek a tabulka ukazuje čtyři třídy zpráv z hlediska zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="5df4f-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="5df4f-145">Aktivace zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="5df4f-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="5df4f-146">Registrační zprávy (registr a RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="5df4f-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="5df4f-147">Protokol zprávy (připravit, vrácení změn, potvrzení, přerušeno a tak dále).</span><span class="sxs-lookup"><span data-stu-id="5df4f-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="5df4f-148">Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-148">Application messages.</span></span>  
  
 <span data-ttu-id="5df4f-149">První tři zpráva třídy jsou považovány za správce transakcí zpráv a jejich vazbu konfigurace je popsaná v "Aplikace zpráv Exchange" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5df4f-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="5df4f-150">Čtvrtý třída zprávy zprávy do aplikací a je popsaný v části "Zpráva příklady" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5df4f-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="5df4f-151">Tato část popisuje protokol vazby používá pro každou z těchto tříd WCF.</span><span class="sxs-lookup"><span data-stu-id="5df4f-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="5df4f-152">V tomto dokumentu se používá následující obory názvů XML a přidružené předpony.</span><span class="sxs-lookup"><span data-stu-id="5df4f-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="5df4f-153">Předpona</span><span class="sxs-lookup"><span data-stu-id="5df4f-153">Prefix</span></span>|<span data-ttu-id="5df4f-154">Identifikátor URI Namespace</span><span class="sxs-lookup"><span data-stu-id="5df4f-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="5df4f-155">s11</span><span class="sxs-lookup"><span data-stu-id="5df4f-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="5df4f-156">wsa</span><span class="sxs-lookup"><span data-stu-id="5df4f-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="5df4f-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="5df4f-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="5df4f-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="5df4f-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="5df4f-159">t</span><span class="sxs-lookup"><span data-stu-id="5df4f-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="5df4f-160">o</span><span class="sxs-lookup"><span data-stu-id="5df4f-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="5df4f-161">XSD</span><span class="sxs-lookup"><span data-stu-id="5df4f-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="5df4f-162">Správce transakcí vazby</span><span class="sxs-lookup"><span data-stu-id="5df4f-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="5df4f-163">R1001: Správci transakcí musí používat protokol SOAP 1.1 a WS-Addressing 2004/08 protokolu WS-AtomicTransaction a výměny zpráv WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="5df4f-164">Zprávy aplikace nejsou omezeny na těchto vazeb a jsou popsané dále.</span><span class="sxs-lookup"><span data-stu-id="5df4f-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="5df4f-165">Vazba HTTPS správce transakcí</span><span class="sxs-lookup"><span data-stu-id="5df4f-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="5df4f-166">Vazba HTTPS správce transakcí spoléhá výhradně na zabezpečení přenosu k zajištění zabezpečení a navázání vztahu důvěryhodnosti mezi každý pár odesílatele příjemce ve stromové struktuře transakce.</span><span class="sxs-lookup"><span data-stu-id="5df4f-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="5df4f-167">Konfigurace protokolu HTTPS přenosu</span><span class="sxs-lookup"><span data-stu-id="5df4f-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="5df4f-168">Zřízení správce transakcí Identity se používají certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="5df4f-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="5df4f-169">Je požadováno ověření klient/server a klient/server autorizace je ponechané jako podrobnost implementace:</span><span class="sxs-lookup"><span data-stu-id="5df4f-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="5df4f-170">R1111: Certifikáty X.509 zobrazí přenosu musí mít název subjektu, který odpovídá plně kvalifikovaný název domény (FQDN) počítači původce.</span><span class="sxs-lookup"><span data-stu-id="5df4f-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="5df4f-171">B1112: DNS musí být funkční mezi každý pár odesílatele příjemce v systému pro kontroly název subjektu X.509 proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5df4f-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="5df4f-172">Aktivace a konfigurace vazby registrace</span><span class="sxs-lookup"><span data-stu-id="5df4f-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="5df4f-173">WCF vyžaduje požadavek nebo odpověď duplexní vazby s korelací přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5df4f-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="5df4f-174">(Další informace o korelaci a popisy vzorů exchange zpráv žádost odpověď, najdete v protokolu WS-AtomicTransaction, část 8.)</span><span class="sxs-lookup"><span data-stu-id="5df4f-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="5df4f-175">Konfigurace vazeb protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="5df4f-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="5df4f-176">WCF podporuje zprávy jednosměrné (datagram) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5df4f-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="5df4f-177">Korelace mezi zprávy je ponechané jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="5df4f-178">B2131: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelace zpráv WCF vaší 2PC.</span><span class="sxs-lookup"><span data-stu-id="5df4f-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="5df4f-179">Správce transakcí ve smíšeném vazby zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5df4f-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="5df4f-180">Toto je alternativní (ve smíšeném režimu) vazby zabezpečení přenosu používá v kombinaci s modelem WS-koordinace vystavený Token pro účely identity zařízení.</span><span class="sxs-lookup"><span data-stu-id="5df4f-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="5df4f-181">Aktivace a registrace jsou pouze prvky, které se liší mezi dvě vazby.</span><span class="sxs-lookup"><span data-stu-id="5df4f-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="5df4f-182">Konfigurace protokolu HTTPS přenosu</span><span class="sxs-lookup"><span data-stu-id="5df4f-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="5df4f-183">Zřízení správce transakcí Identity se používají certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="5df4f-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="5df4f-184">Vyžaduje se klientem a serverem ověřování a autorizace klienta nebo serveru je ponecháno jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="5df4f-185">Konfigurace vazby zprávy aktivace</span><span class="sxs-lookup"><span data-stu-id="5df4f-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="5df4f-186">Aktivace zprávy obvykle nejsou součástí interoperability vzhledem k tomu obvykle dochází mezi aplikací a její místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="5df4f-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="5df4f-187">B1221: WCF používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivaci zprávy.</span><span class="sxs-lookup"><span data-stu-id="5df4f-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="5df4f-188">Žádost a odpověď zprávy se korelují pomocí WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5df4f-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="5df4f-189">Specifikace WS-Atomic Transactions, 8 část popisuje další podrobnosti o korelaci a vzory zpráv exchange.</span><span class="sxs-lookup"><span data-stu-id="5df4f-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="5df4f-190">R1222: Po přijetí `CreateCoordinationContext`, musíte vydat koordinátor `SecurityContextToken` s tajným klíčem přidružené `STx`.</span><span class="sxs-lookup"><span data-stu-id="5df4f-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="5df4f-191">Tento token se vrátí uvnitř `t:IssuedTokens` záhlaví podle specifikace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="5df4f-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="5df4f-192">R1223: Pokud dojde k aktivaci v rámci existující kontext koordinace `t:IssuedTokens` záhlaví s `SecurityContextToken` spojené s existujícím kontextu toku na `CreateCoordinationContext` zprávy.</span><span class="sxs-lookup"><span data-stu-id="5df4f-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="5df4f-193">Nový `t:IssuedTokens` záhlaví by měl být vygenerován pro připojení k odchozích dat `wscoor:CreateCoordinationContextResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="5df4f-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="5df4f-194">Konfigurace vazby zpráva registrace</span><span class="sxs-lookup"><span data-stu-id="5df4f-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="5df4f-195">B1231: WCF používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="5df4f-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="5df4f-196">Žádost a odpověď zprávy se korelují pomocí WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5df4f-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="5df4f-197">WS-AtomicTransaction, část 8, popisuje další podrobnosti o korelaci a popisy vzorů zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="5df4f-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="5df4f-198">R1232: Odchozí `wscoor:Register` musí používat zprávy `IssuedTokenOverTransport` režim ověřování je popsáno v [protokoly zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="5df4f-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="5df4f-199">`wsse:Timestamp` Elementu musí být podepsané pomocí `SecurityContextToken STx` vydané.</span><span class="sxs-lookup"><span data-stu-id="5df4f-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="5df4f-200">Tento podpis je doklad o vlastnictví tokenu přidružený k konkrétní transakce a slouží k ověřování účastníka uvedení v transakci.</span><span class="sxs-lookup"><span data-stu-id="5df4f-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="5df4f-201">RegistrationResponse zpráva se pošle zpět prostřednictvím protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5df4f-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="5df4f-202">Konfigurace vazeb protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="5df4f-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="5df4f-203">WCF podporuje zprávy jednosměrné (datagram) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5df4f-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="5df4f-204">Korelace mezi zprávy je ponechané jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="5df4f-205">B2131: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelace zpráv WCF vaší 2PC.</span><span class="sxs-lookup"><span data-stu-id="5df4f-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="5df4f-206">Aplikace zprávy Exchange</span><span class="sxs-lookup"><span data-stu-id="5df4f-206">Application Message Exchange</span></span>  
 <span data-ttu-id="5df4f-207">Aplikace se můžete používat konkrétní vazbu pro zprávy aplikace do aplikace, tak dlouho, dokud vazbu splňuje následující požadavky na zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="5df4f-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="5df4f-208">R2001: Toku aplikace aplikace zprávy `t:IssuedTokens` záhlaví spolu s `CoordinationContext` v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="5df4f-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="5df4f-209">R2002: Integritu a důvěrnost `t:IssuedToken` musí být zadaná.</span><span class="sxs-lookup"><span data-stu-id="5df4f-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="5df4f-210">`CoordinationContext` Obsahuje záhlaví `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="5df4f-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="5df4f-211">Při definici `xsd:AnyURI` umožňuje použít absolutní a relativní identifikátory URI, WCF podporuje pouze `wscoor:Identifiers`, které jsou absolutní URI.</span><span class="sxs-lookup"><span data-stu-id="5df4f-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="5df4f-212">Pokud `wscoor:Identifier` z `wscoor:CoordinationContext` je relativní identifikátor URI, vrátí se chyby z transakční služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="5df4f-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="5df4f-213">Příklady zprávy</span><span class="sxs-lookup"><span data-stu-id="5df4f-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="5df4f-214">Zprávy požadavků/odpovědí CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="5df4f-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="5df4f-215">Tyto zprávy se řídí vzorem žádostí a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5df4f-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="5df4f-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="5df4f-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="5df4f-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="5df4f-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="5df4f-218">Registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="5df4f-218">Registration Messages</span></span>  
 <span data-ttu-id="5df4f-219">Tyto zprávy jsou zprávy registrace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="5df4f-220">Registr</span><span class="sxs-lookup"><span data-stu-id="5df4f-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="5df4f-221">Registrovat odpovědi</span><span class="sxs-lookup"><span data-stu-id="5df4f-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="5df4f-222">Dvě fáze potvrzení protokolu zpráv</span><span class="sxs-lookup"><span data-stu-id="5df4f-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="5df4f-223">Tato zpráva má vztah k protokol dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="5df4f-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="5df4f-224">Potvrzení změn</span><span class="sxs-lookup"><span data-stu-id="5df4f-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="5df4f-225">Aplikace zprávy</span><span class="sxs-lookup"><span data-stu-id="5df4f-225">Application Messages</span></span>  
 <span data-ttu-id="5df4f-226">Tyto zprávy jsou zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="5df4f-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="5df4f-227">Zpráva žádosti</span><span class="sxs-lookup"><span data-stu-id="5df4f-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
