---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143769"
---
# <a name="transport-udp"></a><span data-ttu-id="81976-102">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="81976-102">Transport: UDP</span></span>
<span data-ttu-id="81976-103">Ukázka přenosu UDP ukazuje, jak implementovat jednosměrové a vícesměrové vysílání UDP jako vlastní přenos Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="81976-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="81976-104">Ukázka popisuje doporučený postup pro vytvoření vlastní přenos v WCF pomocí rozhraní kanálu a následující WCF osvědčené postupy.</span><span class="sxs-lookup"><span data-stu-id="81976-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="81976-105">Kroky k vytvoření vlastní přenos jsou následující:</span><span class="sxs-lookup"><span data-stu-id="81976-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="81976-106">Rozhodněte, který z kanálu [Vzorky výměny zpráv](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel nebo IReplyChannel) bude podporovat vaše ChannelFactory a ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="81976-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="81976-107">Pak se rozhodněte, zda budete podporovat relace varianty těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81976-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="81976-108">Vytvořte továrnu kanálu a naslouchací proces, který podporuje váš vzor výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="81976-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="81976-109">Ujistěte se, že všechny výjimky specifické pro síť <xref:System.ServiceModel.CommunicationException>jsou normalizovány na příslušnou odvozenou třídu .</span><span class="sxs-lookup"><span data-stu-id="81976-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="81976-110">Přidejte element [ \<>vazby,](../../configure-apps/file-schema/wcf/bindings.md) který přidá vlastní přenos do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="81976-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="81976-111">Další informace naleznete [v tématu Přidání elementu vazby](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="81976-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="81976-112">Přidejte oddíl rozšíření elementu vazby, který zpřístupní nový element vazby do konfiguračního systému.</span><span class="sxs-lookup"><span data-stu-id="81976-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="81976-113">Přidejte rozšíření metadat pro komunikaci schopností s jinými koncovými body.</span><span class="sxs-lookup"><span data-stu-id="81976-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="81976-114">Přidejte vazbu, která předem konfiguruje zásobník prvků vazby podle dobře definovaného profilu.</span><span class="sxs-lookup"><span data-stu-id="81976-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="81976-115">Další informace naleznete [v tématu Přidání standardní vazby](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="81976-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="81976-116">Přidejte oddíl vazby a prvek konfigurace vazby, abyste zpřístupní vazbu konfiguračnímu systému.</span><span class="sxs-lookup"><span data-stu-id="81976-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="81976-117">Další informace naleznete [v tématu Adding Configuration Support](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="81976-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="81976-118">Vzory výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="81976-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="81976-119">Prvním krokem při psaní vlastní přenos je rozhodnout, které vzory výměny zpráv (MEPs) jsou požadovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="81976-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="81976-120">Na výběr jsou tři poslanci:</span><span class="sxs-lookup"><span data-stu-id="81976-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="81976-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="81976-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="81976-122">Při použití datagram MEP, klient odešle zprávu pomocí "fire and forget" exchange.</span><span class="sxs-lookup"><span data-stu-id="81976-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="81976-123">Výměna ohně a zapomenout je ten, který vyžaduje mimo-of-band potvrzení úspěšnédodávky.</span><span class="sxs-lookup"><span data-stu-id="81976-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="81976-124">Zpráva může být při přenosu ztracena a nikdy se nedostanete ke službě.</span><span class="sxs-lookup"><span data-stu-id="81976-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="81976-125">Pokud operace odeslání úspěšně dokončena na konci klienta, nezaručuje, že vzdálený koncový bod přijal zprávu.</span><span class="sxs-lookup"><span data-stu-id="81976-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="81976-126">Datagram je základním stavebním kamenem pro zasílání zpráv, protože můžete vytvořit vlastní protokoly na vrcholu - včetně spolehlivých protokolů a zabezpečených protokolů.</span><span class="sxs-lookup"><span data-stu-id="81976-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="81976-127">Kanály datagramu <xref:System.ServiceModel.Channels.IOutputChannel> klienta implementují <xref:System.ServiceModel.Channels.IInputChannel> rozhraní a kanály datagramů služeb implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81976-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="81976-128">Požadavek-odpověď (iRequestChannel/iReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="81976-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="81976-129">V tomto poslanci EP je odeslána zpráva a je přijata odpověď.</span><span class="sxs-lookup"><span data-stu-id="81976-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="81976-130">Vzor se skládá z dvojice požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="81976-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="81976-131">Příklady volání požadavek odpověď jsou vzdálená volání procedur (RPC) a prohlížeče GETs.</span><span class="sxs-lookup"><span data-stu-id="81976-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="81976-132">Tento vzor je také známý jako Half-Duplex.</span><span class="sxs-lookup"><span data-stu-id="81976-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="81976-133">V tomto MEP klientské kanály implementují <xref:System.ServiceModel.Channels.IRequestChannel> a služby implementují <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="81976-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="81976-134">Duplex (iduplexchannel)</span><span class="sxs-lookup"><span data-stu-id="81976-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="81976-135">Duplexní MEP umožňuje libovolný počet zpráv, které mají být odeslány klientem a přijaty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="81976-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="81976-136">Duplexní europoslanec je jako telefonní rozhovor, kde každé slovo, které se mluví, je zpráva.</span><span class="sxs-lookup"><span data-stu-id="81976-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="81976-137">Vzhledem k tomu, že obě strany mohou odesílat a <xref:System.ServiceModel.Channels.IDuplexChannel>přijímat v tomto MEP, rozhraní implementované klientem a kanály služeb je .</span><span class="sxs-lookup"><span data-stu-id="81976-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="81976-138">Každý z těchto poslanců evropského parlamentu může rovněž podpořit zasedání.</span><span class="sxs-lookup"><span data-stu-id="81976-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="81976-139">Přidané funkce poskytované relace podporující kanál je, že koreluje všechny zprávy odeslané a přijaté na kanálu.</span><span class="sxs-lookup"><span data-stu-id="81976-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="81976-140">Vzor požadavek odpověď je samostatná relace dvou zpráv, jako požadavek a odpověď jsou korelovány.</span><span class="sxs-lookup"><span data-stu-id="81976-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="81976-141">Naproti tomu vzor požadavku a odpovědi, který podporuje relace znamená, že všechny páry požadavků a odpovědí na tomto kanálu jsou vzájemně korelovány.</span><span class="sxs-lookup"><span data-stu-id="81976-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="81976-142">Získáte tak celkem šest poslanců – Datagram, Požadavek na odpověď, Oboustranný tisk, Datagram s relacemi, Požadavek na odpověď s relacemi a Oboustranný tisk s relacemi – ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="81976-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81976-143">Pro přenos UDP je jediným podporovaným mep datagramem, protože Protokol UDP je ze své podstaty protokol "fire and forget".</span><span class="sxs-lookup"><span data-stu-id="81976-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="81976-144">Životní cyklus objektu ICommunicationObject a objektu WCF</span><span class="sxs-lookup"><span data-stu-id="81976-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="81976-145">WCF má společný stavový počítač, který se používá <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory>pro <xref:System.ServiceModel.Channels.IChannelListener> správu životního cyklu objektů, jako je , a které se používají pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="81976-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="81976-146">Existuje pět stavů, ve kterých mohou existovat tyto komunikační objekty.</span><span class="sxs-lookup"><span data-stu-id="81976-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="81976-147">Tyto stavy jsou <xref:System.ServiceModel.CommunicationState> reprezentovány výčtu a jsou následující:</span><span class="sxs-lookup"><span data-stu-id="81976-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="81976-148">Vytvořeno: Toto je <xref:System.ServiceModel.ICommunicationObject> stav, kdy je první instance.</span><span class="sxs-lookup"><span data-stu-id="81976-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="81976-149">V tomto stavu se nevyskytuje žádný vstup/výstup (V/V).</span><span class="sxs-lookup"><span data-stu-id="81976-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="81976-150">Otevření: Objekty přechod <xref:System.ServiceModel.ICommunicationObject.Open%2A> do tohoto stavu, když je volána.</span><span class="sxs-lookup"><span data-stu-id="81976-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="81976-151">V tomto okamžiku jsou vlastnosti neměnné a vstup/výstup může začít.</span><span class="sxs-lookup"><span data-stu-id="81976-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="81976-152">Tento přechod je platný pouze ze stavu Vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="81976-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="81976-153">Otevřeno: Objekty přecházejí do tohoto stavu po dokončení otevřeného procesu.</span><span class="sxs-lookup"><span data-stu-id="81976-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="81976-154">Tento přechod je platný pouze ze stavu Otevření.</span><span class="sxs-lookup"><span data-stu-id="81976-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="81976-155">V tomto okamžiku je objekt plně použitelný pro přenos.</span><span class="sxs-lookup"><span data-stu-id="81976-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="81976-156">Uzávěrka: Objekty <xref:System.ServiceModel.ICommunicationObject.Close%2A> přechod do tohoto stavu, když se nazývá pro řádné vypnutí.</span><span class="sxs-lookup"><span data-stu-id="81976-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="81976-157">Tento přechod je platný pouze ze stavu Otevřeno.</span><span class="sxs-lookup"><span data-stu-id="81976-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="81976-158">Uzavřeno: V uzavřeném stavu objekty již nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="81976-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="81976-159">Obecně platí, že většina konfigurace je stále přístupná pro kontrolu, ale nemůže dojít k žádné komunikaci.</span><span class="sxs-lookup"><span data-stu-id="81976-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="81976-160">Tento stav je ekvivalentní vyřazení.</span><span class="sxs-lookup"><span data-stu-id="81976-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="81976-161">Chyba: V chybovaném stavu jsou objekty přístupné kontrole, ale již nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="81976-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="81976-162">Dojde-li k neobnovitelné chybě, objekt přejde do tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="81976-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="81976-163">Jediný platný přechod z tohoto `Closed` stavu je do stavu.</span><span class="sxs-lookup"><span data-stu-id="81976-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="81976-164">Existují události, které požár u každého přechodu stavu.</span><span class="sxs-lookup"><span data-stu-id="81976-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="81976-165">Metoda <xref:System.ServiceModel.ICommunicationObject.Abort%2A> může být volána kdykoli a způsobí, že objekt přechod okamžitě z aktuálního stavu do stavu Uzavřeno.</span><span class="sxs-lookup"><span data-stu-id="81976-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="81976-166">Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.</span><span class="sxs-lookup"><span data-stu-id="81976-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="81976-167">Factory kanálu a naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="81976-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="81976-168">Dalším krokem při psaní vlastní přenos je <xref:System.ServiceModel.Channels.IChannelFactory> vytvořit implementaci pro <xref:System.ServiceModel.Channels.IChannelListener> klientské kanály a pro kanály služeb.</span><span class="sxs-lookup"><span data-stu-id="81976-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="81976-169">Vrstva kanálu používá pro vytváření kanálů vzor výroby.</span><span class="sxs-lookup"><span data-stu-id="81976-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="81976-170">WCF poskytuje základní třídy pomocné soubory pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="81976-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="81976-171">Třída <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavový počítač, který byl dříve popsán v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="81976-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="81976-172">Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="81976-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="81976-173">Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> pracuje ve <xref:System.ServiceModel.Channels.ChannelBase>spojení s , což je <xref:System.ServiceModel.Channels.IChannel>základní třída, která implementuje .</span><span class="sxs-lookup"><span data-stu-id="81976-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="81976-174">Třída <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.IChannelFactory> a `CreateChannel` konsoliduje `OnCreateChannel` přetížení do jedné abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="81976-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="81976-175">Třída <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="81976-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="81976-176">Stará se o základní státní řízení.</span><span class="sxs-lookup"><span data-stu-id="81976-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="81976-177">V této ukázce je implementace továrny obsažena v UdpChannelFactory.cs a implementace naslouchací proces je obsažena v UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="81976-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="81976-178">Implementace <xref:System.ServiceModel.Channels.IChannel> jsou v UdpOutputChannel.cs a UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="81976-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="81976-179">Továrna kanálu UDP</span><span class="sxs-lookup"><span data-stu-id="81976-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="81976-180">Pochází `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="81976-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="81976-181">Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> poskytnout přístup k verzi zprávy kodéru zprávy.</span><span class="sxs-lookup"><span data-stu-id="81976-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="81976-182">Ukázka také <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přepíše, takže můžeme strhnout naši instanci <xref:System.ServiceModel.Channels.BufferManager> při přechodu stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="81976-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="81976-183">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="81976-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="81976-184">Nářadí `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="81976-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="81976-185">Konstruktor ověří argumenty a vytvoří <xref:System.Net.EndPoint> cílový objekt <xref:System.ServiceModel.EndpointAddress> na základě, který je předán palců</span><span class="sxs-lookup"><span data-stu-id="81976-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="81976-186">Kanál může být uzavřen elegantně nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="81976-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="81976-187">Pokud je kanál řádně uzavřen, soket je uzavřen a `OnClose` je provedeno volání metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="81976-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="81976-188">Pokud to vyvolá výjimku, `Abort` volání infrastruktury k zajištění kanálu je vyčištěna.</span><span class="sxs-lookup"><span data-stu-id="81976-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="81976-189">Pak `Send()` implementujeme a `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="81976-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="81976-190">To se rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="81976-190">This breaks down into two main sections.</span></span> <span data-ttu-id="81976-191">Nejprve serializujeme zprávu do bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="81976-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="81976-192">Pak pošleme výsledná data na drátu.</span><span class="sxs-lookup"><span data-stu-id="81976-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="81976-193">Naslouchací proces UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="81976-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="81976-194">Ukázka `UdpChannelListener` implementuje odvodí z třídy. <xref:System.ServiceModel.Channels.ChannelListenerBase></span><span class="sxs-lookup"><span data-stu-id="81976-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="81976-195">Používá jeden soket UDP pro příjem datagramů.</span><span class="sxs-lookup"><span data-stu-id="81976-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="81976-196">Metoda `OnOpen` přijímá data pomocí soketu UDP v asynchronní smyčce.</span><span class="sxs-lookup"><span data-stu-id="81976-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="81976-197">Data jsou pak převedeny na zprávy pomocí rozhraní pro kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="81976-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="81976-198">Vzhledem k tomu, že stejný kanál datagram `UdpChannelListener` představuje zprávy, které přicházejí z několika zdrojů, je naslouchací proces singleton.</span><span class="sxs-lookup"><span data-stu-id="81976-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="81976-199">Je maximálně jeden aktivní <xref:System.ServiceModel.Channels.IChannel> přidružené k tomuto naslouchací proces v době.</span><span class="sxs-lookup"><span data-stu-id="81976-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="81976-200">Vzorek generuje jiný pouze v případě, že `AcceptChannel` kanál, který je vrácen metodou je následně vyřazen.</span><span class="sxs-lookup"><span data-stu-id="81976-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="81976-201">Po přijetí zprávy je zařazendo fronty do tohoto kanálu singleton.</span><span class="sxs-lookup"><span data-stu-id="81976-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="81976-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="81976-202">UdpInputChannel</span></span>  
 <span data-ttu-id="81976-203">Třída `UdpInputChannel` implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="81976-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="81976-204">Skládá se z fronty příchozích zpráv, která `UdpChannelListener`je naplněna soketem společnosti .</span><span class="sxs-lookup"><span data-stu-id="81976-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="81976-205">Tyto zprávy jsou dequeued `IInputChannel.Receive` metodou.</span><span class="sxs-lookup"><span data-stu-id="81976-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="81976-206">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="81976-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="81976-207">Nyní, když jsou vytvořeny továrny a kanály, musíme vystavit je ServiceModel runtime prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="81976-208">Vazba je kolekce elementů vazby, která představuje zásobník komunikace přidružené k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="81976-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="81976-209">Každý prvek v zásobníku je reprezentován [ \<vazby>](../../configure-apps/file-schema/wcf/bindings.md) prvek.</span><span class="sxs-lookup"><span data-stu-id="81976-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="81976-210">Ve vzorku je `UdpTransportBindingElement`prvek vazby , <xref:System.ServiceModel.Channels.TransportBindingElement>který je odvozen od .</span><span class="sxs-lookup"><span data-stu-id="81976-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="81976-211">Přepíše následující metody k vybudování továrny spojené s naší vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="81976-212">Obsahuje také členy pro `BindingElement` klonování a vrácení našeho schématu (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="81976-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="81976-213">Přidání podpory metadat pro prvek vazby přenosu</span><span class="sxs-lookup"><span data-stu-id="81976-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="81976-214">Abychom integrovali náš transport do systému metadat, musíme podporovat jak import, tak export politiky.</span><span class="sxs-lookup"><span data-stu-id="81976-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="81976-215">To nám umožňuje generovat klienty naší vazby prostřednictvím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="81976-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="81976-216">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="81976-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="81976-217">Prvek vazby přenosu ve vazbě je zodpovědný za export a import adresování informací v metadatech.</span><span class="sxs-lookup"><span data-stu-id="81976-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="81976-218">Při použití soap vazby, prvek vazby přenosu by měl také exportovat správný identifikátor URI přenosu v metadatech.</span><span class="sxs-lookup"><span data-stu-id="81976-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="81976-219">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="81976-219">WSDL Export</span></span>  
 <span data-ttu-id="81976-220">Chcete-li exportovat adresování informace `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81976-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="81976-221">Metoda `ExportEndpoint` přidá správné informace o adresování wsdl port.</span><span class="sxs-lookup"><span data-stu-id="81976-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="81976-222">Implementace `UdpTransportBindingElement` `ExportEndpoint` metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP.</span><span class="sxs-lookup"><span data-stu-id="81976-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="81976-223">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="81976-223">WSDL Import</span></span>  
 <span data-ttu-id="81976-224">Chcete-li rozšířit systém importu WSDL pro zpracování importu adres, musíme přidat následující konfiguraci do konfiguračního souboru pro Svcutil.exe, jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="81976-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="81976-225">Při spuštění svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="81976-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="81976-226">Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.</span><span class="sxs-lookup"><span data-stu-id="81976-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="81976-227">Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="81976-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="81976-228">Typ `UdpBindingElementImporter` implementuje `IWsdlImportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81976-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="81976-229">Metoda `ImportEndpoint` importuje adresu z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="81976-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="81976-230">Přidání podpory zásad</span><span class="sxs-lookup"><span data-stu-id="81976-230">Adding Policy Support</span></span>  
 <span data-ttu-id="81976-231">Vlastní element vazby můžete exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby vyjádřit možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="81976-232">Export zásad</span><span class="sxs-lookup"><span data-stu-id="81976-232">Policy Export</span></span>  
 <span data-ttu-id="81976-233">Typ `UdpTransportBindingElement` implementuje `IPolicyExportExtension` přidat podporu pro zásady exportu.</span><span class="sxs-lookup"><span data-stu-id="81976-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="81976-234">V důsledku `System.ServiceModel.MetadataExporter` toho `UdpTransportBindingElement` zahrnuje v generování zásad pro všechny vazby, která ji zahrnuje.</span><span class="sxs-lookup"><span data-stu-id="81976-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="81976-235">V `IPolicyExportExtension.ExportPolicy`aplikaci přidáme kontrolní výraz pro UDP a další kontrolní výraz, pokud jsme v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="81976-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="81976-236">Důvodem je, že režim vícesměrového vysílání ovlivňuje způsob vytvoření zásobníku komunikace, a proto musí být koordinován mezi oběma stranami.</span><span class="sxs-lookup"><span data-stu-id="81976-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="81976-237">Vzhledem k tomu, že vlastní `IPolicyExportExtension` prvky `UdpTransportBindingElement` vazby přenosu jsou zodpovědné za zpracování adresování, implementace na musí také zpracovat export příslušných výrazů zásad WS-Addressing k označení verze ws adresování se používá.</span><span class="sxs-lookup"><span data-stu-id="81976-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="81976-238">Import zásad</span><span class="sxs-lookup"><span data-stu-id="81976-238">Policy Import</span></span>  
 <span data-ttu-id="81976-239">Chcete-li rozšířit systém importu zásad, musíme přidat následující konfiguraci do konfiguračního souboru pro Svcutil.exe, jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="81976-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="81976-240">Pak implementujeme `IPolicyImporterExtension` z`UdpBindingElementImporter`naší registrované třídy ( ).</span><span class="sxs-lookup"><span data-stu-id="81976-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="81976-241">V `ImportPolicy()`oblasti se podíváme na kontrolní výrazy v našem oboru názvů a zpracujeme ty, které generují přenos, a zkontrolujeme, zda se jedná o vícesměrové vysílání.</span><span class="sxs-lookup"><span data-stu-id="81976-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="81976-242">Musíme také odebrat tvrzení, které zpracováváme ze seznamu tvrzení vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="81976-243">Opět platí, že při spuštění Svcutil.exe existují dvě možnosti integrace:</span><span class="sxs-lookup"><span data-stu-id="81976-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="81976-244">Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.</span><span class="sxs-lookup"><span data-stu-id="81976-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="81976-245">Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="81976-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="81976-246">Přidání standardní vazby</span><span class="sxs-lookup"><span data-stu-id="81976-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="81976-247">Náš vázací prvek lze použít následujícími dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="81976-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="81976-248">Prostřednictvím vlastní vazby: Vlastní vazba umožňuje uživateli vytvořit vlastní vazbu na základě libovolné sady prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="81976-249">Pomocí systémově poskytované vazby, která zahrnuje náš element vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="81976-250">WCF poskytuje řadu těchto systémem definované vazby, například `BasicHttpBinding`, `NetTcpBinding`a `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="81976-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="81976-251">Každá z těchto vazeb je spojena s dobře definovaným profilem.</span><span class="sxs-lookup"><span data-stu-id="81976-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="81976-252">Ukázka implementuje `SampleProfileUdpBinding`profil vazby <xref:System.ServiceModel.Channels.Binding>v , který je odvozen z .</span><span class="sxs-lookup"><span data-stu-id="81976-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="81976-253">Obsahuje `SampleProfileUdpBinding` v něm až čtyři `UdpTransportBindingElement`elementy vazby: , `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="81976-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="81976-254">Přidání vlastního standardního importu vazeb</span><span class="sxs-lookup"><span data-stu-id="81976-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="81976-255">Svcutil.exe a `WsdlImporter` typ ve výchozím nastavení rozpozná a importuje systémem definované vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="81976-256">V opačném případě vazba `CustomBinding` získá importován jako instance.</span><span class="sxs-lookup"><span data-stu-id="81976-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="81976-257">Chcete-li povolit Svcutil.exe `SampleProfileUdpBinding` `UdpBindingElementImporter` a `WsdlImporter` importovat také působí jako vlastní standardní vázací dovozce.</span><span class="sxs-lookup"><span data-stu-id="81976-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="81976-258">Vlastní standardní importér `ImportEndpoint` vazby `IWsdlImportExtension` implementuje `CustomBinding` metodu na rozhraní prozkoumat instanci importované z metadat a zjistit, zda mohla být generována konkrétní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="81976-259">Obecně platí, že implementace vlastní standardní vazby import zahrnuje kontrolu vlastností importované elementy vazby k ověření, že pouze vlastnosti, které mohly být nastaveny standardní vazby byly změněny a všechny ostatní vlastnosti jsou jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="81976-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="81976-260">Základní strategií pro implementaci standardního importu vazby je vytvoření instance standardní vazby, šíření vlastností z elementů vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnání vazby prvky ze standardní vazby s importovanými prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="81976-261">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="81976-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="81976-262">Chcete-li vystavit náš přenos prostřednictvím konfigurace, musíme implementovat dvě části konfigurace.</span><span class="sxs-lookup"><span data-stu-id="81976-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="81976-263">První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="81976-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="81976-264">To je `CustomBinding` tak, že implementace můžete odkazovat na náš element vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="81976-265">Druhý je `Configuration` pro `SampleProfileUdpBinding`naše .</span><span class="sxs-lookup"><span data-stu-id="81976-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="81976-266">Element rozšíření prvku vazby</span><span class="sxs-lookup"><span data-stu-id="81976-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="81976-267">Sekce `UdpTransportElement` `BindingElementExtensionElement` je, která `UdpTransportBindingElement` zpřístupňuje konfiguračnísystém.</span><span class="sxs-lookup"><span data-stu-id="81976-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="81976-268">Pomocí několika základních přepsání definujeme název konfiguračního oddílu, typ našeho prvku vazby a způsob vytvoření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="81976-269">Naši příponou pak můžeme zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81976-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="81976-270">Rozšíření lze odkazovat z vlastní vazby použít UDP jako přenos.</span><span class="sxs-lookup"><span data-stu-id="81976-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="81976-271">Oddíl vazby</span><span class="sxs-lookup"><span data-stu-id="81976-271">Binding Section</span></span>  
 <span data-ttu-id="81976-272">Sekce `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` je, která `SampleProfileUdpBinding` zpřístupňuje konfiguračnísystém.</span><span class="sxs-lookup"><span data-stu-id="81976-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="81976-273">Převážná část implementace je delegována `SampleProfileUdpBindingConfigurationElement`na `StandardBindingElement`, který je odvozen z .</span><span class="sxs-lookup"><span data-stu-id="81976-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="81976-274">Má `SampleProfileUdpBindingConfigurationElement` vlastnosti, které odpovídají `SampleProfileUdpBinding`vlastnosti na , `ConfigurationElement` a funkce mapovat z vazby.</span><span class="sxs-lookup"><span data-stu-id="81976-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="81976-275">Nakonec přepsat metodu `OnApplyConfiguration` v `SampleProfileUdpBinding`našem , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="81976-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="81976-276">Chcete-li zaregistrovat tuto obslužnou rutinu v konfiguračním systému, přidáme do příslušného konfiguračního souboru následující část.</span><span class="sxs-lookup"><span data-stu-id="81976-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="81976-277">Potom lze odkazovat z části konfigurace serviceModel.</span><span class="sxs-lookup"><span data-stu-id="81976-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="81976-278">Testovací služba UDP a klient</span><span class="sxs-lookup"><span data-stu-id="81976-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="81976-279">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích UdpTestService a UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="81976-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="81976-280">Kód služby se skládá ze dvou testů – jeden test nastaví vazby a koncové body z kódu a druhý to provede prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="81976-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="81976-281">Oba testy používají dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="81976-281">Both tests use two endpoints.</span></span> <span data-ttu-id="81976-282">Jeden koncový bod `SampleUdpProfileBinding` používá s [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="81976-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="81976-283">Druhý koncový bod používá vlastní `UdpTransportBindingElement`vazbu s .</span><span class="sxs-lookup"><span data-stu-id="81976-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="81976-284">To je ekvivalentní `SampleUdpProfileBinding` použití s [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="81976-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="81976-285">Oba testy vytvoří službu, přidají koncový bod pro každou vazbu, otevřou službu a před ukončením služby počkáte na klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="81976-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="81976-286">Při spuštění aplikace test služby byste měli vidět následující výstup.</span><span class="sxs-lookup"><span data-stu-id="81976-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="81976-287">Potom můžete spustit testovací klientskou aplikaci proti publikovaným koncovým bodům.</span><span class="sxs-lookup"><span data-stu-id="81976-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="81976-288">Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odešle pět zpráv do každého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="81976-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="81976-289">Následující výstup je na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="81976-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="81976-290">Následuje úplný výstup ve službě.</span><span class="sxs-lookup"><span data-stu-id="81976-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="81976-291">Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER ve službě a spusťte testovacího klienta znovu.</span><span class="sxs-lookup"><span data-stu-id="81976-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="81976-292">Měli byste vidět následující výstup na službu.</span><span class="sxs-lookup"><span data-stu-id="81976-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="81976-293">Spuštění klienta znovu dává stejné jako předchozí výsledky.</span><span class="sxs-lookup"><span data-stu-id="81976-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="81976-294">Chcete-li znovu vygenerovat klientský kód a konfiguraci pomocí programu Svcutil.exe, spusťte aplikaci služby a spusťte následující soubor Svcutil.exe z kořenového adresáře ukázky.</span><span class="sxs-lookup"><span data-stu-id="81976-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="81976-295">Všimněte si, že Svcutil.exe negeneruje `SampleProfileUdpBinding`konfiguraci rozšíření vazby pro , takže je nutné přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="81976-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81976-296">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="81976-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="81976-297">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81976-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="81976-298">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81976-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="81976-299">Odkazovat na předchozí části "Testovací služba UDP a klienta".</span><span class="sxs-lookup"><span data-stu-id="81976-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="81976-300">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="81976-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81976-301">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="81976-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="81976-302">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="81976-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81976-303">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="81976-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
