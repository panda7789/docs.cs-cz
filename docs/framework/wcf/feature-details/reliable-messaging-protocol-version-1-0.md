---
title: "Protokol spolehlivého zasílání zpráv verze 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5657b48a648603f24e89c0eebd1285ed9a505e54
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="14b28-102">Protokol spolehlivého zasílání zpráv verze 1.0</span><span class="sxs-lookup"><span data-stu-id="14b28-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="14b28-103">Toto téma popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podrobnosti implementace služby WS-spolehlivé zasílání zpráv protokolu únor 2005 (verze 1.0) nezbytné pro vzájemná spolupráce pomocí přenosového protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-104">dodržuje specifikaci WS-spolehlivé zasílání zpráv s omezení a objasnění, která jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="14b28-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="14b28-105">Poznámka: verze 1.0 protokolu WS-ReliableMessaging je implementováno počínaje [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14b28-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="14b28-106">Protokolu WS-spolehlivé zasílání zpráv únor 2005 protokol je implementována ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="14b28-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="14b28-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="14b28-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="14b28-108">Iniciátor: klienta, která zahájí vytváření sekvence WS-spolehlivé zpráv</span><span class="sxs-lookup"><span data-stu-id="14b28-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="14b28-109">Respondér: na službu, kterou přijme je iniciátor požadavky</span><span class="sxs-lookup"><span data-stu-id="14b28-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="14b28-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="14b28-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="14b28-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="14b28-111">Prefix</span></span>|<span data-ttu-id="14b28-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="14b28-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="14b28-113">Správce systémových prostředků</span><span class="sxs-lookup"><span data-stu-id="14b28-113">wsrm</span></span>|<span data-ttu-id="14b28-114">http://schemas.xmlsoap.org/ws/2005/02/RM</span><span class="sxs-lookup"><span data-stu-id="14b28-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="14b28-115">netrm</span><span class="sxs-lookup"><span data-stu-id="14b28-115">netrm</span></span>|<span data-ttu-id="14b28-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="14b28-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="14b28-117">s</span><span class="sxs-lookup"><span data-stu-id="14b28-117">s</span></span>|<span data-ttu-id="14b28-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="14b28-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="14b28-119">wsa</span><span class="sxs-lookup"><span data-stu-id="14b28-119">wsa</span></span>|<span data-ttu-id="14b28-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="14b28-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="14b28-121">wsse</span><span class="sxs-lookup"><span data-stu-id="14b28-121">wsse</span></span>|<span data-ttu-id="14b28-122">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="14b28-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="14b28-123">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="14b28-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="14b28-124">Pořadí vytváření zpráv</span><span class="sxs-lookup"><span data-stu-id="14b28-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-125">implementuje `CreateSequence` a `CreateSequenceResponse` zprávy a pokuste se vytvořit sekvenci spolehlivé zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="14b28-126">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="14b28-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="14b28-127">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor negeneruje Volitelný element Expires v `CreateSequence` zpráva nebo v případech při `CreateSequence` zpráva obsahuje `Offer` element, volitelné `Expires` element v `Offer` element.</span><span class="sxs-lookup"><span data-stu-id="14b28-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="14b28-128">B1102: Při přístupu k `CreateSequence` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` odesílá a přijímá obě `Expires` elementů, pokud existují, ale nepoužívá jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="14b28-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="14b28-129">WS-spolehlivé zasílání zpráv představuje `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.</span><span class="sxs-lookup"><span data-stu-id="14b28-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="14b28-130">R1103: Pokud `CreateSequence` obsahuje `Offer` element spolehlivého zasílání zpráv respondér musíte buď přijmout sekvenci a odpoví `CreateSequenceResponse` obsahující `wsrm:Accept` elementu, které tvoří dvě korelační komunikaci pořadí nebo odmítnout `CreateSequence` požadavku.</span><span class="sxs-lookup"><span data-stu-id="14b28-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="14b28-131">R1104: `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="14b28-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="14b28-132">R1105: `AcksTo` a `ReplyTo` v odkazuje na koncový bod `CreateSequence` musí mít hodnoty adres, které odpovídají octet-wise.</span><span class="sxs-lookup"><span data-stu-id="14b28-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="14b28-133">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér ověřuje, že část identifikátoru URI `AcksTo` a `ReplyTo` odkazy na koncové body jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="14b28-134">R1106: `AcksTo` a `ReplyTo` koncový bod odkazů v `CreateSequence` by měly mít stejnou sadu parametrů odkaz.</span><span class="sxs-lookup"><span data-stu-id="14b28-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-135">nevynucuje, ale předpokládá, že [odkaz na parametry] `AcksTo` a `ReplyTo` na `CreateSequence` jsou identické a používá [odkaz na parametry] z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="14b28-136">R1107: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="14b28-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="14b28-137">R1108: Pokud dva komunikaci pořadí jsou vytvořena pomocí nabídky mechanismus, `[address]` vlastnost `wsrm:AcksTo` podřízený prvek Reference koncového bodu `wsrm:Accept` element `CreateSequenceResponse` musí odpovídat byte-wise cílový identifikátor URI z `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="14b28-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="14b28-138">R1109: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, zprávy odeslané iniciátor a potvrzení na zprávy pomocí respondér musí být odeslána na odkaz na stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="14b28-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-139">k vytvoření spolehlivé relace mezi iniciátor a respondér používá WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-140">pro implementaci protokolu WS-spolehlivé zasílání zpráv poskytuje spolehlivé relace pro jednosměrné, požadavku a odpovědi a úplné duplexní režim vzory pro zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="14b28-141">WS-spolehlivé zasílání zpráv `Offer` mechanismus na `CreateSequence` / `CreateSequenceResponse` umožňuje vytvořit dva pořadí korelační konverzace a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body.</span><span class="sxs-lookup"><span data-stu-id="14b28-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="14b28-142">Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje záruku zabezpečení pro takové relace včetně ochrany začátku do konce relace integritu, je praktické aby přicházejí zprávy určené pro stejné stranu stejný cíl.</span><span class="sxs-lookup"><span data-stu-id="14b28-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="14b28-143">To také umožňuje Prasátko zálohování pořadí potvrzení u zpráv s aplikací.</span><span class="sxs-lookup"><span data-stu-id="14b28-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="14b28-144">Proto se týkají omezení R1104, R1105 a R1108 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14b28-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="14b28-145">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-145">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="14b28-146">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="14b28-147">Pořadí</span><span class="sxs-lookup"><span data-stu-id="14b28-147">Sequence</span></span>  
 <span data-ttu-id="14b28-148">Následuje seznam omezení, která se týkají pořadí:</span><span class="sxs-lookup"><span data-stu-id="14b28-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="14b28-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a přistupuje k pořadová čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="14b28-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="14b28-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy vygeneruje prázdný vozidlo poslední zprávy pomocí akce http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="14b28-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="14b28-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obdrží a doručí zprávu s hlavičkou pořadí, který obsahuje `LastMessage` elementu, pokud identifikátor URI akce není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="14b28-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="14b28-152">Příklad hlavičky pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-152">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="14b28-153">AckRequested záhlaví</span><span class="sxs-lookup"><span data-stu-id="14b28-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-154">používá `AckRequested` záhlaví jako mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="14b28-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-155">negeneruje nepovinný `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="14b28-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="14b28-156">Po přijetí zprávy s `AckRequested` hlavičky, která obsahuje `MessageNumber` elementu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `MessageNumber` hodnota elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14b28-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="14b28-157">Záhlaví SequenceAcknowledgement do důvěryhodné</span><span class="sxs-lookup"><span data-stu-id="14b28-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-158">používá Prasátko zpětný mechanismus pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="14b28-159">R1401: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="14b28-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="14b28-160">B1402: Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musíte vygenerovat potvrzení před obdržením všechny zprávy pořadí (třeba, aby pokryl `AckRequested` zpráva), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `SequenceAcknowledgement` hlavičky, která obsahuje rozsah 0-0, jak je znázorněno v následujícím Příklad.</span><span class="sxs-lookup"><span data-stu-id="14b28-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="14b28-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementu, ale podporuje `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="14b28-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="14b28-162">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="14b28-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="14b28-163">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-spolehlivé zasílání zpráv chyb:</span><span class="sxs-lookup"><span data-stu-id="14b28-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="14b28-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="14b28-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="14b28-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncového bodu může generovat `CreateSequenceRefused` chyb, jak je popsáno ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="14b28-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="14b28-166">B1503:when koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vygeneruje další `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14b28-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="14b28-167">Adresování WS chyb</span><span class="sxs-lookup"><span data-stu-id="14b28-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="14b28-168">Protože WS-spolehlivé zasílání zpráv používá adresování WS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-spolehlivé zasílání zpráv může generovat WS-Addressing chyb.</span><span class="sxs-lookup"><span data-stu-id="14b28-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="14b28-169">Tato část zahrnuje WS-Addressing chyb, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitně generuje ve vrstvě služby WS-spolehlivé zasílání zpráv:</span><span class="sxs-lookup"><span data-stu-id="14b28-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="14b28-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje chyby zpráva adresování záhlaví vyžaduje, pokud platí jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="14b28-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="14b28-171">Chybí zprávu `Sequence` záhlaví a `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="14b28-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="14b28-172">A `CreateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="14b28-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="14b28-173">A `CreateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="14b28-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="14b28-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje selhání akce není podporována odpovědi na zprávu, která chybí `Sequence` záhlaví a má `Action` záhlaví, který není rozpoznaný ve specifikaci WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="14b28-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje koncový bod k dispozici k označení, že koncový bod nezpracovává pořadí na základě zkoumání selhání `CreateSequence` zprávu o adrese hlavičky.</span><span class="sxs-lookup"><span data-stu-id="14b28-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="14b28-176">Protokol složení</span><span class="sxs-lookup"><span data-stu-id="14b28-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="14b28-177">Složení s adresováním WS</span><span class="sxs-lookup"><span data-stu-id="14b28-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-178">podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="14b28-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="14b28-179">Při zmínkami WS-spolehlivé zasílání zpráv specifikaci WS-Addressing 2004/08 pouze se neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="14b28-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="14b28-180">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="14b28-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="14b28-181">R2101: obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="14b28-182">Jedna verze R2102:A WS-Addressing musí použít v rámci dané WS-spolehlivé zasílání zpráv pořadí nebo pár konverzace pořadí korelační pomocí `wsrm:Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="14b28-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="14b28-183">Složení protokol SOAP</span><span class="sxs-lookup"><span data-stu-id="14b28-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-184">podporuje použití SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="14b28-185">Složení s WS-zabezpečení a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="14b28-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-186">poskytuje ochranu pořadí WS-spolehlivé zasílání zpráv pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="14b28-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="14b28-187">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="14b28-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="14b28-188">R2301: K ochraně integrity pořadí WS-spolehlivé zasílání zpráv kromě integrity a důvěrnosti jednotlivých zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje, že se musí použít WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="14b28-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="14b28-189">R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením sequence(s) WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="14b28-190">R2303: Pokud WS-spolehlivé zasílání zpráv pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="14b28-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="14b28-191">B2304:ws-spolehlivé zasílání zpráv pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="14b28-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="14b28-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zdroj generuje `wsse:SecurityTokenReference` element v části rozšiřitelnost element `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="14b28-193">R2305:when skládá s WS zabezpečené konverzace `CreateSequence` zpráva musí obsahovat `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="14b28-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="14b28-194">WS-spolehlivého zasílání zpráv výraz WS-zásad</span><span class="sxs-lookup"><span data-stu-id="14b28-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-195">používá WS-spolehlivého zasílání zpráv WS-Policy kontrolní výraz `wsrm:RMAssertion` k popisu možnosti koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="14b28-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="14b28-196">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="14b28-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="14b28-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] připojí `wsrm:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="14b28-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-198">podporuje oba přílohy do `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="14b28-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="14b28-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje následující volitelné vlastnosti assertion WS-spolehlivé zasílání zpráv a umožňuje řídit je na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="14b28-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="14b28-200">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="14b28-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="14b28-201">Tok řízení WS-spolehlivé zasílání zpráv rozšíření</span><span class="sxs-lookup"><span data-stu-id="14b28-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-202">volitelné další náročnější řídit tok zpráv pořadí využívá rozšiřitelnost WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="14b28-203">Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``bool` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="14b28-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="14b28-204">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="14b28-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="14b28-205">B4001: Když spolehlivého zasílání zpráv toku řízení je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="14b28-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="14b28-206">B4002: Když spolehlivého zasílání zpráv toku řízení je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14b28-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="14b28-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá `netrm:BufferRemaining` indikující, kolik nových zpráv spolehlivého zasílání zpráv cílové můžete ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14b28-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="14b28-208">B4004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivá Služba zasílání zpráv omezí generovaný počet zpráv přenášených při cílové aplikace spolehlivého zasílání zpráv nemůže přijímat rychlé zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="14b28-209">Zpráv spolehlivého zasílání zpráv cílové vyrovnávací paměti a hodnota elementu hodnota klesne na 0.</span><span class="sxs-lookup"><span data-stu-id="14b28-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="14b28-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="14b28-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="14b28-211">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="14b28-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="14b28-212">Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na chování při WS-spolehlivé zasílání zpráv se používá pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="14b28-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="14b28-213">Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:</span><span class="sxs-lookup"><span data-stu-id="14b28-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="14b28-214">Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv k iniciátoru jenom v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="14b28-215">Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.</span><span class="sxs-lookup"><span data-stu-id="14b28-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="14b28-216">Jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="14b28-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="14b28-217">Vazba</span><span class="sxs-lookup"><span data-stu-id="14b28-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-218">poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-219">používá k přenosu všech zpráv ze serveru RMS RMD a odpovědi protokolu HTTP k přenosu všech zprávy RMD RMS požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="14b28-220">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="14b28-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="14b28-222">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje `CreateSequence` nemá žádné nabídky před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="14b28-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="14b28-224">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="14b28-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="14b28-225">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="14b28-226">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vždy vygeneruje samostatné potvrzení v odpovědi na obou pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="14b28-227">Zpráva TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="14b28-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-228">zpracovává `TerminateSequence` jako Jednosměrná operace znamená odpověď HTTP, která má prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="14b28-229">Jedním ze způsobů, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="14b28-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="14b28-230">Vazba</span><span class="sxs-lookup"><span data-stu-id="14b28-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-231">poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes příchozí a odchozí kanál protokolu Http.</span><span class="sxs-lookup"><span data-stu-id="14b28-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-232">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="14b28-233">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="14b28-234">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-235">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="14b28-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="14b28-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` nemá žádné nabídky před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="14b28-237">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `CreateSequenceResponse` zprávu na požadavek HTTP řešit pomocí `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="14b28-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="14b28-238">Duplexní, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="14b28-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="14b28-239">Vazba</span><span class="sxs-lookup"><span data-stu-id="14b28-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-240">poskytuje vzorce výměny zpráv plně asynchronní obousměrný pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-241">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="14b28-242">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="14b28-243">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-244">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="14b28-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="14b28-245">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-246">odešle `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="14b28-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="14b28-247">Doba platnosti pořadí</span><span class="sxs-lookup"><span data-stu-id="14b28-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-248">dvě pořadí považuje za jednu relaci plně duplexní.</span><span class="sxs-lookup"><span data-stu-id="14b28-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="14b28-249">Při generování chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává vzdálený koncový bod pro poruch obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="14b28-250">Při čtení chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] závady obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-251">můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="14b28-252">Naopak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] může zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="14b28-253">Požadavek odpověď,-adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="14b28-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="14b28-254">Vazba</span><span class="sxs-lookup"><span data-stu-id="14b28-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-255">poskytuje jednosměrný a požadavku a odpovědi vzorce výměny zpráv pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-256">používá požadavků HTTP k přenosu zpráv je žádost o pořadí a odpovědi HTTP používá k přenosu zpráv sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="14b28-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="14b28-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="14b28-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="14b28-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="14b28-260">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="14b28-261">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="14b28-261">One-way Message</span></span>  
 <span data-ttu-id="14b28-262">Protokol exchange jednosměrný zprávy úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="14b28-263">`SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="14b28-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="14b28-264">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na žádost o potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="14b28-265">Dvě způsob zprávy</span><span class="sxs-lookup"><span data-stu-id="14b28-265">Two Way Messages</span></span>  
 <span data-ttu-id="14b28-266">Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="14b28-267">Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.</span><span class="sxs-lookup"><span data-stu-id="14b28-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="14b28-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="14b28-269">Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="14b28-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="14b28-270">Opakováním odpovědi</span><span class="sxs-lookup"><span data-stu-id="14b28-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-271">spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="14b28-272">Z toho důvodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale spíš při představuje odpověď HTTP potvrzení, uživatel zpráv nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="14b28-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="14b28-273">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér opakování odpovědi na větev požadavku HTTP požadavku, ke kterému je korelační odpovědi.</span><span class="sxs-lookup"><span data-stu-id="14b28-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="14b28-274">Třídy LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="14b28-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje a odesílá prázdný vozidlo poslední zprávy na větev požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-276">vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="14b28-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="14b28-277">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér reaguje na požadavek pořadí prázdný vozidlo poslední zprávu s prázdný vozidlo poslední zprávu odpovědi pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="14b28-278">Pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér přijme zprávu o poslední, ve kterém akce identifikátor URI není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpovědi s poslední zprávou.</span><span class="sxs-lookup"><span data-stu-id="14b28-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="14b28-279">V případě protokol pro výměnu obousměrný zpráva poslední zprávou představuje aplikace zpráva; v případě protokol pro výměnu jednosměrný zpráva poslední zprávou je prázdný.</span><span class="sxs-lookup"><span data-stu-id="14b28-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="14b28-280">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér nevyžaduje potvrzení pro prázdný vozidlo poslední zprávu odpovědi pořadí.</span><span class="sxs-lookup"><span data-stu-id="14b28-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="14b28-281">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-282">Když všechny požadavky obdrželi platný odpovědi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor generuje a odesílá požadavek pořadí `TerminateSequence` zprávu na větev požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-283">vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="14b28-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="14b28-284">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér reaguje na požadavek pořadí `TerminateSequence` zprávu s odpovědí pořadí `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="14b28-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="14b28-285">V pořadí normální vypnutí i `TerminateSequence` zprávy provádění plný rozsah `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="14b28-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="14b28-286">Požadavek nebo odpověď, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="14b28-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="14b28-287">Vazba</span><span class="sxs-lookup"><span data-stu-id="14b28-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-288">poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-289">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="14b28-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="14b28-290">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="14b28-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="14b28-291">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="14b28-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="14b28-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor generuje `CreateSequence` zprávu s nabídku.</span><span class="sxs-lookup"><span data-stu-id="14b28-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="14b28-293">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="14b28-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="14b28-294">odešle `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="14b28-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="14b28-295">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="14b28-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="14b28-296">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor zajistí všechny opatřeny zprávy žádost o aplikaci `MessageId` a `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="14b28-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="14b28-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor se vztahuje `CreateSequence` zprávy `ReplyTo` koncový bod odkazu na každou zprávu požadavku aplikací.</span><span class="sxs-lookup"><span data-stu-id="14b28-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="14b28-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vyžaduje, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="14b28-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="14b28-299">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že odkaz na koncový bod URI i `CreateSequence` a všechny zprávy požadavku aplikace jsou identické.</span><span class="sxs-lookup"><span data-stu-id="14b28-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
