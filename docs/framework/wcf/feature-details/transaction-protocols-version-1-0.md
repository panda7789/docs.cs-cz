---
title: Protokoly transakce verze 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a775ca395e01e7ecbc676ba3ec97d19ae10b4f49
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464020"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="15094-102">Protokoly transakce verze 1.0</span><span class="sxs-lookup"><span data-stu-id="15094-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="15094-103">Windows Communication Foundation (WCF) verze 1 implementuje verzi 1.0 ws-atomic k transakcím a ws-koordinace protokolů.</span><span class="sxs-lookup"><span data-stu-id="15094-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="15094-104">Další informace o verzi 1.1 naleznete [v tématu Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="15094-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="15094-105">Specifikace/dokument</span><span class="sxs-lookup"><span data-stu-id="15094-105">Specification/Document</span></span>|<span data-ttu-id="15094-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="15094-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="15094-107">WS-Koordinace</span><span class="sxs-lookup"><span data-stu-id="15094-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="15094-108">WS AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="15094-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="15094-109">Interoperabilita těchto specifikací protokolu je vyžadována na dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek).</span><span class="sxs-lookup"><span data-stu-id="15094-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="15094-110">Specifikace podrobně popisují formáty zpráv a výměnu zpráv pro obě úrovně interoperability.</span><span class="sxs-lookup"><span data-stu-id="15094-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="15094-111">Některé zabezpečení, spolehlivost a kódování pro výměnu mezi aplikacemi platí stejně jako pro pravidelnou výměnu aplikací.</span><span class="sxs-lookup"><span data-stu-id="15094-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="15094-112">Úspěšná interoperabilita mezi správci transakcí však vyžaduje dohodu o konkrétní vazbě, protože ji uživatel obvykle nenakonfiguruje.</span><span class="sxs-lookup"><span data-stu-id="15094-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="15094-113">Toto téma popisuje složení specifikace WS-Atomic Transaction (WS-AT) se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="15094-114">Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination, včetně IBM, IONA, Sun Microsystems a dalších.</span><span class="sxs-lookup"><span data-stu-id="15094-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="15094-115">Následující obrázek znázorňuje interoperabilitu mezi dvěma správci transakcí, Správcetransakcí 1 a Správce transakcí 2 a dvě aplikace, Aplikace 1 a Aplikace 2:</span><span class="sxs-lookup"><span data-stu-id="15094-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje interakci mezi správci transakcí.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="15094-117">Zvažte typický scénář WS-Coordination/WS-Atomic Transaction s jedním iniciátorem (I) a jedním účastníkem (P).</span><span class="sxs-lookup"><span data-stu-id="15094-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="15094-118">Iniciátor i účastník mají správce transakcí (ITM a PTM).</span><span class="sxs-lookup"><span data-stu-id="15094-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="15094-119">Dvoufázové potvrzení se v tomto tématu označuje jako 2PC.</span><span class="sxs-lookup"><span data-stu-id="15094-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15094-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="15094-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="15094-121">12. Odpověď na zprávu aplikace</span><span class="sxs-lookup"><span data-stu-id="15094-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="15094-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="15094-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="15094-123">13. Potvrzení (dokončení)</span><span class="sxs-lookup"><span data-stu-id="15094-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="15094-124">3. Registr (dokončení)</span><span class="sxs-lookup"><span data-stu-id="15094-124">3. Register (Completion)</span></span>|<span data-ttu-id="15094-125">14. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="15094-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="15094-126">4. RegisterResponse</span></span>|<span data-ttu-id="15094-127">15. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="15094-128">5. Zpráva aplikace</span><span class="sxs-lookup"><span data-stu-id="15094-128">5. Application Message</span></span>|<span data-ttu-id="15094-129">16. Připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="15094-130">6. CreateCoordinationContext s kontextem</span><span class="sxs-lookup"><span data-stu-id="15094-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="15094-131">17. Připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="15094-132">7. Registrovat (trvanlivé)</span><span class="sxs-lookup"><span data-stu-id="15094-132">7. Register (Durable)</span></span>|<span data-ttu-id="15094-133">18. Potvrzené (dokončení)</span><span class="sxs-lookup"><span data-stu-id="15094-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="15094-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="15094-134">8. RegisterResponse</span></span>|<span data-ttu-id="15094-135">19. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="15094-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="15094-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="15094-137">20. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="15094-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="15094-138">10. Registrovat (trvanlivé)</span><span class="sxs-lookup"><span data-stu-id="15094-138">10. Register (Durable)</span></span>|<span data-ttu-id="15094-139">21.</span><span class="sxs-lookup"><span data-stu-id="15094-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="15094-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="15094-140">11. RegisterResponse</span></span>|<span data-ttu-id="15094-141">22.</span><span class="sxs-lookup"><span data-stu-id="15094-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="15094-142">Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="15094-143">Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="15094-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="15094-144">Obrázek a tabulka znázorňují čtyři třídy zpráv z hlediska zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="15094-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="15094-145">Aktivační zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="15094-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="15094-146">Registrační zprávy (Register and RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="15094-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="15094-147">Zprávy protokolu (Příprava, Vrácení zpět, Potvrzení, Přerušeno a tak dále).</span><span class="sxs-lookup"><span data-stu-id="15094-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="15094-148">Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="15094-148">Application messages.</span></span>  
  
 <span data-ttu-id="15094-149">První tři třídy zpráv jsou považovány za zprávy Správce transakcí a jejich konfigurace vazby je popsána v části "Výměna zpráv aplikace" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="15094-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="15094-150">Čtvrtá třída zprávy je aplikace pro zprávy aplikace a je popsána v části "Příklady zpráv" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="15094-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="15094-151">Tato část popisuje vazby protokolu používané pro každou z těchto tříd WCF.</span><span class="sxs-lookup"><span data-stu-id="15094-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="15094-152">V celém dokumentu se používají následující obory názvů XML a přidružené předpony.</span><span class="sxs-lookup"><span data-stu-id="15094-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="15094-153">Předpona</span><span class="sxs-lookup"><span data-stu-id="15094-153">Prefix</span></span>|<span data-ttu-id="15094-154">Identifikátor URI oboru názvů</span><span class="sxs-lookup"><span data-stu-id="15094-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="15094-155">S11</span><span class="sxs-lookup"><span data-stu-id="15094-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="15094-156">wsa</span><span class="sxs-lookup"><span data-stu-id="15094-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="15094-157">wscoor řekl:</span><span class="sxs-lookup"><span data-stu-id="15094-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="15094-158">wsat</span><span class="sxs-lookup"><span data-stu-id="15094-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="15094-159">t</span><span class="sxs-lookup"><span data-stu-id="15094-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="15094-160">o</span><span class="sxs-lookup"><span data-stu-id="15094-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="15094-161">Xsd</span><span class="sxs-lookup"><span data-stu-id="15094-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="15094-162">Vazby správce transakcí</span><span class="sxs-lookup"><span data-stu-id="15094-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="15094-163">R1001: Správci transakcí musí používat SOAP 1.1 a WS-Addressing 2004/08 pro ws-atomické transakce a WS koordinace zprávy výměny.</span><span class="sxs-lookup"><span data-stu-id="15094-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="15094-164">Zprávy aplikace nejsou omezeny na tyto vazby a jsou popsány později.</span><span class="sxs-lookup"><span data-stu-id="15094-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="15094-165">Vazba HTTPS správce transakcí</span><span class="sxs-lookup"><span data-stu-id="15094-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="15094-166">Vazba HTTPS správce transakcí závisí výhradně na zabezpečení přenosu k dosažení zabezpečení a vytvoření vztahu důvěryhodnosti mezi jednotlivými dvojicemi odesílatele a příjemce ve stromu transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="15094-167">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="15094-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="15094-168">Certifikáty X.509 se používají k vytvoření identity správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="15094-169">Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako podrobnost implementace:</span><span class="sxs-lookup"><span data-stu-id="15094-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="15094-170">R1111: Certifikáty X.509 prezentované po drátě musí mít název subjektu, který odpovídá plně kvalifikovanému názvu domény (Plně kvalifikovaný název domény) původního počítače.</span><span class="sxs-lookup"><span data-stu-id="15094-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="15094-171">B1112: Dns musí být funkční mezi každou dvojici odesílatele a příjemce v systému pro X.509 kontroly názvů předmětů úspěšné.</span><span class="sxs-lookup"><span data-stu-id="15094-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="15094-172">Konfigurace aktivační a registrační vazby</span><span class="sxs-lookup"><span data-stu-id="15094-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="15094-173">WCF vyžaduje oboustrannou vazbu požadavku a odpovědi s korelací přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15094-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="15094-174">(Další informace o korelaci a popisy vzorců výměny zpráv požadavku a odpovědi naleznete v tématu WS-Atomic Transaction, oddíl 8.)</span><span class="sxs-lookup"><span data-stu-id="15094-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="15094-175">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="15094-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="15094-176">WCF podporuje jednosměrné (datagram) zprávy přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15094-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="15094-177">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="15094-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="15094-178">B2131: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.</span><span class="sxs-lookup"><span data-stu-id="15094-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="15094-179">Vazba smíšeného zabezpečení správce transakcí</span><span class="sxs-lookup"><span data-stu-id="15094-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="15094-180">Toto je alternativní (smíšený režim) vazby, která používá zabezpečení přenosu v kombinaci s WS koordinace vydaný token model pro účely vytváření identit.</span><span class="sxs-lookup"><span data-stu-id="15094-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="15094-181">Aktivace a registrace jsou pouze prvky, které se liší mezi dvě vazby.</span><span class="sxs-lookup"><span data-stu-id="15094-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="15094-182">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="15094-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="15094-183">Certifikáty X.509 se používají k vytvoření identity správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="15094-184">Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako detail implementace.</span><span class="sxs-lookup"><span data-stu-id="15094-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="15094-185">Konfigurace vazby aktivační zprávy</span><span class="sxs-lookup"><span data-stu-id="15094-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="15094-186">Aktivační zprávy se obvykle neúčastní interoperability, protože se obvykle vyskytují mezi aplikací a jejím místním správcem transakcí.</span><span class="sxs-lookup"><span data-stu-id="15094-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="15094-187">B1221: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivační zprávy.</span><span class="sxs-lookup"><span data-stu-id="15094-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="15094-188">Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="15094-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="15094-189">WS-Atomic Transaction specifikace, oddíl 8, popisuje další podrobnosti o korelaci a vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="15094-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="15094-190">R1222: Po `CreateCoordinationContext`obdržení a musí `SecurityContextToken` koordinátor vydat `STx`a s přidruženým tajným tajemstvím .</span><span class="sxs-lookup"><span data-stu-id="15094-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="15094-191">Tento token je `t:IssuedTokens` vrácena uvnitř záhlaví podle ws-trust specifikace.</span><span class="sxs-lookup"><span data-stu-id="15094-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="15094-192">R1223: Pokud dojde k aktivaci v `t:IssuedTokens` rámci `SecurityContextToken` existující kontextu koordinace, `CreateCoordinationContext` záhlaví s přidružené k existující context musí tok na zprávu.</span><span class="sxs-lookup"><span data-stu-id="15094-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="15094-193">Pro `t:IssuedTokens` připojení k odchozí `wscoor:CreateCoordinationContextResponse` zprávě by měla být generována nová hlavička.</span><span class="sxs-lookup"><span data-stu-id="15094-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="15094-194">Konfigurace vazby registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="15094-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="15094-195">B1231: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv).](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="15094-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="15094-196">Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="15094-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="15094-197">WS-AtomicTransaction, Oddíl 8, popisuje další podrobnosti o korelaci a popisy vzorů výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="15094-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="15094-198">R1232: Odchozí `wscoor:Register` zprávy musí `IssuedTokenOverTransport` používat režim ověřování popsaný v [protokolech zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="15094-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="15094-199">Prvek `wsse:Timestamp` musí být podepsán `SecurityContextToken STx` pomocí vydané.</span><span class="sxs-lookup"><span data-stu-id="15094-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="15094-200">Tento podpis je dokladem o vlastnictví tokenu přidruženého k určité transakci a používá se k ověření účastníka zařazení do transakce.</span><span class="sxs-lookup"><span data-stu-id="15094-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="15094-201">Zpráva Response RegistrationResponse je odeslána zpět přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15094-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="15094-202">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="15094-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="15094-203">WCF podporuje jednosměrné (datagram) zprávy přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="15094-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="15094-204">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="15094-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="15094-205">B2131: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.</span><span class="sxs-lookup"><span data-stu-id="15094-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="15094-206">Výměna zpráv aplikace</span><span class="sxs-lookup"><span data-stu-id="15094-206">Application Message Exchange</span></span>  
 <span data-ttu-id="15094-207">Aplikace mohou používat určitou vazbu pro zprávy aplikace k aplikaci, pokud vazba splňuje následující požadavky na zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="15094-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="15094-208">R2001: Zprávy aplikace k aplikaci `t:IssuedTokens` musí tok záhlaví spolu s `CoordinationContext` v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="15094-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="15094-209">R2002: Musí být zajištěna `t:IssuedToken` integrita a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="15094-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="15094-210">Záhlaví `CoordinationContext` obsahuje `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="15094-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="15094-211">Zatímco definice `xsd:AnyURI` umožňuje použití absolutních i relativních identifikátorů `wscoor:Identifiers`URI, WCF podporuje pouze , což jsou absolutní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="15094-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="15094-212">Pokud `wscoor:Identifier` `wscoor:CoordinationContext` je relativní identifikátor URI, budou vráceny chyby z transakčních služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="15094-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="15094-213">Příklady zpráv</span><span class="sxs-lookup"><span data-stu-id="15094-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="15094-214">Zprávy požadavků/odpovědí CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="15094-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="15094-215">Následující zprávy postupujte podle vzoru požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="15094-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="15094-216">VytvořitcoordinationContext</span><span class="sxs-lookup"><span data-stu-id="15094-216">CreateCoordinationContext</span></span>  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="15094-217">Vytvořitodpověď kontextukoordinace</span><span class="sxs-lookup"><span data-stu-id="15094-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="15094-218">Registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="15094-218">Registration Messages</span></span>  
 <span data-ttu-id="15094-219">Následující zprávy jsou registrační zprávy.</span><span class="sxs-lookup"><span data-stu-id="15094-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="15094-220">Zaregistrovat</span><span class="sxs-lookup"><span data-stu-id="15094-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="15094-221">Zaregistrovat odpověď</span><span class="sxs-lookup"><span data-stu-id="15094-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="15094-222">Dvě zprávy protokolu fázového potvrzení</span><span class="sxs-lookup"><span data-stu-id="15094-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="15094-223">Následující zpráva se týká protokolu dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="15094-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="15094-224">Potvrzení</span><span class="sxs-lookup"><span data-stu-id="15094-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="15094-225">Zprávy aplikace</span><span class="sxs-lookup"><span data-stu-id="15094-225">Application Messages</span></span>  
 <span data-ttu-id="15094-226">Následující zprávy jsou zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="15094-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="15094-227">Žádost o zprávu aplikace</span><span class="sxs-lookup"><span data-stu-id="15094-227">Application message-Request</span></span>  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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
