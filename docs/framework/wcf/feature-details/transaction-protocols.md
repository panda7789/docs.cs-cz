---
title: Protokoly transakcí
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 17131c4cd10d9441ec65f9da4137147a703eb87c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600981"
---
# <a name="transaction-protocols"></a><span data-ttu-id="03bb2-102">Protokoly transakcí</span><span class="sxs-lookup"><span data-stu-id="03bb2-102">Transaction Protocols</span></span>
<span data-ttu-id="03bb2-103">Windows Communication Foundation (WCF) implementuje WS-Atomic transakce a protokoly WS-koordinační.</span><span class="sxs-lookup"><span data-stu-id="03bb2-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="03bb2-104">Specifikace/dokument</span><span class="sxs-lookup"><span data-stu-id="03bb2-104">Specification/Document</span></span>|<span data-ttu-id="03bb2-105">Verze</span><span class="sxs-lookup"><span data-stu-id="03bb2-105">Version</span></span>|<span data-ttu-id="03bb2-106">Odkaz</span><span class="sxs-lookup"><span data-stu-id="03bb2-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="03bb2-107">WS-koordinace</span><span class="sxs-lookup"><span data-stu-id="03bb2-107">WS-Coordination</span></span>|<span data-ttu-id="03bb2-108">1.0</span><span class="sxs-lookup"><span data-stu-id="03bb2-108">1.0</span></span><br /><br /> <span data-ttu-id="03bb2-109">1.1</span><span class="sxs-lookup"><span data-stu-id="03bb2-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="03bb2-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="03bb2-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="03bb2-111">1.0</span><span class="sxs-lookup"><span data-stu-id="03bb2-111">1.0</span></span><br /><br /> <span data-ttu-id="03bb2-112">1.1</span><span class="sxs-lookup"><span data-stu-id="03bb2-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="03bb2-113">Interoperabilita těchto specifikací protokolu je povinná na dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek).</span><span class="sxs-lookup"><span data-stu-id="03bb2-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="03bb2-114">Specifikace popisují Skvělé údaje o formátech zpráv a výměně zpráv pro obě úrovně interoperability.</span><span class="sxs-lookup"><span data-stu-id="03bb2-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="03bb2-115">Určité zabezpečení, spolehlivost a kódování pro Exchange mezi aplikacemi platí jako při běžném výměně aplikací.</span><span class="sxs-lookup"><span data-stu-id="03bb2-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="03bb2-116">Úspěšná interoperabilita mezi správci transakcí ale vyžaduje souhlas s konkrétní vazbou, protože obvykle není nakonfigurovaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="03bb2-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="03bb2-117">Toto téma popisuje složení specifikace WS-Atomic Transaction (WS-AT) se zabezpečením a popisuje zabezpečenou vazbu použitou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="03bb2-118">Přístup popsaný v tomto dokumentu byl úspěšně testován s ostatními implementacemi WS-AT a WS-koordinace, včetně IBM, IONA, Sun Microsystems a dalších.</span><span class="sxs-lookup"><span data-stu-id="03bb2-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="03bb2-119">Následující obrázek znázorňuje interoperabilitu mezi dvěma správci transakcí, správce transakcí 1 a správce transakcí 2 a dvěma aplikacemi, aplikací 1 a aplikací 2:</span><span class="sxs-lookup"><span data-stu-id="03bb2-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Snímek obrazovky zobrazující interakci mezi správci transakcí.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="03bb2-121">Zvažte Typický scénář transakce WS-koordinační/WS-Atomic s jedním iniciátorem (I) a jedním účastníkem (P).</span><span class="sxs-lookup"><span data-stu-id="03bb2-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="03bb2-122">Iniciátor i účastník mají správce transakcí (v uvedeném pořadí) (ITM a PTM).</span><span class="sxs-lookup"><span data-stu-id="03bb2-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="03bb2-123">Dvoufázové potvrzení se v tomto tématu označuje jako 2PC.</span><span class="sxs-lookup"><span data-stu-id="03bb2-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03bb2-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="03bb2-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="03bb2-125">12. odpověď na zprávu aplikace</span><span class="sxs-lookup"><span data-stu-id="03bb2-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="03bb2-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="03bb2-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="03bb2-127">13. potvrzení změn (dokončení)</span><span class="sxs-lookup"><span data-stu-id="03bb2-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="03bb2-128">3. Register (dokončení)</span><span class="sxs-lookup"><span data-stu-id="03bb2-128">3. Register (Completion)</span></span>|<span data-ttu-id="03bb2-129">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="03bb2-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="03bb2-130">4. RegisterResponse</span></span>|<span data-ttu-id="03bb2-131">15. Příprava (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="03bb2-132">5. zpráva aplikace</span><span class="sxs-lookup"><span data-stu-id="03bb2-132">5. Application Message</span></span>|<span data-ttu-id="03bb2-133">16. připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="03bb2-134">6. CreateCoordinationContext s kontextem</span><span class="sxs-lookup"><span data-stu-id="03bb2-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="03bb2-135">17. připraveno (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="03bb2-136">7. Register (trvanlivé)</span><span class="sxs-lookup"><span data-stu-id="03bb2-136">7. Register (Durable)</span></span>|<span data-ttu-id="03bb2-137">18. potvrzeno (dokončení)</span><span class="sxs-lookup"><span data-stu-id="03bb2-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="03bb2-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="03bb2-138">8. RegisterResponse</span></span>|<span data-ttu-id="03bb2-139">19. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="03bb2-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="03bb2-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="03bb2-141">20. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="03bb2-142">10. Register (trvalý)</span><span class="sxs-lookup"><span data-stu-id="03bb2-142">10. Register (Durable)</span></span>|<span data-ttu-id="03bb2-143">21. potvrzeno (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="03bb2-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="03bb2-144">11. RegisterResponse</span></span>|<span data-ttu-id="03bb2-145">22. potvrzeno (2PC)</span><span class="sxs-lookup"><span data-stu-id="03bb2-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="03bb2-146">Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a popisuje zabezpečenou vazbu použitou pro komunikaci mezi správci transakcí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="03bb2-147">Přístup popsaný v tomto dokumentu byl úspěšně testován s jinými implementacemi WS-AT a WS-koordinace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="03bb2-148">Obrázek a tabulka znázorňují čtyři třídy zpráv z hlediska zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="03bb2-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="03bb2-149">Aktivační zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="03bb2-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="03bb2-150">Registrační zprávy (registr a RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="03bb2-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="03bb2-151">Zprávy protokolu (příprava, vrácení zpět, potvrzení, přerušení a tak dále).</span><span class="sxs-lookup"><span data-stu-id="03bb2-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="03bb2-152">Zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-152">Application messages.</span></span>  
  
 <span data-ttu-id="03bb2-153">První tři třídy zpráv jsou považovány za zprávy správce transakcí a jejich konfigurace vazeb je popsána v části výměna zpráv aplikace dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="03bb2-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="03bb2-154">Čtvrtá třída zprávy je aplikace na zprávy aplikace a je popsána v části Příklady zpráv dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="03bb2-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="03bb2-155">Tato část popisuje vazby protokolu používané pro každou z těchto tříd pomocí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="03bb2-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="03bb2-156">V celém tomto dokumentu se používají následující obory názvů XML a přidružené předpony.</span><span class="sxs-lookup"><span data-stu-id="03bb2-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="03bb2-157">Předpona</span><span class="sxs-lookup"><span data-stu-id="03bb2-157">Prefix</span></span>|<span data-ttu-id="03bb2-158">Verze</span><span class="sxs-lookup"><span data-stu-id="03bb2-158">Version</span></span>|<span data-ttu-id="03bb2-159">Identifikátor URI oboru názvů</span><span class="sxs-lookup"><span data-stu-id="03bb2-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="03bb2-160">s11</span><span class="sxs-lookup"><span data-stu-id="03bb2-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="03bb2-161">WSA</span><span class="sxs-lookup"><span data-stu-id="03bb2-161">wsa</span></span>|<span data-ttu-id="03bb2-162">Před 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="03bb2-163">1.0</span><span class="sxs-lookup"><span data-stu-id="03bb2-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="03bb2-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="03bb2-164">wscoor</span></span>|<span data-ttu-id="03bb2-165">1.0</span><span class="sxs-lookup"><span data-stu-id="03bb2-165">1.0</span></span><br /><br /> <span data-ttu-id="03bb2-166">1.1</span><span class="sxs-lookup"><span data-stu-id="03bb2-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="03bb2-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="03bb2-167">wsat</span></span>|<span data-ttu-id="03bb2-168">1.0</span><span class="sxs-lookup"><span data-stu-id="03bb2-168">1.0</span></span><br /><br /> <span data-ttu-id="03bb2-169">1.1</span><span class="sxs-lookup"><span data-stu-id="03bb2-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="03bb2-170">t</span><span class="sxs-lookup"><span data-stu-id="03bb2-170">t</span></span>|<span data-ttu-id="03bb2-171">Před 1,3</span><span class="sxs-lookup"><span data-stu-id="03bb2-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="03bb2-172">1.3</span><span class="sxs-lookup"><span data-stu-id="03bb2-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="03bb2-173">o</span><span class="sxs-lookup"><span data-stu-id="03bb2-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="03bb2-174">XSD</span><span class="sxs-lookup"><span data-stu-id="03bb2-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="03bb2-175">Vazby správce transakcí</span><span class="sxs-lookup"><span data-stu-id="03bb2-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="03bb2-176">R1001: Správci transakcí účastnící se transakce WS-AT 1,0 musí používat SOAP 1,1 a WS-addresses 2004/08 pro WS-Atomic transakce a výměny zpráv WS-koordinační.</span><span class="sxs-lookup"><span data-stu-id="03bb2-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="03bb2-177">R1002: Správci transakcí účastnící se transakce WS-AT 1,1 musí používat SOAP 1,1 a WS-addresses 2005/08 pro WS-Atomic transakce a výměny zpráv WS-koordinační.</span><span class="sxs-lookup"><span data-stu-id="03bb2-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="03bb2-178">Zprávy aplikací nejsou omezeny na tyto vazby a jsou popsány později.</span><span class="sxs-lookup"><span data-stu-id="03bb2-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="03bb2-179">Vazba HTTPS správce transakcí</span><span class="sxs-lookup"><span data-stu-id="03bb2-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="03bb2-180">Vazba HTTPS správce transakcí spoléhá výhradně na zabezpečení přenosu, aby dosáhla zabezpečení a navázala důvěryhodnost mezi jednotlivými páry odesílatele ve stromu transakcí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="03bb2-181">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="03bb2-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="03bb2-182">K navázání identity správce transakcí se používají certifikáty X. 509.</span><span class="sxs-lookup"><span data-stu-id="03bb2-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="03bb2-183">Ověření klienta a serveru je povinné a autorizace klienta/serveru je popsána jako podrobnosti implementace:</span><span class="sxs-lookup"><span data-stu-id="03bb2-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="03bb2-184">R1111: certifikáty X. 509 prezentované přes síťový kabel musí mít název subjektu, který odpovídá plně kvalifikovanému názvu domény (FQDN) původního počítače.</span><span class="sxs-lookup"><span data-stu-id="03bb2-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="03bb2-185">B1112: Služba DNS musí být funkční mezi jednotlivými páry odesílatel-přijímač v systému, aby kontrola názvů subjektu X. 509 byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="03bb2-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="03bb2-186">Konfigurace aktivace a registrace vazby</span><span class="sxs-lookup"><span data-stu-id="03bb2-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="03bb2-187">WCF vyžaduje vazbu mezi požadavkem a odpovědí s korelace přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03bb2-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="03bb2-188">(Další informace o korelaci a popisech vzorů pro výměnu zpráv požadavků a odpovědí najdete v tématu WS-Atomic Transaction, Section 8.)</span><span class="sxs-lookup"><span data-stu-id="03bb2-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="03bb2-189">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="03bb2-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="03bb2-190">WCF podporuje jednosměrné (Datagram) zprávy přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03bb2-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="03bb2-191">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="03bb2-192">B1131: implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v tématu Specifikace WS-Addressing, aby bylo možné dosáhnout korelace zpráv 2PC WCF.</span><span class="sxs-lookup"><span data-stu-id="03bb2-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="03bb2-193">Kombinovaná vazba zabezpečení správce transakcí</span><span class="sxs-lookup"><span data-stu-id="03bb2-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="03bb2-194">Toto je alternativní (smíšený režim) vazby, která používá zabezpečení přenosu v kombinaci s modelem tokenu WS-koordinace vydaným pro účely vytvoření identity.</span><span class="sxs-lookup"><span data-stu-id="03bb2-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="03bb2-195">Aktivace a registrace jsou jediné prvky, které se mezi těmito dvěma vazbami liší.</span><span class="sxs-lookup"><span data-stu-id="03bb2-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="03bb2-196">Konfigurace přenosu HTTPS</span><span class="sxs-lookup"><span data-stu-id="03bb2-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="03bb2-197">K navázání identity správce transakcí se používají certifikáty X. 509.</span><span class="sxs-lookup"><span data-stu-id="03bb2-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="03bb2-198">Ověřování klienta a serveru je povinné a ověřování klienta/serveru je ponecháno jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="03bb2-199">Konfigurace vazby aktivační zprávy</span><span class="sxs-lookup"><span data-stu-id="03bb2-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="03bb2-200">Aktivační zprávy obvykle nejsou zapojeny do interoperability, protože se obvykle vyskytují mezi aplikací a jejím místním správcem transakcí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="03bb2-201">B1221: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv](messaging-protocols.md)) pro aktivační zprávy.</span><span class="sxs-lookup"><span data-stu-id="03bb2-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="03bb2-202">Zprávy žádosti a odpovědi se korelují pomocí WS-Addressing 2004/08 pro WS-AT 1,0 a WS-Addressing 2005/08 pro WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="03bb2-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="03bb2-203">Specifikace WS-Atomic transakce, oddíl 8, popisuje další podrobnosti o korelaci a vzorech výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="03bb2-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="03bb2-204">R1222: po přijetí a `CreateCoordinationContext` koordinátor musí vystavit `SecurityContextToken` přidružený tajný klíč `STx` .</span><span class="sxs-lookup"><span data-stu-id="03bb2-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="03bb2-205">Tento token se vrátí v `t:IssuedTokens` hlavičce za specifikací WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="03bb2-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="03bb2-206">R1223: Pokud k aktivaci dojde v rámci existujícího koordinačního kontextu, musí se tato zpráva nacházet v `t:IssuedTokens` záhlaví s `SecurityContextToken` přidruženým ke stávajícímu kontextu `CreateCoordinationContext` .</span><span class="sxs-lookup"><span data-stu-id="03bb2-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="03bb2-207">`t:IssuedTokens`Pro připojení k odchozí zprávě by měla být vygenerována nová hlavička `wscoor:CreateCoordinationContextResponse` .</span><span class="sxs-lookup"><span data-stu-id="03bb2-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="03bb2-208">Konfigurace vazby registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="03bb2-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="03bb2-209">B1231: WCF používá duplexní vazbu HTTPS (popsané v [protokolech zasílání zpráv](messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="03bb2-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="03bb2-210">Zprávy žádosti a odpovědi se korelují pomocí WS-Addressing 2004/08 pro WS-AT 1,0 a WS-Addressing 2005/08 pro WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="03bb2-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="03bb2-211">WS-AtomicTransaction, část 8, popisuje další podrobnosti o korelaci a popisy schémat výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="03bb2-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="03bb2-212">R1232: odchozí `wscoor:Register` zprávy musí používat `IssuedTokenOverTransport` režim ověřování popsaný v [protokolech zabezpečení](security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="03bb2-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="03bb2-213">`wsse:Timestamp`Element musí být podepsán pomocí `SecurityContextToken STx` vydané.</span><span class="sxs-lookup"><span data-stu-id="03bb2-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="03bb2-214">Tento podpis je důkazem vlastnictví tokenu přidruženého k konkrétní transakci a slouží k ověření účastníka, který v transakci zařadí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="03bb2-215">Zpráva RegistrationResponse se pošle zpátky přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03bb2-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="03bb2-216">Konfigurace vazby protokolu 2PC</span><span class="sxs-lookup"><span data-stu-id="03bb2-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="03bb2-217">WCF podporuje jednosměrné (Datagram) zprávy přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03bb2-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="03bb2-218">Korelace mezi zprávami je ponechána jako podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="03bb2-219">B1241: implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v tématu Specifikace WS-Addressing, aby bylo možné dosáhnout korelace zpráv 2PC WCF.</span><span class="sxs-lookup"><span data-stu-id="03bb2-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="03bb2-220">Výměna zpráv aplikace</span><span class="sxs-lookup"><span data-stu-id="03bb2-220">Application Message Exchange</span></span>  
 <span data-ttu-id="03bb2-221">Aplikace jsou zdarma pro použití jakékoli konkrétní vazby pro zprávy aplikace a aplikace, pokud vazba splňuje následující požadavky na zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="03bb2-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="03bb2-222">R2001: zprávy typu aplikace a aplikace musí přesměrovat `t:IssuedTokens` hlavičku spolu s `CoordinationContext` v hlavičce zprávy.</span><span class="sxs-lookup"><span data-stu-id="03bb2-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="03bb2-223">R2002: je nutné zadat integritu a důvěrnost `t:IssuedToken` .</span><span class="sxs-lookup"><span data-stu-id="03bb2-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="03bb2-224">`CoordinationContext`Hlavička obsahuje `wscoor:Identifier` .</span><span class="sxs-lookup"><span data-stu-id="03bb2-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="03bb2-225">I když definice `xsd:AnyURI` umožňuje použití absolutních i relativních identifikátorů URI, podporuje pouze WCF `wscoor:Identifiers` , což jsou absolutní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="03bb2-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="03bb2-226">B2003: Pokud `wscoor:Identifier` je v rámci `wscoor:CoordinationContext` RELATIVNÍho identifikátoru URI, chyby se vrátí z transakční služby WCF.</span><span class="sxs-lookup"><span data-stu-id="03bb2-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="03bb2-227">Příklady zpráv</span><span class="sxs-lookup"><span data-stu-id="03bb2-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="03bb2-228">Zprávy o žádostech a odpovědích CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="03bb2-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="03bb2-229">Následující zprávy následují jako vzor požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="03bb2-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="03bb2-230">CreateCoordinationContext s WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="03bb2-231">CreateCoordinationContext s WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="03bb2-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="03bb2-232">CreateCoordinationContextResponse s důvěryhodností pre-1,3 a WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="03bb2-233">CreateCoordinationContextResponse s důvěryhodností 1,3 a WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="03bb2-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="03bb2-234">Registrační zprávy</span><span class="sxs-lookup"><span data-stu-id="03bb2-234">Registration Messages</span></span>  
 <span data-ttu-id="03bb2-235">Následující zprávy jsou registrační zprávy.</span><span class="sxs-lookup"><span data-stu-id="03bb2-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="03bb2-236">Zaregistrovat v WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="03bb2-237">Zaregistrovat v WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="03bb2-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="03bb2-238">Registrovat odpověď pomocí WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="03bb2-239">Registrovat odpověď pomocí WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="03bb2-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="03bb2-240">Zprávy protokolu dvou fází potvrzení</span><span class="sxs-lookup"><span data-stu-id="03bb2-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="03bb2-241">Následující zpráva se týká protokolu dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="03bb2-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="03bb2-242">Potvrzení pomocí WSAT 1,0</span><span class="sxs-lookup"><span data-stu-id="03bb2-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="03bb2-243">Potvrzení pomocí WSAT 1,1</span><span class="sxs-lookup"><span data-stu-id="03bb2-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="03bb2-244">Zprávy aplikace</span><span class="sxs-lookup"><span data-stu-id="03bb2-244">Application Messages</span></span>  
 <span data-ttu-id="03bb2-245">Následující zprávy jsou zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="03bb2-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="03bb2-246">Zpráva aplikace – požadavek</span><span class="sxs-lookup"><span data-stu-id="03bb2-246">Application message-Request</span></span>  
  
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
