---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143442"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="689d3-102">Protokol spolehlivého zasílání zpráv verze 1.0</span><span class="sxs-lookup"><span data-stu-id="689d3-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="689d3-103">Toto téma obsahuje podrobné informace o implementaci Windows Communication Foundation (WCF) pro protokol WS-Reliable Messaging únor 2005 (verze 1,0), který je nezbytný pro zajištění meziprovozu pomocí přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="689d3-104">WCF sleduje specifikace zasílání zpráv WS-Reliable s omezeními a vyjasněmi popsanými v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="689d3-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="689d3-105">Počítejte s tím, že protokol WS-ReliableMessaging verze 1,0 je implementován od WinFX.</span><span class="sxs-lookup"><span data-stu-id="689d3-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="689d3-106">Protokol WS-Reliable Messaging únor 2005 se implementuje v WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="689d3-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="689d3-107">Pro usnadnění práce téma používá následující role:</span><span class="sxs-lookup"><span data-stu-id="689d3-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="689d3-108">Iniciátor: klient, který iniciuje vytvoření sekvence zpráv WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="689d3-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="689d3-109">Respondér: služba, která přijímá žádosti iniciátora</span><span class="sxs-lookup"><span data-stu-id="689d3-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="689d3-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="689d3-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="689d3-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="689d3-111">Prefix</span></span>|<span data-ttu-id="689d3-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="689d3-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="689d3-113">správcem</span><span class="sxs-lookup"><span data-stu-id="689d3-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="689d3-114">netrm</span><span class="sxs-lookup"><span data-stu-id="689d3-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="689d3-115">s</span><span class="sxs-lookup"><span data-stu-id="689d3-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="689d3-116">WSA</span><span class="sxs-lookup"><span data-stu-id="689d3-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="689d3-117">wsse</span><span class="sxs-lookup"><span data-stu-id="689d3-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="689d3-118">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="689d3-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="689d3-119">Sekvence – zprávy pro vytváření sekvencí</span><span class="sxs-lookup"><span data-stu-id="689d3-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="689d3-120">Technologie WCF `CreateSequence` implementuje `CreateSequenceResponse` zprávy a vytvoří spolehlivé pořadí zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="689d3-121">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="689d3-121">The following constraints apply:</span></span>

- <span data-ttu-id="689d3-122">B1101: iniciátor WCF negeneruje Volitelný element Expires ve `CreateSequence` zprávě nebo v případech, kdy `CreateSequence` zpráva obsahuje `Offer` element, volitelný `Expires` element v `Offer` elementu.</span><span class="sxs-lookup"><span data-stu-id="689d3-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="689d3-123">B1102: při přístupu ke `CreateSequence` zprávě WCF `Responder` odesílá a přijímá oba `Expires` prvky, pokud existují, ale nepoužívá jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="689d3-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="689d3-124">Zasílání zpráv WS-Reliable zavádí `Offer` mechanismus pro vytvoření dvou vzájemně se korelačních sekvencí, které tvoří relaci.</span><span class="sxs-lookup"><span data-stu-id="689d3-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="689d3-125">R1103: Pokud `CreateSequence` obsahuje `Offer` element, musí mít respondér spolehlivého zasílání zpráv buď přijmout sekvenci a reagovat s `CreateSequenceResponse` `wsrm:Accept` elementem, který vytváří dvě korelační posloupnosti konverzace, nebo `CreateSequence` žádost odmítnout.</span><span class="sxs-lookup"><span data-stu-id="689d3-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="689d3-126">R1104: `SequenceAcknowledgement` a zprávy aplikací, které jsou v sekvenci konverzace, musí být odeslány na `ReplyTo` odkaz na koncový bod v `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="689d3-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="689d3-127">R1105: `AcksTo` a `ReplyTo` odkazy koncových bodů v `CreateSequence` musí mít hodnoty adres, které odpovídají oktetu.</span><span class="sxs-lookup"><span data-stu-id="689d3-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="689d3-128">Respondér WCF ověřuje, zda je část identifikátoru URI `AcksTo` a `ReplyTo` EPRs identická před vytvořením sekvence.</span><span class="sxs-lookup"><span data-stu-id="689d3-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="689d3-129">Odkazy R1106: `AcksTo` a `ReplyTo` Endpoint v `CreateSequence` by měly mít stejnou sadu parametrů odkazu.</span><span class="sxs-lookup"><span data-stu-id="689d3-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="689d3-130">WCF vynutilo, ale předpokládá, že [Reference Parameters] `AcksTo` a `ReplyTo` on `CreateSequence` jsou identické a používá [Reference Parameters] z `ReplyTo` reference koncového bodu pro potvrzení a zprávy sekvence konverzace.</span><span class="sxs-lookup"><span data-stu-id="689d3-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="689d3-131">R1107: Pokud jsou vytvořeny dvě sekvence konverzace pomocí `Offer` mechanismu `SequenceAcknowledgement` a zprávy aplikací, které jsou přenášeny do sekvencí konverzace, musí být odeslány na `ReplyTo` odkaz koncového bodu `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="689d3-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="689d3-132">R1108: Pokud jsou vytvořeny dvě posloupnosti konverzace pomocí mechanismu nabídky, `[address]` vlastnost `wsrm:AcksTo` podřízeného prvku odkazu koncového bodu `wsrm:Accept` prvku `CreateSequenceResponse` musí odpovídat cílovému identifikátoru URI `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="689d3-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="689d3-133">R1109: při vytváření dvou sekvencí konverzace pomocí `Offer` mechanismu se zprávy odesílané iniciátorem a potvrzením zpráv podle respondéru musí odeslat do stejného odkazu na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="689d3-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="689d3-134">WCF používá zasílání zpráv WS-Reliable k navazování spolehlivých relací mezi iniciátorem a respondérem.</span><span class="sxs-lookup"><span data-stu-id="689d3-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="689d3-135">Implementace zasílání zpráv WS-Reliable pro WCF zajišťuje spolehlivou relaci pro jednosměrné, požadavek-odpověď a plně duplexní vzory zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="689d3-136">Mechanizmus pro zasílání zpráv WS-Reliable `Offer` `CreateSequence` / `CreateSequenceResponse` vám umožní vytvořit dvě korelační posloupnosti konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy.</span><span class="sxs-lookup"><span data-stu-id="689d3-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="689d3-137">Vzhledem k tomu, že WCF poskytuje záruku zabezpečení pro takovou relaci, včetně ucelené ochrany integrity relace, je praktické zajistit, aby zprávy určené ke stejné straně byly doručeny do stejného umístění.</span><span class="sxs-lookup"><span data-stu-id="689d3-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="689d3-138">To také umožňuje piggyé potvrzení sekvence pro zprávy aplikací.</span><span class="sxs-lookup"><span data-stu-id="689d3-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="689d3-139">Proto se omezení R1104, R1105 a R1108 vztahují na WCF.</span><span class="sxs-lookup"><span data-stu-id="689d3-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="689d3-140">Příklad `CreateSequence` zprávy</span><span class="sxs-lookup"><span data-stu-id="689d3-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="689d3-141">Příklad `CreateSequenceResponse` zprávy</span><span class="sxs-lookup"><span data-stu-id="689d3-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="689d3-142">Sequence</span><span class="sxs-lookup"><span data-stu-id="689d3-142">Sequence</span></span>

<span data-ttu-id="689d3-143">Následuje seznam omezení, která platí pro sekvence:</span><span class="sxs-lookup"><span data-stu-id="689d3-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="689d3-144">B1201: WCF generuje a přistupuje k pořadovým číslům, která nejsou vyšší než `xs:long` maximální celková hodnota, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="689d3-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="689d3-145">B1202: WCF vždy generuje poslední zprávu těle s identifikátorem URI akce `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="689d3-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="689d3-146">B1203: WCF přijme a doručí zprávu s hlavičkou sekvence, která obsahuje `LastMessage` element, pokud identifikátor URI akce není `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="689d3-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="689d3-147">Příklad záhlaví sekvence</span><span class="sxs-lookup"><span data-stu-id="689d3-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="689d3-148">AckRequested hlavičku</span><span class="sxs-lookup"><span data-stu-id="689d3-148">AckRequested Header</span></span>

<span data-ttu-id="689d3-149">WCF používá `AckRequested` záhlaví jako mechanismus pro udržení naživu.</span><span class="sxs-lookup"><span data-stu-id="689d3-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="689d3-150">WCF negeneruje Volitelný `MessageNumber` element.</span><span class="sxs-lookup"><span data-stu-id="689d3-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="689d3-151">Po přijetí zprávy s `AckRequested` hlavičkou, která obsahuje `MessageNumber` element, WCF ignoruje `MessageNumber` hodnotu prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="689d3-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="689d3-152">SequenceAcknowledgement hlavičku</span><span class="sxs-lookup"><span data-stu-id="689d3-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="689d3-153">WCF používá Piggy mechanismus pro potvrzení sekvencí, která jsou k dispozici v zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="689d3-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="689d3-154">R1401: Pokud se pomocí mechanismu vytvoří dvě posloupnosti konverzace `Offer` , `SequenceAcknowledgement` může se hlavička zahrnout do jakékoli zprávy aplikace předané zamýšlenému příjemci.</span><span class="sxs-lookup"><span data-stu-id="689d3-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="689d3-155">B1402: Pokud WCF musí vygenerovat potvrzení před přijetím zpráv sekvence (například pro splnění `AckRequested` zprávy), WCF vygeneruje `SequenceAcknowledgement` hlavičku, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="689d3-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="689d3-156">B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` element, ale podporuje `Nack` prvky.</span><span class="sxs-lookup"><span data-stu-id="689d3-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="689d3-157">Chyby WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="689d3-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="689d3-158">Následující seznam obsahuje omezení, která se vztahují na implementaci WCF pro zasílání zpráv WS-Reliable:</span><span class="sxs-lookup"><span data-stu-id="689d3-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="689d3-159">B1501: WCF negeneruje `MessageNumberRollover` chyby.</span><span class="sxs-lookup"><span data-stu-id="689d3-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="689d3-160">B1502: koncový bod WCF může generovat `CreateSequenceRefused` chyby, jak je popsáno ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="689d3-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="689d3-161">B1503: když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje další `CreateSequenceRefused` podkód chyby, `netrm:ConnectionLimitReached` jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="689d3-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="689d3-162">Chyby WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="689d3-162">WS-Addressing Faults</span></span>

<span data-ttu-id="689d3-163">Protože zasílání zpráv WS-Reliable používá WS-Addressing, služba WCF WS-Reliable Messaging může způsobit chyby WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="689d3-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="689d3-164">Tato část se zabývá chybami WS-Addressing, které WCF explicitně generuje ve vrstvě zasílání zpráv WS-Reliable:</span><span class="sxs-lookup"><span data-stu-id="689d3-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="689d3-165">B1601: WCF vygeneruje hlavičku adresování zpráv o chybách, která je vyžadována, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="689d3-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="689d3-166">Ve zprávě chybí `Sequence` záhlaví a `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="689d3-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="689d3-167">Ve `CreateSequence` zprávě chybí `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="689d3-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="689d3-168">Ve `CreateSequence` zprávě chybí `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="689d3-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="689d3-169">B1602: WCF vygeneruje akci selhání, která není podporována v odpovědi na zprávu s chybějící `Sequence` hlavičkou a má `Action` záhlaví, které není rozpoznáno ve specifikaci zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="689d3-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="689d3-170">B1603: WCF generuje koncový bod selhání, aby označoval, že koncový bod nezpracovává sekvenci na základě zkoumání `CreateSequence` hlaviček adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="689d3-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="689d3-171">Složení protokolu</span><span class="sxs-lookup"><span data-stu-id="689d3-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="689d3-172">Složení pomocí WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="689d3-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="689d3-173">Služba WCF podporuje dvě verze elementu WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="689d3-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="689d3-174">Specifikace zasílání zpráv WS-Reliable zmiňuje pouze WS-Addressing 2004/08, ale neomezuje použití verze WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="689d3-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="689d3-175">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="689d3-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="689d3-176">R2101: Služba WS-Addressing 2004/08 a WS-Addressing 1,0 se dá použít se zasíláním zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="689d3-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="689d3-177">R2102: v rámci dané sekvence zasílání zpráv WS-Reliable musí být použita jedna verze elementu WS-Addressing nebo dvojice sekvencí konverzace v souvislosti s použitím `wsrm:Offer` mechanismu.</span><span class="sxs-lookup"><span data-stu-id="689d3-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="689d3-178">Složení pomocí protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="689d3-178">Composition with SOAP</span></span>

<span data-ttu-id="689d3-179">Služba WCF podporuje použití protokolu SOAP 1,1 i SOAP 1,2 se zasíláním zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="689d3-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="689d3-180">Složení pomocí WS-Security a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="689d3-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="689d3-181">Služba WCF poskytuje ochranu pro sekvence zasílání zpráv WS-Reliable pomocí zabezpečeného přenosu (HTTPS), složení WS-Security a složení s konverzací WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="689d3-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="689d3-182">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="689d3-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="689d3-183">R2301: aby byla zajištěna ochrana integrity sekvence zasílání zpráv WS-Reliable, kromě integrity a důvěrnosti jednotlivých zpráv, vyžaduje WCF použití konverzace WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="689d3-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="689d3-184">R2302: AWS – před vytvořením posloupností zasílání zpráv WS-Reliable je nutné zřídit relaci konverzace s zabezpečeným zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="689d3-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="689d3-185">R2303: Pokud doba trvání sekvence zasílání zpráv WS-Reliable přesáhne dobu života relace WS-Secure, je `SecurityContextToken` nutné obnovit pomocí příslušné vazby obnovení WS-Secure konverzaci.</span><span class="sxs-lookup"><span data-stu-id="689d3-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="689d3-186">B2304: sekvence zasílání zpráv WS-Reliable nebo dvojice korelačních sekvencí konverzace jsou vždycky vázané na jednu relaci WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="689d3-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="689d3-187">Zdroj WCF generuje `wsse:SecurityTokenReference` element v sekci rozšiřitelnosti elementu `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="689d3-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="689d3-188">R2305: Pokud se skládá s konverzací WS-Secure, `CreateSequence` musí zpráva obsahovat `wsse:SecurityTokenReference` element.</span><span class="sxs-lookup"><span data-stu-id="689d3-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="689d3-189">WS-Reliable Messaging WS-Policy – kontrolní výraz</span><span class="sxs-lookup"><span data-stu-id="689d3-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="689d3-190">WCF používá kontrolní výraz WS-Reliable zasílání zpráv WS-Policy `wsrm:RMAssertion` k popisu možností koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="689d3-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="689d3-191">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="689d3-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="689d3-192">B3001: WCF připojí `wsrm:RMAssertion` kontrolní výraz WS-Policy k `wsdl:binding` elementům.</span><span class="sxs-lookup"><span data-stu-id="689d3-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="689d3-193">WCF podporuje obě přílohy až `wsdl:binding` po `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="689d3-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="689d3-194">B3002: WCF podporuje následující volitelné vlastnosti kontrolního výrazu protokolu WS-Reliable pro zasílání zpráv a poskytuje kontrolu nad nimi na WCF `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="689d3-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="689d3-195">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="689d3-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="689d3-196">Rozšíření pro zasílání zpráv WS-Reliable pro řízení toku</span><span class="sxs-lookup"><span data-stu-id="689d3-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="689d3-197">WCF používá rozšiřitelnost zpráv WS-Reliable k zajištění volitelného dalšího užšího řízení nad tokem zpráv sekvence.</span><span class="sxs-lookup"><span data-stu-id="689d3-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="689d3-198">Řízení toku je povoleno nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnosti na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="689d3-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="689d3-199">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="689d3-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="689d3-200">B4001: Pokud je povoleno řízení toku spolehlivého zasílání zpráv, WCF vygeneruje `netrm:BufferRemaining` element v rozšiřitelnosti elementu v `SequenceAcknowledgement` hlavičce.</span><span class="sxs-lookup"><span data-stu-id="689d3-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="689d3-201">B4002: Pokud je povoleno řízení toku spolehlivého zasílání zpráv, WCF nevyžaduje `netrm:BufferRemaining` element, který by měl být přítomen v `SequenceAcknowledgement` hlavičce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="689d3-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="689d3-202">B4003: WCF používá `netrm:BufferRemaining` k určení, kolik nových zpráv může být cílem spolehlivého zasílání zpráv ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="689d3-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="689d3-203">B4004: služba spolehlivého zasílání zpráv WCF omezuje počet přenesených zpráv, když cílová aplikace spolehlivého zasílání zpráv nemůže přijímat zprávy rychle.</span><span class="sxs-lookup"><span data-stu-id="689d3-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="689d3-204">Zprávy cíle spolehlivého zasílání zpráv a hodnota elementu se přemístí na 0.</span><span class="sxs-lookup"><span data-stu-id="689d3-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="689d3-205">B4005: WCF generuje `netrm:BufferRemaining` celočíselné hodnoty mezi 0 a 4096 včetně a čte celočíselné hodnoty mezi 0 `xs:int` a `maxInclusive` hodnotou 214748364 včetně.</span><span class="sxs-lookup"><span data-stu-id="689d3-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="689d3-206">Vzorce výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="689d3-206">Message Exchange Patterns</span></span>

<span data-ttu-id="689d3-207">Tato část popisuje chování služby WCF při zasílání zpráv WS-Reliable pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="689d3-208">Pro každý vzor výměny zpráv se považují za tyto dva scénáře nasazení:</span><span class="sxs-lookup"><span data-stu-id="689d3-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="689d3-209">Iniciátor bez adresování: iniciátor je za bránou firewall; Respondér může doručovat zprávy iniciátorovi pouze v odpovědích HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="689d3-210">Adresovatelný iniciátor: odesílat požadavky HTTP můžou jenom iniciátor a respondér. Jinými slovy, lze navázat dvě připojení s opačným protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="689d3-211">Jednosměrný, neadresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="689d3-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="689d3-212">Vazba</span><span class="sxs-lookup"><span data-stu-id="689d3-212">Binding</span></span>

<span data-ttu-id="689d3-213">WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="689d3-214">WCF používá požadavky HTTP k přenosu všech zpráv z RMS do RMD a odpověď protokolu HTTP pro přenos všech zpráv z RMD do služby RMS.</span><span class="sxs-lookup"><span data-stu-id="689d3-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="689d3-215">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-215">CreateSequence Exchange</span></span>

<span data-ttu-id="689d3-216">Iniciátor WCF vygeneruje `CreateSequence` zprávu bez nabídky.</span><span class="sxs-lookup"><span data-stu-id="689d3-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="689d3-217">Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence neobsahuje žádnou nabídku.</span><span class="sxs-lookup"><span data-stu-id="689d3-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="689d3-218">Respondér WCF odpoví na `CreateSequence` požadavek `CreateSequenceResponse` zprávou.</span><span class="sxs-lookup"><span data-stu-id="689d3-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="689d3-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="689d3-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="689d3-220">Iniciátor WCF zpracovává potvrzení odpovědi všech zpráv kromě zpráv `CreateSequence` a zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="689d3-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="689d3-221">Respondér WCF vždy generuje samostatné potvrzení v reakci na jak sekvenci, tak `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="689d3-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="689d3-222">Zpráva TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="689d3-222">TerminateSequence message</span></span>

<span data-ttu-id="689d3-223">WCF se považuje `TerminateSequence` za jednosměrnou operaci, což znamená, že odpověď HTTP má prázdný kód a stavový kód http 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="689d3-224">Jedním ze způsobů, jak adresovatelné iniciátory</span><span class="sxs-lookup"><span data-stu-id="689d3-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="689d3-225">Vazba</span><span class="sxs-lookup"><span data-stu-id="689d3-225">Binding</span></span>

<span data-ttu-id="689d3-226">WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes příchozí a odchozí kanál http.</span><span class="sxs-lookup"><span data-stu-id="689d3-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="689d3-227">WCF používá požadavky HTTP k přenosu všech zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="689d3-228">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="689d3-229">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-229">CreateSequence Exchange</span></span>

<span data-ttu-id="689d3-230">Iniciátor WCF vygeneruje `CreateSequence` zprávu bez nabídky.</span><span class="sxs-lookup"><span data-stu-id="689d3-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="689d3-231">Respondér WCF zajišťuje, aby `CreateSequence` před vytvořením sekvence nedošlo k žádné nabídce.</span><span class="sxs-lookup"><span data-stu-id="689d3-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="689d3-232">Respondér WCF přenáší `CreateSequenceResponse` zprávu na požadavek HTTP adresovaný `ReplyTo` odkazem na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="689d3-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="689d3-233">Duplexní, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="689d3-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="689d3-234">Vazba</span><span class="sxs-lookup"><span data-stu-id="689d3-234">Binding</span></span>

<span data-ttu-id="689d3-235">WCF poskytuje plně asynchronní obousměrný vzor výměny zpráv pomocí dvou sekvencí přes příchozí a odchozí kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="689d3-236">WCF používá požadavky HTTP k přenosu všech zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="689d3-237">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="689d3-238">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-238">CreateSequence Exchange</span></span>

<span data-ttu-id="689d3-239">Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou.</span><span class="sxs-lookup"><span data-stu-id="689d3-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="689d3-240">Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku.</span><span class="sxs-lookup"><span data-stu-id="689d3-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="689d3-241">WCF pošle `CreateSequenceResponse` požadavek na protokol HTTP adresovaný na `CreateSequence` `ReplyTo` odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="689d3-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="689d3-242">Doba platnosti sekvence</span><span class="sxs-lookup"><span data-stu-id="689d3-242">Sequence Lifetime</span></span>

<span data-ttu-id="689d3-243">WCF považuje dvě sekvence za jednu plně duplexní relaci.</span><span class="sxs-lookup"><span data-stu-id="689d3-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="689d3-244">Při generování chyby, která chybí jednu sekvenci, služba WCF očekává, že vzdálený koncový bod selže v obou sekvencích.</span><span class="sxs-lookup"><span data-stu-id="689d3-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="689d3-245">Při čtení chyby, která chybí jednu sekvenci, chyby WCF obě sekvence.</span><span class="sxs-lookup"><span data-stu-id="689d3-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="689d3-246">WCF může zavřít svou odchozí sekvenci a nadále zpracovávat zprávy v její vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="689d3-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="689d3-247">V opačném případě může WCF zpracovat ukončení příchozí sekvence a pokračovat v posílání zpráv ve výstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="689d3-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="689d3-248">Požadavek-odpověď, neadresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="689d3-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="689d3-249">Vazba</span><span class="sxs-lookup"><span data-stu-id="689d3-249">Binding</span></span>

<span data-ttu-id="689d3-250">WCF poskytuje jednosměrné a rychlé zprávy s požadavkem na odpověď pomocí dvou sekvencí přes jeden kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="689d3-251">WCF používá požadavky HTTP k přenosu zpráv sekvence požadavků a používá odpovědi HTTP k přenosu zpráv sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="689d3-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="689d3-252">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-252">CreateSequence Exchange</span></span>

<span data-ttu-id="689d3-253">Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou.</span><span class="sxs-lookup"><span data-stu-id="689d3-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="689d3-254">Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku.</span><span class="sxs-lookup"><span data-stu-id="689d3-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="689d3-255">Respondér WCF odpoví na `CreateSequence` požadavek `CreateSequenceResponse` zprávou.</span><span class="sxs-lookup"><span data-stu-id="689d3-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="689d3-256">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="689d3-256">One-way Message</span></span>

<span data-ttu-id="689d3-257">Aby bylo možné úspěšně provést jednosměrnou výměnu zpráv, iniciátor WCF přenáší zprávu sekvence požadavků na požadavek HTTP a obdrží samostatnou `SequenceAcknowledgement` zprávu o odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="689d3-258">`SequenceAcknowledgement`Musí potvrdit přenesenou zprávu.</span><span class="sxs-lookup"><span data-stu-id="689d3-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="689d3-259">Respondér WCF může odpovědět na žádost s potvrzením, chybou nebo odpovědí s prázdným tělem a kódem stavu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="689d3-260">Dvě jednosměrné zprávy</span><span class="sxs-lookup"><span data-stu-id="689d3-260">Two Way Messages</span></span>

<span data-ttu-id="689d3-261">Aby bylo možné úspěšně dokončit oboustranný protokol výměny zpráv, iniciátor WCF přenese zprávu sekvence požadavku na požadavek HTTP a obdrží zprávu sekvence odpovědi v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="689d3-262">Odpověď musí `SequenceAcknowledgement` zasílat potvrzení přenosu zprávy sekvence požadavku.</span><span class="sxs-lookup"><span data-stu-id="689d3-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="689d3-263">Respondér WCF může odpovědět na požadavek pomocí odpovědi aplikace, chyby nebo odpovědi s prázdným kódem a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="689d3-264">Z důvodu přítomnosti jednosměrných zpráv a časování odpovědí na aplikace není pořadové číslo zprávy sekvence požadavku a pořadové číslo zprávy odpovědi nijak korelace.</span><span class="sxs-lookup"><span data-stu-id="689d3-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="689d3-265">Opakování odpovědí</span><span class="sxs-lookup"><span data-stu-id="689d3-265">Retrying Replies</span></span>

<span data-ttu-id="689d3-266">WCF spoléhá na korelaci požadavku HTTP na korelaci protokolu výměny zpráv se dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="689d3-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="689d3-267">Z tohoto důvodu se iniciátor WCF neukončí opakování zprávy sekvence požadavku při potvrzení zprávy sekvence požadavku, ale místo toho, aby odpověď protokolu HTTP zajišťovala potvrzení, zprávu uživatele nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="689d3-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="689d3-268">Respondér WCF reaguje na odezvu požadavku HTTP žádosti, na kterou je tato odpověď korelační.</span><span class="sxs-lookup"><span data-stu-id="689d3-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="689d3-269">Třídy LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-269">LastMessage Exchange</span></span>

<span data-ttu-id="689d3-270">Iniciátor WCF vygeneruje a přenáší prázdnou poslední zprávu těle na nožkě požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="689d3-271">WCF vyžaduje odpověď, ale ignoruje skutečnou zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="689d3-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="689d3-272">Respondér WCF odpovídá poslední zprávě s prázdným těle sekvencí požadavku pomocí poslední zprávy těle sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="689d3-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="689d3-273">Pokud respondér WCF obdrží poslední zprávu, ve které není identifikátor URI akce, odešle `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` odpověď WCF k poslední zprávě.</span><span class="sxs-lookup"><span data-stu-id="689d3-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="689d3-274">V případě obousměrného protokolu výměny zpráv ponese Poslední zpráva zprávu aplikace. v případě jednosměrného protokolu výměny zpráv je poslední zpráva prázdná.</span><span class="sxs-lookup"><span data-stu-id="689d3-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="689d3-275">V rámci služby WCF Responder není vyžadováno potvrzení pro poslední zprávu prázdného těle sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="689d3-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="689d3-276">TerminateSequence – Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="689d3-277">Když všechny požadavky obdrží platnou odpověď, iniciátor WCF vygeneruje a přenese zprávu sekvence požadavků `TerminateSequence` na nožku požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="689d3-278">WCF vyžaduje odpověď, ale ignoruje skutečnou zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="689d3-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="689d3-279">Respondér WCF odpoví na zprávu pořadí požadavků `TerminateSequence` pomocí zprávy sekvence odpovědí `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="689d3-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="689d3-280">V normální sekvenci vypnutí obě `TerminateSequence` zprávy zanášejí celý rozsah `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="689d3-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="689d3-281">Požadavek nebo odpověď, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="689d3-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="689d3-282">Vazba</span><span class="sxs-lookup"><span data-stu-id="689d3-282">Binding</span></span>

<span data-ttu-id="689d3-283">WCF poskytuje vzor výměny zpráv požadavek-odpověď pomocí dvou sekvencí přes příchozí a odchozí kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="689d3-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="689d3-284">WCF používá požadavky HTTP k přenosu všech zpráv.</span><span class="sxs-lookup"><span data-stu-id="689d3-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="689d3-285">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="689d3-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="689d3-286">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="689d3-286">CreateSequence Exchange</span></span>

<span data-ttu-id="689d3-287">Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou.</span><span class="sxs-lookup"><span data-stu-id="689d3-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="689d3-288">Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku.</span><span class="sxs-lookup"><span data-stu-id="689d3-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="689d3-289">WCF pošle `CreateSequenceResponse` požadavek na protokol HTTP adresovaný na `CreateSequence` `ReplyTo` odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="689d3-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="689d3-290">Korelace žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="689d3-290">Request/Reply Correlation</span></span>

<span data-ttu-id="689d3-291">Iniciátor WCF zajišťuje, aby všechny zprávy žádosti o aplikace byly označeny `MessageId` `ReplyTo` odkazem a koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="689d3-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="689d3-292">Iniciátor WCF používá `CreateSequence` `ReplyTo` odkaz na koncový bod zprávy na každé zprávě žádosti o aplikaci.</span><span class="sxs-lookup"><span data-stu-id="689d3-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="689d3-293">Respondér WCF vyžaduje, aby příchozí zprávy žádosti byly označeny `MessageId` a `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="689d3-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="689d3-294">Respondér WCF zajišťuje shodu identifikátoru URI odkazu koncového bodu pro `CreateSequence` všechny zprávy žádostí o aplikaci i všechny.</span><span class="sxs-lookup"><span data-stu-id="689d3-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
