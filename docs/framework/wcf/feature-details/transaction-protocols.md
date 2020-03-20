---
title: Protokoly transakcí
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 5ae8aa5112f737d3000e221d0a199c3ee36eac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184371"
---
# <a name="transaction-protocols"></a><span data-ttu-id="d40cf-102">Protokoly transakcí</span><span class="sxs-lookup"><span data-stu-id="d40cf-102">Transaction Protocols</span></span>
<span data-ttu-id="d40cf-103">Windows Communication Foundation (WCF) implementuje ws-atomic k transakcím a ws-koordinační protokoly.</span><span class="sxs-lookup"><span data-stu-id="d40cf-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="d40cf-104">Specifikace/dokument</span><span class="sxs-lookup"><span data-stu-id="d40cf-104">Specification/Document</span></span>|<span data-ttu-id="d40cf-105">Version</span><span class="sxs-lookup"><span data-stu-id="d40cf-105">Version</span></span>|<span data-ttu-id="d40cf-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d40cf-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="d40cf-107">WS-Koordinace</span><span class="sxs-lookup"><span data-stu-id="d40cf-107">WS-Coordination</span></span>|<span data-ttu-id="d40cf-108">1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-108">1.0</span></span><br /><br /> <span data-ttu-id="d40cf-109">1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="d40cf-110">WS AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="d40cf-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="d40cf-111">1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-111">1.0</span></span><br /><br /> <span data-ttu-id="d40cf-112">1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="d40cf-113">Interoperabilita těchto specifikací protokolu je vyžadována na dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek).</span><span class="sxs-lookup"><span data-stu-id="d40cf-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="d40cf-114">Specifikace podrobně popisují formáty zpráv a výměnu zpráv pro obě úrovně interoperability.</span><span class="sxs-lookup"><span data-stu-id="d40cf-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="d40cf-115">Některé zabezpečení, spolehlivost a kódování pro výměnu mezi aplikacemi platí stejně jako pro pravidelnou výměnu aplikací.</span><span class="sxs-lookup"><span data-stu-id="d40cf-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="d40cf-116">Úspěšná interoperabilita mezi správci transakcí však vyžaduje dohodu o konkrétní vazbě, protože ji uživatel obvykle nenakonfiguruje.</span><span class="sxs-lookup"><span data-stu-id="d40cf-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="d40cf-117">Toto téma popisuje složení specifikace WS-Atomic Transaction (WS-AT) se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="d40cf-118">Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination, včetně IBM, IONA, Sun Microsystems a dalších.</span><span class="sxs-lookup"><span data-stu-id="d40cf-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="d40cf-119">Následující obrázek znázorňuje interoperabilitu mezi dvěma správci transakcí, Správcetransakcí 1 a Správce transakcí 2 a dvě aplikace, Aplikace 1 a Aplikace 2:</span><span class="sxs-lookup"><span data-stu-id="d40cf-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje interakci mezi správci transakcí.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="d40cf-121">Zvažte typický scénář WS-Coordination/WS-Atomic Transaction s jedním iniciátorem (I) a jedním účastníkem (P).</span><span class="sxs-lookup"><span data-stu-id="d40cf-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="d40cf-122">Iniciátor i účastník mají správce transakcí (ITM a PTM).</span><span class="sxs-lookup"><span data-stu-id="d40cf-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="d40cf-123">Dvoufázové potvrzení se v tomto tématu označuje jako 2PC.</span><span class="sxs-lookup"><span data-stu-id="d40cf-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d40cf-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="d40cf-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="d40cf-125">12. Odpověď na zprávu aplikace</span><span class="sxs-lookup"><span data-stu-id="d40cf-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="d40cf-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="d40cf-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="d40cf-127">13. Potvrzení (dokončení)</span><span class="sxs-lookup"><span data-stu-id="d40cf-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="d40cf-128">3. Registr (dokončení)</span><span class="sxs-lookup"><span data-stu-id="d40cf-128">3. Register (Completion)</span></span>|<span data-ttu-id="d40cf-129">14. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="d40cf-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="d40cf-130">4. RegisterResponse</span></span>|<span data-ttu-id="d40cf-131">15. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="d40cf-132">5. Zpráva aplikace</span><span class="sxs-lookup"><span data-stu-id="d40cf-132">5. Application Message</span></span>|<span data-ttu-id="d40cf-133">16. Připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="d40cf-134">6. CreateCoordinationContext s kontextem</span><span class="sxs-lookup"><span data-stu-id="d40cf-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="d40cf-135">17. Připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="d40cf-136">7. Registrovat (trvanlivé)</span><span class="sxs-lookup"><span data-stu-id="d40cf-136">7. Register (Durable)</span></span>|<span data-ttu-id="d40cf-137">18. Potvrzené (dokončení)</span><span class="sxs-lookup"><span data-stu-id="d40cf-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="d40cf-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="d40cf-138">8. RegisterResponse</span></span>|<span data-ttu-id="d40cf-139">19. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="d40cf-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="d40cf-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="d40cf-141">20. Potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="d40cf-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="d40cf-142">10. Registrovat (trvanlivé)</span><span class="sxs-lookup"><span data-stu-id="d40cf-142">10. Register (Durable)</span></span>|<span data-ttu-id="d40cf-143">21.</span><span class="sxs-lookup"><span data-stu-id="d40cf-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="d40cf-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="d40cf-144">11. RegisterResponse</span></span>|<span data-ttu-id="d40cf-145">22.</span><span class="sxs-lookup"><span data-stu-id="d40cf-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="d40cf-146">Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="d40cf-147">Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="d40cf-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="d40cf-148">Obrázek a tabulka znázorňují čtyři třídy zpráv z hlediska zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="d40cf-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="d40cf-149">Aktivační zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="d40cf-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="d40cf-150">Registrační zprávy (Register and RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="d40cf-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="d40cf-151">Zprávy protokolu (Příprava, Vrácení zpět, Potvrzení, Přerušeno a tak dále).</span><span class="sxs-lookup"><span data-stu-id="d40cf-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="d40cf-152">Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-152">Application messages.</span></span>  
  
 <span data-ttu-id="d40cf-153">První tři třídy zpráv jsou považovány za zprávy Správce transakcí a jejich konfigurace vazby je popsána v části "Výměna zpráv aplikace" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d40cf-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="d40cf-154">Čtvrtá třída zprávy je aplikace pro zprávy aplikace a je popsána v části "Příklady zpráv" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d40cf-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="d40cf-155">Tato část popisuje vazby protokolu používané pro každou z těchto tříd WCF.</span><span class="sxs-lookup"><span data-stu-id="d40cf-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="d40cf-156">V celém dokumentu se používají následující obory názvů XML a přidružené předpony.</span><span class="sxs-lookup"><span data-stu-id="d40cf-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="d40cf-157">Předpona</span><span class="sxs-lookup"><span data-stu-id="d40cf-157">Prefix</span></span>|<span data-ttu-id="d40cf-158">Version</span><span class="sxs-lookup"><span data-stu-id="d40cf-158">Version</span></span>|<span data-ttu-id="d40cf-159">Identifikátor URI oboru názvů</span><span class="sxs-lookup"><span data-stu-id="d40cf-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="d40cf-160">S11</span><span class="sxs-lookup"><span data-stu-id="d40cf-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="d40cf-161">wsa</span><span class="sxs-lookup"><span data-stu-id="d40cf-161">wsa</span></span>|<span data-ttu-id="d40cf-162">Před 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="d40cf-163">1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="d40cf-164">wscoor řekl:</span><span class="sxs-lookup"><span data-stu-id="d40cf-164">wscoor</span></span>|<span data-ttu-id="d40cf-165">1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-165">1.0</span></span><br /><br /> <span data-ttu-id="d40cf-166">1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="d40cf-167">wsat</span><span class="sxs-lookup"><span data-stu-id="d40cf-167">wsat</span></span>|<span data-ttu-id="d40cf-168">1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-168">1.0</span></span><br /><br /> <span data-ttu-id="d40cf-169">1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="d40cf-170">t</span><span class="sxs-lookup"><span data-stu-id="d40cf-170">t</span></span>|<span data-ttu-id="d40cf-171">Před 1,3</span><span class="sxs-lookup"><span data-stu-id="d40cf-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="d40cf-172">1.3</span><span class="sxs-lookup"><span data-stu-id="d40cf-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="d40cf-173">o</span><span class="sxs-lookup"><span data-stu-id="d40cf-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="d40cf-174">Xsd</span><span class="sxs-lookup"><span data-stu-id="d40cf-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="d40cf-175">Vazby správce transakcí</span><span class="sxs-lookup"><span data-stu-id="d40cf-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="d40cf-176">R1001: Správci transakcí účastnící se transakce WS-AT 1.0 musí používat SOAP 1.1 a WS-Addressing 2004/08 pro výměny zpráv WS-Atomic Transaction a WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="d40cf-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="d40cf-177">R1002: Správci transakcí účastnící se transakce WS-AT 1.1 musí používat SOAP 1.1 a WS-Addressing 2005/08 pro výměny zpráv WS-Atomic Transaction a WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="d40cf-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="d40cf-178">Zprávy aplikace nejsou omezeny na tyto vazby a jsou popsány později.</span><span class="sxs-lookup"><span data-stu-id="d40cf-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="d40cf-179">Vazba HTTPS správce transakcí</span><span class="sxs-lookup"><span data-stu-id="d40cf-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="d40cf-180">Vazba HTTPS správce transakcí závisí výhradně na zabezpečení přenosu k dosažení zabezpečení a vytvoření vztahu důvěryhodnosti mezi jednotlivými dvojicemi odesílatele a příjemce ve stromu transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="d40cf-181">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="d40cf-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="d40cf-182">Certifikáty X.509 se používají k vytvoření identity správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="d40cf-183">Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako podrobnost implementace:</span><span class="sxs-lookup"><span data-stu-id="d40cf-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="d40cf-184">R1111: Certifikáty X.509 prezentované po drátě musí mít název subjektu, který odpovídá plně kvalifikovanému názvu domény (Plně kvalifikovaný název domény) původního počítače.</span><span class="sxs-lookup"><span data-stu-id="d40cf-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="d40cf-185">B1112: Dns musí být funkční mezi každou dvojici odesílatele a příjemce v systému pro X.509 kontroly názvů předmětů úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d40cf-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="d40cf-186">Konfigurace aktivační a registrační vazby</span><span class="sxs-lookup"><span data-stu-id="d40cf-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="d40cf-187">WCF vyžaduje oboustrannou vazbu požadavku a odpovědi s korelací přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d40cf-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="d40cf-188">(Další informace o korelaci a popisy vzorců výměny zpráv požadavku a odpovědi naleznete v tématu WS-Atomic Transaction, oddíl 8.)</span><span class="sxs-lookup"><span data-stu-id="d40cf-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="d40cf-189">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="d40cf-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="d40cf-190">WCF podporuje jednosměrné (datagram) zprávy přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d40cf-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="d40cf-191">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="d40cf-192">B1131: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.</span><span class="sxs-lookup"><span data-stu-id="d40cf-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="d40cf-193">Vazba smíšeného zabezpečení správce transakcí</span><span class="sxs-lookup"><span data-stu-id="d40cf-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="d40cf-194">Toto je alternativní (smíšený režim) vazby, která používá zabezpečení přenosu v kombinaci s WS koordinace vydaný token model pro účely vytváření identit.</span><span class="sxs-lookup"><span data-stu-id="d40cf-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="d40cf-195">Aktivace a registrace jsou pouze prvky, které se liší mezi dvě vazby.</span><span class="sxs-lookup"><span data-stu-id="d40cf-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="d40cf-196">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="d40cf-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="d40cf-197">Certifikáty X.509 se používají k vytvoření identity správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="d40cf-198">Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako detail implementace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="d40cf-199">Konfigurace vazby aktivační zprávy</span><span class="sxs-lookup"><span data-stu-id="d40cf-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="d40cf-200">Aktivační zprávy se obvykle neúčastní interoperability, protože se obvykle vyskytují mezi aplikací a jejím místním správcem transakcí.</span><span class="sxs-lookup"><span data-stu-id="d40cf-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="d40cf-201">B1221: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivační zprávy.</span><span class="sxs-lookup"><span data-stu-id="d40cf-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="d40cf-202">Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08 pro WS-AT 1.0 a WS-Addressing 2005/08 pro WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="d40cf-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="d40cf-203">WS-Atomic Transaction specifikace, oddíl 8, popisuje další podrobnosti o korelaci a vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="d40cf-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="d40cf-204">R1222: Po `CreateCoordinationContext`obdržení a musí `SecurityContextToken` koordinátor vydat `STx`a s přidruženým tajným tajemstvím .</span><span class="sxs-lookup"><span data-stu-id="d40cf-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="d40cf-205">Tento token je `t:IssuedTokens` vrácena uvnitř záhlaví podle ws-trust specifikace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="d40cf-206">R1223: Pokud dojde k aktivaci v `t:IssuedTokens` rámci `SecurityContextToken` existující kontextu koordinace, `CreateCoordinationContext` záhlaví s přidružené k existující context musí tok na zprávu.</span><span class="sxs-lookup"><span data-stu-id="d40cf-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="d40cf-207">Pro `t:IssuedTokens` připojení k odchozí `wscoor:CreateCoordinationContextResponse` zprávě by měla být generována nová hlavička.</span><span class="sxs-lookup"><span data-stu-id="d40cf-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="d40cf-208">Konfigurace vazby registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="d40cf-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="d40cf-209">B1231: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv).](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="d40cf-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="d40cf-210">Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08 pro WS-AT 1.0 a WS-Addressing 2005/08 pro WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="d40cf-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="d40cf-211">WS-AtomicTransaction, Oddíl 8, popisuje další podrobnosti o korelaci a popisy vzorů výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="d40cf-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="d40cf-212">R1232: Odchozí `wscoor:Register` zprávy musí `IssuedTokenOverTransport` používat režim ověřování popsaný v [protokolech zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="d40cf-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="d40cf-213">Prvek `wsse:Timestamp` musí být podepsán `SecurityContextToken STx` pomocí vydané.</span><span class="sxs-lookup"><span data-stu-id="d40cf-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="d40cf-214">Tento podpis je dokladem o vlastnictví tokenu přidruženého k určité transakci a používá se k ověření účastníka zařazení do transakce.</span><span class="sxs-lookup"><span data-stu-id="d40cf-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="d40cf-215">Zpráva Response RegistrationResponse je odeslána zpět přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d40cf-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="d40cf-216">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="d40cf-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="d40cf-217">WCF podporuje jednosměrné (datagram) zprávy přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d40cf-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="d40cf-218">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="d40cf-219">B1241: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.</span><span class="sxs-lookup"><span data-stu-id="d40cf-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="d40cf-220">Výměna zpráv aplikace</span><span class="sxs-lookup"><span data-stu-id="d40cf-220">Application Message Exchange</span></span>  
 <span data-ttu-id="d40cf-221">Aplikace mohou používat určitou vazbu pro zprávy aplikace k aplikaci, pokud vazba splňuje následující požadavky na zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="d40cf-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="d40cf-222">R2001: Zprávy aplikace k aplikaci `t:IssuedTokens` musí tok záhlaví spolu s `CoordinationContext` v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="d40cf-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="d40cf-223">R2002: Musí být zajištěna `t:IssuedToken` integrita a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="d40cf-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="d40cf-224">Záhlaví `CoordinationContext` obsahuje `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="d40cf-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="d40cf-225">Zatímco definice `xsd:AnyURI` umožňuje použití absolutních i relativních identifikátorů `wscoor:Identifiers`URI, WCF podporuje pouze , což jsou absolutní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="d40cf-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="d40cf-226">B2003: Pokud `wscoor:Identifier` `wscoor:CoordinationContext` je relativní IDENTIFIKÁTOR URI, chyby budou vráceny z transakčníwcf služby.</span><span class="sxs-lookup"><span data-stu-id="d40cf-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="d40cf-227">Příklady zpráv</span><span class="sxs-lookup"><span data-stu-id="d40cf-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="d40cf-228">Zprávy požadavků/odpovědí CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="d40cf-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="d40cf-229">Následující zprávy postupujte podle vzoru požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d40cf-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="d40cf-230">CreateCoordinationContext s WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="d40cf-231">CreateCoordinationContext s WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="d40cf-232">CreateCoordinationContextResponse s důvěrou Pre-1.3 a WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="d40cf-233">CreateCoordinationContextResponse s trustem 1.3 a WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="d40cf-234">Registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="d40cf-234">Registration Messages</span></span>  
 <span data-ttu-id="d40cf-235">Následující zprávy jsou registrační zprávy.</span><span class="sxs-lookup"><span data-stu-id="d40cf-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="d40cf-236">Zaregistrujte se u WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="d40cf-237">Zaregistrujte se u WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="d40cf-238">Zaregistrovat odpověď s WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="d40cf-239">Zaregistrovat odpověď s WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="d40cf-240">Dvě zprávy protokolu fázového potvrzení</span><span class="sxs-lookup"><span data-stu-id="d40cf-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="d40cf-241">Následující zpráva se týká protokolu dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="d40cf-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="d40cf-242">Potvrzení pomocí wsat 1.0</span><span class="sxs-lookup"><span data-stu-id="d40cf-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="d40cf-243">Potvrzení pomocí wsat 1.1</span><span class="sxs-lookup"><span data-stu-id="d40cf-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="d40cf-244">Zprávy aplikace</span><span class="sxs-lookup"><span data-stu-id="d40cf-244">Application Messages</span></span>  
 <span data-ttu-id="d40cf-245">Následující zprávy jsou zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="d40cf-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="d40cf-246">Žádost o zprávu aplikace</span><span class="sxs-lookup"><span data-stu-id="d40cf-246">Application message-Request</span></span>  
  
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
