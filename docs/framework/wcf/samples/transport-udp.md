---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 4f69730831ec57efc782a95d7412496aa69a4afb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808413"
---
# <a name="transport-udp"></a><span data-ttu-id="33ad2-102">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="33ad2-102">Transport: UDP</span></span>
<span data-ttu-id="33ad2-103">Ukázka přenosu UDP ukazuje, jak implementovat jednosměrového vysílání UDP a vícesměrového vysílání jako vlastní přenosu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="33ad2-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="33ad2-104">Ukázka popisuje doporučený postup pro vytvoření vlastní přenosu ve WCF, pomocí rozhraní kanálu a následující osvědčené postupy WCF.</span><span class="sxs-lookup"><span data-stu-id="33ad2-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="33ad2-105">Postup vytvoření vlastního přenosu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="33ad2-105">The steps to create a custom transport are as follows:</span></span>  
  
1.  <span data-ttu-id="33ad2-106">Rozhodněte, které kanálu [zpráva Exchange vzory](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) ChannelFactory a ChannelListener bude podporovat.</span><span class="sxs-lookup"><span data-stu-id="33ad2-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="33ad2-107">Rozhodněte se, zda bude podporovat relacemi variace tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33ad2-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2.  <span data-ttu-id="33ad2-108">Vytvoření postupu kanálu a naslouchací proces, který podporují vaše vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="33ad2-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3.  <span data-ttu-id="33ad2-109">Ujistěte se, že jsou všechny výjimky sítě normalizovány na příslušné odvozené třídy z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4.  <span data-ttu-id="33ad2-110">Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) element, který přidá vlastní přenos do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="33ad2-111">Další informace najdete v tématu [přidání Element vazby](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="33ad2-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5.  <span data-ttu-id="33ad2-112">Přidáte oddíl rozšíření element vazby ke zveřejnění nového elementu vazby v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="33ad2-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6.  <span data-ttu-id="33ad2-113">Přidejte rozšíření metadata pro komunikaci funkce pro ostatní koncové body.</span><span class="sxs-lookup"><span data-stu-id="33ad2-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7.  <span data-ttu-id="33ad2-114">Přidejte vazbu, která předem nakonfiguruje zásobníku elementů vazby podle dobře definovaný profil.</span><span class="sxs-lookup"><span data-stu-id="33ad2-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="33ad2-115">Další informace najdete v tématu [přidání standardní vazbu](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="33ad2-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8.  <span data-ttu-id="33ad2-116">Přidáte oddíl vazby a konfigurace prvku vazby ke zveřejnění vazby ke konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="33ad2-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="33ad2-117">Další informace najdete v tématu [přidání podpory konfigurace](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="33ad2-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="33ad2-118">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="33ad2-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="33ad2-119">První krok v zápisu vlastní přenosu je rozhodnout, jaké zprávy Exchange vzory (MEPs) jsou požadovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="33ad2-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="33ad2-120">Existují tři MEPs zvolit:</span><span class="sxs-lookup"><span data-stu-id="33ad2-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="33ad2-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="33ad2-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="33ad2-122">Pokud používáte datagram MEP, klient odešle zprávu pomocí systému exchange "fire a zapomněli".</span><span class="sxs-lookup"><span data-stu-id="33ad2-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="33ad2-123">A fire a zapomněli exchange je ten, který vyžaduje out-of-band potvrzení úspěšné doručení.</span><span class="sxs-lookup"><span data-stu-id="33ad2-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="33ad2-124">Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí službu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="33ad2-125">Operaci odeslání po úspěšném dokončení na konci klienta, nezaručuje to, že vzdálený koncový bod se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="33ad2-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="33ad2-126">Datagram je základní stavební blok pro zasílání zpráv, jak můžete vytvořit vlastní protokoly nad jeho – včetně protokoly spolehlivé a bezpečné protokoly.</span><span class="sxs-lookup"><span data-stu-id="33ad2-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="33ad2-127">Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33ad2-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="33ad2-128">Požadavků a odpovědí (třídu IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="33ad2-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="33ad2-129">V této MEP je odeslána zpráva a odpoví.</span><span class="sxs-lookup"><span data-stu-id="33ad2-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="33ad2-130">Vzor se skládá z dvojice požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="33ad2-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="33ad2-131">Volání požadavků a odpovědí příklady vzdálených volání procedur (RPC) a prohlížeč získá.</span><span class="sxs-lookup"><span data-stu-id="33ad2-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="33ad2-132">Tento vzor se také označuje jako poloduplexní.</span><span class="sxs-lookup"><span data-stu-id="33ad2-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="33ad2-133">V této MEP klienta kanály implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementaci služby kanály <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="33ad2-134">Duplexní režim (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="33ad2-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="33ad2-135">Duplexní MEP umožňuje libovolný počet zpráv, které mají být odeslány klientem a přijaté v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="33ad2-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="33ad2-136">Duplexní MEP je třeba je telefonní hovor, kde je jednotlivých slov použitém zprávu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="33ad2-137">Vzhledem k tomu, že na obou stranách můžete odesílat a přijímat v této MEP, rozhraní implementované kanály klienta a služby je <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="33ad2-138">Každý z těchto MEPs může také podporovat relací.</span><span class="sxs-lookup"><span data-stu-id="33ad2-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="33ad2-139">Přidané funkce poskytované službou deklaracemi relace kanál je, že ho korelaci všechny zprávy odeslané a přijaté v kanálu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="33ad2-140">Vzor požadavků a odpovědí je samostatné relaci dvě zprávy, jako jsou korelační požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="33ad2-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="33ad2-141">Naproti tomu vzor požadavků a odpovědí, který podporuje relací znamená, že všechny páry požadavků a odpovědí v tomto kanálu jsou korelační mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="33ad2-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="33ad2-142">To vám dává celkem šest MEPs – Datagram, požadavků a odpovědí, duplexní režim, Datagram s relací, požadavků a odpovědí s relací a duplexní s relací – lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="33ad2-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33ad2-143">Pro přenosu UDP pouze MEP, která je podporována je Datagram, protože UDP je ze své podstaty protokol "fire a zapomněli".</span><span class="sxs-lookup"><span data-stu-id="33ad2-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="33ad2-144">ICommunicationObject a životního cyklu objekt WCF</span><span class="sxs-lookup"><span data-stu-id="33ad2-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="33ad2-145">Běžné stavu počítače, který se používá pro správu životního cyklu objektů, jako má WCF <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, a <xref:System.ServiceModel.Channels.IChannelListener> používané pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="33ad2-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="33ad2-146">Nejsou k dispozici pět stavy, při kterých může existovat tyto objekty komunikace.</span><span class="sxs-lookup"><span data-stu-id="33ad2-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="33ad2-147">Tyto stavy jsou reprezentované pomocí <xref:System.ServiceModel.CommunicationState> výčet a jsou následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="33ad2-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="33ad2-148">Vytvoří: Toto je stav <xref:System.ServiceModel.ICommunicationObject> při prvním vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="33ad2-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="33ad2-149">V tomto stavu dojde k žádné vstupní a výstupní (I/O).</span><span class="sxs-lookup"><span data-stu-id="33ad2-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="33ad2-150">Otevírání: Přechod objekty do tohoto stavu, kdy <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="33ad2-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="33ad2-151">Vlastnosti jsou vytvářeny v tomto okamžiku nezměnitelná a můžete začít vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="33ad2-152">Tento přechod je platný pouze z stavu vytvořen.</span><span class="sxs-lookup"><span data-stu-id="33ad2-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="33ad2-153">Otevřené: Přechod objekty do tohoto stavu po dokončení procesu otevřete.</span><span class="sxs-lookup"><span data-stu-id="33ad2-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="33ad2-154">Tento přechod je platný pouze z otevírání stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="33ad2-155">Objekt je nyní plně použitelné pro přenos.</span><span class="sxs-lookup"><span data-stu-id="33ad2-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="33ad2-156">Ukončovací: Přechod objekty do tohoto stavu, kdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána pro řádné vypnutí.</span><span class="sxs-lookup"><span data-stu-id="33ad2-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="33ad2-157">Tento přechod je platný pouze z stavu otevřeno.</span><span class="sxs-lookup"><span data-stu-id="33ad2-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="33ad2-158">Uzavřené: V poli Uzavřeno stavu objektů již nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="33ad2-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="33ad2-159">Obecně platí většina konfigurace je stále přístupné pro kontrolu, ale může nastat žádná komunikace.</span><span class="sxs-lookup"><span data-stu-id="33ad2-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="33ad2-160">Tento stav je ekvivalentní vyřazována.</span><span class="sxs-lookup"><span data-stu-id="33ad2-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="33ad2-161">Faulted: V chybném stavu, jsou objekty přístupné pro kontrolu, ale již není použitelná.</span><span class="sxs-lookup"><span data-stu-id="33ad2-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="33ad2-162">Když dojde k nezotavitelnou chybu, objekt přechází do tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="33ad2-163">Je platné pouze přechod z tohoto stavu do `Closed` stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="33ad2-164">Nejsou události, které budou spuštěny pro každý přechod stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="33ad2-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metodu lze volat kdykoli a způsobí, že objekt přecházení mezi okamžitě z jeho aktuální stav v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="33ad2-166">Volání metody <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechna nedokončené práce.</span><span class="sxs-lookup"><span data-stu-id="33ad2-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="33ad2-167">Postup kanálu a naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="33ad2-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="33ad2-168">Dalším krokem při psaní vlastních přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klienta a z <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="33ad2-169">Vrstvy kanálu využívá vzor objekt factory pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="33ad2-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="33ad2-170">WCF poskytuje pomocné rutiny základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="33ad2-170">WCF provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="33ad2-171"><xref:System.ServiceModel.Channels.CommunicationObject> Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stav stavového stroje výše popsané v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="33ad2-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="33ad2-172">''<xref:System.ServiceModel.Channels.ChannelManagerBase> Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-172">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="33ad2-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídu, která implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="33ad2-174">''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a dojde ke konsolidaci `CreateChannel` přetížení do jednoho `OnCreateChannel` abstraktní metodu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-174">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="33ad2-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="33ad2-176">Se má na starosti správu základních stavu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="33ad2-177">V této ukázce implementace objektu factory, je součástí UdpChannelFactory.cs a implementace naslouchací proces je obsažený v UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="33ad2-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="33ad2-178"><xref:System.ServiceModel.Channels.IChannel> Implementace jsou UdpOutputChannel.cs a UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="33ad2-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="33ad2-179">UDP kanálu</span><span class="sxs-lookup"><span data-stu-id="33ad2-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="33ad2-180">`UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="33ad2-181">Ukázka přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> k poskytování přístupu k zpráva verzi kodér zpráv.</span><span class="sxs-lookup"><span data-stu-id="33ad2-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="33ad2-182">Ukázka také přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby jsme přerušit naše instanci <xref:System.ServiceModel.Channels.BufferManager> když přejde stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="33ad2-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="33ad2-183">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="33ad2-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="33ad2-184">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="33ad2-185">Ověří argumenty konstruktoru a vytvoří cíl <xref:System.Net.EndPoint> na základě objektu <xref:System.ServiceModel.EndpointAddress> , je předaná.</span><span class="sxs-lookup"><span data-stu-id="33ad2-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="33ad2-186">Kanál je možné uzavřít řádně nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="33ad2-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="33ad2-187">Pokud je kanál řádně uzavřen soketu se zavře a je volána v základní třídě `OnClose` metoda.</span><span class="sxs-lookup"><span data-stu-id="33ad2-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="33ad2-188">Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="33ad2-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="33ad2-189">Potom implementovat `Send()` a `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="33ad2-190">To rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="33ad2-190">This breaks down into two main sections.</span></span> <span data-ttu-id="33ad2-191">Nejprve jsme serializovat zprávy do bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="33ad2-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="33ad2-192">Potom pošleme Výsledná data v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="33ad2-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="33ad2-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="33ad2-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="33ad2-194">'' UdpChannelListener, který implementuje ukázce je odvozena z <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="33ad2-194">The``UdpChannelListener that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="33ad2-195">Pro jediný soket UDP používá pro příjem datagramy.</span><span class="sxs-lookup"><span data-stu-id="33ad2-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="33ad2-196">`OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčce.</span><span class="sxs-lookup"><span data-stu-id="33ad2-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="33ad2-197">Data jsou potom převedou do zprávy pomocí rozhraní kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="33ad2-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="33ad2-198">Protože stejné kanálu datagramu představuje zprávy, které přicházejí z mnoha zdrojů, `UdpChannelListener` naslouchací proces typu singleton.</span><span class="sxs-lookup"><span data-stu-id="33ad2-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="33ad2-199">Není ve většině, jednu aktivní <xref:System.ServiceModel.Channels.IChannel>'' přidružené k této naslouchací proces najednou.</span><span class="sxs-lookup"><span data-stu-id="33ad2-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel>``associated with this listener at a time.</span></span> <span data-ttu-id="33ad2-200">Ukázka generuje jiný pouze v případě, že kanál, který je vrácen rutinou `AcceptChannel` metoda je následně zlikvidován.</span><span class="sxs-lookup"><span data-stu-id="33ad2-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="33ad2-201">Při příjmu zprávy je zařazených do fronty do tohoto kanálu, typu singleton.</span><span class="sxs-lookup"><span data-stu-id="33ad2-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="33ad2-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="33ad2-202">UdpInputChannel</span></span>  
 <span data-ttu-id="33ad2-203">`UdpInputChannel` Třída implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="33ad2-204">Skládá se z fronty příchozích zpráv, které se nacházejí `UdpChannelListener`je soketu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="33ad2-205">Tyto zprávy jsou vyjmutou pomocí `IInputChannel.Receive` metoda.</span><span class="sxs-lookup"><span data-stu-id="33ad2-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="33ad2-206">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="33ad2-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="33ad2-207">Teď, když jsou vytvořeny objekty pro vytváření a kanály, jsme musí vystavit modulu runtime ServiceModel prostřednictvím vazbu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="33ad2-208">Vazba je kolekci elementů vazby, která reprezentuje komunikačního balíku přidružená adresa služby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="33ad2-209">Každý prvek v zásobníku je reprezentována [ \<vazby >](../../../../docs/framework/misc/binding.md) element.</span><span class="sxs-lookup"><span data-stu-id="33ad2-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="33ad2-210">V ukázce je prvku vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="33ad2-211">Přepíše následující metody pro vytvoření objektů Factory související s naše vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="33ad2-212">Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="33ad2-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="33ad2-213">Přidání podpory Metadata pro přenos vazby – Element</span><span class="sxs-lookup"><span data-stu-id="33ad2-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="33ad2-214">Při integraci naše přenosu do systému metadata, jsme musí podporovat import a export zásad.</span><span class="sxs-lookup"><span data-stu-id="33ad2-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="33ad2-215">To umožňuje vygenerovat klienti naše vazby prostřednictvím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="33ad2-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="33ad2-216">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="33ad2-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="33ad2-217">Element vazby přenosu ve vazbě zodpovídá pro export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="33ad2-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="33ad2-218">Při použití vazby protokolu SOAP, element vazby přenosu by také exportovat správné přenosu URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="33ad2-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="33ad2-219">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="33ad2-219">WSDL Export</span></span>  
 <span data-ttu-id="33ad2-220">Chcete-li exportovat informace o přidělování `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33ad2-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="33ad2-221">`ExportEndpoint` Metoda přidá správné informace o přidělování do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="33ad2-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="33ad2-222">`UdpTransportBindingElement` Implementace `ExportEndpoint` metoda zároveň exportuje přenos identifikátor URI, pokud koncový bod používá vazbu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="33ad2-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="33ad2-223">Import schématu WSDL</span><span class="sxs-lookup"><span data-stu-id="33ad2-223">WSDL Import</span></span>  
 <span data-ttu-id="33ad2-224">Rozšíření systému importu WSDL pro zpracování importu adres, nemůžeme přidat následující konfigurace konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="33ad2-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="33ad2-225">Když spustíte Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst import rozšíření schématu WSDL:</span><span class="sxs-lookup"><span data-stu-id="33ad2-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="33ad2-226">Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.</span><span class="sxs-lookup"><span data-stu-id="33ad2-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="33ad2-227">Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="33ad2-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="33ad2-228">`UdpBindingElementImporter` Zadejte implementuje `IWsdlImportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33ad2-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="33ad2-229">`ImportEndpoint` Metoda importuje adresu z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="33ad2-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="33ad2-230">Přidání zásady podpory</span><span class="sxs-lookup"><span data-stu-id="33ad2-230">Adding Policy Support</span></span>  
 <span data-ttu-id="33ad2-231">Vlastní vazby element můžete exportovat zásady kontrolní výrazy ve vazbě WSDL pro koncový bod služby do express možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="33ad2-232">Export zásad</span><span class="sxs-lookup"><span data-stu-id="33ad2-232">Policy Export</span></span>  
 <span data-ttu-id="33ad2-233">`UdpTransportBindingElement` Zadejte implementuje `IPolicyExportExtension` přidání podpory pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="33ad2-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="33ad2-234">V důsledku toho `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` při generování zásad u všech vazby, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="33ad2-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="33ad2-235">V `IPolicyExportExtension.ExportPolicy`, přidáme kontrolní výrazy pro UDP a jiné assertion Pokud Snažíme se v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="33ad2-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="33ad2-236">Toto je vzhledem k tomu, že má vliv na režimu vícesměrového vysílání jak komunikačního balíku je vytvořený a proto musí být koordinované mezi na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="33ad2-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="33ad2-237">Protože elementů přenosové vlastní vazby je zodpovědná za zpracování adresy, `IPolicyExportExtension` implementace na `UdpTransportBindingElement` musí také zpracovat export příslušné WS-Addressing kontrolních výrazů zásad označující verzi adresování WS používá.</span><span class="sxs-lookup"><span data-stu-id="33ad2-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="33ad2-238">Import zásady</span><span class="sxs-lookup"><span data-stu-id="33ad2-238">Policy Import</span></span>  
 <span data-ttu-id="33ad2-239">Rozšířit systém Import zásady, nemůžeme přidat následující konfigurace konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="33ad2-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="33ad2-240">Pak můžeme implementovat `IPolicyImporterExtension` z našich registrované třídy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="33ad2-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="33ad2-241">V `ImportPolicy()`, jsme Projděte kontrolní výrazy v našem oboru názvů a zpracovat těm, které jsou pro generování přenosu a zkontrolujte, zda je vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="33ad2-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="33ad2-242">Také jsme musí odebrat příslušné kontrolní výrazy, které jsme zpracovat ze seznamu vazby kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="33ad2-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="33ad2-243">Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:</span><span class="sxs-lookup"><span data-stu-id="33ad2-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="33ad2-244">Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.</span><span class="sxs-lookup"><span data-stu-id="33ad2-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="33ad2-245">Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="33ad2-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="33ad2-246">Přidání standardní vazby</span><span class="sxs-lookup"><span data-stu-id="33ad2-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="33ad2-247">Naše prvku vazby lze použít v následujících dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="33ad2-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="33ad2-248">Prostřednictvím vlastní vazby: vlastní vazby umožňuje uživateli vytvoření vlastní vazby založené na libovolnou sadu elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="33ad2-249">Pomocí vazby poskytované systémem, který zahrnuje naše prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="33ad2-250">WCF poskytuje několik z těchto vazeb definovaná systémem, jako `BasicHttpBinding`, `NetTcpBinding`, a `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="33ad2-251">Každá z těchto vazeb je přidružen k profilu dobře definovaný.</span><span class="sxs-lookup"><span data-stu-id="33ad2-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="33ad2-252">Ukázka implementuje vazba profilu v `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="33ad2-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="33ad2-253">`SampleProfileUdpBinding` Obsahuje až čtyři prvky vazeb v něm: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="33ad2-254">Přidání vlastních standardní vazby – Importér</span><span class="sxs-lookup"><span data-stu-id="33ad2-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="33ad2-255">Svcutil.exe a `WsdlImporter` typu, ve výchozím nastavení, rozpozná a importuje definovaná systémem vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="33ad2-256">Jinak získává importovat, protože vazba `CustomBinding` instance.</span><span class="sxs-lookup"><span data-stu-id="33ad2-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="33ad2-257">Chcete-li povolit Svcutil.exe a `WsdlImporter` k importu `SampleProfileUdpBinding` `UdpBindingElementImporter` taky funguje jako – Importér vlastní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="33ad2-258">Implementuje – Importér vlastní standardní vazby `ImportEndpoint` metodu `IWsdlImportExtension` rozhraní prozkoumat `CustomBinding` instance importovat z metadat zobrazíte, zda se může vygenerovat konkrétní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="33ad2-259">Obecně platí implementace – Importér vlastní standardní vazby zahrnuje kontrolu vlastnosti prvky importované vazby pro ověření, že pouze vlastnosti, které by mohly být nastaveny standardní vazbou změnily a všechny ostatní vlastnosti jsou jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33ad2-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="33ad2-260">Základní strategii pro implementaci – Importér standardní vazba je vytvoření instance standardní vazby, rozšířit vlastnosti z elementů vazby standardní vazby instanci, která podporuje standardní vazby a porovnání vazby elementy ze standardní vazba s prvky importované vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="33ad2-261">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="33ad2-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="33ad2-262">Ke zveřejnění naše přenosu prostřednictvím konfigurace, musíme implementovat dvě konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="33ad2-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="33ad2-263">První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="33ad2-264">Toto je tak, aby `CustomBinding` implementace může odkazovat naše prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="33ad2-265">Druhý `Configuration` pro naše `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="33ad2-266">Rozšíření elementu vazby</span><span class="sxs-lookup"><span data-stu-id="33ad2-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="33ad2-267">V části `UdpTransportElement` je `BindingElementExtensionElement` která zveřejňuje `UdpTransportBindingElement` v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="33ad2-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="33ad2-268">S několika základní přepsání jsme definovali naše název konfiguračního oddílu, typ elementu naše vazby a postup vytvoření naše prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="33ad2-269">Naše oddílu rozšíření jsme pak můžete zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="33ad2-270">Rozšíření můžete odkazovat z vlastních vazeb, používat UDP jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="33ad2-271">Část vazby</span><span class="sxs-lookup"><span data-stu-id="33ad2-271">Binding Section</span></span>  
 <span data-ttu-id="33ad2-272">V části `SampleProfileUdpBindingCollectionElement` je `StandardBindingCollectionElement` která zveřejňuje `SampleProfileUdpBinding` v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="33ad2-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="33ad2-273">Hromadné implementace je delegovaný jako `SampleProfileUdpBindingConfigurationElement`, která je odvozena z `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="33ad2-274">`SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `SampleProfileUdpBinding`a funkce pro mapování z `ConfigurationElement` vazby.</span><span class="sxs-lookup"><span data-stu-id="33ad2-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="33ad2-275">Nakonec přepsání `OnApplyConfiguration` metoda v našem `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="33ad2-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="33ad2-276">K registraci této obslužné rutiny konfigurace systému, přidáme v následující části relevantní konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="33ad2-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="33ad2-277">Potom může být odkaz z serviceModel konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="33ad2-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="33ad2-278">Služba Test UDP a klienta</span><span class="sxs-lookup"><span data-stu-id="33ad2-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="33ad2-279">Testovacího kódu pro použití přenosu Tato ukázka je dostupná v adresáři UdpTestService a UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="33ad2-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="33ad2-280">Kód služby se skládá ze dvou testy – jeden test nastaví vazby a koncových bodů z kódu a dalších nemá prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="33ad2-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="33ad2-281">Oba testy používají dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="33ad2-281">Both tests use two endpoints.</span></span> <span data-ttu-id="33ad2-282">Používá jeden koncový bod `SampleUdpProfileBinding` s [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `true`.</span></span> <span data-ttu-id="33ad2-283">Jiný koncový bod používá vlastní vazby s `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="33ad2-284">Jde o ekvivalent pomocí `SampleUdpProfileBinding` s [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="33ad2-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `false`.</span></span> <span data-ttu-id="33ad2-285">Oba testy vytvoření služby, přidat koncový bod pro každou vazbu, otevřete službu a potom počkejte uživatelům před jeho zavřením službu stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="33ad2-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="33ad2-286">Když spustíte testovací aplikaci služby byste měli vidět následující výstup.</span><span class="sxs-lookup"><span data-stu-id="33ad2-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="33ad2-287">Když pak spustíte test klientská aplikace proti publikované koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="33ad2-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="33ad2-288">Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odesílá zprávy pět na každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="33ad2-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="33ad2-289">Následující výstup je v klientovi.</span><span class="sxs-lookup"><span data-stu-id="33ad2-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="33ad2-290">Níže je úplný výstup ve službě.</span><span class="sxs-lookup"><span data-stu-id="33ad2-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="33ad2-291">Ke spouštění klientskou aplikaci publikovat pomocí konfigurace koncových bodů, stiskněte ENTER na službu a poté znovu spusťte testovacího klienta.</span><span class="sxs-lookup"><span data-stu-id="33ad2-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="33ad2-292">Měli byste vidět následující výstup ve službě.</span><span class="sxs-lookup"><span data-stu-id="33ad2-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="33ad2-293">Znovu spustit klienta vypočítá stejný jako předchozí výsledky.</span><span class="sxs-lookup"><span data-stu-id="33ad2-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="33ad2-294">Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující Svcutil.exe z kořenového adresáře vzorku.</span><span class="sxs-lookup"><span data-stu-id="33ad2-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="33ad2-295">Všimněte si, že Svcutil.exe negeneruje vazby konfigurace rozšíření pro `SampleProfileUdpBinding`, takže je třeba přidat ji ručně.</span><span class="sxs-lookup"><span data-stu-id="33ad2-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33ad2-296">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="33ad2-296">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="33ad2-297">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33ad2-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="33ad2-298">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33ad2-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="33ad2-299">Naleznete v předchozí části "UDP testovací služby a klient".</span><span class="sxs-lookup"><span data-stu-id="33ad2-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33ad2-300">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="33ad2-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33ad2-301">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="33ad2-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33ad2-302">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="33ad2-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33ad2-303">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="33ad2-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
