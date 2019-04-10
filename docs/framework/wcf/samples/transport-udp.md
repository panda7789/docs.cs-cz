---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 8d72ab5c7d8c461cd2ce4d4003d449ac9fe7e807
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334663"
---
# <a name="transport-udp"></a><span data-ttu-id="5c121-102">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="5c121-102">Transport: UDP</span></span>
<span data-ttu-id="5c121-103">Přenos UDP ukázka ukazuje, jak implementovat jednosměrového vysílání UDP a vícesměrového vysílání jako vlastní přenosu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5c121-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="5c121-104">Ukázka popisuje doporučený postup pro vytvoření vlastní přenos ve službě WCF, pomocí architektura kanálů a osvědčených postupů WCF.</span><span class="sxs-lookup"><span data-stu-id="5c121-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="5c121-105">Postup vytvoření vlastní přenosu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5c121-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="5c121-106">Rozhodnout, které z kanálu [zpráv Exchange vzory](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) budou podporovat třídu ChannelFactory a ChannelListener.</span><span class="sxs-lookup"><span data-stu-id="5c121-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="5c121-107">Následně se rozhodnete, zda bude podporovat s relacemi varianty těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5c121-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="5c121-108">Vytvoření postupu kanálu a posluchače, které podporují vaše vzorce výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="5c121-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="5c121-109">Ujistěte se, že všechny výjimky pro konkrétní sítě jsou normalizovány na příslušné třídy odvozené z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="5c121-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="5c121-110">Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) element, který přidá vlastní přenosu do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="5c121-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="5c121-111">Další informace najdete v tématu [přidání prvku vazby](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="5c121-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="5c121-112">Přidání sekce rozšíření elementu vazby vystavit nový element vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="5c121-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="5c121-113">Přidejte rozšíření metadat pro komunikaci funkce pro další koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c121-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="5c121-114">Přidáte vazbu, která předem nakonfiguruje sady elementů vazby podle přesně definovaného profilu.</span><span class="sxs-lookup"><span data-stu-id="5c121-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="5c121-115">Další informace najdete v tématu [přidání standardní vazby](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="5c121-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="5c121-116">Přidáte vazbu oddíl a vazeb konfiguračního prvku vystavit vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="5c121-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="5c121-117">Další informace najdete v tématu [přidání podpory konfigurace](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="5c121-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="5c121-118">Vzorky serveru Exchange zprávu</span><span class="sxs-lookup"><span data-stu-id="5c121-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="5c121-119">Prvním krokem v psaní vlastních přenosu je rozhodnout, jaké zprávy Exchange vzory (MEPs) jsou požadovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="5c121-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="5c121-120">Existují tři MEPs lze vybírat:</span><span class="sxs-lookup"><span data-stu-id="5c121-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="5c121-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="5c121-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="5c121-122">Při použití datagram MEP, klient odešle zprávu pomocí exchange "vypal a zapomeň".</span><span class="sxs-lookup"><span data-stu-id="5c121-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="5c121-123">A vypal a zapomeň exchange je ten, který vyžaduje out-of-band potvrzení úspěšné dodání.</span><span class="sxs-lookup"><span data-stu-id="5c121-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="5c121-124">Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí služby.</span><span class="sxs-lookup"><span data-stu-id="5c121-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="5c121-125">Pokud se operace odeslání se úspěšně dokončí na straně klienta, není zaručeno, že vzdálený koncový bod přijal zprávu.</span><span class="sxs-lookup"><span data-stu-id="5c121-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="5c121-126">Datagram je základním stavebním blokem pro zasílání zpráv, jak můžete vytvářet vlastní protokoly, dojde k jeho zvýraznění – včetně protokolů spolehlivé a zabezpečené protokoly.</span><span class="sxs-lookup"><span data-stu-id="5c121-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="5c121-127">Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5c121-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="5c121-128">Request-Response (třídu IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="5c121-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="5c121-129">V tomto MEP je odeslána zpráva a přijetí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5c121-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="5c121-130">Vzor se skládá z dvojice žádost odpověď.</span><span class="sxs-lookup"><span data-stu-id="5c121-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="5c121-131">Odpověď na požadavek volání příklady vzdálených volání procedur (RPC) a prohlížeče získá.</span><span class="sxs-lookup"><span data-stu-id="5c121-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="5c121-132">Tento model se také označuje jako poloduplexní.</span><span class="sxs-lookup"><span data-stu-id="5c121-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="5c121-133">V tomto MEP kanály klientů implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementují kanály service <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="5c121-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="5c121-134">Duplexní režim (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="5c121-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="5c121-135">Duplexní MEP umožňuje libovolný počet zpráv pro klientem odesílat a přijímat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5c121-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="5c121-136">Duplexní MEP je jako je telefonní hovor, kde je zpráva každého slova, se kterým se mluví.</span><span class="sxs-lookup"><span data-stu-id="5c121-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="5c121-137">Vzhledem k tomu, že obě strany můžete odesílat a přijímat v tomto MEP, rozhraní implementované pomocí kanálů klient a služba je <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="5c121-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="5c121-138">Každá z těchto MEPs může také podporovat relace.</span><span class="sxs-lookup"><span data-stu-id="5c121-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="5c121-139">Přidání funkce poskytované službou s ohledem na relaci kanálu je, že souvisí všechny zprávy odeslané a přijaté v kanálu.</span><span class="sxs-lookup"><span data-stu-id="5c121-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="5c121-140">Vzor typu žádost-odpověď je samostatné relace dvě zprávy, jako jsou korelována žádost a odpověď.</span><span class="sxs-lookup"><span data-stu-id="5c121-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="5c121-141">Vzor typu žádost-odpověď, která podporuje relací naproti tomu znamená, že všechny páry žádostí a odpovědí v tomto kanálu jsou korelována mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="5c121-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="5c121-142">To vám dává celkem šest MEPs – Datagram typu žádost-odpověď, duplexní, Datagram s relacemi, odpověď na požadavek s relacemi a duplexní s relacemi – lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="5c121-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c121-143">Pro přenos UDP pouze MEP, který je podporovaný totiž Datagram, UDP je ze své podstaty protokol "vypal a zapomeň".</span><span class="sxs-lookup"><span data-stu-id="5c121-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="5c121-144">Objekt ICommunicationObject a životního cyklu objektu WCF</span><span class="sxs-lookup"><span data-stu-id="5c121-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="5c121-145">WCF obsahuje běžné stavového stroje, který se používá pro správu životního cyklu objektů, jako jsou <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, a <xref:System.ServiceModel.Channels.IChannelListener> , která se používají ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="5c121-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="5c121-146">Existuje pět stavy, ve kterých lze tyto komunikace objekty existují.</span><span class="sxs-lookup"><span data-stu-id="5c121-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="5c121-147">Tyto stavy jsou reprezentovány <xref:System.ServiceModel.CommunicationState> výčtu a jsou následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5c121-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="5c121-148">Vytvořit: Toto je stav <xref:System.ServiceModel.ICommunicationObject> kdy je poprvé vytvořena.</span><span class="sxs-lookup"><span data-stu-id="5c121-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="5c121-149">Vyvolá se v tomto stavu žádný vstup/výstup (vstupně-výstupní operace).</span><span class="sxs-lookup"><span data-stu-id="5c121-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="5c121-150">Otevřít: Objekty přechodu na tento stav, kdy <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="5c121-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="5c121-151">V tomto okamžiku byly neměnné vlastnosti a začít vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="5c121-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="5c121-152">Tento převod je platný pouze ze stavu vytvořen.</span><span class="sxs-lookup"><span data-stu-id="5c121-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="5c121-153">Otevřít: Objekty přechod do tohoto stavu po dokončení procesu otevřít.</span><span class="sxs-lookup"><span data-stu-id="5c121-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="5c121-154">Tento převod je platný pouze ze stavu otevření.</span><span class="sxs-lookup"><span data-stu-id="5c121-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="5c121-155">V tomto okamžiku objektu je plně použitelné pro přenos.</span><span class="sxs-lookup"><span data-stu-id="5c121-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="5c121-156">Uzavření: Objekty přechodu na tento stav, kdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> se volá pro řádné vypnutí.</span><span class="sxs-lookup"><span data-stu-id="5c121-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="5c121-157">Tento převod je platný pouze ze stavu otevřen.</span><span class="sxs-lookup"><span data-stu-id="5c121-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="5c121-158">Zavřít: V poli Uzavřeno stavu objekty už nejsou použitelné.</span><span class="sxs-lookup"><span data-stu-id="5c121-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="5c121-159">Obecně platí je pořád přístupný pro kontrolu největší konfiguraci, ale žádná komunikace může dojít.</span><span class="sxs-lookup"><span data-stu-id="5c121-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="5c121-160">Tento stav je ekvivalentní vyřazována.</span><span class="sxs-lookup"><span data-stu-id="5c121-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="5c121-161">Došlo k chybě: Objekty v chybovém stavu, jsou přístupné pro kontrolu, ale už nebude použitelná.</span><span class="sxs-lookup"><span data-stu-id="5c121-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="5c121-162">Pokud dojde k nezotavitelné chybě, objekt přejde do tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="5c121-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="5c121-163">Je platné pouze přechod z tohoto stavu do `Closed` stavu.</span><span class="sxs-lookup"><span data-stu-id="5c121-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="5c121-164">Existují události, které se aktivují pro každý přechod stavu.</span><span class="sxs-lookup"><span data-stu-id="5c121-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="5c121-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metoda může být volána v každém okamžiku a způsobí, že objekt přechod okamžitě v jejím aktuálním stavu do uzavřeného stavu.</span><span class="sxs-lookup"><span data-stu-id="5c121-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="5c121-166">Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.</span><span class="sxs-lookup"><span data-stu-id="5c121-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="5c121-167">Objekt pro vytváření kanálů a modul pro naslouchání kanálu</span><span class="sxs-lookup"><span data-stu-id="5c121-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="5c121-168">Dalším krokem při psaní vlastních přenosu je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů a jejich <xref:System.ServiceModel.Channels.IChannelListener> pro kanály service.</span><span class="sxs-lookup"><span data-stu-id="5c121-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="5c121-169">Vrstvy kanálu používá vzor factory pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="5c121-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="5c121-170">WCF poskytuje pomocné rutiny základní třídy pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="5c121-170">WCF provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="5c121-171"><xref:System.ServiceModel.Channels.CommunicationObject> Implementuje třída <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavového stroje výše popsaný v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="5c121-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="5c121-172"><xref:System.ServiceModel.Channels.ChannelManagerBase> Implementuje třída <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotné základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="5c121-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="5c121-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> Třídy funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídy, která implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="5c121-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="5c121-174"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Implementuje třída <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a slučuje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="5c121-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="5c121-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Implementuje třída <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="5c121-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="5c121-176">Postará se o správu základního stavu.</span><span class="sxs-lookup"><span data-stu-id="5c121-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="5c121-177">V této ukázce je implementace objektu factory součástí UdpChannelFactory.cs a naslouchací proces implementace je obsažený v UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="5c121-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="5c121-178"><xref:System.ServiceModel.Channels.IChannel> Implementace jsou v UdpOutputChannel.cs a UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="5c121-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="5c121-179">Objekt pro vytváření kanálů UDP</span><span class="sxs-lookup"><span data-stu-id="5c121-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="5c121-180">`UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="5c121-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="5c121-181">Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pro poskytnutí přístupu k verze kodér zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c121-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="5c121-182">Ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby můžete odstraňujeme naše instanci <xref:System.ServiceModel.Channels.BufferManager> když změní stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="5c121-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="5c121-183">Výstupní kanál UDP</span><span class="sxs-lookup"><span data-stu-id="5c121-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="5c121-184">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="5c121-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="5c121-185">Konstruktor ověří argumenty a vytvoří cíl <xref:System.Net.EndPoint> objektu na základě <xref:System.ServiceModel.EndpointAddress> , který je předán.</span><span class="sxs-lookup"><span data-stu-id="5c121-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="5c121-186">Kanál můžete zavřít, bez výpadku nebo ungracefully.</span><span class="sxs-lookup"><span data-stu-id="5c121-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="5c121-187">Pokud kanál je uzavřen řádně soketu se zavře a základní třídy je provedeno volání `OnClose` metoda.</span><span class="sxs-lookup"><span data-stu-id="5c121-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="5c121-188">Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěn.</span><span class="sxs-lookup"><span data-stu-id="5c121-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="5c121-189">Pak implementovat `Send()` a `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="5c121-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="5c121-190">Tím je prolomen na dvě hlavní části.</span><span class="sxs-lookup"><span data-stu-id="5c121-190">This breaks down into two main sections.</span></span> <span data-ttu-id="5c121-191">Nejprve můžeme serializovat zprávu do bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="5c121-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="5c121-192">Potom pošleme Výsledná data na lince.</span><span class="sxs-lookup"><span data-stu-id="5c121-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="5c121-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="5c121-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="5c121-194">`UdpChannelListener` , Že implementuje vzorek je odvozen od <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="5c121-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="5c121-195">Pro příjem datagramy používá pro jediný soket UDP.</span><span class="sxs-lookup"><span data-stu-id="5c121-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="5c121-196">`OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčka.</span><span class="sxs-lookup"><span data-stu-id="5c121-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="5c121-197">Data se pak převedeno do zprávy pomocí rozhraní kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="5c121-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="5c121-198">Vzhledem k tomu, že představuje stejný kanálu datagramu zprávy přicházející z mnoha různých zdrojů, `UdpChannelListener` běží naslouchací proces typu singleton.</span><span class="sxs-lookup"><span data-stu-id="5c121-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="5c121-199">Existuje na většině, jednu aktivní <xref:System.ServiceModel.Channels.IChannel> spojené s tímto naslouchacím procesem najednou.</span><span class="sxs-lookup"><span data-stu-id="5c121-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="5c121-200">Ukázka generuje jiný pouze v případě, že kanál, který je vrácený `AcceptChannel` metoda následně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="5c121-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="5c121-201">Při doručení zprávy do je zařazených do fronty do tohoto kanálu typu singleton.</span><span class="sxs-lookup"><span data-stu-id="5c121-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="5c121-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="5c121-202">UdpInputChannel</span></span>  
 <span data-ttu-id="5c121-203">`UdpInputChannel` Implementuje třída `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="5c121-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="5c121-204">Skládá se z front příchozích zpráv, které je vyplněn `UdpChannelListener`uživatele soketu.</span><span class="sxs-lookup"><span data-stu-id="5c121-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="5c121-205">Tyto zprávy jsou odstraněné z fronty podle `IInputChannel.Receive` metody.</span><span class="sxs-lookup"><span data-stu-id="5c121-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="5c121-206">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="5c121-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="5c121-207">Teď, když jsou vytvořeny objekty pro vytváření a kanály, jsme musí vystavit do modulu runtime ServiceModel prostřednictvím vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="5c121-208">Vazba je kolekce elementů vazby, který představuje komunikační balík přidružené k adrese služby.</span><span class="sxs-lookup"><span data-stu-id="5c121-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="5c121-209">Každý prvek v zásobníku je reprezentována [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5c121-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="5c121-210">V ukázce je element vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5c121-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="5c121-211">Přepíše následujících metod k vytváření továrny spojené s využitím naší vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="5c121-212">Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="5c121-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="5c121-213">Přidání podpory metadat pro Element vazby přenosu</span><span class="sxs-lookup"><span data-stu-id="5c121-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="5c121-214">K integraci naší přenosu do metadat systému, musí Podporujeme import a export zásad.</span><span class="sxs-lookup"><span data-stu-id="5c121-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="5c121-215">Díky tomu můžeme ke generování klientů prostřednictvím našich vazby [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5c121-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="5c121-216">Přidání podpory WSDL</span><span class="sxs-lookup"><span data-stu-id="5c121-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="5c121-217">Element vazby přenosu ve vazbě je zodpovědná za export a import informací o adresách v metadatech.</span><span class="sxs-lookup"><span data-stu-id="5c121-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="5c121-218">Při použití vazby protokolu SOAP, element vazby přenosu by měl také exportovat správné přepravy identifikátoru URI v metadatech.</span><span class="sxs-lookup"><span data-stu-id="5c121-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="5c121-219">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="5c121-219">WSDL Export</span></span>  
 <span data-ttu-id="5c121-220">Chcete-li exportovat informace o adresách `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5c121-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="5c121-221">`ExportEndpoint` Metoda přidá správné informace o adresování na WSDL port.</span><span class="sxs-lookup"><span data-stu-id="5c121-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="5c121-222">`UdpTransportBindingElement` Provádění `ExportEndpoint` metoda zároveň exportuje přepravy identifikátoru URI při používá koncový bod vazbou SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c121-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="5c121-223">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="5c121-223">WSDL Import</span></span>  
 <span data-ttu-id="5c121-224">Rozšíření systému importu WSDL pro zpracování importu adres, jsme musíte přidat následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="5c121-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="5c121-225">Při spuštění Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe k načítání rozšíření importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="5c121-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="5c121-226">Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.</span><span class="sxs-lookup"><span data-stu-id="5c121-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="5c121-227">Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="5c121-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="5c121-228">`UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5c121-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="5c121-229">`ImportEndpoint` Metoda importuje adresu z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="5c121-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="5c121-230">Přidání podpory pro zásady</span><span class="sxs-lookup"><span data-stu-id="5c121-230">Adding Policy Support</span></span>  
 <span data-ttu-id="5c121-231">Vlastní prvek vazby můžete export kontrolních výrazů zásad Vazba WSDL pro koncový bod služby vyjádřit možnosti daného prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="5c121-232">Export zásad</span><span class="sxs-lookup"><span data-stu-id="5c121-232">Policy Export</span></span>  
 <span data-ttu-id="5c121-233">`UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` přidává funkce pro export zásad.</span><span class="sxs-lookup"><span data-stu-id="5c121-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="5c121-234">V důsledku toho `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` při generování zásad pro všechny vazby, který ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="5c121-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="5c121-235">V `IPolicyExportExtension.ExportPolicy`, můžeme přidat kontrolní výraz pro UDP a další kontrolní výraz Pokud se nám v režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="5c121-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="5c121-236">Jak komunikačního balíku je vytvořen a proto musí být koordinovaní mezi obě strany jde vzhledem k tomu, že má vliv na režimu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="5c121-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="5c121-237">Protože jsou zodpovědného za obsluhu adresování elementů přenosové vlastní vazby `IPolicyExportExtension` implementace v prostředí `UdpTransportBindingElement` musí také zpracovat export odpovídající WS-Addressing kontrolní výrazy zásad označující verzi elementu WS-Addressing používá.</span><span class="sxs-lookup"><span data-stu-id="5c121-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="5c121-238">Import zásady</span><span class="sxs-lookup"><span data-stu-id="5c121-238">Policy Import</span></span>  
 <span data-ttu-id="5c121-239">Rozšíření importu zásady systému jsme musíte přidat následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="5c121-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="5c121-240">Pak můžeme implementovat `IPolicyImporterExtension` z našich registrované třídy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="5c121-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="5c121-241">V `ImportPolicy()`, jsme v našem oboru názvů, prohlédněte si kontrolní výrazy a zpracovat pro generování přenos a zkontrolujte, zda je vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="5c121-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="5c121-242">Také musíte Odebereme kontrolní výrazy, které My se postaráme ze seznamu vazby kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="5c121-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="5c121-243">Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:</span><span class="sxs-lookup"><span data-stu-id="5c121-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="5c121-244">Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.</span><span class="sxs-lookup"><span data-stu-id="5c121-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="5c121-245">Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="5c121-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="5c121-246">Přidání standardní vazbu</span><span class="sxs-lookup"><span data-stu-id="5c121-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="5c121-247">Naše element vazby lze použít v následujících dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="5c121-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="5c121-248">Prostřednictvím vlastní vazby: Vlastní vazba umožňuje uživateli vytvořit své vlastní vazbu na základě libovolného sady elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="5c121-249">S použitím vazeb poskytovaných systémem, který zahrnuje naše element vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="5c121-250">WCF poskytuje několik z těchto vazeb definovaných systémem, jako `BasicHttpBinding`, `NetTcpBinding`, a `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c121-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="5c121-251">Každá z těchto vazeb souvisí s dobře definovaného profilu.</span><span class="sxs-lookup"><span data-stu-id="5c121-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="5c121-252">Ukázka implementuje vazba profilu v `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="5c121-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="5c121-253">`SampleProfileUdpBinding` Obsahuje až čtyři elementy vazby v něm: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5c121-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="5c121-254">Přidání vlastní standardní vazby programu pro import</span><span class="sxs-lookup"><span data-stu-id="5c121-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="5c121-255">Svcutil.exe a `WsdlImporter` typ, ve výchozím nastavení, rozpozná a importuje systémem definované vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="5c121-256">V opačném případě získá importovat, protože vazba `CustomBinding` instance.</span><span class="sxs-lookup"><span data-stu-id="5c121-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="5c121-257">Povolit Svcutil.exe a `WsdlImporter` import `SampleProfileUdpBinding` `UdpBindingElementImporter` taky pracuje jako import standardní vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="5c121-258">Implementuje programu pro import standardní vlastní vazby `ImportEndpoint` metodu na `IWsdlImportExtension` rozhraní k prozkoumání `CustomBinding` instance naimportované z metadat najdete v článku, zda ho může být vygenerováno konkrétní standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="5c121-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="5c121-259">Obecně platí implementace programu pro import vlastních vazeb standard zahrnuje ověření vlastností elementů importované vazby k ověření, že jste změnili pouze vlastnosti, které může nastavit standardní vazbou a všechny ostatní vlastnosti se jejich výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="5c121-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="5c121-260">Základní strategií pro implementaci standardní vazbu Importér je vytvoření instance standardní vazbu, rozšíří vlastnosti z elementů vazby instanci standardní vazbu, která podporuje standardní vazbu, a porovnat vazby elementy ze standardní vazba s prvky importované vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="5c121-261">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="5c121-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="5c121-262">Pokud chcete zpřístupnit naše přenosu prostřednictvím konfigurace, musíme implementovat dvě konfigurační oddíly funkce.</span><span class="sxs-lookup"><span data-stu-id="5c121-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="5c121-263">První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5c121-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="5c121-264">Toto je tak, aby `CustomBinding` implementace může odkazovat na naše element vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="5c121-265">Druhým je `Configuration` pro naše `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c121-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="5c121-266">Element rozšíření elementu vazby</span><span class="sxs-lookup"><span data-stu-id="5c121-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="5c121-267">V části `UdpTransportElement` je `BindingElementExtensionElement` , která zveřejní `UdpTransportBindingElement` k systému konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5c121-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="5c121-268">S několika základní přepsání definujeme naše název oddílu konfigurace, typ naše element vazby a vytvoření naší element vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="5c121-269">Naše rozšíření části jsme pak můžete zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c121-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5c121-270">Rozšíření můžete odkazovat z vlastní vazby pro použití jako přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="5c121-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="5c121-271">Část vazby</span><span class="sxs-lookup"><span data-stu-id="5c121-271">Binding Section</span></span>  
 <span data-ttu-id="5c121-272">V části `SampleProfileUdpBindingCollectionElement` je `StandardBindingCollectionElement` , která zveřejní `SampleProfileUdpBinding` k systému konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5c121-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="5c121-273">Hromadné implementace se deleguje na `SampleProfileUdpBindingConfigurationElement`, která je odvozena z `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5c121-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="5c121-274">`SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnostem v `SampleProfileUdpBinding`a funkce mapování `ConfigurationElement` vazby.</span><span class="sxs-lookup"><span data-stu-id="5c121-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="5c121-275">Nakonec přepsání `OnApplyConfiguration` metoda v našich `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5c121-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5c121-276">K registraci této obslužné rutiny konfigurace systému, přidáme do příslušných konfigurační soubor v následující části.</span><span class="sxs-lookup"><span data-stu-id="5c121-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="5c121-277">Poté jej lze odkazovat z konfiguračního oddílu serviceModel.</span><span class="sxs-lookup"><span data-stu-id="5c121-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="5c121-278">Služba testovacího UDP a klienta</span><span class="sxs-lookup"><span data-stu-id="5c121-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="5c121-279">Testovací kód pro tento přenos ukázkový používání je k dispozici v adresářích UdpTestService a UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="5c121-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="5c121-280">Kódu služby se skládá ze dvou testy – jeden test nastaví vazby a koncových bodů z kódu a druhý se prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5c121-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="5c121-281">Oba testy použít dva koncové body.</span><span class="sxs-lookup"><span data-stu-id="5c121-281">Both tests use two endpoints.</span></span> <span data-ttu-id="5c121-282">Použije jeden koncový bod `SampleUdpProfileBinding` s [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="5c121-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="5c121-283">Jiný koncový bod používá vlastní vazby s `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5c121-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="5c121-284">To je ekvivalentní k použití `SampleUdpProfileBinding` s [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="5c121-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="5c121-285">Oba testy vytvoření služby, přidat koncový bod pro každou vazbu, otevřete službu a potom počkejte uživateli před jeho zavřením službu stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="5c121-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="5c121-286">Při spuštění testu aplikace službu byste měli vidět následující výstup.</span><span class="sxs-lookup"><span data-stu-id="5c121-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="5c121-287">Test klientská aplikace může potom spuštěním příkazu publikované koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5c121-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="5c121-288">Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odesílá pět zprávy pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5c121-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="5c121-289">Následující výstup je na klientovi.</span><span class="sxs-lookup"><span data-stu-id="5c121-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="5c121-290">Následuje úplný výstup ve službě.</span><span class="sxs-lookup"><span data-stu-id="5c121-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="5c121-291">Ke spuštění klientské aplikace publikované pomocí konfigurace koncových bodů, stiskněte ENTER na službu a poté znovu spusťte testovací klient.</span><span class="sxs-lookup"><span data-stu-id="5c121-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="5c121-292">Ve službě byste měli vidět následující výstup.</span><span class="sxs-lookup"><span data-stu-id="5c121-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="5c121-293">Spuštění klienta znovu provede stejné jako předchozí výsledky.</span><span class="sxs-lookup"><span data-stu-id="5c121-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="5c121-294">Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující Svcutil.exe z kořenového adresáře vzorku.</span><span class="sxs-lookup"><span data-stu-id="5c121-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="5c121-295">Všimněte si, že Svcutil.exe negeneruje pro konfiguraci rozšíření vazby `SampleProfileUdpBinding`, takže je třeba přidat ji ručně.</span><span class="sxs-lookup"><span data-stu-id="5c121-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c121-296">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="5c121-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5c121-297">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c121-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5c121-298">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c121-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5c121-299">Přečtěte si předchozí část "The UDP testu a klient služby".</span><span class="sxs-lookup"><span data-stu-id="5c121-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c121-300">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="5c121-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c121-301">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5c121-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5c121-302">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5c121-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c121-303">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5c121-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
