---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 44e47dd2d291ffc27d1777a04b645d57984919cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591433"
---
# <a name="transport-udp"></a><span data-ttu-id="d306e-102">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="d306e-102">Transport: UDP</span></span>
<span data-ttu-id="d306e-103">Ukázka přenosu UDP demonstruje, jak implementovat jednosměrovou vysílání UDP a vícesměrové vysílání jako vlastní přenos Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d306e-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="d306e-104">Ukázka popisuje doporučený postup pro vytvoření vlastního přenosu ve službě WCF pomocí architektury kanálů a následujících osvědčených postupů pro WCF.</span><span class="sxs-lookup"><span data-stu-id="d306e-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="d306e-105">Postup vytvoření vlastního přenosu je následující:</span><span class="sxs-lookup"><span data-stu-id="d306e-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="d306e-106">Rozhodněte, které ze [vzorů výměny zpráv](#MessageExchangePatterns) kanálu (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) bude vaše třída ChannelFactory a ChannelListener podporovat.</span><span class="sxs-lookup"><span data-stu-id="d306e-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="d306e-107">Pak se rozhodněte, jestli budete podporovat variace relace těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d306e-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="d306e-108">Vytvořte objekt pro vytváření a naslouchací proces kanálu, který podporuje váš vzor výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="d306e-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="d306e-109">Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na příslušnou odvozenou třídu třídy <xref:System.ServiceModel.CommunicationException> .</span><span class="sxs-lookup"><span data-stu-id="d306e-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="d306e-110">Přidejte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, který přidá vlastní přenos do zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="d306e-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="d306e-111">Další informace naleznete v tématu [Přidání prvku vazby](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="d306e-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="d306e-112">Přidejte část rozšíření elementu vazby, která zpřístupňuje nový prvek vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="d306e-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="d306e-113">Přidejte rozšíření metadat pro komunikaci s funkcemi do jiných koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d306e-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="d306e-114">Přidejte vazbu, která předem nakonfiguruje zásobník prvků vazby podle dobře definovaného profilu.</span><span class="sxs-lookup"><span data-stu-id="d306e-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="d306e-115">Další informace najdete v tématu [Přidání standardní vazby](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="d306e-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="d306e-116">Přidáním oddílu vazby a elementu konfigurace vazby zpřístupníte vazbu ke konfiguračnímu systému.</span><span class="sxs-lookup"><span data-stu-id="d306e-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="d306e-117">Další informace najdete v tématu [Přidání podpory konfigurace](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="d306e-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="d306e-118">Vzorce výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="d306e-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="d306e-119">Prvním krokem při psaní vlastního přenosu je rozhodování o tom, které vzory výměny zpráv (MEPs) jsou pro přenos povinné.</span><span class="sxs-lookup"><span data-stu-id="d306e-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="d306e-120">Existují tři MEPsy, ze kterých si můžete vybrat:</span><span class="sxs-lookup"><span data-stu-id="d306e-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="d306e-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="d306e-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="d306e-122">Při použití dataMEP datagramu pošle klient zprávu s výměnou "Fire and zapomene".</span><span class="sxs-lookup"><span data-stu-id="d306e-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="d306e-123">Výměna požáru a zapomenutí je taková, která vyžaduje vzdálené potvrzení úspěšného doručení.</span><span class="sxs-lookup"><span data-stu-id="d306e-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="d306e-124">Zpráva může být ztracena při přenosu a nikdy se nespojit se službou.</span><span class="sxs-lookup"><span data-stu-id="d306e-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="d306e-125">Pokud se operace odeslání na konci klienta úspěšně dokončí, nezaručuje, že vzdálený koncový bod obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="d306e-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="d306e-126">Datagram je základní stavební blok pro zasílání zpráv, protože můžete sestavovat vlastní protokoly nad ním, včetně spolehlivých protokolů a zabezpečených protokolů.</span><span class="sxs-lookup"><span data-stu-id="d306e-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="d306e-127">Kanály datagramů klienta implementují rozhraní <xref:System.ServiceModel.Channels.IOutputChannel> a kanály Datagram Service implementující <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d306e-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="d306e-128">Požadavek-odpověď (třídu IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="d306e-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="d306e-129">V tomto MEP zpráva se pošle a odpověď se přijme.</span><span class="sxs-lookup"><span data-stu-id="d306e-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="d306e-130">Vzor se skládá z párů požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="d306e-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="d306e-131">Příklady volání požadavků a odpovědí jsou vzdálená volání procedur (RPC) a prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="d306e-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="d306e-132">Tento model se také označuje jako poloduplexní.</span><span class="sxs-lookup"><span data-stu-id="d306e-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="d306e-133">V tomto MEP implementují klientské kanály <xref:System.ServiceModel.Channels.IRequestChannel> a implementuje kanály pro služby <xref:System.ServiceModel.Channels.IReplyChannel> .</span><span class="sxs-lookup"><span data-stu-id="d306e-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="d306e-134">Duplexní přenos (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="d306e-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="d306e-135">Duplexní MEP umožňuje klientovi poslat libovolný počet zpráv a přijatý v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d306e-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="d306e-136">Duplexní MEP je jako telefonická konverzace, kde každé mluvené slovo je zpráva.</span><span class="sxs-lookup"><span data-stu-id="d306e-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="d306e-137">Vzhledem k tomu, že obě strany mohou v tomto MEP odesílat a přijímat, rozhraní implementované kanály klienta a služby je <xref:System.ServiceModel.Channels.IDuplexChannel> .</span><span class="sxs-lookup"><span data-stu-id="d306e-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="d306e-138">Každý z těchto MEPs může také podporovat relace.</span><span class="sxs-lookup"><span data-stu-id="d306e-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="d306e-139">Přidaná funkce poskytovaná kanálem podporujícím relaci je to, že koreluje všechny zprávy odesílané a přijímané na kanálu.</span><span class="sxs-lookup"><span data-stu-id="d306e-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="d306e-140">Vzor požadavků a odpovědí je samostatná relace dvou zpráv, protože se jedná o korelační požadavek a odpověď.</span><span class="sxs-lookup"><span data-stu-id="d306e-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="d306e-141">Oproti tomu vzor požadavek-odpověď, který podporuje relace, implikuje vzájemnou korelaci mezi všemi páry požadavků a odpovědí na daném kanálu.</span><span class="sxs-lookup"><span data-stu-id="d306e-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="d306e-142">Získáte tak celkem šest MEPs – datagram, požadavek-odpověď, duplexní, datagram s relacemi, požadavek-odpověď s relacemi a duplexní s relacemi – pro výběr z.</span><span class="sxs-lookup"><span data-stu-id="d306e-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d306e-143">Pro přenos UDP je jedinou podporovanou MEP datagram, protože UDP je ze své podstaty protokolem "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="d306e-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="d306e-144">Životní cyklus objekt ICommunicationObject a objektu WCF</span><span class="sxs-lookup"><span data-stu-id="d306e-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="d306e-145">WCF má společný Stavový počítač, který se používá ke správě životního cyklu objektů <xref:System.ServiceModel.Channels.IChannel> , jako jsou, <xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener> používané pro komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d306e-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="d306e-146">Existuje pět stavů, ve kterých tyto komunikační objekty můžou existovat.</span><span class="sxs-lookup"><span data-stu-id="d306e-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="d306e-147">Tyto stavy jsou reprezentovány <xref:System.ServiceModel.CommunicationState> výčtem a jsou následující:</span><span class="sxs-lookup"><span data-stu-id="d306e-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="d306e-148">Vytvořeno: Jedná se o stav <xref:System.ServiceModel.ICommunicationObject> při prvním vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="d306e-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="d306e-149">V tomto stavu se nevyskytují vstupně-výstupní operace (v/v).</span><span class="sxs-lookup"><span data-stu-id="d306e-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="d306e-150">Otevření: objekty přecházejí do tohoto stavu, když <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="d306e-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="d306e-151">V tomto okamžiku jsou vlastnosti neměnné a vstupní/výstupní může začít.</span><span class="sxs-lookup"><span data-stu-id="d306e-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="d306e-152">Tento přechod je platný pouze ze stavu Created (vytvořeno).</span><span class="sxs-lookup"><span data-stu-id="d306e-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="d306e-153">Otevřené: po dokončení otevřeného procesu převede objekty do tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="d306e-154">Tento přechod je platný jenom z počátečního stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="d306e-155">V tomto okamžiku je objekt plně použitelný pro přenos.</span><span class="sxs-lookup"><span data-stu-id="d306e-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="d306e-156">Uzavírání: probíhá přechod objektů do tohoto stavu, když <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána pro řádné vypnutí.</span><span class="sxs-lookup"><span data-stu-id="d306e-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="d306e-157">Tento přechod je platný jenom z otevřeného stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="d306e-158">Uzavřeno: objekty uzavřených stavů již nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="d306e-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="d306e-159">Obecně platí, že většina konfigurací je stále k dispozici pro kontrolu, ale nemůžete k tomu dojít k žádné komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d306e-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="d306e-160">Tento stav je stejný jako vyřazený.</span><span class="sxs-lookup"><span data-stu-id="d306e-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="d306e-161">Došlo k chybě: v chybovém stavu jsou objekty přístupné pro kontrolu, ale již nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="d306e-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="d306e-162">Pokud dojde k neobnovitelné chybě, objekt přejde do tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="d306e-163">Jediný platný přechod z tohoto stavu je do `Closed` stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="d306e-164">Existují události, které se aktivují pro každý přechod stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="d306e-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A>Metodu lze volat kdykoli a způsobí, že se objekt přenese hned z aktuálního stavu do zavřeného stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="d306e-166">Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.</span><span class="sxs-lookup"><span data-stu-id="d306e-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="d306e-167">Modul pro vytváření kanálů a naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="d306e-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="d306e-168">Dalším krokem při psaní vlastního přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály a <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.</span><span class="sxs-lookup"><span data-stu-id="d306e-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="d306e-169">Vrstva kanálu používá model továrny pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="d306e-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="d306e-170">WCF poskytuje pomocníky pro základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="d306e-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="d306e-171"><xref:System.ServiceModel.Channels.CommunicationObject>Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač dříve popsaný v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="d306e-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="d306e-172"><xref:System.ServiceModel.Channels.ChannelManagerBase>Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje sjednocenou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase> .</span><span class="sxs-lookup"><span data-stu-id="d306e-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="d306e-173"><xref:System.ServiceModel.Channels.ChannelManagerBase>Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase> , což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel> .</span><span class="sxs-lookup"><span data-stu-id="d306e-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="d306e-174"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="d306e-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="d306e-175"><xref:System.ServiceModel.Channels.ChannelListenerBase>Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="d306e-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="d306e-176">Je potřeba se starat o základní správu stavu.</span><span class="sxs-lookup"><span data-stu-id="d306e-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="d306e-177">V této ukázce je implementace továrny obsažena v UdpChannelFactory.cs a implementace naslouchacího procesu je obsažena v UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="d306e-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="d306e-178"><xref:System.ServiceModel.Channels.IChannel>Implementace jsou v UdpOutputChannel.cs a UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="d306e-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="d306e-179">Objekt pro vytváření kanálů UDP</span><span class="sxs-lookup"><span data-stu-id="d306e-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="d306e-180">Je `UdpChannelFactory` odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase> .</span><span class="sxs-lookup"><span data-stu-id="d306e-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="d306e-181">Vzor přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> , aby poskytoval přístup k verzi zprávy kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="d306e-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="d306e-182">Ukázka také přepisuje, aby bylo <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> možné odtrhnout naši instanci <xref:System.ServiceModel.Channels.BufferManager> při přechodu stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="d306e-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="d306e-183">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="d306e-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="d306e-184">`UdpOutputChannel`Implementuje rozhraní <xref:System.ServiceModel.Channels.IOutputChannel> .</span><span class="sxs-lookup"><span data-stu-id="d306e-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="d306e-185">Konstruktor ověřuje argumenty a vytvoří cílový <xref:System.Net.EndPoint> objekt na základě <xref:System.ServiceModel.EndpointAddress> předaného objektu.</span><span class="sxs-lookup"><span data-stu-id="d306e-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="d306e-186">Kanál může být řádně uzavřený nebo neřádný.</span><span class="sxs-lookup"><span data-stu-id="d306e-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="d306e-187">Pokud je kanál řádně uzavřený, soket je uzavřen a volání metody základní třídy je provedeno `OnClose` .</span><span class="sxs-lookup"><span data-stu-id="d306e-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="d306e-188">Pokud to vyvolá výjimku, zavolá infrastruktura, aby `Abort` zajistila vyčištění kanálu.</span><span class="sxs-lookup"><span data-stu-id="d306e-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="d306e-189">Následně implementujeme `Send()` a `BeginSend()` / `EndSend()` .</span><span class="sxs-lookup"><span data-stu-id="d306e-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="d306e-190">Tato část se rozdělí na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="d306e-190">This breaks down into two main sections.</span></span> <span data-ttu-id="d306e-191">Nejdřív jsme tuto zprávu serializováni do pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="d306e-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="d306e-192">Pak pošleme výsledná data na kabel.</span><span class="sxs-lookup"><span data-stu-id="d306e-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="d306e-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="d306e-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="d306e-194">Rozhraní `UdpChannelListener` , které ukázka implementuje, je odvozena od <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="d306e-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="d306e-195">K příjmu datagramů používá jeden soket UDP.</span><span class="sxs-lookup"><span data-stu-id="d306e-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="d306e-196">`OnOpen`Metoda přijímá data pomocí soketu UDP v asynchronní smyčce.</span><span class="sxs-lookup"><span data-stu-id="d306e-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="d306e-197">Data se pak převedou na zprávy pomocí architektury kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="d306e-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="d306e-198">Vzhledem k tomu, že stejný kanál datagram představuje zprávy, které přicházejí z řady zdrojů, `UdpChannelListener` je naslouchací proces typu singleton.</span><span class="sxs-lookup"><span data-stu-id="d306e-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="d306e-199">K <xref:System.ServiceModel.Channels.IChannel> tomuto naslouchacímu procesu je v jednu chvíli přidružená maximálně jedna aktivní služba.</span><span class="sxs-lookup"><span data-stu-id="d306e-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="d306e-200">Ukázka vygeneruje další pouze v případě, že kanál vrácený `AcceptChannel` metodou je následně vyřazen.</span><span class="sxs-lookup"><span data-stu-id="d306e-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="d306e-201">Po přijetí zprávy se do tohoto kanálu singleton zařazování do fronty.</span><span class="sxs-lookup"><span data-stu-id="d306e-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="d306e-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="d306e-202">UdpInputChannel</span></span>  
 <span data-ttu-id="d306e-203">`UdpInputChannel`Třída implementuje `IInputChannel` .</span><span class="sxs-lookup"><span data-stu-id="d306e-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="d306e-204">Skládá se z fronty příchozích zpráv, které jsou vyplněny `UdpChannelListener` soketem.</span><span class="sxs-lookup"><span data-stu-id="d306e-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="d306e-205">Tyto zprávy jsou odřazeny `IInputChannel.Receive` metodou.</span><span class="sxs-lookup"><span data-stu-id="d306e-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="d306e-206">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="d306e-207">Teď, když jsou továrny a kanály sestavené, je nutné je vystavit modulu runtime ServiceModel prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="d306e-208">Vazba je kolekce elementů vazby, které představují komunikační zásobník přidružený k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="d306e-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="d306e-209">Každý prvek v zásobníku je reprezentován [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvkem.</span><span class="sxs-lookup"><span data-stu-id="d306e-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="d306e-210">V ukázce je prvek vazby `UdpTransportBindingElement` , který je odvozen z <xref:System.ServiceModel.Channels.TransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="d306e-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="d306e-211">Přepíše následující metody pro sestavení továrn přidružených k naší vazbě.</span><span class="sxs-lookup"><span data-stu-id="d306e-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="d306e-212">Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (SOAP. UDP).</span><span class="sxs-lookup"><span data-stu-id="d306e-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="d306e-213">Přidání podpory metadat pro element transportní vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="d306e-214">Pro integraci našeho přenosu do systému metadat musíme podporovat import i export zásad.</span><span class="sxs-lookup"><span data-stu-id="d306e-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="d306e-215">To nám umožňuje vygenerovat klienty naší vazby prostřednictvím nástroje pro dodávání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d306e-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="d306e-216">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="d306e-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="d306e-217">Element vazby přenosu ve vazbě zodpovídá za export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="d306e-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="d306e-218">Při použití vazby SOAP by měl element vazby přenosu také exportovat správný přenosový identifikátor URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="d306e-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="d306e-219">Export WSDL</span><span class="sxs-lookup"><span data-stu-id="d306e-219">WSDL Export</span></span>  
 <span data-ttu-id="d306e-220">Chcete-li exportovat informace o adresách, `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d306e-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="d306e-221">`ExportEndpoint`Metoda přidá správné informace o adresování do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="d306e-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="d306e-222">`UdpTransportBindingElement`Implementace `ExportEndpoint` metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d306e-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="d306e-223">Import WSDL</span><span class="sxs-lookup"><span data-stu-id="d306e-223">WSDL Import</span></span>  
 <span data-ttu-id="d306e-224">Pro rozšiřování systému importu WSDL pro zpracování importu adres je nutné přidat následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="d306e-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="d306e-225">Při spuštění Svcutil. exe jsou k dispozici dvě možnosti, jak Svcutil. exe načíst rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="d306e-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="d306e-226">Najeďte Svcutil. exe na náš konfigurační soubor pomocí/SvcutilConfig: \<file> .</span><span class="sxs-lookup"><span data-stu-id="d306e-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d306e-227">Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d306e-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="d306e-228">`UdpBindingElementImporter`Typ implementuje `IWsdlImportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d306e-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="d306e-229">`ImportEndpoint`Metoda importuje adresu z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="d306e-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="d306e-230">Přidání podpory zásad</span><span class="sxs-lookup"><span data-stu-id="d306e-230">Adding Policy Support</span></span>  
 <span data-ttu-id="d306e-231">Vlastní element vazby může exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby, aby bylo možné vyjádřit možnosti tohoto prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="d306e-232">Export zásad</span><span class="sxs-lookup"><span data-stu-id="d306e-232">Policy Export</span></span>  
 <span data-ttu-id="d306e-233">`UdpTransportBindingElement`Typ implementuje `IPolicyExportExtension` k přidání podpory pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="d306e-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="d306e-234">Výsledkem je, že `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` generování zásad pro všechny vazby, které ji obsahují.</span><span class="sxs-lookup"><span data-stu-id="d306e-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="d306e-235">V nástroji `IPolicyExportExtension.ExportPolicy` přidáme kontrolní výraz pro UDP a jiný kontrolní výraz, pokud je v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="d306e-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="d306e-236">Je to proto, že režim vícesměrového vysílání ovlivňuje způsob, jakým je vytvořen komunikační zásobník, a proto musí být koordinován mezi oběma stranami.</span><span class="sxs-lookup"><span data-stu-id="d306e-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="d306e-237">Vzhledem k tomu, že vlastní prvky vazby přenosu jsou zodpovědné za zpracování adresování, `IPolicyExportExtension` implementace v `UdpTransportBindingElement` musí také zpracovávat příslušné kontrolní výrazy WS-Addressing, aby označovaly verzi WS-Addressing, která se používá.</span><span class="sxs-lookup"><span data-stu-id="d306e-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="d306e-238">Import zásad</span><span class="sxs-lookup"><span data-stu-id="d306e-238">Policy Import</span></span>  
 <span data-ttu-id="d306e-239">Pro rozšiřování systému pro import zásad je nutné přidat následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="d306e-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="d306e-240">Pak implementujeme `IPolicyImporterExtension` z naší registrované třídy ( `UdpBindingElementImporter` ).</span><span class="sxs-lookup"><span data-stu-id="d306e-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="d306e-241">V nástroji `ImportPolicy()` se podíváme na kontrolní výrazy v našem oboru názvů a zpracujeme je pro generování přenosu a kontrolu, jestli se jedná o vícesměrové vysílání.</span><span class="sxs-lookup"><span data-stu-id="d306e-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="d306e-242">Je také nutné odebrat kontrolní výrazy, které zpracováváme ze seznamu kontrolních výrazů vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="d306e-243">Při spuštění Svcutil. exe existují dvě možnosti integrace:</span><span class="sxs-lookup"><span data-stu-id="d306e-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="d306e-244">Najeďte Svcutil. exe na náš konfigurační soubor pomocí/SvcutilConfig: \<file> .</span><span class="sxs-lookup"><span data-stu-id="d306e-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d306e-245">Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d306e-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="d306e-246">Přidání standardní vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="d306e-247">Náš element vazby lze použít následujícími dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="d306e-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="d306e-248">Pomocí vlastní vazby: vlastní vazba umožňuje uživateli vytvořit vlastní vazbu založenou na libovolné sadě prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="d306e-249">Pomocí systémové vazby, která zahrnuje náš element vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="d306e-250">WCF poskytuje řadu těchto vazeb definovaných systémem, jako například `BasicHttpBinding` , `NetTcpBinding` a `WsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="d306e-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="d306e-251">Každá z těchto vazeb je přidružená k dobře definovanému profilu.</span><span class="sxs-lookup"><span data-stu-id="d306e-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="d306e-252">Ukázka implementuje vazbu profilu v `SampleProfileUdpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="d306e-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="d306e-253">`SampleProfileUdpBinding`Obsahuje až čtyři prvky vazby v rámci něj: `UdpTransportBindingElement` , `TextMessageEncodingBindingElement CompositeDuplexBindingElement` a `ReliableSessionBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="d306e-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="d306e-254">Přidání vlastního programu pro import standardních vazeb</span><span class="sxs-lookup"><span data-stu-id="d306e-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="d306e-255">Svcutil. exe a `WsdlImporter` typ ve výchozím nastavení rozpoznává a importuje vazby definované systémem.</span><span class="sxs-lookup"><span data-stu-id="d306e-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="d306e-256">V opačném případě se vazba naimportuje jako `CustomBinding` instance.</span><span class="sxs-lookup"><span data-stu-id="d306e-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="d306e-257">Chcete-li povolit Svcutil. exe a `WsdlImporter` importovat `SampleProfileUdpBinding` `UdpBindingElementImporter` také jako vlastní import standardních vazeb.</span><span class="sxs-lookup"><span data-stu-id="d306e-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="d306e-258">Vlastní nástroj pro import standardních vazeb implementuje `ImportEndpoint` metodu na `IWsdlImportExtension` rozhraní, aby prověřil `CustomBinding` instanci importovanou z metadat, aby bylo možné zjistit, zda mohla být vygenerována konkrétní standardní vazbou.</span><span class="sxs-lookup"><span data-stu-id="d306e-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="d306e-259">Obecně implementace vlastního programu pro importování standardní vazby zahrnuje kontrolu vlastností importovaných prvků vazby, aby bylo možné ověřit, zda byly změněny pouze vlastnosti, které by mohly být nastaveny standardní vazbou, a všechny ostatní vlastnosti jsou jejich výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="d306e-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="d306e-260">Základní strategií pro implementaci importu standardních vazeb je vytvoření instance standardní vazby, šíření vlastností z prvků vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnáním prvků vazby z standardní vazby s importovanými prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="d306e-261">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="d306e-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="d306e-262">Abychom mohli naše přenosy zveřejnit prostřednictvím konfigurace, je nutné implementovat dva konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="d306e-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="d306e-263">První je `BindingElementExtensionElement` pro `UdpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="d306e-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="d306e-264">To je tak proto, že `CustomBinding` implementace mohou odkazovat na náš element vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="d306e-265">Druhý je `Configuration` pro náš `SampleProfileUdpBinding` .</span><span class="sxs-lookup"><span data-stu-id="d306e-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="d306e-266">Element rozšíření elementu vazby</span><span class="sxs-lookup"><span data-stu-id="d306e-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="d306e-267">Oddíl `UdpTransportElement` `BindingElementExtensionElement` , který zveřejňuje `UdpTransportBindingElement` konfiguračnímu systému.</span><span class="sxs-lookup"><span data-stu-id="d306e-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="d306e-268">Při několika základních přepsáních definujeme název konfiguračního oddílu, typ našeho prvku vazby a postup vytvoření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="d306e-269">Náš oddíl rozšíření můžeme zaregistrovat do konfiguračního souboru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d306e-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d306e-270">Na rozšíření se dá odkazovat z vlastních vazeb na použití UDP jako přenosu.</span><span class="sxs-lookup"><span data-stu-id="d306e-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="d306e-271">Oddíl Binding</span><span class="sxs-lookup"><span data-stu-id="d306e-271">Binding Section</span></span>  
 <span data-ttu-id="d306e-272">Oddíl `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` , který zveřejňuje `SampleProfileUdpBinding` konfiguračnímu systému.</span><span class="sxs-lookup"><span data-stu-id="d306e-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="d306e-273">Hromadná implementace je delegována na `SampleProfileUdpBindingConfigurationElement` , který je odvozen z `StandardBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="d306e-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="d306e-274">`SampleProfileUdpBindingConfigurationElement`Obsahuje vlastnosti, které odpovídají vlastnostem na `SampleProfileUdpBinding` , a funkce, které mají být mapovány z `ConfigurationElement` vazby.</span><span class="sxs-lookup"><span data-stu-id="d306e-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="d306e-275">Nakonec přepište `OnApplyConfiguration` metodu v našem `SampleProfileUdpBinding` , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d306e-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d306e-276">K registraci této obslužné rutiny v konfiguračním systému přidáme následující oddíl do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d306e-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="d306e-277">Pak na něj můžete odkazovat z oddílu konfigurace serviceModel.</span><span class="sxs-lookup"><span data-stu-id="d306e-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="d306e-278">Testovací služba a klient UDP</span><span class="sxs-lookup"><span data-stu-id="d306e-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="d306e-279">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích UdpTestService a UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="d306e-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="d306e-280">Kód služby se skládá ze dvou testů – jeden test nastaví vazby a koncové body z kódu a druhý provede konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d306e-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="d306e-281">Oba testy používají dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="d306e-281">Both tests use two endpoints.</span></span> <span data-ttu-id="d306e-282">Jeden koncový bod používá `SampleUdpProfileBinding` [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) sadu s nastavenou na `true` .</span><span class="sxs-lookup"><span data-stu-id="d306e-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="d306e-283">Druhý koncový bod používá vlastní vazbu s `UdpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="d306e-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="d306e-284">Jedná se o ekvivalent použití `SampleUdpProfileBinding` s [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavením na `false` .</span><span class="sxs-lookup"><span data-stu-id="d306e-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="d306e-285">Oba testy vytvoří službu, přidejte koncový bod pro každou vazbu, otevřete službu a potom počkejte, než uživatel před zavřením služby zahájí zadání.</span><span class="sxs-lookup"><span data-stu-id="d306e-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="d306e-286">Při spuštění aplikace testování služby by se měl zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d306e-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="d306e-287">Pak můžete spustit testovací klientskou aplikaci proti publikovaným koncovým bodům.</span><span class="sxs-lookup"><span data-stu-id="d306e-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="d306e-288">Aplikace test klienta vytvoří klienta pro každý koncový bod a odešle pět zpráv do každého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d306e-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="d306e-289">Následující výstup je na klientovi.</span><span class="sxs-lookup"><span data-stu-id="d306e-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="d306e-290">Následuje úplný výstup služby.</span><span class="sxs-lookup"><span data-stu-id="d306e-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="d306e-291">Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER ve službě a spusťte testovacího klienta znovu.</span><span class="sxs-lookup"><span data-stu-id="d306e-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="d306e-292">Ve službě by se měl zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d306e-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="d306e-293">Po opětovném spuštění klienta bude výsledek stejný jako u předchozích výsledků.</span><span class="sxs-lookup"><span data-stu-id="d306e-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="d306e-294">Chcete-li znovu vygenerovat kód klienta a konfiguraci pomocí nástroje Svcutil. exe, spusťte aplikaci služby a spusťte následující soubor Svcutil. exe z kořenového adresáře ukázky.</span><span class="sxs-lookup"><span data-stu-id="d306e-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="d306e-295">Všimněte si, že Svcutil. exe negeneruje konfiguraci rozšíření vazby pro `SampleProfileUdpBinding` , takže je potřeba ho přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="d306e-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d306e-296">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d306e-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d306e-297">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d306e-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="d306e-298">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d306e-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d306e-299">Přečtěte si předchozí část "testovací služba a klient protokolu UDP".</span><span class="sxs-lookup"><span data-stu-id="d306e-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d306e-300">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d306e-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d306e-301">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d306e-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d306e-302">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="d306e-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d306e-303">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d306e-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
