---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933988"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="db11d-102">Protokol spolehlivého zasílání zpráv verze 1.1</span><span class="sxs-lookup"><span data-stu-id="db11d-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="db11d-103">Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-ReliableMessaging protokol února 2007 (verze 1.1) nezbytné pro spolupráci pomocí přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="db11d-104">WCF dodržuje specifikaci WS-ReliableMessaging s omezením a vyjasnění je vysvětleno v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="db11d-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="db11d-105">Všimněte si, že se implementuje protokol WS-ReliableMessaging verze 1.1 počínaje [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db11d-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="db11d-106">WS-ReliableMessaging února 2007 protokol je implementován ve službě WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="db11d-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="db11d-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="db11d-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="db11d-108">Iniciátor: Klient, který zahájí vytváření pořadí zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="db11d-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="db11d-109">Respondér: Služba, která bude přijímat žádosti je iniciátor.</span><span class="sxs-lookup"><span data-stu-id="db11d-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="db11d-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="db11d-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="db11d-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="db11d-111">Prefix</span></span>|<span data-ttu-id="db11d-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="db11d-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="db11d-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="db11d-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="db11d-114">netrm</span><span class="sxs-lookup"><span data-stu-id="db11d-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="db11d-115">s</span><span class="sxs-lookup"><span data-stu-id="db11d-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="db11d-116">wsa</span><span class="sxs-lookup"><span data-stu-id="db11d-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="db11d-117">wsse</span><span class="sxs-lookup"><span data-stu-id="db11d-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="db11d-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="db11d-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="db11d-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="db11d-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="db11d-120">wsp</span><span class="sxs-lookup"><span data-stu-id="db11d-120">wsp</span></span>|<span data-ttu-id="db11d-121">(WS-Policy 1.2 nebo WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="db11d-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="db11d-122">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="db11d-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="db11d-123">Vytváření pořadí</span><span class="sxs-lookup"><span data-stu-id="db11d-123">Sequence Creation</span></span>  
 <span data-ttu-id="db11d-124">Implementuje WCF `CreateSequence` a `CreateSequenceResponse` pořadí zpráv k navázání spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="db11d-125">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="db11d-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="db11d-126">B1101: Iniciátor WCF používá stejný koncový bod odkaz jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="db11d-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="db11d-127">R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zpráva musí mít identickou řetězcovou reprezentaci hodnoty adres tak, aby odpovídaly octet-wise.</span><span class="sxs-lookup"><span data-stu-id="db11d-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="db11d-128">WCF respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` Reference koncového bodu jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="db11d-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="db11d-129">R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zpráva by měla mít stejnou sadu parametrů odkazu.</span><span class="sxs-lookup"><span data-stu-id="db11d-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="db11d-130">WCF nevynucuje, ale předpokládá velikost tento odkaz parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkazů z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="db11d-131">B1104: Iniciátor WCF negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="db11d-132">B1105: Při přístupu k `CreateSequence` zprávy WCF respondér používá `Expires` hodnota v `CreateSequence` prvek jako `Expires` hodnota v `CreateSequenceResponse` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="db11d-133">V opačném případě respondér WCF přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db11d-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="db11d-134">B1106: Při přístupu k `CreateSequenceResponse` zprávu, iniciátor WCF načte volitelný `Expires` hodnotu, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="db11d-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="db11d-135">B1107: WCF iniciátor i respondér vždy generovat nepovinný `IncompleteSequenceBehavior` prvek `CreateSequence/Offer` a `CreateSequenceResponse` elementy.</span><span class="sxs-lookup"><span data-stu-id="db11d-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="db11d-136">B1108: WCF použije pouze `DiscardFollowingFirstGap` a `NoDiscard` hodnoty v `IncompleteSequenceBehavior` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="db11d-137">Využívá WS-ReliableMessaging `Offer` mechanismus k navázání dvou komunikaci korelační sekvence, které tvoří relace.</span><span class="sxs-lookup"><span data-stu-id="db11d-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="db11d-138">B1109: Pokud `CreateSequence` obsahuje `Offer` elementu jedním ze způsobů respondér WCF odmítne nabízený pořadí reakcí s `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="db11d-139">B1110: Pokud spolehlivé zasílání zpráv respondér odmítne nabízený pořadí, iniciátor WCF chyb nově zavedených pořadí.</span><span class="sxs-lookup"><span data-stu-id="db11d-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="db11d-140">B1111: Pokud `CreateSequence` neobsahuje `Offer` prvku obousměrný respondér WCF odmítne nabízený pořadí reakcí s `CreateSequenceRefused` selhání.</span><span class="sxs-lookup"><span data-stu-id="db11d-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="db11d-141">R1112: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.</span><span class="sxs-lookup"><span data-stu-id="db11d-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="db11d-142">R1113: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, všechny zprávy v obou pořadí z iniciátoru tok na straně odpovídajícího se musí odeslat na stejné reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="db11d-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="db11d-143">WCF WS-ReliableMessaging používá k navázání spolehlivé relace mezi iniciátorem a příjemce.</span><span class="sxs-lookup"><span data-stu-id="db11d-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="db11d-144">Implementace WCF WS-ReliableMessaging poskytuje spolehlivé relace pro jednosměrný požadavek odpověď a plně duplexní způsobů zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="db11d-145">WS-ReliableMessaging `Offer` mechanismus `CreateSequence` a `CreateSequenceResponse` vám umožní navázání dvou korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="db11d-146">Protože WCF poskytuje záruku zabezpečení pro relaci, včetně začátku do konce ochranu integrity relace, je potřeba Ujistěte se, že zprávy určené pro stejný stranu přejít na stejný cíl.</span><span class="sxs-lookup"><span data-stu-id="db11d-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="db11d-147">Díky tomu také "Prasátko zálohováním" pořadí potvrzení na zprávy aplikace.</span><span class="sxs-lookup"><span data-stu-id="db11d-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="db11d-148">Proto platí omezení R1102 R1112 a R1113 pro WCF.</span><span class="sxs-lookup"><span data-stu-id="db11d-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="db11d-149">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="db11d-150">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="db11d-151">Zavření sekvence</span><span class="sxs-lookup"><span data-stu-id="db11d-151">Closing a Sequence</span></span>  
 <span data-ttu-id="db11d-152">Používá WCF `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spuštěno zdrojem.</span><span class="sxs-lookup"><span data-stu-id="db11d-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="db11d-153">Spolehlivé zasílání zpráv WCF cílové nespustí, vypnutí a zdroj spolehlivé zasílání zpráv WCF nepodporuje vypnutí iniciované cílové spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="db11d-154">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="db11d-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="db11d-155">B1201: Spolehlivé zasílání zpráv WCF zdroje vždy posílá `CloseSequence` zprávu ukončení sekvence.</span><span class="sxs-lookup"><span data-stu-id="db11d-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="db11d-156">B1202: Zdroj spolehlivé zasílání zpráv čeká na potvrzení z široké spektrum pořadí zprávy před odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="db11d-157">B1203: Spolehlivé zasílání zpráv zdroj vždy obsahuje volitelný `LastMsgNumber` element není-li posloupnost neobsahuje zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="db11d-158">R1204: Spolehlivé zasílání zpráv cílové nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="db11d-159">B1205: Po přijetí `CloseSequence` zprávy, zdroje spolehlivé zasílání zpráv WCF považuje za neúplné sekvence a odesílá chybu.</span><span class="sxs-lookup"><span data-stu-id="db11d-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="db11d-160">Příklad `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-160">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="db11d-161">Ukončení sekvence</span><span class="sxs-lookup"><span data-stu-id="db11d-161">Sequence Termination</span></span>  
 <span data-ttu-id="db11d-162">WCF primárně používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="db11d-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="db11d-163">Spolehlivé zasílání zpráv WCF cílové nespustí, ukončení a spolehlivé zasílání zpráv zdroj nepodporuje ukončení iniciované cílové spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="db11d-164">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="db11d-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="db11d-165">B1301: Iniciátor WCF odesílá pouze `TerminateSequence` po úspěšném dokončení se zobrazí zpráva `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="db11d-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="db11d-166">R1302: WCF ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zpráv pro dané sekvence.</span><span class="sxs-lookup"><span data-stu-id="db11d-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="db11d-167">To znamená, že `LastMsgNumber` buď není k dispozici na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je k dispozici a stejné ve všech `CloseSequence` a `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="db11d-168">B1303: Při přijímání `TerminateSequence` zpráv po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="db11d-169">Vzhledem k tomu, že zdroj spolehlivé zasílání zpráv má závěrečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv ví bez nepochybně, že sekvence se ukončí a okamžitě uvolní prostředky.</span><span class="sxs-lookup"><span data-stu-id="db11d-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="db11d-170">B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové WCF spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="db11d-171">Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v sekvenci, spolehlivé zasílání zpráv místo určení čeká, dobu zadané cílové aplikace před uvolní prostředky, by klientovi umožňoval riziko pro příjem závěrečné potvrzení.</span><span class="sxs-lookup"><span data-stu-id="db11d-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="db11d-172">V opačném případě cílové spolehlivé zasílání zpráv okamžitě uvolní prostředky a označuje cílové aplikace, že sekvence končí nejisté vyvoláním `Faulted` událostí.</span><span class="sxs-lookup"><span data-stu-id="db11d-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="db11d-173">Příklad `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-173">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="db11d-174">Sekvence</span><span class="sxs-lookup"><span data-stu-id="db11d-174">Sequences</span></span>  
 <span data-ttu-id="db11d-175">Následuje seznam omezení, které se vztahují na pořadí:</span><span class="sxs-lookup"><span data-stu-id="db11d-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="db11d-176">Generuje B1401:WCF a přístupy pořadí čísel vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="db11d-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="db11d-177">Příklad `Sequence` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="db11d-178">Žádost o potvrzení</span><span class="sxs-lookup"><span data-stu-id="db11d-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="db11d-179">Používá WCF `AckRequested` záhlaví jako vhodný mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="db11d-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="db11d-180">Příklad `AckRequested` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="db11d-181">Třída SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="db11d-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="db11d-182">WCF používá mechanismus "Prasátko zpět" pro potvrzení pořadí součástí zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="db11d-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="db11d-183">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="db11d-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="db11d-184">R1601: Po dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví mohou být zahrnuty do jakékoli aplikace zprávy odesílané informace zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="db11d-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="db11d-185">Vzdálený koncový bod musí být schopen získat přístup zařazována složená `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="db11d-186">B1602: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="db11d-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="db11d-187">WCF ověří, že každý `Nack` element obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="db11d-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="db11d-188">Příklad `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="db11d-189">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="db11d-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="db11d-190">Následuje seznam omezení, které se vztahují k implementaci WCF WS-ReliableMessaging chyb.</span><span class="sxs-lookup"><span data-stu-id="db11d-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="db11d-191">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="db11d-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="db11d-192">B1701: WCF negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="db11d-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="db11d-193">B1702: Přes protokol SOAP 1.2, když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje vnořený `CreateSequenceRefused` selhání podřízeného, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="db11d-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="db11d-194">WS-Addressing chyb</span><span class="sxs-lookup"><span data-stu-id="db11d-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="db11d-195">Vzhledem k tomu WS-ReliableMessaging používá WS-Addressing, může provádění WCF WS-ReliableMessaging generování a přenosu WS-Addressing chyb.</span><span class="sxs-lookup"><span data-stu-id="db11d-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="db11d-196">Tato část zahrnuje chyby WS-Addressing, WCF explicitně generuje a odesílá ve vrstvě WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="db11d-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="db11d-197">B1801:WCF generuje a přenáší `Message Addressing Header Required` selhání, když je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="db11d-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="db11d-198">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="db11d-199">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="db11d-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="db11d-201">B1802:WCF generuje a přenáší `Endpoint Unavailable` selhání k označení, neexistuje žádný koncový bod, který dokáže zpracovat pořadí založené na posouzení adresování záhlaví ve `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="db11d-202">Protokol sestavení</span><span class="sxs-lookup"><span data-stu-id="db11d-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="db11d-203">Kompozice s WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="db11d-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="db11d-204">WCF podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1.0 doporučení [WS-ADDR – CORE] a [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="db11d-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="db11d-205">Zatímco zmínky WS-ReliableMessaging specifikace WS-Addressing 2004/08 pouze neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="db11d-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="db11d-206">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="db11d-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="db11d-207">R2101: WS-Addressing 2004/08 a WS-Addressing 1.0 je možné pomocí zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="db11d-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="db11d-208">R2102: Jednu verzi elementu WS-Addressing musí využívat v rámci dané sekvence WS-ReliableMessaging nebo dvojice posloupností první korelační pomocí `Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="db11d-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="db11d-209">Složení u protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="db11d-209">Composition with SOAP</span></span>  
 <span data-ttu-id="db11d-210">WCF podporuje použití SOAP 1.1 a SOAP 1.2 zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="db11d-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="db11d-211">Kompozice s WS-Security a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="db11d-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="db11d-212">WCF poskytuje ochranu pro WS-ReliableMessaging pořadí pomocí zabezpečeného přenosu (HTTPS), kompozice s WS-Security a skládání s WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="db11d-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="db11d-213">Protokol WS-ReliableMessaging 1.1, WS-Security 1.1 a protokol WS-Secure 1.3 konverzace musí použít společně.</span><span class="sxs-lookup"><span data-stu-id="db11d-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="db11d-214">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="db11d-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="db11d-215">R2301: Pro ochranu integrity WS-ReliableMessaging pořadí kromě integritu a důvěrnost jednotlivé zprávy, WCF vyžaduje, že musí použít WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="db11d-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="db11d-216">R2302:awS-zabezpečenou konverzací relace musí být vytvořen před navazování WS-ReliableMessaging sequence(s).</span><span class="sxs-lookup"><span data-stu-id="db11d-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="db11d-217">R2303: Pokud pořadí životnost WS-ReliableMessaging překročí WS-Secure Conversation životnost relace `SecurityContextToken` lze navázat pomocí WS-Secure Conversation musí obnovovat pomocí odpovídající vazby WS-Secure obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="db11d-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="db11d-218">B2304:WS-ReliableMessaging pořadí nebo dvojice posloupností korelační konverzace jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="db11d-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="db11d-219">R2305: Při skládání s WS-Secure Conversation, respondér WCF vyžaduje, aby `CreateSequence` zpráva obsahovat `wsse:SecurityTokenReference` elementu a `wsrm:UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="db11d-220">Příklad `UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="db11d-221">Složení pomocí relace protokolu SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="db11d-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="db11d-222">WCF nepodporuje složení pomocí relace protokolu SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="db11d-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="db11d-223">B2401: WCF negeneruje `wsrm:UsesSequenceSSL` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="db11d-224">R2402: Spolehlivé zasílání zpráv iniciátoru nesmí odeslat `CreateSequence` zprávy s `wsrm:UsesSequenceSSL` záhlaví respondér WCF.</span><span class="sxs-lookup"><span data-stu-id="db11d-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="db11d-225">Kompozice s WS-Policy</span><span class="sxs-lookup"><span data-stu-id="db11d-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="db11d-226">WCF podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="db11d-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="db11d-227">WS-ReliableMessaging WS-kontrolní výraz zásad</span><span class="sxs-lookup"><span data-stu-id="db11d-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="db11d-228">WCF používá WS-ReliableMessaging WS-Policy kontrolní `wsrm:RMAssertion` k popisu funkce koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="db11d-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="db11d-229">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="db11d-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="db11d-230">B3001: Připojí WCF `wsrmn:RMAssertion` WS-Policy kontrolního výrazu k `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="db11d-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="db11d-231">WCF podporuje obě příloh `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="db11d-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="db11d-232">B3002: Nikdy generuje WCF `wsp:Optional` značky.</span><span class="sxs-lookup"><span data-stu-id="db11d-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="db11d-233">B3003: Při přístupu k `wsrmp:RMAssertion` kontrolní výraz WS-Policy, ignoruje WCF `wsp:Optional` označit a zpracovává zásady WS-RM jako povinné.</span><span class="sxs-lookup"><span data-stu-id="db11d-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="db11d-234">R3004: Protože WCF compose není s relací SSL/TLS, WCF nepřijímá žádné zásady, které určují `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="db11d-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="db11d-235">B3005: Vždy generovat WCF `wsrmp:DeliveryAssurance` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="db11d-236">B3006: Vždy určuje WCF `wsrmp:ExactlyOnce` pojištění doručení.</span><span class="sxs-lookup"><span data-stu-id="db11d-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="db11d-237">B3007: WCF generuje a přečte následující vlastnosti WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad nimi v WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="db11d-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="db11d-238">Příklad `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="db11d-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="db11d-239">Tok řízení WS-ReliableMessaging rozšíření</span><span class="sxs-lookup"><span data-stu-id="db11d-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="db11d-240">K zajištění volitelné další přesnější kontrolu nad tok pořadí zpráv WCF používá WS-ReliableMessaging rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="db11d-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="db11d-241">Řízení toku se povoluje nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="db11d-241">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="db11d-242">Následuje seznam omezení, které se vztahují na WCF:</span><span class="sxs-lookup"><span data-stu-id="db11d-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="db11d-243">B4001: Pokud spolehlivé zasílání zpráv řízení toku je povolena, vygeneruje WCF `netrm:BufferRemaining` element v elementu rozšiřitelnost `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="db11d-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="db11d-244">B4002: I když spolehlivé zasílání zpráv řízení toku je povoleno, WCF nevyžaduje, aby `netrm:BufferRemaining` prvek `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="db11d-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="db11d-245">B4003: Cíl pro spolehlivé zasílání zpráv WCF používá `netrm:BufferRemaining` označuje, kolik nové zprávy uložit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="db11d-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="db11d-246">Je povolený B4004:when spolehlivé zasílání zpráv řízení toku, zdroj WCF spolehlivé zasílání zpráv používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.</span><span class="sxs-lookup"><span data-stu-id="db11d-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="db11d-247">B4005: Generuje WCF `netrm:BufferRemaining` celočíselné hodnoty rozsahu od 0 do 4096 (včetně) a čte hodnoty celé číslo mezi 0 a `xs:int`společnosti `maxInclusive` hodnota 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="db11d-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="db11d-248">Vzorky serveru Exchange zprávu</span><span class="sxs-lookup"><span data-stu-id="db11d-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="db11d-249">Tato část popisuje chování WCF. Pokud WS-ReliableMessaging slouží pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="db11d-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="db11d-250">Pro každý vzoru výměny zpráv se považují následující scénáře dvě nasazení:</span><span class="sxs-lookup"><span data-stu-id="db11d-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="db11d-251">Bajtově Adresovatelného iniciátor: Iniciátor nachází za bránou firewall; Respondér doručovat zprávy do iniciátor pouze na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="db11d-252">Adresovatelný iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy je možné navázat připojení prostřednictvím protokolu HTTP dvě konverzace.</span><span class="sxs-lookup"><span data-stu-id="db11d-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="db11d-253">Jednosměrný, bajtově adresovatelného iniciátor</span><span class="sxs-lookup"><span data-stu-id="db11d-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="db11d-254">Vazba</span><span class="sxs-lookup"><span data-stu-id="db11d-254">Binding</span></span>  
 <span data-ttu-id="db11d-255">WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="db11d-256">Přenést všechny zprávy z iniciátoru do odpovědí respondéru a HTTP přenášet všechny zprávy z straně odpovídajícího iniciátoru pomocí WCF požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="db11d-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-258">Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` elementu na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="db11d-259">Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávu bez `Accept` element na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="db11d-260">Třída SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="db11d-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="db11d-261">Iniciátor WCF zpracovává potvrzování odpověď všech zpráv s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="db11d-262">WCF respondér vždy přenese samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="db11d-263">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="db11d-264">Iniciátor WCF přenáší `CloseSequence` zprávy na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="db11d-265">Přenáší respondér WCF `CloseSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="db11d-266">TerminateSequence dříve Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-267">Iniciátor WCF přenáší `TerminateSequence` zprávy na požadavek HTTP a očekává, že `TerminateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="db11d-268">Přenáší respondér WCF `TerminateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="db11d-269">Jedním ze způsobů, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="db11d-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="db11d-270">Vazba</span><span class="sxs-lookup"><span data-stu-id="db11d-270">Binding</span></span>  
 <span data-ttu-id="db11d-271">WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jednu vstupní a jednu výstupní kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="db11d-272">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="db11d-273">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="db11d-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="db11d-274">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-275">Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="db11d-276">Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="db11d-277">Duplexní, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="db11d-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="db11d-278">Vazba</span><span class="sxs-lookup"><span data-stu-id="db11d-278">Binding</span></span>  
 <span data-ttu-id="db11d-279">Poskytuje WCF pomocí dvou vzoru výměny zpráv plně asynchronní, pokud vytvoříte obousměrný pořadí více než jeden vstupní a jednu výstupní kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="db11d-280">Tento vzorce výměny zpráv lze kombinovat s `Request/Reply`, `Addressable` vzoru výměny zpráv iniciátoru omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="db11d-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="db11d-281">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="db11d-282">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="db11d-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="db11d-283">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-284">Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="db11d-285">WCF respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávy s `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="db11d-286">Doba života pořadí</span><span class="sxs-lookup"><span data-stu-id="db11d-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="db11d-287">WCF považuje dvou sekvencí jeden plně duplexní relace.</span><span class="sxs-lookup"><span data-stu-id="db11d-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="db11d-288">Při generování chybu, která chyb jedním sekvenčním WCF očekává, že vzdálený koncový bod na selhání obou pořadí.</span><span class="sxs-lookup"><span data-stu-id="db11d-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="db11d-289">Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obou pořadí.</span><span class="sxs-lookup"><span data-stu-id="db11d-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="db11d-290">WCF zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy na jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="db11d-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="db11d-291">Naopak WCF zpracovávat zavřít příchozí pořadí a i nadále odesílat zprávy v jeho výstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="db11d-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="db11d-292">Požadavek odpověď a jednosměrný, bajtově Adresovatelného iniciátor</span><span class="sxs-lookup"><span data-stu-id="db11d-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="db11d-293">Vazba</span><span class="sxs-lookup"><span data-stu-id="db11d-293">Binding</span></span>  
 <span data-ttu-id="db11d-294">Poskytuje jednosměrný WCF a vzorce výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="db11d-295">Přenést všechny zprávy z iniciátoru do odpovědí respondéru a HTTP přenášet všechny zprávy z straně odpovídajícího iniciátoru pomocí WCF požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="db11d-296">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-297">Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="db11d-298">Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávy s `Accept` element na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="db11d-299">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="db11d-299">One-way Message</span></span>  
 <span data-ttu-id="db11d-300">Jednosměrná zpráva exchange úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá samostatný `SequenceAcknowledgement` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="db11d-301">`SequenceAcknowledgement` Musí potvrzení zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="db11d-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="db11d-302">WCF respondér může odpovědět na požadavek na potvrzení, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="db11d-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="db11d-303">Dvě způsob, jak zprávy</span><span class="sxs-lookup"><span data-stu-id="db11d-303">Two Way Messages</span></span>  
 <span data-ttu-id="db11d-304">Protokol pro výměnu zpráv dvousměrné úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá zprávy sekvence odpovědí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="db11d-305">Odpovědi musí mít `SequenceAcknowledgement` potvrdil pořadí zprávy s požadavkem přenosu.</span><span class="sxs-lookup"><span data-stu-id="db11d-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="db11d-306">WCF respondér může odpovědět na požadavek odpovědi na žádost, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="db11d-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="db11d-307">Z důvodu přítomnosti jednosměrné zprávy a načasování odpovědi aplikace mít žádnou souvislost pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="db11d-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="db11d-308">Opakování pokusu o odpovědi</span><span class="sxs-lookup"><span data-stu-id="db11d-308">Retrying Replies</span></span>  
 <span data-ttu-id="db11d-309">WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="db11d-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="db11d-310">Z tohoto důvodu je iniciátor WCF nezastaví opakování zprávy sekvence do požadavku při potvrzení pořadí zprávy s požadavkem, ale spíše, při představuje odpověď HTTP `SequenceAcknowledgement`, odpověď aplikace nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="db11d-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="db11d-311">WCF respondér zopakuje pokus o odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpověď.</span><span class="sxs-lookup"><span data-stu-id="db11d-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="db11d-312">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="db11d-313">Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy sekvence jednosměrný požadavek, přenáší iniciátoru WCF `CloseSequence` zpráva sekvence požadavku na požadavek HTTP a očekává, že `CloseSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="db11d-314">Zavřením sekvence požadavku implicitně zavření sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="db11d-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="db11d-315">To znamená, že je iniciátor WCF obsahuje koncový sekvence odpovědí `SequenceAcknowledgement` na `CloseSequence` zprávu a sekvence odpovědí nemá `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="db11d-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="db11d-316">WCF respondér zajišťuje všechny odpovědi jsou potvrzeny a vysílá `CloseSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="db11d-317">TerminateSequence dříve Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-318">Po přijetí `CloseSequenceResponse` přenáší zprávy, iniciátor WCF `TerminateSequence` zpráva sekvence požadavku na požadavek HTTP a očekává, že `TerminateSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="db11d-319">Podobně jako `CloseSequence` exchange ukončuje sekvence požadavku implicitně ukončí sekvence odpovědí.</span><span class="sxs-lookup"><span data-stu-id="db11d-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="db11d-320">To znamená, že je iniciátor WCF obsahuje koncový sekvence odpovědí `SequenceAcknowledgement` na `TerminateSequence` zprávu a sekvence odpovědí nemá `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="db11d-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="db11d-321">Přenáší respondér WCF `TerminateSequenceResponse` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="db11d-322">Žádost odpověď, adresovatelný iniciátor</span><span class="sxs-lookup"><span data-stu-id="db11d-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="db11d-323">Vazba</span><span class="sxs-lookup"><span data-stu-id="db11d-323">Binding</span></span>  
 <span data-ttu-id="db11d-324">WCF poskytuje vzoru výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden vstupní a jednu výstupní kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="db11d-325">Tento vzorce výměny zpráv lze kombinovat s `Duplex, Addressable` vzoru výměny zpráv iniciátoru omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="db11d-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="db11d-326">WCF používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="db11d-327">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="db11d-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="db11d-328">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="db11d-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="db11d-329">Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="db11d-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="db11d-330">WCF respondér zajišťuje, že `CreateSequence` má `Offer` prvek pak vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávy s `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="db11d-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="db11d-331">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="db11d-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="db11d-332">Následující část se vztahuje na všechny korelační požadavky a odpovědi:</span><span class="sxs-lookup"><span data-stu-id="db11d-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="db11d-333">Zajišťuje také nesete zprávy požadavku všechny aplikace, WCF `ReplyTo` reference koncového bodu a `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="db11d-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="db11d-334">WCF platí odkaz na místní koncový bod jako každou zprávu požadavku aplikace `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="db11d-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="db11d-335">Odkaz na místním koncovým bodem je `CreateSequence` zprávy `ReplyTo` pro iniciátor a `CreateSequence` zprávy `To` pro respondér.</span><span class="sxs-lookup"><span data-stu-id="db11d-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="db11d-336">WCF zajišťuje také nesete zprávy příchozí žádosti `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="db11d-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="db11d-337">Zajišťuje WCF `ReplyTo` reference koncového bodu identifikátor URI zprávy požadavku všechny aplikace odpovídat odkaz na místní koncový bod definovaný dříve.</span><span class="sxs-lookup"><span data-stu-id="db11d-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="db11d-338">WCF se zajistí, že všechny odpovědi označena správná `RelatesTo` a `To` záhlaví po `wsa` pravidla korelace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="db11d-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
