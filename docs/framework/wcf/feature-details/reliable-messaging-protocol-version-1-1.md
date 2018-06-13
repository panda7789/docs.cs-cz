---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496955"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="722d1-102">Protokol spolehlivého zasílání zpráv verze 1.1</span><span class="sxs-lookup"><span data-stu-id="722d1-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="722d1-103">Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-ReliableMessaging protokol února 2007 (verze 1.1) nezbytné pro vzájemná spolupráce pomocí přenosového protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="722d1-104">WCF dodržuje specifikaci WS-ReliableMessaging s omezení a objasnění, která jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="722d1-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="722d1-105">Poznámka: verze 1.1 protokolu WS-ReliableMessaging je implementováno začínající [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="722d1-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="722d1-106">Protokolu WS-ReliableMessaging. února 2007 protokol je implementována ve WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="722d1-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="722d1-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="722d1-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="722d1-108">Iniciátor: Klienta, která zahájí vytváření sekvence WS-spolehlivé zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="722d1-109">Respondér: Služba, která přijímá požadavky je iniciátor.</span><span class="sxs-lookup"><span data-stu-id="722d1-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="722d1-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="722d1-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="722d1-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="722d1-111">Prefix</span></span>|<span data-ttu-id="722d1-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="722d1-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="722d1-113">Správce systémových prostředků</span><span class="sxs-lookup"><span data-stu-id="722d1-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="722d1-114">netrm</span><span class="sxs-lookup"><span data-stu-id="722d1-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="722d1-115">s</span><span class="sxs-lookup"><span data-stu-id="722d1-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="722d1-116">wsa</span><span class="sxs-lookup"><span data-stu-id="722d1-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="722d1-117">wsse</span><span class="sxs-lookup"><span data-stu-id="722d1-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="722d1-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="722d1-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="722d1-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="722d1-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="722d1-120">WSP</span><span class="sxs-lookup"><span data-stu-id="722d1-120">wsp</span></span>|<span data-ttu-id="722d1-121">(WS-Policy 1.2 nebo WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="722d1-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="722d1-122">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="722d1-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="722d1-123">Vytvoření pořadí</span><span class="sxs-lookup"><span data-stu-id="722d1-123">Sequence Creation</span></span>  
 <span data-ttu-id="722d1-124">Implementuje WCF `CreateSequence` a `CreateSequenceResponse` pořadí zprávy a pokuste se vytvořit spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="722d1-125">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="722d1-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="722d1-126">B1101: Iniciátoru WCF používá koncový bod odkaz na stejné jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="722d1-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="722d1-127">R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zprávy musí mít hodnoty adres s identické řetězcové vyjádření tak, že budou odpovídat octet-wise.</span><span class="sxs-lookup"><span data-stu-id="722d1-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="722d1-128">WCF respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` odkazy koncového bodu jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="722d1-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="722d1-129">R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` odkazy na koncový bod v `CreateSequence` zprávy musí mít stejnou sadu parametrů odkaz.</span><span class="sxs-lookup"><span data-stu-id="722d1-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="722d1-130">WCF nevynucuje, ale předpokládá, že odkaz parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkaz z `ReplyTo` reference koncového bodu pro konverzace pořadí zprávy a potvrzení.</span><span class="sxs-lookup"><span data-stu-id="722d1-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="722d1-131">B1104: Iniciátoru WCF negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="722d1-132">B1105: Při přístupu k `CreateSequence` používá respondér WCF zpráva, `Expires` hodnotu `CreateSequence` element jako `Expires` hodnotu ve `CreateSequenceResponse` element.</span><span class="sxs-lookup"><span data-stu-id="722d1-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="722d1-133">Jinak respondér WCF přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="722d1-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="722d1-134">B1106: Při přístupu k `CreateSequenceResponse` zpráva iniciátoru WCF načte volitelné `Expires` hodnotu, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="722d1-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="722d1-135">B1107: Iniciátor WCF a respondér vždy generovat nepovinný `IncompleteSequenceBehavior` element v `CreateSequence/Offer` a `CreateSequenceResponse` elementy.</span><span class="sxs-lookup"><span data-stu-id="722d1-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="722d1-136">B1108: WCF se používá pouze `DiscardFollowingFirstGap` a `NoDiscard` hodnoty ve `IncompleteSequenceBehavior` elementu.</span><span class="sxs-lookup"><span data-stu-id="722d1-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="722d1-137">Využívá WS-ReliableMessaging `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.</span><span class="sxs-lookup"><span data-stu-id="722d1-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="722d1-138">B1109: Pokud `CreateSequence` obsahuje `Offer` elementu jedním ze způsobů respondér WCF odmítne nabízený pořadí podle reagovat se `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="722d1-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="722d1-139">B1110: Pokud spolehlivého zasílání zpráv respondér odmítne nabízený pořadí, závady iniciátoru WCF nově vytvořeným pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="722d1-140">B1111: Pokud `CreateSequence` neobsahuje `Offer` elementu obousměrný respondér WCF odmítne nabízený pořadí podle reagovat se `CreateSequenceRefused` selhání.</span><span class="sxs-lookup"><span data-stu-id="722d1-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="722d1-141">R1112: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.</span><span class="sxs-lookup"><span data-stu-id="722d1-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="722d1-142">R1113: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, musí se poslat všechny zprávy na obou pořadí předávaných z iniciátoru k příjemce, na odkaz na stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="722d1-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="722d1-143">WCF pomocí protokolu WS-ReliableMessaging zřizuje spolehlivé relace mezi iniciátoru a odpovídající počítač.</span><span class="sxs-lookup"><span data-stu-id="722d1-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="722d1-144">Implementace WCF WS-ReliableMessaging poskytuje spolehlivé relace jednosměrné, požadavku a odpovědi a plně duplexní režim vzory pro zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="722d1-145">WS-ReliableMessaging `Offer` mechanismus na `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dva korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body.</span><span class="sxs-lookup"><span data-stu-id="722d1-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="722d1-146">Protože WCF poskytuje záruku zabezpečení relace, včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné strany na stejný cíl.</span><span class="sxs-lookup"><span data-stu-id="722d1-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="722d1-147">To také umožňuje "Prasátko zálohování" pořadí potvrzení u zpráv s aplikací.</span><span class="sxs-lookup"><span data-stu-id="722d1-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="722d1-148">Proto platí omezení R1102, R1112 a R1113 pro WCF.</span><span class="sxs-lookup"><span data-stu-id="722d1-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="722d1-149">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="722d1-150">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="722d1-151">Zavřením sekvenci</span><span class="sxs-lookup"><span data-stu-id="722d1-151">Closing a Sequence</span></span>  
 <span data-ttu-id="722d1-152">Používá WCF `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spouštěná zdroje.</span><span class="sxs-lookup"><span data-stu-id="722d1-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="722d1-153">Spolehlivé zasílání zpráv WCF cílové neiniciuje vypnutí a zdroji WCF spolehlivé zasílání zpráv nepodporuje vypnutí spolehlivé zasílání zpráv spouštěná na cílový.</span><span class="sxs-lookup"><span data-stu-id="722d1-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="722d1-154">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="722d1-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="722d1-155">B1201: Zdroji spolehlivé zasílání zpráv WCF vždycky odešle `CloseSequence` zpráva vypnout sekvenci.</span><span class="sxs-lookup"><span data-stu-id="722d1-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="722d1-156">B1202: Zdroji spolehlivé zasílání zpráv čeká na potvrzení plný rozsah pořadí zprávy před odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="722d1-157">B1203: Zdroji spolehlivé zasílání zpráv vždy obsahuje volitelné `LastMsgNumber` element Pokud sekvenci neobsahuje zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="722d1-158">R1204: Cílový spolehlivé zasílání zpráv nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="722d1-159">B1205: po přijetí `CloseSequence` zprávu, zdroji WCF spolehlivé zasílání zpráv považuje pořadí nekompletní a odešle chybu.</span><span class="sxs-lookup"><span data-stu-id="722d1-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="722d1-160">Příklad `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-160">An example of a `CloseSequence` message.</span></span>  
  
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
Example CloseSequenceResponse message:  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="722d1-161">Pořadí ukončení</span><span class="sxs-lookup"><span data-stu-id="722d1-161">Sequence Termination</span></span>  
 <span data-ttu-id="722d1-162">WCF primárně používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` metody handshake.</span><span class="sxs-lookup"><span data-stu-id="722d1-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="722d1-163">Spolehlivé zasílání zpráv WCF cílové neiniciuje ukončení a zdroji spolehlivé zasílání zpráv nepodporuje ukončení spolehlivé zasílání zpráv spouštěná na cílový.</span><span class="sxs-lookup"><span data-stu-id="722d1-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="722d1-164">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="722d1-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="722d1-165">B1301: Iniciátoru WCF pouze odešle `TerminateSequence` zpráva po úspěšném dokončení `CloseSequence/CloseSequenceResponse` metody handshake.</span><span class="sxs-lookup"><span data-stu-id="722d1-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="722d1-166">R1302: WCF ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zprávy pro daného pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="722d1-167">To znamená, že `LastMsgNumber` buď není přítomen na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je přítomen a na všechny stejné `CloseSequence` a `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="722d1-168">B1303: Při přijímání `TerminateSequence` zprávy po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="722d1-169">Protože má zdroj spolehlivé zasílání zpráv konečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv zná bez nepochybně, že je pořadí skončí a uvolní prostředky okamžitě.</span><span class="sxs-lookup"><span data-stu-id="722d1-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="722d1-170">B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové WCF spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="722d1-171">Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v pořadí, cílový spolehlivé zasílání zpráv čeká na dobu zadané cílové aplikace před opětovného získání prostředků, aby klient riziko pro příjem konečné potvrzení.</span><span class="sxs-lookup"><span data-stu-id="722d1-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="722d1-172">Jinak cílové spolehlivé zasílání zpráv okamžitě získá prostředky a označuje cílové aplikace, že je pořadí končí nejistých zobrazením `Faulted` událostí.</span><span class="sxs-lookup"><span data-stu-id="722d1-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="722d1-173">Příklad `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-173">An example of a `TerminateSequence` message.</span></span>  
  
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
Example TerminateSequenceResponse message:  
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
  
### <a name="sequences"></a><span data-ttu-id="722d1-174">Sekvence</span><span class="sxs-lookup"><span data-stu-id="722d1-174">Sequences</span></span>  
 <span data-ttu-id="722d1-175">Následuje seznam omezení, která se týkají pořadí:</span><span class="sxs-lookup"><span data-stu-id="722d1-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="722d1-176">Generuje B1401:WCF a přístupů pořadí čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="722d1-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="722d1-177">Příklad `Sequence` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="722d1-178">Žádost o potvrzení</span><span class="sxs-lookup"><span data-stu-id="722d1-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="722d1-179">Používá WCF `AckRequested` záhlaví jako mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="722d1-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="722d1-180">Příklad `AckRequested` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="722d1-181">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="722d1-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="722d1-182">WCF používá mechanismus "Prasátko zpětným" pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="722d1-183">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="722d1-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="722d1-184">R1601: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="722d1-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="722d1-185">Vzdálený koncový bod musí být schopni přistupovat zařazována složená `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="722d1-186">B1602: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="722d1-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="722d1-187">WCF ověří, že každý `Nack` elementu obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="722d1-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="722d1-188">Příklad `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="722d1-189">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="722d1-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="722d1-190">Následuje seznam omezení, které se vztahují na WCF implementaci protokolu WS-ReliableMessaging chyb.</span><span class="sxs-lookup"><span data-stu-id="722d1-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="722d1-191">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="722d1-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="722d1-192">B1701: WCF negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="722d1-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="722d1-193">B1702: Přes SOAP 1.2, pokud koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF generuje vnořený `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="722d1-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="722d1-194">Adresování WS chyb</span><span class="sxs-lookup"><span data-stu-id="722d1-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="722d1-195">Protože WS-ReliableMessaging používá WS-Addressing, implementace WCF WS-ReliableMessaging může generovat a přenášet WS-Addressing chyb.</span><span class="sxs-lookup"><span data-stu-id="722d1-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="722d1-196">Tato část se zabývá WS-Addressing chyb, které WCF explicitně generuje a odesílá ve vrstvě protokolu WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="722d1-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="722d1-197">B1801:WCF generuje a odesílá `Message Addressing Header Required` poruch, když je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="722d1-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="722d1-198">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="722d1-199">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="722d1-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="722d1-201">B1802:WCF generuje a odesílá `Endpoint Unavailable` selhání označíte, neexistuje žádný koncový bod naslouchání, který může zpracovat pořadí podle zkoumání adresování hlavičky v `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="722d1-202">Protokol složení</span><span class="sxs-lookup"><span data-stu-id="722d1-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="722d1-203">Složení s adresováním WS</span><span class="sxs-lookup"><span data-stu-id="722d1-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="722d1-204">Podporuje dvě verze WS-Addressing WCF: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="722d1-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="722d1-205">Při zmínkami specifikace protokolu WS-ReliableMessaging pouze WS-Addressing 2004/08, se neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="722d1-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="722d1-206">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="722d1-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="722d1-207">R2101: Obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="722d1-208">R2102: Jedné verzi protokolu WS-Addressing musí použít v rámci daného pořadí WS-ReliableMessaging nebo pár konverzace pořadí korelační pomocí `Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="722d1-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="722d1-209">Složení protokol SOAP</span><span class="sxs-lookup"><span data-stu-id="722d1-209">Composition with SOAP</span></span>  
 <span data-ttu-id="722d1-210">WCF podporuje použití SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="722d1-211">Složení s WS-zabezpečení a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="722d1-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="722d1-212">WCF poskytuje ochranu WS-ReliableMessaging pořadí pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="722d1-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="722d1-213">Protokol WS-ReliableMessaging 1.1, WS-zabezpečení 1.1 a protokol WS-zabezpečené konverzace 1.3 musí použít společně.</span><span class="sxs-lookup"><span data-stu-id="722d1-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="722d1-214">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="722d1-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="722d1-215">R2301: K ochraně integrity pořadí WS-ReliableMessaging kromě integrity a důvěrnosti jednotlivých zpráv, WCF vyžaduje, aby se musí použít WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="722d1-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="722d1-216">R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením WS-ReliableMessaging sequence(s).</span><span class="sxs-lookup"><span data-stu-id="722d1-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="722d1-217">R2303: Pokud WS-ReliableMessaging pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="722d1-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="722d1-218">B2304:WS-ReliableMessaging pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="722d1-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="722d1-219">R2305: Když skládá s WS zabezpečené konverzace, respondér WCF vyžaduje, aby `CreateSequence` obsahovat zprávy `wsse:SecurityTokenReference` element a `wsrm:UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="722d1-220">Příklad `UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="722d1-221">Složení s relací SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="722d1-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="722d1-222">WCF nepodporuje složení s protokolem SSL/TLS relace:</span><span class="sxs-lookup"><span data-stu-id="722d1-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="722d1-223">B2401: WCF negeneruje `wsrm:UsesSequenceSSL` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="722d1-224">R2402: Spolehlivého zasílání zpráv iniciátor nesmí odesílat `CreateSequence` zpráv s `wsrm:UsesSequenceSSL` hlavičky k respondér WCF.</span><span class="sxs-lookup"><span data-stu-id="722d1-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="722d1-225">Složení zásadám WS</span><span class="sxs-lookup"><span data-stu-id="722d1-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="722d1-226">WCF podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="722d1-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="722d1-227">WS-ReliableMessaging WS-výraz zásad</span><span class="sxs-lookup"><span data-stu-id="722d1-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="722d1-228">WCF pomocí protokolu WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` k popisu možnosti koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="722d1-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="722d1-229">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="722d1-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="722d1-230">B3001: Připojí WCF `wsrmn:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="722d1-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="722d1-231">WCF podporuje obě přílohy do `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="722d1-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="722d1-232">B3002: WCF nikdy vygeneruje `wsp:Optional` značky.</span><span class="sxs-lookup"><span data-stu-id="722d1-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="722d1-233">B3003: Při přístupu k `wsrmp:RMAssertion` Assertion WS-Policy, ignoruje WCF `wsp:Optional` značky a zpracovává zásady WS-RM jako povinné.</span><span class="sxs-lookup"><span data-stu-id="722d1-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="722d1-234">R3004: Protože WCF není tvoří s relací SSL/TLS, WCF nepřijímá zásady, které určují `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="722d1-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="722d1-235">B3005: WCF vždy vygeneruje `wsrmp:DeliveryAssurance` elementu.</span><span class="sxs-lookup"><span data-stu-id="722d1-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="722d1-236">B3006: WCF vždy určuje `wsrmp:ExactlyOnce` záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="722d1-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="722d1-237">B3007: WCF generuje a čte následující vlastnosti protokolu WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad je na WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="722d1-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="722d1-238">Příklad `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="722d1-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="722d1-239">Rozšíření protokolu WS-ReliableMessaging toku řízení</span><span class="sxs-lookup"><span data-stu-id="722d1-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="722d1-240">WCF využívá rozšiřitelnost protokolu WS-ReliableMessaging volitelné další náročnější řídit tok zpráv pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="722d1-241">Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``boolean` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="722d1-241">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="722d1-242">Následuje seznam omezení, která se týkají WCF:</span><span class="sxs-lookup"><span data-stu-id="722d1-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="722d1-243">B4001: WCF generuje Pokud je povoleno spolehlivého zasílání zpráv řízení toku, `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="722d1-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="722d1-244">B4002: I když je povolena spolehlivého zasílání zpráv řízení toku, WCF nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="722d1-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="722d1-245">B4003: Používá WCF spolehlivého zasílání zpráv cílové `netrm:BufferRemaining` indikující, kolik nové zprávy můžete ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="722d1-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="722d1-246">Je povolený B4004:when spolehlivého zasílání zpráv řízení toku, zdroji WCF spolehlivého zasílání zpráv používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.</span><span class="sxs-lookup"><span data-stu-id="722d1-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="722d1-247">B4005: Generuje WCF `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="722d1-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="722d1-248">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="722d1-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="722d1-249">Tato část popisuje WCF na chování při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="722d1-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="722d1-250">Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:</span><span class="sxs-lookup"><span data-stu-id="722d1-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="722d1-251">Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv na iniciátoru pouze na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="722d1-252">Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.</span><span class="sxs-lookup"><span data-stu-id="722d1-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="722d1-253">Jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="722d1-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="722d1-254">Vazba</span><span class="sxs-lookup"><span data-stu-id="722d1-254">Binding</span></span>  
 <span data-ttu-id="722d1-255">WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="722d1-256">WCF využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="722d1-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-258">Přenáší iniciátoru WCF `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="722d1-259">Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="722d1-260">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="722d1-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="722d1-261">Iniciátor WCF zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="722d1-262">WCF respondér vždy přenáší samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="722d1-263">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="722d1-264">Přenáší iniciátoru WCF `CloseSequence` zpráva na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="722d1-265">Přenáší respondér WCF `CloseSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="722d1-266">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-267">Přenáší iniciátoru WCF `TerminateSequence` zpráva na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="722d1-268">Přenáší respondér WCF `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="722d1-269">Jedním ze způsobů, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="722d1-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="722d1-270">Vazba</span><span class="sxs-lookup"><span data-stu-id="722d1-270">Binding</span></span>  
 <span data-ttu-id="722d1-271">Poskytuje WCF pomocí jednoho pořadí přes jeden vzorce výměny zpráv jednosměrný příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="722d1-272">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="722d1-273">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="722d1-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="722d1-274">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-275">Přenáší iniciátoru WCF `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="722d1-276">Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="722d1-277">Duplexní, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="722d1-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="722d1-278">Vazba</span><span class="sxs-lookup"><span data-stu-id="722d1-278">Binding</span></span>  
 <span data-ttu-id="722d1-279">Poskytuje WCF pomocí dvou vzorce výměny zpráv plně asynchronní, obousměrný pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="722d1-280">Tato vzorce výměny zpráv můžete kombinovat s `Request/Reply`, `Addressable` vzorce výměny zpráv iniciátor omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="722d1-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="722d1-281">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="722d1-282">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="722d1-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="722d1-283">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-284">Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="722d1-285">WCF respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.</span><span class="sxs-lookup"><span data-stu-id="722d1-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="722d1-286">Doba platnosti pořadí</span><span class="sxs-lookup"><span data-stu-id="722d1-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="722d1-287">WCF považuje za jednu relaci plně duplexní dvě pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="722d1-288">Při generování chybu, která závady jedním sekvenčním, WCF očekává, že vzdálený koncový bod pro poruch obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="722d1-289">Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="722d1-290">WCF můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="722d1-291">Naopak WCF můžete zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="722d1-292">Požadavek odpověď a jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="722d1-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="722d1-293">Vazba</span><span class="sxs-lookup"><span data-stu-id="722d1-293">Binding</span></span>  
 <span data-ttu-id="722d1-294">Poskytuje jednosměrný WCF a vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="722d1-295">WCF využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="722d1-296">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-297">Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="722d1-298">Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="722d1-299">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="722d1-299">One-way Message</span></span>  
 <span data-ttu-id="722d1-300">Úspěšné dokončení jednosměrný zpráva systému exchange, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="722d1-301">`SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="722d1-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="722d1-302">Respondér WCF může odpovědět na požadavek potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="722d1-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="722d1-303">Dvě způsob zprávy</span><span class="sxs-lookup"><span data-stu-id="722d1-303">Two Way Messages</span></span>  
 <span data-ttu-id="722d1-304">Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="722d1-305">Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.</span><span class="sxs-lookup"><span data-stu-id="722d1-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="722d1-306">Respondér WCF může odpovědět na požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="722d1-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="722d1-307">Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="722d1-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="722d1-308">Opakováním odpovědi</span><span class="sxs-lookup"><span data-stu-id="722d1-308">Retrying Replies</span></span>  
 <span data-ttu-id="722d1-309">WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="722d1-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="722d1-310">Z toho důvodu iniciátoru WCF nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale spíš, když představuje odpověď HTTP `SequenceAcknowledgement`, aplikace a odpovědi nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="722d1-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="722d1-311">WCF respondér opakuje odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpovědi.</span><span class="sxs-lookup"><span data-stu-id="722d1-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="722d1-312">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="722d1-313">Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy s jedním ze způsobů požadavky pořadí, přenáší iniciátoru WCF `CloseSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `CloseSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="722d1-314">Zavřením sekvence požadavku implicitně zavře odpověď pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="722d1-315">To znamená, že iniciátoru WCF zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `CloseSequence` zprávu a pořadí odpovědi nemá `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="722d1-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="722d1-316">WCF respondér zajistí všechny odpovědi jsou potvrzené a odesílá `CloseSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="722d1-317">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-318">Po přijetí `CloseSequenceResponse` odesílá zprávy iniciátoru WCF `TerminateSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `TerminateSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="722d1-319">Podobně jako `CloseSequence` systému exchange, ukončení pořadí žádost implicitně ukončí odpověď pořadí.</span><span class="sxs-lookup"><span data-stu-id="722d1-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="722d1-320">To znamená, že iniciátoru WCF zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `TerminateSequence` zprávu a pořadí odpovědi nemá `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="722d1-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="722d1-321">Přenáší respondér WCF `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="722d1-322">Požadavek nebo odpověď, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="722d1-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="722d1-323">Vazba</span><span class="sxs-lookup"><span data-stu-id="722d1-323">Binding</span></span>  
 <span data-ttu-id="722d1-324">WCF poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="722d1-325">Tato vzorce výměny zpráv můžete kombinovat s `Duplex, Addressable` vzorce výměny zpráv iniciátor omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="722d1-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="722d1-326">WCF využívá k přenosu všechny zprávy požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="722d1-327">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="722d1-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="722d1-328">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="722d1-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="722d1-329">Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="722d1-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="722d1-330">Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element potom vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.</span><span class="sxs-lookup"><span data-stu-id="722d1-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="722d1-331">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="722d1-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="722d1-332">Následující část se vztahuje na všechny korelační požadavky a odpovědi:</span><span class="sxs-lookup"><span data-stu-id="722d1-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="722d1-333">WCF zajistí všechny opatřeny zprávy žádost o aplikaci `ReplyTo` reference koncového bodu a `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="722d1-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="722d1-334">WCF platí odkaz na místní koncový bod jako každou zprávu žádosti o aplikace `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="722d1-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="722d1-335">Odkaz na místní koncový bod je `CreateSequence` zprávy `ReplyTo` pro iniciátory a `CreateSequence` zprávy `To` pro respondér.</span><span class="sxs-lookup"><span data-stu-id="722d1-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="722d1-336">WCF zajistí, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="722d1-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="722d1-337">Zajišťuje WCF `ReplyTo` identifikátor URI koncového bodu odkaz všechny zprávy požadavku aplikace odkaz na místní koncový bod shodovat s dříve definovaným.</span><span class="sxs-lookup"><span data-stu-id="722d1-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="722d1-338">WCF zajistí, že všechny odpovědi berte správný `RelatesTo` a `To` hlavičky následující `wsa` pravidla korelace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="722d1-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
