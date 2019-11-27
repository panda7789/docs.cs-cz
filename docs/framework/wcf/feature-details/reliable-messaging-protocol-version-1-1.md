---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283302"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="632e0-102">Protokol spolehlivého zasílání zpráv verze 1.1</span><span class="sxs-lookup"><span data-stu-id="632e0-102">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="632e0-103">Toto téma obsahuje podrobnosti o implementaci Windows Communication Foundation (WCF) pro protokol WS-ReliableMessaging únor 2007 (verze 1,1), který je nezbytný pro meziprovozu pomocí přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="632e0-104">WCF sleduje specifikace WS-ReliableMessaging s omezeními a vysvětleními, které jsou vysvětleny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="632e0-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="632e0-105">Počítejte s tím, že protokol WS-ReliableMessaging verze 1,1 je implementován od .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="632e0-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="632e0-106">Protokol WS-ReliableMessaging únor 2007 je v rámci WCF implementován pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="632e0-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="632e0-107">Pro usnadnění práce téma používá následující role:</span><span class="sxs-lookup"><span data-stu-id="632e0-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="632e0-108">Iniciátor: klient, který iniciuje vytvoření sekvence zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="632e0-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="632e0-109">Responder: služba, která přijímá žádosti iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="632e0-109">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="632e0-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="632e0-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="632e0-111">směr</span><span class="sxs-lookup"><span data-stu-id="632e0-111">Prefix</span></span>|<span data-ttu-id="632e0-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="632e0-112">Namespace</span></span>|
|-|-|
|<span data-ttu-id="632e0-113">správcem</span><span class="sxs-lookup"><span data-stu-id="632e0-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|<span data-ttu-id="632e0-114">netrm</span><span class="sxs-lookup"><span data-stu-id="632e0-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="632e0-115">s</span><span class="sxs-lookup"><span data-stu-id="632e0-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="632e0-116">wsa</span><span class="sxs-lookup"><span data-stu-id="632e0-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="632e0-117">wsse</span><span class="sxs-lookup"><span data-stu-id="632e0-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|<span data-ttu-id="632e0-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="632e0-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|<span data-ttu-id="632e0-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="632e0-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|<span data-ttu-id="632e0-120">WSP</span><span class="sxs-lookup"><span data-stu-id="632e0-120">wsp</span></span>|<span data-ttu-id="632e0-121">(WS-Policy 1,2 nebo WS-Policy 1,5)</span><span class="sxs-lookup"><span data-stu-id="632e0-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="632e0-122">Messaging</span><span class="sxs-lookup"><span data-stu-id="632e0-122">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="632e0-123">Vytvoření sekvence</span><span class="sxs-lookup"><span data-stu-id="632e0-123">Sequence Creation</span></span>

<span data-ttu-id="632e0-124">Služba WCF implementuje `CreateSequence` a `CreateSequenceResponse` zprávy k navázání spolehlivé sekvence zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="632e0-125">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="632e0-125">The following constraints apply:</span></span>

- <span data-ttu-id="632e0-126">B1101: iniciátor WCF používá stejný odkaz na koncový bod jako `ReplyTo``CreateSequence` zprávy, `AcksTo` a `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="632e0-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="632e0-127">R1102: odkazy na koncový bod `AcksTo`, `ReplyTo` a `Offer/Endpoint` ve zprávě `CreateSequence` musí mít hodnoty adresy se identickými reprezentacemi řetězců tak, aby odpovídaly oktetu.</span><span class="sxs-lookup"><span data-stu-id="632e0-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="632e0-128">Respondér WCF ověřuje, zda je část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` odkazů na koncový bod před vytvořením sekvence identická.</span><span class="sxs-lookup"><span data-stu-id="632e0-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="632e0-129">R1103: odkazy na koncový bod `AcksTo`, `ReplyTo` a `Offer/Endpoint` ve zprávě `CreateSequence` by měly mít stejnou sadu parametrů odkazu.</span><span class="sxs-lookup"><span data-stu-id="632e0-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="632e0-130">Služba WCF neuplatňuje, ale předpokládá, že referenční parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` odkazy koncového bodu na `CreateSequence` jsou identické a používají referenční parametry z referenčního bodu `ReplyTo` pro zprávy o potvrzeních a sekvenci konverzace.</span><span class="sxs-lookup"><span data-stu-id="632e0-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="632e0-131">B1104: iniciátor WCF negeneruje v `CreateSequence` zprávě volitelný prvek `Expires` nebo `Offer/Expires`.</span><span class="sxs-lookup"><span data-stu-id="632e0-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="632e0-132">B1105: při přístupu ke zprávě `CreateSequence` použije respondér WCF hodnotu `Expires` v elementu `CreateSequence` jako hodnotu `Expires` v prvku `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="632e0-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="632e0-133">V opačném případě respondér WCF načte a ignoruje hodnoty `Expires` a `Offer/Expires`.</span><span class="sxs-lookup"><span data-stu-id="632e0-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="632e0-134">B1106: při přístupu k `CreateSequenceResponse` zprávě vyhledá iniciátor WCF volitelnou `Expires` hodnotu, ale nepoužije ji.</span><span class="sxs-lookup"><span data-stu-id="632e0-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="632e0-135">B1107: iniciátor WCF a respondér vždy vygeneruje volitelný `IncompleteSequenceBehavior` element v elementech `CreateSequence/Offer` a `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="632e0-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="632e0-136">B1108: WCF používá v elementu `IncompleteSequenceBehavior` pouze hodnoty `DiscardFollowingFirstGap` a `NoDiscard`.</span><span class="sxs-lookup"><span data-stu-id="632e0-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="632e0-137">WS-ReliableMessaging využívá mechanismus `Offer` k vytvoření dvou převedených korelačních sekvencí, které tvoří relaci.</span><span class="sxs-lookup"><span data-stu-id="632e0-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="632e0-138">B1109: Pokud `CreateSequence` obsahuje `Offer` element, pak jednosměrné respondér WCF odmítne nabízenou sekvenci tím, že reaguje na `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="632e0-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="632e0-139">B1110: Pokud spolehlivý respondér zasílání zpráv odmítne nabízenou sekvenci, vyhledá iniciátor WCF nově vytvořenou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="632e0-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="632e0-140">B1111: Pokud `CreateSequence` neobsahuje element `Offer`, obousměrný respondér WCF odmítne nabízenou sekvenci tím, že reaguje na chybu `CreateSequenceRefused`.</span><span class="sxs-lookup"><span data-stu-id="632e0-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="632e0-141">R1112: při vytváření dvou sekvencí konverzace pomocí mechanismu `Offer` musí vlastnost `[address]` odkazu na koncový bod `CreateSequenceResponse/Accept/AcksTo` odpovídat cílovému identifikátoru URI `CreateSequence` bajtu zprávy.</span><span class="sxs-lookup"><span data-stu-id="632e0-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="632e0-142">R1113: při vytváření dvou sekvencí konverzace pomocí mechanismu `Offer` musí být všechny zprávy v obou sekvencích toku od iniciátoru k tomuto partnerovi odesílány do stejného odkazu na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="632e0-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="632e0-143">WCF používá ke zřízení spolehlivých relací mezi iniciátorem a respondérem WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="632e0-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="632e0-144">Implementace WCF WS-ReliableMessaging poskytuje spolehlivou relaci pro jednosměrné, požadavek-odpověď a plně duplexní vzory zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="632e0-145">Mechanismus `Offer` WS-ReliableMessaging na `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dvě korelační posloupnosti konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy.</span><span class="sxs-lookup"><span data-stu-id="632e0-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="632e0-146">Vzhledem k tomu, že WCF poskytuje záruku zabezpečení pro takovou relaci, včetně ucelené ochrany integrity relací, je praktické zajistit, aby zprávy určené pro stejnou stranu byly doručeny do stejného umístění.</span><span class="sxs-lookup"><span data-stu-id="632e0-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="632e0-147">To také umožňuje "Piggy-Back" (potvrzování sekvencí) pro zprávy aplikací.</span><span class="sxs-lookup"><span data-stu-id="632e0-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="632e0-148">Proto se omezení R1102, R1112 a R1113 vztahují na WCF.</span><span class="sxs-lookup"><span data-stu-id="632e0-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="632e0-149">Příklad zprávy `CreateSequence`</span><span class="sxs-lookup"><span data-stu-id="632e0-149">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="632e0-150">Příklad zprávy `CreateSequenceResponse`</span><span class="sxs-lookup"><span data-stu-id="632e0-150">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a><span data-ttu-id="632e0-151">Uzavírání sekvence</span><span class="sxs-lookup"><span data-stu-id="632e0-151">Closing a Sequence</span></span>

<span data-ttu-id="632e0-152">WCF používá `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivého zdroje zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="632e0-153">Cíl spolehlivého zasílání zpráv WCF neinicializuje vypnutí a zdroj spolehlivého zasílání zpráv WCF nepodporuje vypnutí spolehlivého cíle zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="632e0-154">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="632e0-154">The following constraints apply:</span></span>

- <span data-ttu-id="632e0-155">B1201: zdroj spolehlivého zasílání zpráv WCF vždy pošle zprávu `CloseSequence` pro vypnutí sekvence.</span><span class="sxs-lookup"><span data-stu-id="632e0-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="632e0-156">B1202: zdroj spolehlivého zasílání zpráv čeká na potvrzení plného rozsahu zpráv sekvence před odesláním zprávy `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="632e0-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="632e0-157">B1203: spolehlivý zdroj zasílání zpráv vždy obsahuje volitelný element `LastMsgNumber`, pokud sekvence neobsahuje zprávy.</span><span class="sxs-lookup"><span data-stu-id="632e0-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="632e0-158">R1204: cíl spolehlivého zasílání zpráv nesmí iniciovat vypnutí odesláním zprávy `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="632e0-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="632e0-159">B1205: po přijetí `CloseSequence` zprávy nepovažuje zdroj spolehlivých zpráv WCF pořadí za nekompletní a pošle chybu.</span><span class="sxs-lookup"><span data-stu-id="632e0-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="632e0-160">Příklad zprávy `CloseSequence`</span><span class="sxs-lookup"><span data-stu-id="632e0-160">An example of a `CloseSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="632e0-161">Příklad `CloseSequenceResponse` zpráva:</span><span class="sxs-lookup"><span data-stu-id="632e0-161">Example `CloseSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a><span data-ttu-id="632e0-162">Ukončení sekvence</span><span class="sxs-lookup"><span data-stu-id="632e0-162">Sequence Termination</span></span>

<span data-ttu-id="632e0-163">WCF primárně používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="632e0-163">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="632e0-164">Cíl spolehlivého zasílání zpráv WCF nezahajuje ukončení a spolehlivý zdroj přenosu dat nepodporuje ukončení iniciované spolehlivým cílem zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-164">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="632e0-165">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="632e0-165">The following constraints apply:</span></span>

- <span data-ttu-id="632e0-166">B1301: iniciátor WCF odesílá zprávu `TerminateSequence` až po úspěšném dokončení `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="632e0-166">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="632e0-167">R1302: WCF ověří, že `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence`ými zprávami pro danou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="632e0-167">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="632e0-168">To znamená, že `LastMsgNumber` buď není přítomna na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je přítomna a shodná se všemi `CloseSequence` a `TerminateSequence`mi zprávami.</span><span class="sxs-lookup"><span data-stu-id="632e0-168">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="632e0-169">B1303: když se po `CloseSequence/CloseSequenceResponse` handshake dokončí zpráva `TerminateSequence`, bude cíl spolehlivého zasílání zpráv odpovídat `TerminateSequenceResponse` zprávě.</span><span class="sxs-lookup"><span data-stu-id="632e0-169">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="632e0-170">Vzhledem k tomu, že zdroj spolehlivého zasílání zpráv obsahuje závěrečné potvrzení před odesláním `TerminateSequence` zprávy, bude cíl spolehlivého zasílání zpráv vědět bez pochybnosti o ukončení sekvence a okamžitě Redeklarace prostředků.</span><span class="sxs-lookup"><span data-stu-id="632e0-170">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="632e0-171">B1304: při přijímání zprávy o `TerminateSequence` před `CloseSequence/CloseSequenceResponse` handshake se jako cíl služby WCF pro doručování zpráv odpoví zpráva `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="632e0-171">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="632e0-172">Pokud cíl spolehlivého zasílání zpráv zjistí, že v sekvenci nejsou žádné nekonzistence, čeká cíl spolehlivého zasílání zpráv po dobu určenou pro určitý cíl aplikace, aby mohl klientovi získat možnost přijímání. konečné potvrzení.</span><span class="sxs-lookup"><span data-stu-id="632e0-172">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="632e0-173">V opačném případě cíl spolehlivého zasílání zpráv Redeklarace prostředků okamžitě a označuje cíl aplikace, který sekvence končí, tím, že vyvolává událost `Faulted`.</span><span class="sxs-lookup"><span data-stu-id="632e0-173">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="632e0-174">Příklad zprávy `TerminateSequence`</span><span class="sxs-lookup"><span data-stu-id="632e0-174">An example of a `TerminateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="632e0-175">Příklad `TerminateSequenceResponse` zpráva:</span><span class="sxs-lookup"><span data-stu-id="632e0-175">Example `TerminateSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a><span data-ttu-id="632e0-176">Sekvence</span><span class="sxs-lookup"><span data-stu-id="632e0-176">Sequences</span></span>

<span data-ttu-id="632e0-177">Následuje seznam omezení, která platí pro sekvence:</span><span class="sxs-lookup"><span data-stu-id="632e0-177">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="632e0-178">B1401: WCF vygeneruje a přistupuje k pořadovým číslům, která nejsou větší než maximální povolená hodnota `xs:long`9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="632e0-178">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="632e0-179">Příklad záhlaví `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="632e0-179">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="632e0-180">Potvrzení žádosti</span><span class="sxs-lookup"><span data-stu-id="632e0-180">Request Acknowledgement</span></span>

<span data-ttu-id="632e0-181">WCF používá hlavičku `AckRequested` jako mechanizmus Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="632e0-181">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="632e0-182">Příklad záhlaví `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="632e0-182">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="632e0-183">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="632e0-183">SequenceAcknowledgement</span></span>

<span data-ttu-id="632e0-184">WCF používá mechanizmus "Piggy-Back" pro potvrzení sekvencí, které jsou k dispozici v zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="632e0-184">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="632e0-185">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="632e0-185">The following constraints apply:</span></span>

- <span data-ttu-id="632e0-186">R1601: při vytváření dvou sekvencí konverzace pomocí mechanismu `Offer` může být záhlaví `SequenceAcknowledgement` zahrnuté do jakékoli zprávy aplikace předané zamýšlenému příjemci.</span><span class="sxs-lookup"><span data-stu-id="632e0-186">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="632e0-187">Vzdálený koncový bod musí být schopný získat přístup k hlavičce složeného `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="632e0-187">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="632e0-188">B1602: WCF negeneruje `SequenceAcknowledgement` hlaviček, které obsahují `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="632e0-188">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="632e0-189">WCF ověřuje, že každý prvek `Nack` obsahuje pořadové číslo, ale v opačném případě ignoruje `Nack` prvek a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="632e0-189">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="632e0-190">Příklad záhlaví `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="632e0-190">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="632e0-191">Chyby WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="632e0-191">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="632e0-192">Následující seznam obsahuje omezení, která se vztahují na implementaci WCF s chybami WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="632e0-192">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="632e0-193">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="632e0-193">The following constraints apply:</span></span>

- <span data-ttu-id="632e0-194">B1701: WCF negeneruje chyby `MessageNumberRollover`.</span><span class="sxs-lookup"><span data-stu-id="632e0-194">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="632e0-195">B1702: přes SOAP 1,2, když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje podřízený kód chyby `CreateSequenceRefused`, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="632e0-195">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a><span data-ttu-id="632e0-196">Chyby WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="632e0-196">WS-Addressing Faults</span></span>

<span data-ttu-id="632e0-197">Vzhledem k tomu, že WS-ReliableMessaging používá WS-ReliableMessaging, implementace WCF WS-ReliableMessaging může generovat a odesílat chyby WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="632e0-197">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="632e0-198">Tato část se zabývá chybami WS-Addressing, které WCF explicitně generuje a odesílá ve vrstvě WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="632e0-198">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="632e0-199">B1801: WCF generuje a přenáší chybu `Message Addressing Header Required`, pokud je splněna jedna z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="632e0-199">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="632e0-200">Ve zprávě `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí hlavička `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="632e0-200">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="632e0-201">Ve zprávě `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí hlavička `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="632e0-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="632e0-202">Ve zprávě `CreateSequenceResponse`, `CloseSequenceResponse`nebo `TerminateSequenceResponse` chybí hlavička `RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="632e0-202">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="632e0-203">B1802: WCF vygeneruje a přenáší chybu `Endpoint Unavailable`, aby označovala, že nenaslouchá žádný koncový bod, který může zpracovat sekvenci na základě zkoumání hlaviček adres ve zprávě `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="632e0-203">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="632e0-204">Složení protokolu</span><span class="sxs-lookup"><span data-stu-id="632e0-204">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="632e0-205">Složení pomocí WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="632e0-205">Composition with WS-Addressing</span></span>

<span data-ttu-id="632e0-206">Služba WCF podporuje dvě verze elementu WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="632e0-206">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="632e0-207">I když specifikace WS-ReliableMessaging zmiňuje pouze WS-Addressing 2004/08, neomezuje použití verze WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="632e0-207">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="632e0-208">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="632e0-208">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="632e0-209">R2101: Služba WS-Addressing 2004/08 a WS-Addressing 1,0 se dá použít se zasíláním zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="632e0-209">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="632e0-210">R2102: v rámci dané sekvence WS-ReliableMessaging musí být použita jedna verze elementu WS-Addressing nebo dvojice sekvencí konverzace s použitím mechanismu `Offer`.</span><span class="sxs-lookup"><span data-stu-id="632e0-210">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="632e0-211">Složení pomocí protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="632e0-211">Composition with SOAP</span></span>

<span data-ttu-id="632e0-212">Služba WCF podporuje použití protokolu SOAP 1,1 i SOAP 1,2 se zasíláním zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="632e0-212">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="632e0-213">Složení pomocí WS-Security a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="632e0-213">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="632e0-214">Služba WCF poskytuje ochranu pro sekvence WS-ReliableMessaging pomocí zabezpečeného přenosu (HTTPS), složení pomocí WS-Security a složení pomocí konverzace WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="632e0-214">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="632e0-215">Protokol WS-ReliableMessaging 1,1, WS-Security 1,1 a WS-Secure konverzace 1,3 by se měl používat společně.</span><span class="sxs-lookup"><span data-stu-id="632e0-215">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="632e0-216">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="632e0-216">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="632e0-217">R2301: aby byla zajištěna ochrana integrity sekvence WS-ReliableMessaging Kromě integrity a důvěrnosti jednotlivých zpráv, služba WCF vyžaduje, aby se používala konverzace WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="632e0-217">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="632e0-218">R2302: AWS – před vytvořením posloupností WS-ReliableMessaging je nutné vytvořit relaci konverzace s zabezpečenou relací.</span><span class="sxs-lookup"><span data-stu-id="632e0-218">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="632e0-219">R2303: Pokud doba trvání sekvence WS-ReliableMessaging přesáhne dobu života relace WS-, je nutné obnovit `SecurityContextToken` navázané pomocí konverzace protokolu WS-Secure pomocí odpovídající vazby obnovení WS-Secure konverzace.</span><span class="sxs-lookup"><span data-stu-id="632e0-219">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="632e0-220">B2304: sekvence WS-ReliableMessaging nebo dvojice korelačních sekvencí konverzace jsou vždycky vázané na jednu relaci WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="632e0-220">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="632e0-221">R2305: Pokud se skládá s konverzací WS-Secure, WCF respondér WCF vyžaduje, aby zpráva `CreateSequence` obsahovala `wsse:SecurityTokenReference` prvek a hlavičku `wsrm:UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="632e0-221">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="632e0-222">Příklad záhlaví `UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="632e0-222">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="632e0-223">Složení s relacemi SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="632e0-223">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="632e0-224">WCF nepodporuje kompozici s relacemi SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="632e0-224">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="632e0-225">B2401: WCF negeneruje hlavičku `wsrm:UsesSequenceSSL`.</span><span class="sxs-lookup"><span data-stu-id="632e0-225">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="632e0-226">R2402: iniciátor spolehlivého zasílání zpráv nesmí odeslat zprávu `CreateSequence` s hlavičkou `wsrm:UsesSequenceSSL` na respondér WCF.</span><span class="sxs-lookup"><span data-stu-id="632e0-226">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="632e0-227">Složení pomocí WS-Policy</span><span class="sxs-lookup"><span data-stu-id="632e0-227">Composition with WS-Policy</span></span>

<span data-ttu-id="632e0-228">WCF podporuje dvě verze WS-Policy: WS-Policy 1,2 a WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="632e0-228">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="632e0-229">Kontrolní výraz WS-ReliableMessaging WS-Policy</span><span class="sxs-lookup"><span data-stu-id="632e0-229">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="632e0-230">WCF používá kontrolní výraz WS-ReliableMessaging WS-Policy `wsrm:RMAssertion` k popisu možností koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="632e0-230">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="632e0-231">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="632e0-231">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="632e0-232">B3001: WCF připojí `wsrmn:RMAssertion` kontrolní výraz WS-Policy pro `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="632e0-232">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="632e0-233">WCF podporuje obě přílohy pro `wsdl:binding` a `wsdl:port` prvky.</span><span class="sxs-lookup"><span data-stu-id="632e0-233">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="632e0-234">B3002: WCF nikdy negeneruje značku `wsp:Optional`.</span><span class="sxs-lookup"><span data-stu-id="632e0-234">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="632e0-235">B3003: při přístupu `wsrmp:RMAssertion` k kontrolnímu výrazu WS-Policy technologie WCF ignoruje značku `wsp:Optional` a považuje zásadu WS-RM za povinnou.</span><span class="sxs-lookup"><span data-stu-id="632e0-235">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="632e0-236">R3004: protože WCF nevytváří relace SSL/TLS, WCF neakceptuje zásady, které určují `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="632e0-236">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="632e0-237">B3005: WCF vždy generuje prvek `wsrmp:DeliveryAssurance`.</span><span class="sxs-lookup"><span data-stu-id="632e0-237">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="632e0-238">B3006: WCF vždy určuje záruku doručování `wsrmp:ExactlyOnce`.</span><span class="sxs-lookup"><span data-stu-id="632e0-238">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="632e0-239">B3007: WCF generuje a přečte následující vlastnosti kontrolního výrazu WS-ReliableMessaging a poskytuje jejich kontrolu na`ReliableSessionBindingElement`WCF:</span><span class="sxs-lookup"><span data-stu-id="632e0-239">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="632e0-240">Příklad `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="632e0-240">An example of a `RMAssertion`.</span></span>

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="632e0-241">Rozšíření pro řízení toku WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="632e0-241">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="632e0-242">WCF používá rozšiřitelnost WS-ReliableMessaging k zajištění volitelného dalšího užšího řízení toku zpráv sekvence.</span><span class="sxs-lookup"><span data-stu-id="632e0-242">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="632e0-243">Řízení toku je povoleno nastavením vlastnosti <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="632e0-243">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="632e0-244">Následuje seznam omezení, která platí pro WCF:</span><span class="sxs-lookup"><span data-stu-id="632e0-244">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="632e0-245">B4001: když je povolený spolehlivý ovládací prvek toku zpráv, WCF vygeneruje element `netrm:BufferRemaining` v rozšiřitelnosti elementu `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="632e0-245">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="632e0-246">B4002: i když je povolené řízení toku spolehlivého zasílání zpráv, WCF nevyžaduje `netrm:BufferRemaining` element v hlavičce `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="632e0-246">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="632e0-247">B4003: cíl spolehlivého zasílání zpráv WCF používá `netrm:BufferRemaining` k určení, kolik nových zpráv může ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="632e0-247">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="632e0-248">B4004: když je povolené řízení toku spolehlivých přenosů zpráv, používá zdroj dat služby WCF hodnotu `netrm:BufferRemaining` k omezení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-248">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="632e0-249">B4005: WCF generuje `netrm:BufferRemaining` celočíselné hodnoty mezi 0 a 4096 včetně a čte celočíselné hodnoty mezi 0 a `xs:int``maxInclusive` hodnotou 214748364 včetně.</span><span class="sxs-lookup"><span data-stu-id="632e0-249">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="632e0-250">Vzorce výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="632e0-250">Message Exchange Patterns</span></span>

<span data-ttu-id="632e0-251">Tato část popisuje chování služby WCF při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-251">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="632e0-252">Pro každý vzor výměny zpráv se považují za tyto dva scénáře nasazení:</span><span class="sxs-lookup"><span data-stu-id="632e0-252">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="632e0-253">Neadresovatelný iniciátor: iniciátor je za bránou firewall; Respondér může doručovat zprávy do iniciátoru pouze na odpovědích HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-253">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="632e0-254">Adresovatelný iniciátor: odesílat požadavky HTTP můžou jenom iniciátor a respondér. Jinými slovy, lze navázat dvě připojení s opačným protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-254">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="632e0-255">Jednosměrný, neadresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="632e0-255">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="632e0-256">Vazba</span><span class="sxs-lookup"><span data-stu-id="632e0-256">Binding</span></span>

<span data-ttu-id="632e0-257">WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-257">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="632e0-258">WCF používá požadavky HTTP k přenosu všech zpráv od iniciátoru do respondérů a odpovědí HTTP na předávání všech zpráv od odpovídajícího příjemce k iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="632e0-258">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="632e0-259">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-259">CreateSequence Exchange</span></span>

<span data-ttu-id="632e0-260">Iniciátor WCF přenáší zprávu `CreateSequence` bez `Offer` elementu na požadavku HTTP a očekává zprávu `CreateSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-260">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="632e0-261">Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-261">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="632e0-262">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="632e0-262">SequenceAcknowledgement</span></span>

<span data-ttu-id="632e0-263">Iniciátor WCF zpracovává odpověď na odpověď všech zpráv s výjimkou `CreateSequence` zprávy a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="632e0-263">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="632e0-264">Respondér WCF vždy přenáší samostatné potvrzení odezvy HTTP na všechny sekvence a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="632e0-264">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="632e0-265">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-265">CloseSequence Exchange</span></span>

<span data-ttu-id="632e0-266">Iniciátor WCF přenáší zprávu `CloseSequence` na požadavek HTTP a očekává `CreateSequenceResponse` zprávu v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-266">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="632e0-267">Respondér WCF přenáší zprávu `CloseSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-267">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="632e0-268">TerminateSequence – Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-268">TerminateSequence Exchange</span></span>

<span data-ttu-id="632e0-269">Iniciátor WCF přenáší zprávu `TerminateSequence` na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-269">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="632e0-270">Respondér WCF přenáší zprávu `TerminateSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-270">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="632e0-271">Jedním ze způsobů, jak adresovatelné iniciátory</span><span class="sxs-lookup"><span data-stu-id="632e0-271">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="632e0-272">Vazba</span><span class="sxs-lookup"><span data-stu-id="632e0-272">Binding</span></span>

<span data-ttu-id="632e0-273">WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden příchozí a jeden odchozí kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-273">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="632e0-274">WCF používá požadavky HTTP k přenosu všech zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-274">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="632e0-275">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="632e0-275">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="632e0-276">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-276">CreateSequence Exchange</span></span>

<span data-ttu-id="632e0-277">Iniciátor WCF přenáší zprávu `CreateSequence` bez `Offer` elementu v požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-277">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="632e0-278">Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-278">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="632e0-279">Duplexní, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="632e0-279">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="632e0-280">Vazba</span><span class="sxs-lookup"><span data-stu-id="632e0-280">Binding</span></span>

<span data-ttu-id="632e0-281">WCF poskytuje plně asynchronní obousměrný způsob výměny zpráv pomocí dvou sekvencí přes jeden příchozí a jeden odchozí kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-281">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="632e0-282">Tento vzor výměny zpráv je možné kombinovat s `Request/Reply`, `Addressable` vzor výměny zpráv iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="632e0-282">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="632e0-283">WCF používá k přenosu všech zpráv požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-283">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="632e0-284">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="632e0-284">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="632e0-285">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-285">CreateSequence Exchange</span></span>

<span data-ttu-id="632e0-286">Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementu v požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-286">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="632e0-287">Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element, pak vytvoří sekvenci a přenáší zprávu `CreateSequenceResponse` s `Accept` elementem.</span><span class="sxs-lookup"><span data-stu-id="632e0-287">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="632e0-288">Doba platnosti sekvence</span><span class="sxs-lookup"><span data-stu-id="632e0-288">Sequence Lifetime</span></span>

<span data-ttu-id="632e0-289">WCF považuje dvě sekvence za jednu plně duplexní relaci.</span><span class="sxs-lookup"><span data-stu-id="632e0-289">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="632e0-290">Při generování chyby, která chybí jednu sekvenci, služba WCF očekává, že vzdálený koncový bod selže v obou sekvencích.</span><span class="sxs-lookup"><span data-stu-id="632e0-290">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="632e0-291">Při čtení chyby, která chybí jednu sekvenci, chyby WCF obě sekvence.</span><span class="sxs-lookup"><span data-stu-id="632e0-291">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="632e0-292">WCF může zavřít svou odchozí sekvenci a nadále zpracovávat zprávy v její vstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="632e0-292">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="632e0-293">V opačném případě může WCF zpracovat ukončení příchozí sekvence a pokračovat v posílání zpráv ve výstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="632e0-293">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="632e0-294">Požadavek – odpověď a jednosměrný, neadresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="632e0-294">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="632e0-295">Vazba</span><span class="sxs-lookup"><span data-stu-id="632e0-295">Binding</span></span>

<span data-ttu-id="632e0-296">WCF poskytuje jednosměrné a rychlé zprávy s požadavkem na odpověď pomocí dvou sekvencí přes jeden kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-296">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="632e0-297">WCF používá požadavky HTTP k přenosu všech zpráv od iniciátoru do respondérů a odpovědí HTTP na předávání všech zpráv od odpovídajícího příjemce k iniciátoru.</span><span class="sxs-lookup"><span data-stu-id="632e0-297">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="632e0-298">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-298">CreateSequence Exchange</span></span>

<span data-ttu-id="632e0-299">Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementu v požadavku HTTP a očekává zprávu `CreateSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-299">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="632e0-300">Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse`ovou zprávu pomocí elementu `Accept` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-300">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="632e0-301">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="632e0-301">One-way Message</span></span>

<span data-ttu-id="632e0-302">Aby bylo možné provést jednosměrnou výměnu zpráv, iniciátor WCF odešle zprávu sekvence požadavku na požadavek HTTP a obdrží samostatnou `SequenceAcknowledgement`ovou zprávu s odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-302">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="632e0-303">`SequenceAcknowledgement` musí potvrdit přenesenou zprávu.</span><span class="sxs-lookup"><span data-stu-id="632e0-303">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="632e0-304">Respondér WCF může odpovědět na žádost s potvrzením, chybou nebo odpovědí s prázdným tělem a kódem stavu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="632e0-304">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="632e0-305">Dvě jednosměrné zprávy</span><span class="sxs-lookup"><span data-stu-id="632e0-305">Two Way Messages</span></span>

<span data-ttu-id="632e0-306">Aby bylo možné úspěšně dokončit oboustranný protokol výměny zpráv, iniciátor WCF přenese zprávu sekvence požadavku na požadavek HTTP a obdrží zprávu sekvence odpovědi v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-306">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="632e0-307">Odpověď musí mít `SequenceAcknowledgement` potvrzující zprávu sekvence požadavků.</span><span class="sxs-lookup"><span data-stu-id="632e0-307">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="632e0-308">Respondér WCF může odpovědět na požadavek pomocí odpovědi aplikace, chyby nebo odpovědi s prázdným kódem a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="632e0-308">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="632e0-309">Z důvodu přítomnosti jednosměrných zpráv a časování odpovědí na aplikace není pořadové číslo zprávy sekvence požadavku a pořadové číslo zprávy odpovědi nijak korelace.</span><span class="sxs-lookup"><span data-stu-id="632e0-309">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="632e0-310">Opakování odpovědí</span><span class="sxs-lookup"><span data-stu-id="632e0-310">Retrying Replies</span></span>

<span data-ttu-id="632e0-311">WCF spoléhá na korelaci požadavku HTTP na korelaci protokolu výměny zpráv se dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="632e0-311">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="632e0-312">Z tohoto důvodu se iniciátor WCF neukončí opakování zprávy sekvence požadavku při potvrzení zprávy sekvence požadavku, ale místo toho, aby odpověď protokolu HTTP zajišťovala `SequenceAcknowledgement`, odpověď aplikace nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="632e0-312">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="632e0-313">Služby WCF respondér opakuje odpovědi na odpověď HTTP žádosti, na kterou je tato odpověď korelační.</span><span class="sxs-lookup"><span data-stu-id="632e0-313">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="632e0-314">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-314">CloseSequence Exchange</span></span>

<span data-ttu-id="632e0-315">Po přijetí všech zpráv sekvence odpovědí a potvrzení pro všechny jednosměrné zprávy sekvence požadavků iniciátor WCF přenáší `CloseSequence`ovou zprávu pro sekvenci požadavku HTTP a očekává `CloseSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-315">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="632e0-316">Uzavírání sekvence požadavků implicitně uzavře sekvenci odpovědí.</span><span class="sxs-lookup"><span data-stu-id="632e0-316">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="632e0-317">To znamená, že iniciátor WCF zahrnuje konečné `SequenceAcknowledgement` sekvence odpovědí ve zprávě `CloseSequence` a sekvence odpovědí nemá `CloseSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="632e0-317">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="632e0-318">Respondér WCF zajišťuje potvrzení všech odpovědí a přenáší zprávu `CloseSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-318">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="632e0-319">TerminateSequence – Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-319">TerminateSequence Exchange</span></span>

<span data-ttu-id="632e0-320">Po přijetí zprávy `CloseSequenceResponse` odešle iniciátor WCF zprávu `TerminateSequence` pro sekvenci požadavku HTTP a očekává `TerminateSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-320">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="632e0-321">Stejně jako u `CloseSequence` Exchange ukončí sekvence požadavku implicitně ukončení sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="632e0-321">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="632e0-322">To znamená, že iniciátor WCF zahrnuje konečné `SequenceAcknowledgement` sekvence odpovědí ve zprávě `TerminateSequence` a sekvence odpovědí nemá `TerminateSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="632e0-322">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="632e0-323">Respondér WCF přenáší zprávu `TerminateSequenceResponse` v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-323">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="632e0-324">Požadavek nebo odpověď, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="632e0-324">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="632e0-325">Vazba</span><span class="sxs-lookup"><span data-stu-id="632e0-325">Binding</span></span>

<span data-ttu-id="632e0-326">WCF poskytuje vzor výměny zpráv požadavek-odpověď pomocí dvou sekvencí přes jeden příchozí a jeden odchozí kanál HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-326">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="632e0-327">Tento vzor výměny zpráv může být smíšený se vzorem výměny zpráv iniciátora `Duplex, Addressable`.</span><span class="sxs-lookup"><span data-stu-id="632e0-327">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="632e0-328">WCF používá požadavky HTTP k přenosu všech zpráv.</span><span class="sxs-lookup"><span data-stu-id="632e0-328">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="632e0-329">Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="632e0-329">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="632e0-330">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="632e0-330">CreateSequence Exchange</span></span>

<span data-ttu-id="632e0-331">Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementu v požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="632e0-331">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="632e0-332">Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element, potom vytvoří sekvenci a přenáší zprávu `CreateSequenceResponse` s `Accept` elementem.</span><span class="sxs-lookup"><span data-stu-id="632e0-332">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="632e0-333">Korelace žádosti a odpovědi</span><span class="sxs-lookup"><span data-stu-id="632e0-333">Request/Reply Correlation</span></span>

<span data-ttu-id="632e0-334">Následující postup se týká všech korelačních požadavků a odpovědí:</span><span class="sxs-lookup"><span data-stu-id="632e0-334">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="632e0-335">Služba WCF zajišťuje, aby všechny zprávy žádosti o aplikace byly označeny odkazem na `ReplyTo` koncový bod a `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="632e0-335">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="632e0-336">WCF používá odkaz na místní koncový bod jako každou `ReplyTo`zprávy žádosti o aplikaci.</span><span class="sxs-lookup"><span data-stu-id="632e0-336">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="632e0-337">Odkaz na místní koncový bod je `ReplyTo` `CreateSequence` zprávy pro iniciátor a `To` zprávy `CreateSequence` pro respondér.</span><span class="sxs-lookup"><span data-stu-id="632e0-337">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="632e0-338">WCF zajišťuje, aby příchozí zprávy s požadavkem byly označeny `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="632e0-338">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="632e0-339">Služba WCF zajišťuje, aby se identifikátor URI odkazu na koncový bod `ReplyTo` všech zpráv žádostí o aplikace shodoval s odkazem na místní koncový bod definovaným dříve.</span><span class="sxs-lookup"><span data-stu-id="632e0-339">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="632e0-340">WCF zajišťuje, aby všechny odpovědi byly označeny správnými `RelatesTo` a `To` hlavičkymi po `wsa` pravidla korelace požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="632e0-340">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
