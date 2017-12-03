---
title: "Protokol spolehlivého zasílání zpráv verze 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 586e26825bd01947706bb26061ef1b8879fecb4c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="1ae9d-102">Protokol spolehlivého zasílání zpráv verze 1.1</span><span class="sxs-lookup"><span data-stu-id="1ae9d-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="1ae9d-103">Toto téma popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podrobnosti implementace protokolu WS-ReliableMessaging. února 2007 (verze 1.1) protokolu potřebné pro vzájemná spolupráce pomocí přenosového protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-104">dodržuje specifikaci WS-ReliableMessaging s omezení a objasnění, která jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="1ae9d-105">Poznámka: verze 1.1 protokolu WS-ReliableMessaging je implementováno začínající [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae9d-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="1ae9d-106">Protokolu WS-ReliableMessaging. února 2007 protokol je implementována ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="1ae9d-107">Pro usnadnění práce tématu používá Tyhle role:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="1ae9d-108">Iniciátor: Klienta, která zahájí vytváření sekvence WS-spolehlivé zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="1ae9d-109">Respondér: Služba, která přijímá požadavky je iniciátor.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="1ae9d-110">Tento dokument používá předpony a obory názvů v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="1ae9d-111">Předpona</span><span class="sxs-lookup"><span data-stu-id="1ae9d-111">Prefix</span></span>|<span data-ttu-id="1ae9d-112">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1ae9d-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="1ae9d-113">Správce systémových prostředků</span><span class="sxs-lookup"><span data-stu-id="1ae9d-113">wsrm</span></span>|<span data-ttu-id="1ae9d-114">http://docs.oasis-open.org/ws-RX/wsrm/200702</span><span class="sxs-lookup"><span data-stu-id="1ae9d-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="1ae9d-115">netrm</span><span class="sxs-lookup"><span data-stu-id="1ae9d-115">netrm</span></span>|<span data-ttu-id="1ae9d-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="1ae9d-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="1ae9d-117">s</span><span class="sxs-lookup"><span data-stu-id="1ae9d-117">s</span></span>|<span data-ttu-id="1ae9d-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="1ae9d-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="1ae9d-119">wsa</span><span class="sxs-lookup"><span data-stu-id="1ae9d-119">wsa</span></span>|<span data-ttu-id="1ae9d-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="1ae9d-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="1ae9d-121">wsse</span><span class="sxs-lookup"><span data-stu-id="1ae9d-121">wsse</span></span>|<span data-ttu-id="1ae9d-122">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="1ae9d-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="1ae9d-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="1ae9d-123">wsrmp</span></span>|<span data-ttu-id="1ae9d-124">http://docs.oasis-open.org/ws-RX/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="1ae9d-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="1ae9d-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="1ae9d-125">netrmp</span></span>|<span data-ttu-id="1ae9d-126">http://schemas.microsoft.com/ws-RX/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="1ae9d-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="1ae9d-127">WSP</span><span class="sxs-lookup"><span data-stu-id="1ae9d-127">wsp</span></span>|<span data-ttu-id="1ae9d-128">(WS-Policy 1.2 nebo WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="1ae9d-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="1ae9d-129">Zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="1ae9d-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="1ae9d-130">Vytvoření pořadí</span><span class="sxs-lookup"><span data-stu-id="1ae9d-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-131">implementuje `CreateSequence` a `CreateSequenceResponse` pořadí zprávy a pokuste se vytvořit spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="1ae9d-132">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1ae9d-133">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor používá koncový bod odkaz na stejné jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="1ae9d-134">R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zprávy musí mít hodnoty adres s identické řetězcové vyjádření tak, že budou odpovídat octet-wise.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="1ae9d-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` odkazy koncového bodu jsou identické před vytvořením sekvenci.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="1ae9d-136">R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` odkazy na koncový bod v `CreateSequence` zprávy musí mít stejnou sadu parametrů odkaz.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-137">nevynucuje, ale předpokládá, které se odkazují parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkaz z `ReplyTo` reference koncového bodu pro konverzace pořadí zprávy a potvrzení.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="1ae9d-138">B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="1ae9d-139">B1105: Při přístupu k `CreateSequence` zpráva, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér používá `Expires` hodnotu ve `CreateSequence` element jako `Expires` hodnotu `CreateSequenceResponse` element.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="1ae9d-140">V opačném [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="1ae9d-141">B1106: Při přístupu k `CreateSequenceResponse` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor načte volitelné `Expires` hodnotu, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="1ae9d-142">B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor a respondér vždy generovat nepovinný `IncompleteSequenceBehavior` element v `CreateSequence/Offer` a `CreateSequenceResponse` elementy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="1ae9d-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá jenom `DiscardFollowingFirstGap` a `NoDiscard` hodnoty ve `IncompleteSequenceBehavior` elementu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="1ae9d-144">Využívá WS-ReliableMessaging `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="1ae9d-145">B1109: Pokud `CreateSequence` obsahuje `Offer` elementu, jedním ze způsobů [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér odmítne nabízený pořadí podle reagovat se `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="1ae9d-146">B1110: Pokud spolehlivého zasílání zpráv respondér odmítne nabízený pořadí, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor závady nově vytvořeným pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="1ae9d-147">B1111: Pokud `CreateSequence` neobsahuje `Offer` prvek, obousměrný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér odmítne nabízený pořadí podle reagovat se `CreateSequenceRefused` selhání.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="1ae9d-148">R1112: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="1ae9d-149">R1113: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, musí se poslat všechny zprávy na obou pořadí předávaných z iniciátoru k příjemce, na odkaz na stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-150">pomocí protokolu WS-ReliableMessaging zřizuje spolehlivé relace mezi iniciátoru a odpovídající počítač.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="1ae9d-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Implementaci protokolu WS-ReliableMessaging poskytuje spolehlivé relace jednosměrné, požadavku a odpovědi a plně duplexní režim vzory pro zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="1ae9d-152">WS-ReliableMessaging `Offer` mechanismus na `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dva korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="1ae9d-153">Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje záruku zabezpečení pro takové relace včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné strany na stejný cíl.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="1ae9d-154">To také umožňuje "Prasátko zálohování" pořadí potvrzení u zpráv s aplikací.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="1ae9d-155">Proto se týkají omezení R1102, R1112 a R1113 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae9d-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="1ae9d-156">Příklad `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-156">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="1ae9d-157">Příklad `CreateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="1ae9d-158">Zavřením sekvenci</span><span class="sxs-lookup"><span data-stu-id="1ae9d-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-159">používá `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spouštěná zdroje.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="1ae9d-160">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Spolehlivé zasílání zpráv cílové neiniciuje vypnutí a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv zdroj nepodporuje vypnutí spouštěná cílové spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="1ae9d-161">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1ae9d-162">B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždycky odešle zdroj spolehlivé zasílání zpráv `CloseSequence` zpráva vypnout sekvenci.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="1ae9d-163">B1202: Zdroji spolehlivé zasílání zpráv čeká na potvrzení plný rozsah pořadí zprávy před odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="1ae9d-164">B1203: Zdroji spolehlivé zasílání zpráv vždy obsahuje volitelné `LastMsgNumber` element Pokud sekvenci neobsahuje zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="1ae9d-165">R1204: Cílový spolehlivé zasílání zpráv nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="1ae9d-166">B1205: po přijetí `CloseSequence` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv zdroj považuje pořadí nekompletní a odešle chybu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="1ae9d-167">Příklad `CloseSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-167">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="1ae9d-168">Pořadí ukončení</span><span class="sxs-lookup"><span data-stu-id="1ae9d-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-169">především používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` metody handshake.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="1ae9d-170">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Spolehlivé zasílání zpráv cílové neiniciuje ukončení a zdroji spolehlivé zasílání zpráv nepodporuje ukončení spouštěná cílové spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="1ae9d-171">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1ae9d-172">B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor odesílá jenom `TerminateSequence` zpráva po úspěšném dokončení `CloseSequence/CloseSequenceResponse` metody handshake.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="1ae9d-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zprávy pro daného pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="1ae9d-174">To znamená, že `LastMsgNumber` buď není přítomen na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je přítomen a na všechny stejné `CloseSequence` a `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="1ae9d-175">B1303: Při přijímání `TerminateSequence` zprávy po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="1ae9d-176">Protože má zdroj spolehlivé zasílání zpráv konečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv zná bez nepochybně, že je pořadí skončí a uvolní prostředky okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="1ae9d-177">B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv cílové odpoví `TerminateSequenceResponse` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="1ae9d-178">Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v pořadí, cílový spolehlivé zasílání zpráv čeká na dobu zadané cílové aplikace před opětovného získání prostředků, aby klient riziko pro příjem konečné potvrzení.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="1ae9d-179">Jinak cílové spolehlivé zasílání zpráv okamžitě získá prostředky a označuje cílové aplikace, že je pořadí končí nejistých zobrazením `Faulted` událostí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="1ae9d-180">Příklad `TerminateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-180">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="1ae9d-181">Sekvence</span><span class="sxs-lookup"><span data-stu-id="1ae9d-181">Sequences</span></span>  
 <span data-ttu-id="1ae9d-182">Následuje seznam omezení, která se týkají pořadí:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="1ae9d-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a přistupuje k pořadová čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="1ae9d-184">Příklad `Sequence` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="1ae9d-185">Žádost o potvrzení</span><span class="sxs-lookup"><span data-stu-id="1ae9d-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-186">používá `AckRequested` záhlaví jako mechanismus keep-alive.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="1ae9d-187">Příklad `AckRequested` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="1ae9d-188">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="1ae9d-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-189">používá mechanismus "Prasátko zpětným" pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="1ae9d-190">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1ae9d-191">R1601: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="1ae9d-192">Vzdálený koncový bod musí být schopni přistupovat zařazována složená `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="1ae9d-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-194">ověří, že každý `Nack` elementu obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="1ae9d-195">Příklad `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="1ae9d-196">WS-ReliableMessaging chyb</span><span class="sxs-lookup"><span data-stu-id="1ae9d-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="1ae9d-197">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-ReliableMessaging chyb.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="1ae9d-198">Platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="1ae9d-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `MessageNumberRollover` chyb.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="1ae9d-200">B1702: Přes SOAP 1.2, pokud koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje vnořený `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="1ae9d-201">Adresování WS chyb</span><span class="sxs-lookup"><span data-stu-id="1ae9d-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="1ae9d-202">Protože WS-ReliableMessaging používá adresování WS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-ReliableMessaging může vygenerovat a přenést WS-Addressing chyb.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="1ae9d-203">Tato část zahrnuje WS-Addressing chyb, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitně generuje a odesílá ve vrstvě protokolu WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="1ae9d-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a odesílá `Message Addressing Header Required` poruch, když je splněna jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="1ae9d-205">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="1ae9d-206">A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="1ae9d-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="1ae9d-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a odesílá `Endpoint Unavailable` selhání označíte, neexistuje žádný koncový bod naslouchání, který může zpracovat pořadí podle zkoumání adresování hlavičky v `CreateSequence` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="1ae9d-209">Protokol složení</span><span class="sxs-lookup"><span data-stu-id="1ae9d-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="1ae9d-210">Složení s adresováním WS</span><span class="sxs-lookup"><span data-stu-id="1ae9d-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-211">podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="1ae9d-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="1ae9d-212">Při zmínkami specifikace protokolu WS-ReliableMessaging pouze WS-Addressing 2004/08, se neomezuje verze WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="1ae9d-213">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="1ae9d-214">R2101: Obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="1ae9d-215">R2102: Jedné verzi protokolu WS-Addressing musí použít v rámci daného pořadí WS-ReliableMessaging nebo pár konverzace pořadí korelační pomocí `Offer` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="1ae9d-216">Složení protokol SOAP</span><span class="sxs-lookup"><span data-stu-id="1ae9d-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-217">podporuje použití SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="1ae9d-218">Složení s WS-zabezpečení a WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="1ae9d-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-219">poskytuje ochranu WS-ReliableMessaging pořadí pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="1ae9d-220">Protokol WS-ReliableMessaging 1.1, WS-zabezpečení 1.1 a protokol WS-zabezpečené konverzace 1.3 musí použít společně.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="1ae9d-221">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="1ae9d-222">R2301: K ochraně integritu WS-ReliableMessaging pořadí kromě integrity a důvěrnosti jednotlivých zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje, že se musí použít WS zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="1ae9d-223">R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením WS-ReliableMessaging sequence(s).</span><span class="sxs-lookup"><span data-stu-id="1ae9d-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="1ae9d-224">R2303: Pokud WS-ReliableMessaging pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="1ae9d-225">B2304:WS-ReliableMessaging pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="1ae9d-226">R2305: Když skládá s WS zabezpečené konverzace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér vyžaduje, aby `CreateSequence` zpráva obsahovat `wsse:SecurityTokenReference` element a `wsrm:UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="1ae9d-227">Příklad `UsesSequenceSTR` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="1ae9d-228">Složení s relací SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-229">nepodporuje složení s protokolem SSL/TLS relace:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="1ae9d-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `wsrm:UsesSequenceSSL` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="1ae9d-231">R2402: Spolehlivého zasílání zpráv iniciátor nesmí odesílat `CreateSequence` zpráv s `wsrm:UsesSequenceSSL` hlavičky k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="1ae9d-232">Složení zásadám WS</span><span class="sxs-lookup"><span data-stu-id="1ae9d-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-233">podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="1ae9d-234">WS-ReliableMessaging WS-výraz zásad</span><span class="sxs-lookup"><span data-stu-id="1ae9d-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-235">používá výraz WS-zásad protokolu WS-ReliableMessaging `wsrm:RMAssertion` k popisu možnosti koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="1ae9d-236">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="1ae9d-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] připojí `wsrmn:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-238">podporuje oba přílohy do `wsdl:binding` a `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="1ae9d-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy vygeneruje `wsp:Optional` značky.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="1ae9d-240">B3003: Při přístupu k `wsrmp:RMAssertion` výraz WS-zásad [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `wsp:Optional` značky a zpracovává zásady WS-RM jako povinné.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="1ae9d-241">R3004: Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] není tvoří s relací SSL/TLS, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepřijímá zásady, které určují `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="1ae9d-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy vygeneruje `wsrmp:DeliveryAssurance` elementu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="1ae9d-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy určuje `wsrmp:ExactlyOnce` záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="1ae9d-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a čte následující vlastnosti protokolu WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad je na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="1ae9d-245">Příklad `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-245">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="1ae9d-246">Rozšíření protokolu WS-ReliableMessaging toku řízení</span><span class="sxs-lookup"><span data-stu-id="1ae9d-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-247">rozšiřitelnost protokolu WS-ReliableMessaging používá k poskytnutí volitelné další náročnější řídit tok zpráv pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="1ae9d-248">Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``boolean` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="1ae9d-249">Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="1ae9d-250">B4001: Když spolehlivého zasílání zpráv toku řízení je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="1ae9d-251">B4002: I když spolehlivého zasílání zpráv řízení toku je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="1ae9d-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivého zasílání zpráv cílové používá `netrm:BufferRemaining` indikující, kolik nové zprávy můžete ukládat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="1ae9d-253">B4004:when spolehlivého zasílání zpráv řízení toku je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivého zasílání zpráv zdroj používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="1ae9d-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).</span><span class="sxs-lookup"><span data-stu-id="1ae9d-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="1ae9d-255">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="1ae9d-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="1ae9d-256">Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na chování při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="1ae9d-257">Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="1ae9d-258">Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv na iniciátoru pouze na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="1ae9d-259">Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="1ae9d-260">Jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="1ae9d-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1ae9d-261">Vazba</span><span class="sxs-lookup"><span data-stu-id="1ae9d-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-262">poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-263">využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1ae9d-264">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-265">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-266">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="1ae9d-267">Bylo potvrzení SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="1ae9d-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="1ae9d-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="1ae9d-269">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vždy přenáší samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="1ae9d-270">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-271">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CloseSequence` zpráva na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-272">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `CloseSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="1ae9d-273">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `TerminateSequence` zpráva na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="1ae9d-276">Jedním ze způsobů, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="1ae9d-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1ae9d-277">Vazba</span><span class="sxs-lookup"><span data-stu-id="1ae9d-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-278">poskytuje pomocí jednoho pořadí přes jeden vzorce výměny zpráv jednosměrný příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-279">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1ae9d-280">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1ae9d-281">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-282">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="1ae9d-283">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="1ae9d-284">Duplexní, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="1ae9d-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1ae9d-285">Vazba</span><span class="sxs-lookup"><span data-stu-id="1ae9d-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-286">poskytuje dvě pomocí vzorce výměny zpráv plně asynchronní, obousměrný pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="1ae9d-287">Tato vzorce výměny zpráv můžete kombinovat s `Request/Reply`, `Addressable` vzorce výměny zpráv iniciátor omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-288">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1ae9d-289">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1ae9d-290">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-291">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="1ae9d-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="1ae9d-293">Doba platnosti pořadí</span><span class="sxs-lookup"><span data-stu-id="1ae9d-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-294">dvě pořadí považuje za jednu relaci plně duplexní.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="1ae9d-295">Při generování chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává vzdálený koncový bod pro poruch obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="1ae9d-296">Při čtení chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] závady obě pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-297">můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="1ae9d-298">Naopak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] může zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="1ae9d-299">Požadavek odpověď a jednosměrné, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="1ae9d-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1ae9d-300">Vazba</span><span class="sxs-lookup"><span data-stu-id="1ae9d-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-301">poskytuje jednosměrný a požadavku a odpovědi vzorce výměny zpráv pomocí dvou pořadí více než jeden kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-302">využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1ae9d-303">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-304">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-305">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="1ae9d-306">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="1ae9d-306">One-way Message</span></span>  
 <span data-ttu-id="1ae9d-307">Jednosměrné zpráva exchange úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-308">`SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="1ae9d-309">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na požadavek potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="1ae9d-310">Dvě způsob zprávy</span><span class="sxs-lookup"><span data-stu-id="1ae9d-310">Two Way Messages</span></span>  
 <span data-ttu-id="1ae9d-311">Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="1ae9d-312">Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="1ae9d-313">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="1ae9d-314">Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="1ae9d-315">Opakováním odpovědi</span><span class="sxs-lookup"><span data-stu-id="1ae9d-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-316">spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="1ae9d-317">Z toho důvodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale spíš, když představuje odpověď HTTP `SequenceAcknowledgement`, aplikace odpovědi nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="1ae9d-318">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér opakování odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="1ae9d-319">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-320">Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy s jedním ze způsobů požadavky pořadí, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenáší iniciátor `CloseSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `CloseSequenceResponse` na HTTP odpověď.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="1ae9d-321">Zavřením sekvence požadavku implicitně zavře odpověď pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="1ae9d-322">To znamená [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `CloseSequence` zprávu a pořadí odpovědi nemá `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="1ae9d-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajistí všechny odpovědi jsou potvrzené a odesílá `CloseSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="1ae9d-324">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-325">Po přijetí `CloseSequenceResponse` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenáší iniciátor `TerminateSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `TerminateSequenceResponse` na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="1ae9d-326">Podobně jako `CloseSequence` systému exchange, ukončení pořadí žádost implicitně ukončí odpověď pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="1ae9d-327">To znamená [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `TerminateSequence` zprávu a pořadí odpovědi nemá `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="1ae9d-328">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `TerminateSequenceResponse` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="1ae9d-329">Požadavek nebo odpověď, adresovatelné iniciátor</span><span class="sxs-lookup"><span data-stu-id="1ae9d-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="1ae9d-330">Vazba</span><span class="sxs-lookup"><span data-stu-id="1ae9d-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-331">poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="1ae9d-332">Tato vzorce výměny zpráv můžete kombinovat s `Duplex, Addressable` vzorce výměny zpráv iniciátor omezeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-333">používá k přenosu všech zpráv požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="1ae9d-334">Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="1ae9d-335">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="1ae9d-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="1ae9d-336">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="1ae9d-337">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má `Offer` element potom vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="1ae9d-338">Korelace požadavku/odpovědi</span><span class="sxs-lookup"><span data-stu-id="1ae9d-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="1ae9d-339">Následující část se vztahuje na všechny korelační požadavky a odpovědi:</span><span class="sxs-lookup"><span data-stu-id="1ae9d-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-340">zajistí všechny opatřeny zprávy žádost o aplikaci `ReplyTo` reference koncového bodu a `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-341">odkaz na místní koncový bod se vztahuje jako každou zprávu žádosti o aplikace `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="1ae9d-342">Odkaz na místní koncový bod je `CreateSequence` zprávy `ReplyTo` pro iniciátory a `CreateSequence` zprávy `To` pro respondér.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-343">zajišťuje, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-344">zajišťuje `ReplyTo` identifikátor URI koncového bodu odkaz všechny zprávy požadavku aplikace odkaz na místní koncový bod shodovat s dříve definovaným.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1ae9d-345">zajišťuje, že všechny odpovědi berte správný `RelatesTo` a `To` hlavičky následující `wsa` pravidla korelace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1ae9d-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
