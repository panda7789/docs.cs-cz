---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 02a0815f62999c27507ed5e1610f090e944c135a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946702"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="f17ee-102">Protokol spolehlivého zasílání zpráv verze 1.0</span><span class="sxs-lookup"><span data-stu-id="f17ee-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="f17ee-103">Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro posílání WS-Reliable February 2005 (verze 1.0) protokolu, které jsou nezbytné pro spolupráci pomocí přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="f17ee-104">WCF dodržuje specifikaci WS-Reliable zasílání zpráv s omezením a vyjasnění je vysvětleno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="f17ee-105">Všimněte si, že protokol WS-ReliableMessaging verze 1.0 se implementuje počínaje [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f17ee-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="f17ee-106">WS-Reliable zasílání zpráv February 2005 protokol je implementován ve službě WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f17ee-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="f17ee-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="f17ee-107">For convenience, the topic uses the following roles:</span></span>  
  
- <span data-ttu-id="f17ee-108">Iniciátor: klienta, který iniciuje WS-Reliable zpráva sekvence vytvoření</span><span class="sxs-lookup"><span data-stu-id="f17ee-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
- <span data-ttu-id="f17ee-109">Odpovídající zařízení: služby, která bude přijímat žádosti je iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="f17ee-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f17ee-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="f17ee-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="f17ee-111">Prefix</span></span>|<span data-ttu-id="f17ee-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f17ee-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="f17ee-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="f17ee-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="f17ee-114">netrm</span><span class="sxs-lookup"><span data-stu-id="f17ee-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="f17ee-115">s</span><span class="sxs-lookup"><span data-stu-id="f17ee-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="f17ee-116">wsa</span><span class="sxs-lookup"><span data-stu-id="f17ee-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="f17ee-117">wsse</span><span class="sxs-lookup"><span data-stu-id="f17ee-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="f17ee-118">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="f17ee-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="f17ee-119">Pořadí zpráv zařízení</span><span class="sxs-lookup"><span data-stu-id="f17ee-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="f17ee-120">Implementuje WCF `CreateSequence` a `CreateSequenceResponse` zprávy k navázání spolehlivé zprávy sekvence.</span><span class="sxs-lookup"><span data-stu-id="f17ee-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="f17ee-121">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="f17ee-121">The following constraints apply:</span></span>  
  
- <span data-ttu-id="f17ee-122">B1101: Iniciátor WCF negeneruje Volitelný element platnost vyprší v `CreateSequence` zprávy nebo v případech při `CreateSequence` zpráva obsahuje `Offer` elementu, volitelný `Expires` element v `Offer` elementu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
- <span data-ttu-id="f17ee-123">B1102: Při přístupu k `CreateSequence` zpráv WCF`Responder` odesílá a přijímá obě `Expires` elementů, pokud existují, ale nepoužívá jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f17ee-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="f17ee-124">Zasílání zpráv WS-Reliable zavádí `Offer` mechanismus k navázání dvou komunikaci korelační sekvence, které tvoří relace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
- <span data-ttu-id="f17ee-125">R1103: Pokud `CreateSequence` obsahuje `Offer` element spolehlivé zasílání zpráv respondér musí přijmout sekvenci a odpoví `CreateSequenceResponse` , která obsahuje `wsrm:Accept` elementu, které tvoří dvě korelační komunikaci pořadí nebo odmítnout `CreateSequence`požadavku.</span><span class="sxs-lookup"><span data-stu-id="f17ee-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
- <span data-ttu-id="f17ee-126">R1104: `SequenceAcknowledgement` a zprávy aplikace směřující na první sekvenci se musí odeslat na `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
- <span data-ttu-id="f17ee-127">R1105: `AcksTo` a `ReplyTo` v odkazuje na koncový bod `CreateSequence` musí mít adresa hodnoty, které odpovídají octet-wise.</span><span class="sxs-lookup"><span data-stu-id="f17ee-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="f17ee-128">WCF respondér ověřuje, že část identifikátoru URI `AcksTo` a `ReplyTo` odkazy na koncové body jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
- <span data-ttu-id="f17ee-129">R1106: `AcksTo` a `ReplyTo` odkazy na koncový bod v `CreateSequence` by měly mít stejnou sadu parametrů odkazu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="f17ee-130">WCF nevynucuje, ale předpokládá, že [odkaz na parametry] `AcksTo` a `ReplyTo` na `CreateSequence` jsou identické a používá [odkaz na parametry] z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zpráv.</span><span class="sxs-lookup"><span data-stu-id="f17ee-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
- <span data-ttu-id="f17ee-131">R1107: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` a tok na pořadí první zprávy aplikace se musí odeslat na `ReplyTo` odkaz na koncový bod `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
- <span data-ttu-id="f17ee-132">R1108: Při dvou sekvencí konverzace jsou vytvořena pomocí mechanismu nabídku `[address]` vlastnost `wsrm:AcksTo` podřízený element Reference koncového bodu `wsrm:Accept` elementu `CreateSequenceResponse` musí odpovídat byte-wise určení identifikátoru URI `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
- <span data-ttu-id="f17ee-133">R1109: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, zprávy odeslané iniciátoru a potvrzení do zprávy podle respondér se musí odeslat na stejné Reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="f17ee-134">WCF používá k navázání spolehlivé relace mezi iniciátor i respondér zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="f17ee-135">Implementace zasílání zpráv WS-Reliable WCF poskytuje spolehlivé relace pro jednosměrný požadavek odpověď a plně duplexní způsobů zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f17ee-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="f17ee-136">Posílání WS-Reliable `Offer` mechanismus `CreateSequence` / `CreateSequenceResponse` umožňuje vytvoření dvou sekvencí korelační konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="f17ee-137">Protože WCF poskytuje záruku zabezpečení pro relaci, včetně začátku do konce ochranu integrity relace, je potřeba Ujistěte se, že stejný cíl přicházejí zprávy určené stejné osobě.</span><span class="sxs-lookup"><span data-stu-id="f17ee-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="f17ee-138">Díky tomu také Prasátko zálohováním pořadí potvrzení na zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="f17ee-139">Proto platí omezení R1104 R1105 a R1108 pro WCF.</span><span class="sxs-lookup"><span data-stu-id="f17ee-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="f17ee-140">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-140">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="f17ee-141">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="f17ee-142">Pořadí</span><span class="sxs-lookup"><span data-stu-id="f17ee-142">Sequence</span></span>  
 <span data-ttu-id="f17ee-143">Následuje seznam omezení, které se vztahují na pořadí:</span><span class="sxs-lookup"><span data-stu-id="f17ee-143">The following is a list of constraints that apply to sequences:</span></span>  
  
- <span data-ttu-id="f17ee-144">Generuje B1201:WCF a přístupy pořadí čísel vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="f17ee-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
- <span data-ttu-id="f17ee-145">B1202:WCF vždy vygeneruje prázdný-s v těle poslední zprávu s akcí identifikátor URI z `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>  
  
- <span data-ttu-id="f17ee-146">B1203: WCF přijímá a doručí zprávu s hlavičkou sekvenci, který obsahuje `LastMessage` elementu, dokud není identifikátor URI akce `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>  
  
 <span data-ttu-id="f17ee-147">Příklad pořadí záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f17ee-147">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="f17ee-148">Záhlaví AckRequested</span><span class="sxs-lookup"><span data-stu-id="f17ee-148">AckRequested Header</span></span>  
 <span data-ttu-id="f17ee-149">Používá WCF `AckRequested` záhlaví jako vhodný mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="f17ee-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="f17ee-150">WCF negeneruje nepovinný `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="f17ee-151">Při přijetí zprávy s `AckRequested` hlavičku, která obsahuje `MessageNumber` ignoruje WCF elementu, `MessageNumber` hodnota elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="f17ee-152">Záhlaví SequenceAcknowledgement do důvěryhodné</span><span class="sxs-lookup"><span data-stu-id="f17ee-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="f17ee-153">WCF používá Prasátko back mechanismus pro potvrzení pořadí součástí zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
- <span data-ttu-id="f17ee-154">R1401: Po dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví mohou být zahrnuty do jakékoli aplikace zprávy odesílané informace zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="f17ee-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
- <span data-ttu-id="f17ee-155">B1402: WCF musí při generování potvrzení před obdržením všechny zprávy sekvence (například splňují `AckRequested` zpráva), vygeneruje WCF `SequenceAcknowledgement` hlavičku, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- <span data-ttu-id="f17ee-156">B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` element, ale podporuje `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="f17ee-157">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="f17ee-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="f17ee-158">Následuje seznam omezení, které se vztahují k implementaci WCF zasílání zpráv WS-Reliable chyb:</span><span class="sxs-lookup"><span data-stu-id="f17ee-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
- <span data-ttu-id="f17ee-159">B1501: WCF negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="f17ee-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
- <span data-ttu-id="f17ee-160">Koncový bod B1502:WCF může generovat `CreateSequenceRefused` chyb, jak je popsáno ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
- <span data-ttu-id="f17ee-161">B1503:when koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, vygeneruje dalších WCF `CreateSequenceRefused` selhání podřízeného, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="f17ee-162">WS-Addressing chyb</span><span class="sxs-lookup"><span data-stu-id="f17ee-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="f17ee-163">Protože zasílání zpráv WS-Reliable používá WS-Addressing, zasílání zpráv WS-Reliable WCF implementace může způsobit chyby WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f17ee-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="f17ee-164">Tato část zahrnuje chyby WS-Addressing, WCF, které explicitně vytvoří ve vrstvě zasílání zpráv WS-Reliable:</span><span class="sxs-lookup"><span data-stu-id="f17ee-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
- <span data-ttu-id="f17ee-165">B1601:WCF generuje selhání zpráva adresování požadované záhlaví, když je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f17ee-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    - <span data-ttu-id="f17ee-166">Chybí zpráva `Sequence` záhlaví a `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f17ee-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    - <span data-ttu-id="f17ee-167">A `CreateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f17ee-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    - <span data-ttu-id="f17ee-168">A `CreateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f17ee-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
- <span data-ttu-id="f17ee-169">B1602:WCF generuje selhání akce není podporována při zprávu, která chybí `Sequence` záhlaví a má `Action` hlavičku, která není rozpoznaná ve specifikaci zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
- <span data-ttu-id="f17ee-170">B1603:WCF generuje selhání koncového bodu není k dispozici pro označení, že koncový bod nezpracovává pořadí na základě posouzení `CreateSequence` adrese záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="f17ee-171">Protokol sestavení</span><span class="sxs-lookup"><span data-stu-id="f17ee-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="f17ee-172">Kompozice s WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="f17ee-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="f17ee-173">WCF podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1.0 doporučení [WS-ADDR – CORE] a [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="f17ee-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="f17ee-174">While zmínky o zasílání zpráv WS-Reliable specifikace WS-Addressing 2004/08 pouze neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="f17ee-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="f17ee-175">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="f17ee-175">The following is a list of constraints that apply to WCF:</span></span>  
  
- <span data-ttu-id="f17ee-176">R2101: oba WS-Addressing 2004/08 a WS-Addressing 1.0 je možné pomocí zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
- <span data-ttu-id="f17ee-177">R2102:A jednu verzi elementu WS-Addressing musí využívat v rámci dané sekvence WS-Reliable zasílání zpráv nebo dvojice posloupností první korelační pomocí `wsrm:Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="f17ee-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="f17ee-178">Složení u protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="f17ee-178">Composition with SOAP</span></span>  
 <span data-ttu-id="f17ee-179">WCF podporuje použití SOAP 1.1 a SOAP 1.2 zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="f17ee-180">Kompozice s WS-Security a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="f17ee-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="f17ee-181">WCF poskytuje ochranu pro zasílání zpráv WS-Reliable pořadí pomocí zabezpečeného přenosu (HTTPS), kompozice s WS-Security a skládání s WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="f17ee-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="f17ee-182">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="f17ee-182">The following is a list of constraints that apply to WCF:</span></span>  
  
- <span data-ttu-id="f17ee-183">R2301: ochrana integrity sekvenci zasílání zpráv WS-Reliable kromě integritu a důvěrnost jednotlivé zprávy, WCF vyžaduje, že musí použít WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="f17ee-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
- <span data-ttu-id="f17ee-184">R2302:awS-zabezpečenou konverzací relace musí být vytvořen před navazování sequence(s) zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
- <span data-ttu-id="f17ee-185">R2303: Pokud pořadí životnost zasílání zpráv WS-Reliable překročí WS-Secure Conversation životnost relace `SecurityContextToken` lze navázat pomocí WS-Secure Conversation musí obnovovat pomocí odpovídající vazby WS-Secure obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
- <span data-ttu-id="f17ee-186">B2304:ws – pořadí spolehlivé zasílání zpráv nebo dvojice posloupností korelační konverzace jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="f17ee-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="f17ee-187">Vygeneruje zdroj WCF `wsse:SecurityTokenReference` element v oddílu rozšíření elementu `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
- <span data-ttu-id="f17ee-188">R2305:when utvořený za použití WS-Secure Conversation `CreateSequence` musí obsahovat zprávu `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="f17ee-189">WS-Reliable kontrolní výraz zasílání zpráv WS-Policy</span><span class="sxs-lookup"><span data-stu-id="f17ee-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="f17ee-190">WCF používá WS-Reliable zasílání zpráv WS-Policy kontrolní `wsrm:RMAssertion` k popisu funkce koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f17ee-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="f17ee-191">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="f17ee-191">The following is a list of constraints that apply to WCF:</span></span>  
  
- <span data-ttu-id="f17ee-192">B3001: Připojí WCF `wsrm:RMAssertion` WS-Policy kontrolního výrazu k `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="f17ee-193">WCF podporuje obě příloh `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
- <span data-ttu-id="f17ee-194">B3002: WCF podporuje následující volitelné vlastnosti zasílání zpráv WS-Reliable kontrolní výraz a zajišťuje kontrolu nad nimi v WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="f17ee-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    - `wsrm:InactivityTimeout`  
  
    - `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="f17ee-195">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="f17ee-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="f17ee-196">Tok řízení zasílání zpráv WS-Reliable rozšíření</span><span class="sxs-lookup"><span data-stu-id="f17ee-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="f17ee-197">K zajištění volitelné další přesnější kontrolu nad tok pořadí zpráv WCF používá rozšíření zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f17ee-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="f17ee-198">Řízení toku se povoluje nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f17ee-199">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="f17ee-199">The following is a list of constraints that apply to WCF:</span></span>  
  
- <span data-ttu-id="f17ee-200">B4001: Pokud spolehlivé zasílání zpráv řízení toku je povolena, vygeneruje WCF `netrm:BufferRemaining` element v elementu rozšiřitelnost `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f17ee-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
- <span data-ttu-id="f17ee-201">B4002: Pokud je povoleno spolehlivé zasílání zpráv řízení toku, WCF nevyžaduje `netrm:BufferRemaining` prvek nacházet v `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
- <span data-ttu-id="f17ee-202">B4003: Používá WCF `netrm:BufferRemaining` označuje, kolik nové zprávy spolehlivého zasílání zpráv cílové uložit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f17ee-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
- <span data-ttu-id="f17ee-203">B4004: omezuje počet zpráv přenášet-li cílová aplikace spolehlivé zasílání zpráv nelze rychle přijímat zprávy, které služba WCF spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f17ee-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="f17ee-204">Spolehlivé zasílání zpráv cílové vyrovnávací paměti zpráv a název elementu klesne na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="f17ee-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
- <span data-ttu-id="f17ee-205">B4005: Generuje WCF `netrm:BufferRemaining` celočíselné hodnoty rozsahu od 0 do 4096 (včetně) a čte hodnoty celé číslo mezi 0 a `xs:int`společnosti `maxInclusive` hodnota 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="f17ee-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="f17ee-206">Vzorky serveru Exchange zprávu</span><span class="sxs-lookup"><span data-stu-id="f17ee-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="f17ee-207">Tato část popisuje WCF na chování při zasílání zpráv WS-Reliable se používá pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="f17ee-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="f17ee-208">Pro každý vzoru výměny zpráv se považují následující scénáře dvě nasazení:</span><span class="sxs-lookup"><span data-stu-id="f17ee-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
- <span data-ttu-id="f17ee-209">Bajtově Adresovatelného iniciátor: Iniciátor je za bránou firewall; Respondér doručovat zprávy do iniciátoru jenom v odpovědi protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
- <span data-ttu-id="f17ee-210">Adresovatelný iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy je možné navázat připojení prostřednictvím protokolu HTTP dvě konverzace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="f17ee-211">Jednosměrný, bajtově adresovatelného iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f17ee-212">Vazba</span><span class="sxs-lookup"><span data-stu-id="f17ee-212">Binding</span></span>  
 <span data-ttu-id="f17ee-213">WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="f17ee-214">Přenést všechny zprávy ze serveru RMS a odpovědi protokolu HTTP RMD přenášet všechny zprávy z RMD k serveru RMS pomocí WCF požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f17ee-215">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-216">Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="f17ee-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f17ee-217">Zajišťuje respondér WCF `CreateSequence` nemá žádnou nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f17ee-218">Odpovídá respondér WCF `CreateSequence` žádost s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="f17ee-219">Třída SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f17ee-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="f17ee-220">Iniciátor WCF zpracovává potvrzování odpověď všech zpráv s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="f17ee-221">WCF respondér vždy generovat samostatné potvrzení v reakci na obou pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="f17ee-222">Zprávu TerminateSequence dříve</span><span class="sxs-lookup"><span data-stu-id="f17ee-222">TerminateSequence message</span></span>  
 <span data-ttu-id="f17ee-223">Zpracovává WCF `TerminateSequence` jako Jednosměrná operace, což znamená odpovědi protokolu HTTP má prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="f17ee-224">Jedním ze způsobů, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f17ee-225">Vazba</span><span class="sxs-lookup"><span data-stu-id="f17ee-225">Binding</span></span>  
 <span data-ttu-id="f17ee-226">WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí za příchozí a odchozí kanálu protokolu Http.</span><span class="sxs-lookup"><span data-stu-id="f17ee-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="f17ee-227">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f17ee-228">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f17ee-229">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-230">Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky.</span><span class="sxs-lookup"><span data-stu-id="f17ee-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f17ee-231">WCF respondér zajišťuje, že `CreateSequence` nemá žádnou nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f17ee-232">Přenáší respondér WCF `CreateSequenceResponse` mluví zprávu na požadavek HTTP `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="f17ee-233">Duplexní, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f17ee-234">Vazba</span><span class="sxs-lookup"><span data-stu-id="f17ee-234">Binding</span></span>  
 <span data-ttu-id="f17ee-235">WCF poskytuje základní vzor obousměrný plně asynchronních zpráv exchange pomocí dvou sekvencí přes příchozí a odchozí kanálu protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f17ee-236">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f17ee-237">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f17ee-238">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-239">Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou.</span><span class="sxs-lookup"><span data-stu-id="f17ee-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f17ee-240">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f17ee-241">Odešle WCF `CreateSequenceResponse` adresované na požadavku HTTP `CreateSequence`společnosti `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="f17ee-242">Doba života pořadí</span><span class="sxs-lookup"><span data-stu-id="f17ee-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="f17ee-243">WCF považuje dvou sekvencí jeden plně duplexní relace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="f17ee-244">Při generování chybu, která chyb jedním sekvenčním WCF očekává, že vzdálený koncový bod na selhání obou pořadí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="f17ee-245">Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obou pořadí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="f17ee-246">WCF zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy na jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="f17ee-247">Naopak WCF zpracovávat zavřít příchozí pořadí a i nadále odesílat zprávy v jeho výstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="f17ee-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="f17ee-248">Požadavek odpověď, bajtově Adresovatelného iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f17ee-249">Vazba</span><span class="sxs-lookup"><span data-stu-id="f17ee-249">Binding</span></span>  
 <span data-ttu-id="f17ee-250">Poskytuje jednosměrný WCF a vzorce výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="f17ee-251">WCF používá k přenosu žádosti o pořadí zpráv požadavků HTTP a použije odpovědi protokolu HTTP přenášet zprávy sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f17ee-252">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-253">Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou.</span><span class="sxs-lookup"><span data-stu-id="f17ee-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f17ee-254">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f17ee-255">Odpovídá respondér WCF `CreateSequence` žádost s `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="f17ee-256">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="f17ee-256">One-way Message</span></span>  
 <span data-ttu-id="f17ee-257">Protokol exchange jednosměrná zpráva se úspěšně dokončil, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá samostatný `SequenceAcknowledgement` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="f17ee-258">`SequenceAcknowledgement` Musí potvrzení zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="f17ee-259">WCF respondér můžete odpovědět na požadavek na potvrzení, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="f17ee-260">Dvě způsob, jak zprávy</span><span class="sxs-lookup"><span data-stu-id="f17ee-260">Two Way Messages</span></span>  
 <span data-ttu-id="f17ee-261">Protokol pro výměnu zpráv dvousměrné úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá zprávy sekvence odpovědí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="f17ee-262">Odpovědi musí mít `SequenceAcknowledgement` potvrdil pořadí zprávy s požadavkem přenosu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="f17ee-263">WCF respondér můžete odpovědět na požadavek odpovědi na žádost, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="f17ee-264">Z důvodu přítomnosti jednosměrné zprávy a načasování odpovědi aplikace mít žádnou souvislost pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f17ee-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="f17ee-265">Opakování pokusu o odpovědi</span><span class="sxs-lookup"><span data-stu-id="f17ee-265">Retrying Replies</span></span>  
 <span data-ttu-id="f17ee-266">WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="f17ee-267">Z toho důvodu je iniciátor WCF nezastaví opakování zprávy sekvence do žádosti o potvrzení zprávy s požadavkem pořadí ale místo toho v případě, že představuje odpověď HTTP potvrzení, uživatel zpráv nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="f17ee-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="f17ee-268">WCF respondér zopakuje pokus o odpovědi na větev žádosti HTTP požadavku, ke kterému je korelační odpověď.</span><span class="sxs-lookup"><span data-stu-id="f17ee-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="f17ee-269">Třídy LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="f17ee-270">Iniciátor WCF generuje a přenáší prázdnou vozidlo poslední zprávu na větev žádosti protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="f17ee-271">WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f17ee-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f17ee-272">WCF respondér odpovědi na požadavek pořadí s v těle prázdný poslední zprávu s poslední zprávu s v těle prázdná sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="f17ee-273">Pokud respondér WCF obdrží poslední zprávu, ve kterém je identifikátor URI akce není `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF odpovědi s poslední zprávou.</span><span class="sxs-lookup"><span data-stu-id="f17ee-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="f17ee-274">V případě protokol pro výměnu obousměrný zpráva poslední zprávou přenáší zprávy aplikace; v případě protokol pro výměnu jednosměrná zpráva poslední zprávou je prázdný.</span><span class="sxs-lookup"><span data-stu-id="f17ee-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="f17ee-275">WCF respondér nevyžaduje potvrzení pro poslední zprávu s v těle prázdná sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="f17ee-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f17ee-276">TerminateSequence dříve Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-277">Po všech požadavků mít přijetí platné odpovědi iniciátoru WCF generuje a odesílá požadavek pořadí `TerminateSequence` zprávu na větev žádosti protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="f17ee-278">WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f17ee-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f17ee-279">WCF respondér odpoví na požadavek pořadí `TerminateSequence` zprávu s odpovědí pořadí `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="f17ee-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="f17ee-280">V sekvenci normální ukončení obě `TerminateSequence` zprávy mají plný rozsah `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="f17ee-281">Žádost odpověď, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="f17ee-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f17ee-282">Vazba</span><span class="sxs-lookup"><span data-stu-id="f17ee-282">Binding</span></span>  
 <span data-ttu-id="f17ee-283">WCF poskytuje vzoru výměny zpráv žádost odpověď pomocí dvou sekvencí za příchozí a odchozí kanálu protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f17ee-284">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="f17ee-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f17ee-285">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f17ee-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f17ee-286">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f17ee-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f17ee-287">Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou.</span><span class="sxs-lookup"><span data-stu-id="f17ee-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f17ee-288">WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f17ee-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f17ee-289">Odešle WCF `CreateSequenceResponse` adresované na požadavku HTTP `CreateSequence`společnosti `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="f17ee-290">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="f17ee-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="f17ee-291">Iniciátor WCF zajišťuje také nesete zprávy požadavku všechny aplikace `MessageId` a `ReplyTo` reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f17ee-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="f17ee-292">Iniciátor WCF se vztahuje `CreateSequence` zprávy `ReplyTo` reference koncového bodu pro každou zprávu žádosti o aplikace.</span><span class="sxs-lookup"><span data-stu-id="f17ee-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="f17ee-293">Respondér WCF vyžaduje také nesete zprávy příchozí žádosti `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="f17ee-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="f17ee-294">WCF respondér zajišťuje, že identifikátor URI reference koncového bodu z obou `CreateSequence` a všechny zprávy požadavku aplikace jsou identické.</span><span class="sxs-lookup"><span data-stu-id="f17ee-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
