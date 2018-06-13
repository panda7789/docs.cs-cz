---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497049"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="ec0ea-102">Protokol spolehlivého zasílání zpráv verze 1.0</span><span class="sxs-lookup"><span data-stu-id="ec0ea-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="ec0ea-103">Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-spolehlivého zasílání zpráv protokolu únor 2005 (verze 1.0) nezbytné pro vzájemná spolupráce pomocí přenosového protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="ec0ea-104">WCF dodržuje specifikaci WS-spolehlivé zasílání zpráv s omezení a objasnění, která jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="ec0ea-105">Poznámka: verze 1.0 protokolu WS-ReliableMessaging je implementováno počínaje [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec0ea-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="ec0ea-106">Služby WS-spolehlivé zasílání zpráv únor 2005 protokol je implementována ve WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="ec0ea-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="ec0ea-108">Iniciátor: klienta, která zahájí vytváření sekvence WS-spolehlivé zpráv</span><span class="sxs-lookup"><span data-stu-id="ec0ea-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="ec0ea-109">Respondér: na službu, kterou přijme je iniciátor požadavky</span><span class="sxs-lookup"><span data-stu-id="ec0ea-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="ec0ea-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="ec0ea-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="ec0ea-111">Prefix</span></span>|<span data-ttu-id="ec0ea-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ec0ea-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ec0ea-113">Správce systémových prostředků</span><span class="sxs-lookup"><span data-stu-id="ec0ea-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="ec0ea-114">netrm</span><span class="sxs-lookup"><span data-stu-id="ec0ea-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="ec0ea-115">s</span><span class="sxs-lookup"><span data-stu-id="ec0ea-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="ec0ea-116">wsa</span><span class="sxs-lookup"><span data-stu-id="ec0ea-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="ec0ea-117">wsse</span><span class="sxs-lookup"><span data-stu-id="ec0ea-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="ec0ea-118">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="ec0ea-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="ec0ea-119">Pořadí vytváření zpráv</span><span class="sxs-lookup"><span data-stu-id="ec0ea-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="ec0ea-120">Implementuje WCF `CreateSequence` a `CreateSequenceResponse` zprávy a pokuste se vytvořit sekvenci spolehlivé zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="ec0ea-121">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-121">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="ec0ea-122">B1101: Iniciátoru WCF negeneruje Volitelný element Expires v `CreateSequence` zpráva nebo v případech při `CreateSequence` zpráva obsahuje `Offer` element, volitelné `Expires` element v `Offer` elementu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="ec0ea-123">B1102: Při přístupu k `CreateSequence` zprávy, WCF`Responder` odesílá a přijímá obě `Expires` elementů, pokud existují, ale nepoužívá jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="ec0ea-124">WS-spolehlivé zasílání zpráv představuje `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="ec0ea-125">R1103: Pokud `CreateSequence` obsahuje `Offer` element spolehlivého zasílání zpráv respondér musíte buď přijmout sekvenci a odpoví `CreateSequenceResponse` obsahující `wsrm:Accept` elementu, které tvoří dvě korelační komunikaci pořadí nebo odmítnout `CreateSequence` požadavku.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="ec0ea-126">R1104: `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ec0ea-127">R1105: `AcksTo` a `ReplyTo` v odkazuje na koncový bod `CreateSequence` musí mít hodnoty adres, které odpovídají octet-wise.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="ec0ea-128">WCF respondér ověřuje, že část identifikátoru URI `AcksTo` a `ReplyTo` odkazy na koncové body jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="ec0ea-129">R1106: `AcksTo` a `ReplyTo` koncový bod odkazů v `CreateSequence` by měly mít stejnou sadu parametrů odkaz.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="ec0ea-130">WCF nevynucuje, ale předpokládá, že [odkaz na parametry] `AcksTo` a `ReplyTo` na `CreateSequence` jsou identické a používá [odkaz na parametry] z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="ec0ea-131">R1107: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ec0ea-132">R1108: Pokud dva komunikaci pořadí jsou vytvořena pomocí nabídky mechanismus, `[address]` vlastnost `wsrm:AcksTo` podřízený prvek Reference koncového bodu `wsrm:Accept` element `CreateSequenceResponse` musí odpovídat byte-wise cílový identifikátor URI z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ec0ea-133">R1109: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, zprávy odeslané iniciátor a potvrzení na zprávy pomocí respondér musí být odeslána na odkaz na stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="ec0ea-134">WCF používá k vytvoření spolehlivé relace mezi iniciátor a respondér WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="ec0ea-135">Implementace služby WS-spolehlivé zasílání zpráv na WCF poskytuje spolehlivé relace pro jednosměrné, požadavku a odpovědi a úplné duplexní režim vzory pro zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="ec0ea-136">WS-spolehlivé zasílání zpráv `Offer` mechanismus na `CreateSequence` / `CreateSequenceResponse` umožňuje vytvořit dva pořadí korelační konverzace a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="ec0ea-137">Protože WCF poskytuje záruku zabezpečení relace, včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné stranu stejný cíl.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="ec0ea-138">To také umožňuje Prasátko zálohování pořadí potvrzení u zpráv s aplikací.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="ec0ea-139">Proto platí omezení R1104, R1105 a R1108 pro WCF.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="ec0ea-140">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-140">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ec0ea-141">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a><span data-ttu-id="ec0ea-142">Pořadí</span><span class="sxs-lookup"><span data-stu-id="ec0ea-142">Sequence</span></span>  
 <span data-ttu-id="ec0ea-143">Následuje seznam omezení, která se týkají pořadí:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-143">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="ec0ea-144">Generuje B1201:WCF a přístupů pořadí čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="ec0ea-145">B1202:WCF vždy vygeneruje prázdný vozidlo poslední zprávu s akcí URI z http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-145">B1202:WCF always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="ec0ea-146">B1203: WCF obdrží a doručí zprávu s hlavičkou pořadí, který obsahuje `LastMessage` elementu, pokud identifikátor URI akce není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="ec0ea-147">Příklad hlavičky pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-147">An example of a Sequence Header.</span></span>  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a><span data-ttu-id="ec0ea-148">AckRequested záhlaví</span><span class="sxs-lookup"><span data-stu-id="ec0ea-148">AckRequested Header</span></span>  
 <span data-ttu-id="ec0ea-149">Používá WCF `AckRequested` záhlaví jako mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="ec0ea-150">WCF negeneruje nepovinný `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="ec0ea-151">Po přijetí zprávy s `AckRequested` hlavičky, která obsahuje `MessageNumber` ignoruje elementu WCF `MessageNumber` hodnota elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="ec0ea-152">Záhlaví SequenceAcknowledgement do důvěryhodné</span><span class="sxs-lookup"><span data-stu-id="ec0ea-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="ec0ea-153">WCF používá Prasátko zpětný mechanismus pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="ec0ea-154">R1401: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="ec0ea-155">B1402: Když WCF musíte vygenerovat potvrzení před obdržením všechny zprávy pořadí (třeba, aby pokryl `AckRequested` zpráva), vygeneruje WCF `SequenceAcknowledgement` hlavičky, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="ec0ea-156">B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementu, ale podporuje `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="ec0ea-157">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="ec0ea-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="ec0ea-158">Následuje seznam omezení, která se týkají implementace WCF WS-spolehlivé zasílání zpráv chyb:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="ec0ea-159">B1501: WCF negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="ec0ea-160">Koncový bod B1502:WCF může generovat `CreateSequenceRefused` chyb, jak je popsáno ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="ec0ea-161">B1503:when koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, vygeneruje další WCF `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="ec0ea-162">Adresování WS chyb</span><span class="sxs-lookup"><span data-stu-id="ec0ea-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="ec0ea-163">Protože WS-spolehlivé zasílání zpráv používá WS-Addressing, WS-spolehlivého zasílání zpráv WCF implementace může generovat WS-Addressing chyb.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="ec0ea-164">Tato část se zabývá WS-Addressing chyb, které WCF explicitně generuje ve vrstvě služby WS-spolehlivé zasílání zpráv:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="ec0ea-165">B1601:WCF generuje selhání zpráva adresování záhlaví vyžaduje, pokud platí jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="ec0ea-166">Chybí zprávu `Sequence` záhlaví a `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="ec0ea-167">A `CreateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="ec0ea-168">A `CreateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="ec0ea-169">B1602:WCF generuje selhání akce není podporována odpovědi na zprávu, která chybí `Sequence` záhlaví a má `Action` záhlaví, který není rozpoznaný ve specifikaci WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="ec0ea-170">B1603:WCF generuje koncový bod k dispozici k označení, že koncový bod nezpracovává pořadí na základě zkoumání selhání `CreateSequence` zprávu o adrese hlavičky.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="ec0ea-171">Protokol složení</span><span class="sxs-lookup"><span data-stu-id="ec0ea-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="ec0ea-172">Složení s adresováním WS</span><span class="sxs-lookup"><span data-stu-id="ec0ea-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="ec0ea-173">Podporuje dvě verze WS-Addressing WCF: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="ec0ea-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="ec0ea-174">Při zmínkami WS-spolehlivé zasílání zpráv specifikaci WS-Addressing 2004/08 pouze se neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="ec0ea-175">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-175">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="ec0ea-176">R2101: obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="ec0ea-177">Jedna verze R2102:A WS-Addressing musí použít v rámci dané WS-spolehlivé zasílání zpráv pořadí nebo pár konverzace pořadí korelační pomocí `wsrm:Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="ec0ea-178">Složení protokol SOAP</span><span class="sxs-lookup"><span data-stu-id="ec0ea-178">Composition with SOAP</span></span>  
 <span data-ttu-id="ec0ea-179">WCF podporuje SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="ec0ea-180">Složení s WS-zabezpečení a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="ec0ea-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="ec0ea-181">WCF poskytuje ochranu pořadí WS-spolehlivé zasílání zpráv pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="ec0ea-182">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-182">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="ec0ea-183">R2301: K ochraně integrity pořadí WS-spolehlivé zasílání zpráv kromě integrity a důvěrnosti jednotlivých zpráv, WCF vyžaduje, že se musí použít WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="ec0ea-184">R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením sequence(s) WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="ec0ea-185">R2303: Pokud WS-spolehlivé zasílání zpráv pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="ec0ea-186">B2304:ws-spolehlivé zasílání zpráv pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="ec0ea-187">Generuje zdroji WCF `wsse:SecurityTokenReference` element v části rozšiřitelnost element `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="ec0ea-188">R2305:when skládá s WS zabezpečené konverzace `CreateSequence` zpráva musí obsahovat `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="ec0ea-189">WS-spolehlivého zasílání zpráv výraz WS-zásad</span><span class="sxs-lookup"><span data-stu-id="ec0ea-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="ec0ea-190">WCF používá WS-spolehlivého zasílání zpráv WS-Policy kontrolní výraz `wsrm:RMAssertion` k popisu možnosti koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="ec0ea-191">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-191">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="ec0ea-192">B3001: Připojí WCF `wsrm:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="ec0ea-193">WCF podporuje obě přílohy do `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="ec0ea-194">B3002: WCF podporuje následující volitelné vlastnosti assertion WS-spolehlivé zasílání zpráv a umožňuje řídit je na WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="ec0ea-195">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="ec0ea-196">Tok řízení WS-spolehlivé zasílání zpráv rozšíření</span><span class="sxs-lookup"><span data-stu-id="ec0ea-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="ec0ea-197">K poskytování volitelné další náročnější řídit tok zpráv pořadí WCF používá rozšíření WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="ec0ea-198">Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``bool` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-198">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="ec0ea-199">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-199">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="ec0ea-200">B4001: WCF generuje Pokud je povoleno spolehlivého zasílání zpráv řízení toku, `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="ec0ea-201">B4002: Pokud je povoleno spolehlivého zasílání zpráv řízení toku, WCF nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="ec0ea-202">B4003: Používá WCF `netrm:BufferRemaining` indikující, kolik nových zpráv spolehlivého zasílání zpráv cílové můžete ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="ec0ea-203">B4004: Služba WCF spolehlivého zasílání zpráv omezí generovaný počet zpráv přenášených při cílové aplikace spolehlivého zasílání zpráv nemůže přijímat rychlé zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="ec0ea-204">Zpráv spolehlivého zasílání zpráv cílové vyrovnávací paměti a hodnota elementu hodnota klesne na 0.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="ec0ea-205">B4005: Generuje WCF `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="ec0ea-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="ec0ea-206">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="ec0ea-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="ec0ea-207">Tato část popisuje WCF na chování při WS-spolehlivé zasílání zpráv se používá pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="ec0ea-208">Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:</span><span class="sxs-lookup"><span data-stu-id="ec0ea-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="ec0ea-209">Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv k iniciátoru jenom v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="ec0ea-210">Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="ec0ea-211">Jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="ec0ea-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ec0ea-212">Vazba</span><span class="sxs-lookup"><span data-stu-id="ec0ea-212">Binding</span></span>  
 <span data-ttu-id="ec0ea-213">WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="ec0ea-214">WCF používá k přenosu všech zpráv ze serveru RMS RMD a odpovědi protokolu HTTP k přenosu všech zprávy RMD RMS požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ec0ea-215">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-216">Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="ec0ea-217">Zajišťuje respondér WCF `CreateSequence` nemá žádné nabídky před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="ec0ea-218">WCF respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="ec0ea-219">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ec0ea-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="ec0ea-220">Iniciátor WCF zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="ec0ea-221">WCF respondér vždy vygeneruje samostatné potvrzení v odpovědi na obou pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="ec0ea-222">Zpráva TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="ec0ea-222">TerminateSequence message</span></span>  
 <span data-ttu-id="ec0ea-223">Zpracovává WCF `TerminateSequence` jako Jednosměrná operace znamená odpověď HTTP, která má prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="ec0ea-224">Jedním ze způsobů, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="ec0ea-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ec0ea-225">Vazba</span><span class="sxs-lookup"><span data-stu-id="ec0ea-225">Binding</span></span>  
 <span data-ttu-id="ec0ea-226">WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes příchozí a odchozí kanál protokolu Http.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="ec0ea-227">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec0ea-228">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ec0ea-229">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-230">Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="ec0ea-231">WCF respondér zajišťuje, že `CreateSequence` nemá žádné nabídky před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="ec0ea-232">Přenáší respondér WCF `CreateSequenceResponse` zprávu na požadavek HTTP řešit pomocí `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="ec0ea-233">Duplexní, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="ec0ea-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ec0ea-234">Vazba</span><span class="sxs-lookup"><span data-stu-id="ec0ea-234">Binding</span></span>  
 <span data-ttu-id="ec0ea-235">WCF poskytuje vzorce výměny zpráv plně asynchronní obousměrný pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="ec0ea-236">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec0ea-237">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ec0ea-238">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-239">Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ec0ea-240">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="ec0ea-241">Odešle WCF `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="ec0ea-242">Doba platnosti pořadí</span><span class="sxs-lookup"><span data-stu-id="ec0ea-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="ec0ea-243">WCF považuje za jednu relaci plně duplexní dvě pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="ec0ea-244">Při generování chybu, která závady jedním sekvenčním, WCF očekává, že vzdálený koncový bod pro poruch obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="ec0ea-245">Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="ec0ea-246">WCF můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="ec0ea-247">Naopak WCF můžete zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="ec0ea-248">Požadavek odpověď,-adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="ec0ea-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ec0ea-249">Vazba</span><span class="sxs-lookup"><span data-stu-id="ec0ea-249">Binding</span></span>  
 <span data-ttu-id="ec0ea-250">Poskytuje jednosměrný WCF a vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="ec0ea-251">WCF používá požadavků HTTP k přenosu zpráv je žádost o pořadí a odpovědi HTTP používá k přenosu zpráv sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ec0ea-252">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-253">Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ec0ea-254">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="ec0ea-255">WCF respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ec0ea-256">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="ec0ea-256">One-way Message</span></span>  
 <span data-ttu-id="ec0ea-257">Protokol exchange jednosměrný zprávy úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="ec0ea-258">`SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="ec0ea-259">Respondér WCF může odpovědět na žádost o potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="ec0ea-260">Dvě způsob zprávy</span><span class="sxs-lookup"><span data-stu-id="ec0ea-260">Two Way Messages</span></span>  
 <span data-ttu-id="ec0ea-261">Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="ec0ea-262">Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="ec0ea-263">Požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202 může odpovědět respondér WCF.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="ec0ea-264">Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="ec0ea-265">Opakováním odpovědi</span><span class="sxs-lookup"><span data-stu-id="ec0ea-265">Retrying Replies</span></span>  
 <span data-ttu-id="ec0ea-266">WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="ec0ea-267">Z toho důvodu iniciátoru WCF nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale místo v případě, že představuje odpověď HTTP potvrzení, uživatel zpráv nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="ec0ea-268">WCF respondér opakuje odpovědi na větev požadavku HTTP požadavku, ke kterému je korelační odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="ec0ea-269">Třídy LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="ec0ea-270">Iniciátor WCF generuje a odesílá prázdný vozidlo poslední zprávy na větev požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="ec0ea-271">WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="ec0ea-272">WCF respondér odpovědi na požadavek pořadí prázdný vozidlo poslední zprávu s prázdný vozidlo poslední zprávu odpovědi pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="ec0ea-273">Pokud respondér WCF přijme zprávu o poslední, ve kterém akce identifikátor URI není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF odpovědi s poslední zprávou.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-273">If the WCF Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF replies with a last message.</span></span> <span data-ttu-id="ec0ea-274">V případě protokol pro výměnu obousměrný zpráva poslední zprávou představuje aplikace zpráva; v případě protokol pro výměnu jednosměrný zpráva poslední zprávou je prázdný.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="ec0ea-275">WCF respondér nevyžaduje potvrzení pro prázdný vozidlo poslední zprávu odpovědi pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ec0ea-276">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-277">Pokud všechny požadavky obdrželi platný odpovědi, iniciátoru WCF generuje a odesílá požadavek pořadí `TerminateSequence` zprávu na větev požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="ec0ea-278">WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="ec0ea-279">WCF respondér reaguje na požadavek pořadí `TerminateSequence` zprávu s odpovědí pořadí `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="ec0ea-280">V pořadí normální vypnutí i `TerminateSequence` zprávy provádění plný rozsah `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="ec0ea-281">Požadavek nebo odpověď, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="ec0ea-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ec0ea-282">Vazba</span><span class="sxs-lookup"><span data-stu-id="ec0ea-282">Binding</span></span>  
 <span data-ttu-id="ec0ea-283">WCF poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="ec0ea-284">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec0ea-285">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ec0ea-286">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="ec0ea-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ec0ea-287">Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ec0ea-288">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="ec0ea-289">Odešle WCF `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="ec0ea-290">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="ec0ea-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="ec0ea-291">Iniciátor WCF zajistí všechny opatřeny zprávy žádost o aplikaci `MessageId` a `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="ec0ea-292">Iniciátor WCF se vztahuje `CreateSequence` zprávy `ReplyTo` koncový bod odkazu na každou zprávu požadavku aplikací.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="ec0ea-293">Příjemce WCF vyžaduje, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="ec0ea-294">WCF respondér zajišťuje, že odkaz na koncový bod URI i `CreateSequence` a všechny zprávy požadavku aplikace jsou identické.</span><span class="sxs-lookup"><span data-stu-id="ec0ea-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
