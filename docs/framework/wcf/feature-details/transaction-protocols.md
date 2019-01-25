---
title: Protokoly transakcí
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 559b7ec1539a43ec27010031320be144d6f5e24b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533764"
---
# <a name="transaction-protocols"></a><span data-ttu-id="e0b25-102">Protokoly transakcí</span><span class="sxs-lookup"><span data-stu-id="e0b25-102">Transaction Protocols</span></span>
<span data-ttu-id="e0b25-103">Windows Communication Foundation (WCF) implementuje WS-koordinaci a WS-Atomic Transactions protokoly.</span><span class="sxs-lookup"><span data-stu-id="e0b25-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="e0b25-104">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="e0b25-104">Specification/Document</span></span>|<span data-ttu-id="e0b25-105">Version</span><span class="sxs-lookup"><span data-stu-id="e0b25-105">Version</span></span>|<span data-ttu-id="e0b25-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e0b25-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="e0b25-107">Koordinace WS</span><span class="sxs-lookup"><span data-stu-id="e0b25-107">WS-Coordination</span></span>|<span data-ttu-id="e0b25-108">1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-108">1.0</span></span><br /><br /> <span data-ttu-id="e0b25-109">1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-109">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96104](https://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="e0b25-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="e0b25-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="e0b25-111">1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-111">1.0</span></span><br /><br /> <span data-ttu-id="e0b25-112">1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-112">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> https://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="e0b25-113">Vzájemná funkční spolupráce na této specifikaci protokolu vyžádáním ve dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek).</span><span class="sxs-lookup"><span data-stu-id="e0b25-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="e0b25-114">Specifikace podrobnému popisu, skvělé formáty zpráv a zpráv exchange pro obě úrovně interoperability.</span><span class="sxs-lookup"><span data-stu-id="e0b25-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="e0b25-115">Některé zabezpečení, spolehlivost a kódování aplikace aplikace exchange platí, jako je tomu u aplikace regulární systému exchange.</span><span class="sxs-lookup"><span data-stu-id="e0b25-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="e0b25-116">Úspěšné vzájemná funkční spolupráce mezi správci transakcí však vyžaduje smlouvou pro konkrétní vazbu, protože není obvykle nakonfigurovaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e0b25-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="e0b25-117">Toto téma popisuje složení specifikaci WS-Atomic Transactions (WS-AT) se zabezpečením a popisuje zabezpečené vazby používaný ke komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="e0b25-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e0b25-118">Postup popsaný v tomto dokumentu se úspěšně testoval se systémem jiným implementacím WS-AT a WS-koordinace včetně IBM, IONA, Sun Microsystems a dalších.</span><span class="sxs-lookup"><span data-stu-id="e0b25-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="e0b25-119">Následující obrázek znázorňuje interoperabilitu mezi dvěma vedoucími transakce, transakce Manager 1 a 2 správce transakcí a dvě aplikace, aplikace 1 a 2 aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="e0b25-120">![Protokoly transakcí](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="e0b25-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="e0b25-121">Vezměte v úvahu Typický scénář WS-koordinace/WS-Atomic Transactions jednoho iniciátoru (I) a jeden účastník (P).</span><span class="sxs-lookup"><span data-stu-id="e0b25-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="e0b25-122">Iniciátor i účastníka mají správci transakcí (ITM a druh, v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="e0b25-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="e0b25-123">Dvoufázového potvrzení se označuje jako 2PC v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0b25-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0b25-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e0b25-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="e0b25-125">12. Zpráva odpovědi aplikace</span><span class="sxs-lookup"><span data-stu-id="e0b25-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="e0b25-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e0b25-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e0b25-127">13. Potvrzení změn (dokončení)</span><span class="sxs-lookup"><span data-stu-id="e0b25-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="e0b25-128">3. Registr (dokončení)</span><span class="sxs-lookup"><span data-stu-id="e0b25-128">3. Register (Completion)</span></span>|<span data-ttu-id="e0b25-129">14. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e0b25-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e0b25-130">4. RegisterResponse</span></span>|<span data-ttu-id="e0b25-131">15. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e0b25-132">5. Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-132">5. Application Message</span></span>|<span data-ttu-id="e0b25-133">16. Připravené (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e0b25-134">6. CreateCoordinationContext s kontextem</span><span class="sxs-lookup"><span data-stu-id="e0b25-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="e0b25-135">17. Připravené (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e0b25-136">7. Registr (trvale)</span><span class="sxs-lookup"><span data-stu-id="e0b25-136">7. Register (Durable)</span></span>|<span data-ttu-id="e0b25-137">18. Potvrdit (dokončení)</span><span class="sxs-lookup"><span data-stu-id="e0b25-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="e0b25-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e0b25-138">8. RegisterResponse</span></span>|<span data-ttu-id="e0b25-139">19. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="e0b25-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e0b25-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e0b25-141">20. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="e0b25-142">10. Registr (trvale)</span><span class="sxs-lookup"><span data-stu-id="e0b25-142">10. Register (Durable)</span></span>|<span data-ttu-id="e0b25-143">21. Potvrdit (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="e0b25-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e0b25-144">11. RegisterResponse</span></span>|<span data-ttu-id="e0b25-145">22. Potvrdit (2PC)</span><span class="sxs-lookup"><span data-stu-id="e0b25-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="e0b25-146">Tento dokument popisuje složení specifikaci WS-AtomicTransaction se zabezpečením a zabezpečené vazby používaný ke komunikace mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="e0b25-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e0b25-147">Postup popsaný v tomto dokumentu bylo úspěšně otestovat s jinými implementacemi WS-AT a WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="e0b25-148">Obrázek a tabulka ukazuje čtyři třídy zpráv z hlediska zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="e0b25-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="e0b25-149">Aktivace zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="e0b25-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="e0b25-150">Registrační zprávy (registr a RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="e0b25-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="e0b25-151">Protokol zprávy (připravit, vrácení změn, potvrzení, přerušeno a tak dále).</span><span class="sxs-lookup"><span data-stu-id="e0b25-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="e0b25-152">Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-152">Application messages.</span></span>  
  
 <span data-ttu-id="e0b25-153">První tři zpráva třídy jsou považovány za správce transakcí zpráv a jejich vazbu konfigurace je popsaná v "Aplikace zpráv Exchange" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0b25-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="e0b25-154">Čtvrtý třída zprávy zprávy do aplikací a je popsaný v části "Zpráva příklady" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0b25-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="e0b25-155">Tato část popisuje protokol vazby používá pro každou z těchto tříd WCF.</span><span class="sxs-lookup"><span data-stu-id="e0b25-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="e0b25-156">V tomto dokumentu se používá následující obory názvů XML a přidružené předpony.</span><span class="sxs-lookup"><span data-stu-id="e0b25-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="e0b25-157">Předpona</span><span class="sxs-lookup"><span data-stu-id="e0b25-157">Prefix</span></span>|<span data-ttu-id="e0b25-158">Version</span><span class="sxs-lookup"><span data-stu-id="e0b25-158">Version</span></span>|<span data-ttu-id="e0b25-159">Identifikátor URI Namespace</span><span class="sxs-lookup"><span data-stu-id="e0b25-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="e0b25-160">s11</span><span class="sxs-lookup"><span data-stu-id="e0b25-160">s11</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96014](https://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="e0b25-161">wsa</span><span class="sxs-lookup"><span data-stu-id="e0b25-161">wsa</span></span>|<span data-ttu-id="e0b25-162">Pre-1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="e0b25-163">1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96022](https://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="e0b25-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="e0b25-164">wscoor</span></span>|<span data-ttu-id="e0b25-165">1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-165">1.0</span></span><br /><br /> <span data-ttu-id="e0b25-166">1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-166">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96078](https://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="e0b25-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="e0b25-167">wsat</span></span>|<span data-ttu-id="e0b25-168">1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-168">1.0</span></span><br /><br /> <span data-ttu-id="e0b25-169">1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-169">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96081](https://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="e0b25-170">t</span><span class="sxs-lookup"><span data-stu-id="e0b25-170">t</span></span>|<span data-ttu-id="e0b25-171">1.3 předem</span><span class="sxs-lookup"><span data-stu-id="e0b25-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="e0b25-172">1.3</span><span class="sxs-lookup"><span data-stu-id="e0b25-172">1.3</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96082](https://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96100](https://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="e0b25-173">o</span><span class="sxs-lookup"><span data-stu-id="e0b25-173">o</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96101](https://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="e0b25-174">XSD</span><span class="sxs-lookup"><span data-stu-id="e0b25-174">xsd</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96102](https://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="e0b25-175">Správce transakcí vazby</span><span class="sxs-lookup"><span data-stu-id="e0b25-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="e0b25-176">R1001: Správci transakcí účasti na transakci WS-AT 1.0 musí používat protokol SOAP 1.1 a WS-Addressing 2004/08 protokolu WS-AtomicTransaction a výměny zpráv WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="e0b25-177">R1002: Správci transakcí účasti na transakci WS-AT 1.1 musí používat protokol SOAP 1.1 a WS-Addressing 2005/08 protokolu WS-AtomicTransaction a výměny zpráv WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="e0b25-178">Zprávy aplikace nejsou omezeny na těchto vazeb a jsou popsané dále.</span><span class="sxs-lookup"><span data-stu-id="e0b25-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="e0b25-179">Vazba HTTPS správce transakcí</span><span class="sxs-lookup"><span data-stu-id="e0b25-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="e0b25-180">Vazba HTTPS správce transakcí spoléhá výhradně na zabezpečení přenosu k zajištění zabezpečení a navázání vztahu důvěryhodnosti mezi každý pár odesílatele příjemce ve stromové struktuře transakce.</span><span class="sxs-lookup"><span data-stu-id="e0b25-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e0b25-181">Konfigurace protokolu HTTPS přenosu</span><span class="sxs-lookup"><span data-stu-id="e0b25-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e0b25-182">Zřízení správce transakcí Identity se používají certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="e0b25-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e0b25-183">Je požadováno ověření klient/server a klient/server autorizace je ponechané jako podrobnost implementace:</span><span class="sxs-lookup"><span data-stu-id="e0b25-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="e0b25-184">R1111: Certifikáty X.509 zobrazí přenosu musí mít název subjektu, který odpovídá plně kvalifikovaný název domény (FQDN) počítači původce.</span><span class="sxs-lookup"><span data-stu-id="e0b25-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="e0b25-185">B1112: DNS musí být funkční mezi každý pár odesílatele příjemce v systému pro kontroly název subjektu X.509 proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e0b25-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="e0b25-186">Aktivace a konfigurace vazby registrace</span><span class="sxs-lookup"><span data-stu-id="e0b25-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="e0b25-187">WCF vyžaduje požadavek nebo odpověď duplexní vazby s korelací přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e0b25-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="e0b25-188">(Další informace o korelaci a popisy vzorů exchange zpráv žádost odpověď, najdete v protokolu WS-AtomicTransaction, část 8.)</span><span class="sxs-lookup"><span data-stu-id="e0b25-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e0b25-189">Konfigurace vazeb protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="e0b25-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e0b25-190">WCF podporuje zprávy jednosměrné (datagram) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e0b25-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e0b25-191">Korelace mezi zprávy je ponechané jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e0b25-192">B1131: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelace zpráv WCF vaší 2PC.</span><span class="sxs-lookup"><span data-stu-id="e0b25-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="e0b25-193">Správce transakcí ve smíšeném vazby zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e0b25-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="e0b25-194">Toto je alternativní (ve smíšeném režimu) vazby zabezpečení přenosu používá v kombinaci s modelem WS-koordinace vystavený Token pro účely identity zařízení.</span><span class="sxs-lookup"><span data-stu-id="e0b25-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="e0b25-195">Aktivace a registrace jsou pouze prvky, které se liší mezi dvě vazby.</span><span class="sxs-lookup"><span data-stu-id="e0b25-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e0b25-196">Konfigurace protokolu HTTPS přenosu</span><span class="sxs-lookup"><span data-stu-id="e0b25-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e0b25-197">Zřízení správce transakcí Identity se používají certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="e0b25-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e0b25-198">Vyžaduje se klientem a serverem ověřování a autorizace klienta nebo serveru je ponecháno jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="e0b25-199">Konfigurace vazby zprávy aktivace</span><span class="sxs-lookup"><span data-stu-id="e0b25-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="e0b25-200">Aktivace zprávy obvykle nejsou součástí interoperability vzhledem k tomu obvykle dochází mezi aplikací a její místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="e0b25-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="e0b25-201">B1221: WCF používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivaci zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0b25-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="e0b25-202">Žádost a odpověď zprávy se korelují pomocí WS-Addressing 2004/08 WS-AT 1.0 a WS-Addressing 2005/08 WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="e0b25-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="e0b25-203">Specifikace WS-Atomic Transactions, 8 část popisuje další podrobnosti o korelaci a vzory zpráv exchange.</span><span class="sxs-lookup"><span data-stu-id="e0b25-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="e0b25-204">R1222: Po přijetí `CreateCoordinationContext`, musíte vydat koordinátor `SecurityContextToken` s tajným klíčem přidružené `STx`.</span><span class="sxs-lookup"><span data-stu-id="e0b25-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="e0b25-205">Tento token se vrátí uvnitř `t:IssuedTokens` záhlaví podle specifikace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e0b25-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="e0b25-206">R1223: Pokud dojde k aktivaci v rámci existující kontext koordinace `t:IssuedTokens` záhlaví s `SecurityContextToken` spojené s existujícím kontextu toku na `CreateCoordinationContext` zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0b25-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="e0b25-207">Nový `t:IssuedTokens` záhlaví by měl být vygenerován pro připojení k odchozích dat `wscoor:CreateCoordinationContextResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0b25-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="e0b25-208">Konfigurace vazby zpráva registrace</span><span class="sxs-lookup"><span data-stu-id="e0b25-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="e0b25-209">B1231: WCF používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="e0b25-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="e0b25-210">Žádost a odpověď zprávy se korelují pomocí WS-Addressing 2004/08 WS-AT 1.0 a WS-Addressing 2005/08 WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="e0b25-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="e0b25-211">WS-AtomicTransaction, část 8, popisuje další podrobnosti o korelaci a popisy vzorů zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="e0b25-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="e0b25-212">R1232: Odchozí `wscoor:Register` musí používat zprávy `IssuedTokenOverTransport` režim ověřování je popsáno v [protokoly zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e0b25-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="e0b25-213">`wsse:Timestamp` Elementu musí být podepsané pomocí `SecurityContextToken``STx` vydané.</span><span class="sxs-lookup"><span data-stu-id="e0b25-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="e0b25-214">Tento podpis je doklad o vlastnictví tokenu přidružený k konkrétní transakce a slouží k ověřování účastníka uvedení v transakci.</span><span class="sxs-lookup"><span data-stu-id="e0b25-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="e0b25-215">RegistrationResponse zpráva se pošle zpět prostřednictvím protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e0b25-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e0b25-216">Konfigurace vazeb protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="e0b25-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e0b25-217">WCF podporuje zprávy jednosměrné (datagram) přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e0b25-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e0b25-218">Korelace mezi zprávy je ponechané jako podrobnost implementace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e0b25-219">B1241: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelace zpráv WCF vaší 2PC.</span><span class="sxs-lookup"><span data-stu-id="e0b25-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="e0b25-220">Aplikace zprávy Exchange</span><span class="sxs-lookup"><span data-stu-id="e0b25-220">Application Message Exchange</span></span>  
 <span data-ttu-id="e0b25-221">Aplikace se můžete používat konkrétní vazbu pro zprávy aplikace do aplikace, tak dlouho, dokud vazbu splňuje následující požadavky na zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="e0b25-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="e0b25-222">R2001: Toku aplikace aplikace zprávy `t:IssuedTokens` záhlaví spolu s `CoordinationContext` v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0b25-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="e0b25-223">R2002: Integritu a důvěrnost `t:IssuedToken` musí být zadaná.</span><span class="sxs-lookup"><span data-stu-id="e0b25-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="e0b25-224">`CoordinationContext` Obsahuje záhlaví `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="e0b25-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="e0b25-225">Při definici `xsd:AnyURI` umožňuje použít absolutní a relativní identifikátory URI, WCF podporuje pouze `wscoor:Identifiers`, které jsou absolutní URI.</span><span class="sxs-lookup"><span data-stu-id="e0b25-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="e0b25-226">B2003: Pokud `wscoor:Identifier` z `wscoor:CoordinationContext` je relativní identifikátor URI, vrátí se chyby z transakční služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="e0b25-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="e0b25-227">Příklady zprávy</span><span class="sxs-lookup"><span data-stu-id="e0b25-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="e0b25-228">Zprávy požadavků/odpovědí CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e0b25-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="e0b25-229">Tyto zprávy se řídí vzorem žádostí a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="e0b25-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="e0b25-230">CreateCoordinationContext s WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="e0b25-231">CreateCoordinationContext s WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="e0b25-232">CreateCoordinationContextResponse důvěryhodnosti Pre-1.3 a WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="e0b25-233">CreateCoordinationContextResponse s Trust 1.3 a WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
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
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="e0b25-234">Registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="e0b25-234">Registration Messages</span></span>  
 <span data-ttu-id="e0b25-235">Tyto zprávy jsou zprávy registrace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="e0b25-236">Zaregistrovat s WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="e0b25-237">Zaregistrovat s WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="e0b25-238">Registrovat odpovědi s WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="e0b25-239">Registrovat odpovědi s WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="e0b25-240">Dvě fáze potvrzení protokolu zpráv</span><span class="sxs-lookup"><span data-stu-id="e0b25-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="e0b25-241">Tato zpráva má vztah k protokol dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="e0b25-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="e0b25-242">Potvrzení s WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="e0b25-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="e0b25-243">Potvrzení s WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="e0b25-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a><span data-ttu-id="e0b25-244">Aplikace zprávy</span><span class="sxs-lookup"><span data-stu-id="e0b25-244">Application Messages</span></span>  
 <span data-ttu-id="e0b25-245">Tyto zprávy jsou zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0b25-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="e0b25-246">Zpráva žádosti</span><span class="sxs-lookup"><span data-stu-id="e0b25-246">Application message-Request</span></span>  
  
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
