---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 56cc48cd93020f37ac73b7f6b89130fdd1a3f7db
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150601"
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="d2016-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="d2016-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="d2016-103">Definuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="d2016-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="d2016-104">Pokud tento prvek přidán na vlastní vazby, výsledný kanálu může podporovat přesně-jednou záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="d2016-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="d2016-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d2016-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d2016-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d2016-106">\<bindings></span></span>  
<span data-ttu-id="d2016-107">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="d2016-107">\<customBinding></span></span>  
<span data-ttu-id="d2016-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2016-108">\<binding></span></span>  
<span data-ttu-id="d2016-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="d2016-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2016-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2016-110">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2016-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d2016-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2016-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d2016-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2016-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2016-113">Attributes</span></span>  
  
|<span data-ttu-id="d2016-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2016-114">Attribute</span></span>|<span data-ttu-id="d2016-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d2016-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2016-116">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="d2016-116">acknowledgementInterval</span></span>|<span data-ttu-id="d2016-117">A <xref:System.TimeSpan> , která obsahuje maximální časový interval, bude kanál čekat na odeslání potvrzení zpráv až k danému bodu.</span><span class="sxs-lookup"><span data-stu-id="d2016-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="d2016-118">Výchozí hodnota je 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="d2016-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="d2016-119">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="d2016-119">flowControlEnabled</span></span>|<span data-ttu-id="d2016-120">Logická hodnota, která určuje, zda je aktivováno pokročilé řízení toku, specifické pro společnost Microsoft provádění řízení toku pro posílání WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="d2016-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="d2016-121">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d2016-121">The default is `true`.</span></span>|  
|<span data-ttu-id="d2016-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="d2016-122">inactivityTimeout</span></span>|<span data-ttu-id="d2016-123">A <xref:System.TimeSpan> , která určuje maximální dobu, po kterou se bude kanál povolí druhé strany komunikace nechcete poslat žádnou zprávu před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="d2016-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="d2016-124">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d2016-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="d2016-125">Aktivita v kanálu je definován jako přijímající aplikace nebo zprávy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="d2016-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="d2016-126">Tato vlastnost určuje maximální množství času, aby neaktivní relace udrželo aktivní.</span><span class="sxs-lookup"><span data-stu-id="d2016-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="d2016-127">Pokud se žádná aktivita úspěšně projde delší dobu, relace přerušil infrastruktury a chyb kanálu.</span><span class="sxs-lookup"><span data-stu-id="d2016-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="d2016-128">**Poznámka:**  Není nutné pro aplikaci pravidelně odesílat zprávy, aby se připojení udrželo aktivní.</span><span class="sxs-lookup"><span data-stu-id="d2016-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="d2016-129">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="d2016-129">maxPendingChannels</span></span>|<span data-ttu-id="d2016-130">Celé číslo určující maximální počet kanálů, které mohou čekat na straně posluchače na přijetí.</span><span class="sxs-lookup"><span data-stu-id="d2016-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="d2016-131">Tato hodnota by měla být mezi 1 do 16384.</span><span class="sxs-lookup"><span data-stu-id="d2016-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="d2016-132">Výchozí hodnota je 4.</span><span class="sxs-lookup"><span data-stu-id="d2016-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="d2016-133">Kanály představují čekající při čekání na přijetí.</span><span class="sxs-lookup"><span data-stu-id="d2016-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="d2016-134">Po dosažení tohoto limitu jsou vytvořeny žádné kanály.</span><span class="sxs-lookup"><span data-stu-id="d2016-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="d2016-135">Místo toho jsou umístěny do čekající režimu až tento počet přejde (tak, že přijímá čekajících kanálů).</span><span class="sxs-lookup"><span data-stu-id="d2016-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="d2016-136">Jedná se o limit za factory.</span><span class="sxs-lookup"><span data-stu-id="d2016-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="d2016-137">Když je dosaženo prahové hodnoty a vzdálené aplikace se pokusí vytvořit nová stabilní relaci, požadavek se zamítne a operace otevření, která byla příčinou této chyby.</span><span class="sxs-lookup"><span data-stu-id="d2016-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="d2016-138">Toto omezení se nevztahuje na počet čekajících odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="d2016-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="d2016-139">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="d2016-139">maxRetryCount</span></span>|<span data-ttu-id="d2016-140">Celé číslo, které určuje maximální počet pokusů o bezpečný kanál pokusí znovu poslat zprávu, že neobdržel potvrzení, voláním Poslat na svém základním kanálu.</span><span class="sxs-lookup"><span data-stu-id="d2016-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="d2016-141">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="d2016-141">This value should be greater than zero.</span></span> <span data-ttu-id="d2016-142">Výchozí hodnota je 8.</span><span class="sxs-lookup"><span data-stu-id="d2016-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="d2016-143">Tato hodnota by měla být celé číslo větší než nula.</span><span class="sxs-lookup"><span data-stu-id="d2016-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="d2016-144">Pokud po poslední přenosu, k poruchám kanál neobdrží potvrzení.</span><span class="sxs-lookup"><span data-stu-id="d2016-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="d2016-145">Zpráva se považuje za které se mají přenést, pokud jeho doručení na straně příjemce byla potvrzena příjemce.</span><span class="sxs-lookup"><span data-stu-id="d2016-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="d2016-146">Pokud během určité doby pro zprávu, která bylo přeneseno nebyl přijat potvrzení, infrastruktury automaticky odešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="d2016-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="d2016-147">Infrastrukturu se pokusí znovu poslat zprávu pro maximální počet, kolikrát této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d2016-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="d2016-148">Pokud po poslední přenosu, k poruchám kanál neobdrží potvrzení.</span><span class="sxs-lookup"><span data-stu-id="d2016-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="d2016-149">Infrastruktura používá exponenciální regresní algoritmus, který určuje, kdy k opětovnému přenosu, podle vypočítaná průměrná doba odezvy.</span><span class="sxs-lookup"><span data-stu-id="d2016-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="d2016-150">Čas začátku začíná na 1 sekundu před opakovaný přenos zpráv a zpoždění s všechny pokusy o jeho, což vede k přibližně 8,5 minut předávání mezi první pokus o přenos a poslední pokus o opakovaný přenos zdvojnásobení.</span><span class="sxs-lookup"><span data-stu-id="d2016-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="d2016-151">Čas potřebný pro první pokus o opakovaný přenos zpráv je upraven podle počítané dobu odezvy a výsledné stretch času, které využívají tyto pokusy se liší odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d2016-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="d2016-152">To umožňuje dynamicky adaptovat na různých síťových podmínkách čas opakovaný přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="d2016-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="d2016-153">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="d2016-153">maxTransferWindowSize</span></span>|<span data-ttu-id="d2016-154">Celé číslo, které určuje maximální velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2016-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="d2016-155">Platné hodnoty jsou od 1 do 4096 (včetně).</span><span class="sxs-lookup"><span data-stu-id="d2016-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="d2016-156">Na straně klienta tento atribut definuje maximální velikost vyrovnávací paměti používané stabilní kanál pro uložení zpráv ještě nebyla potvrzena příjemce.</span><span class="sxs-lookup"><span data-stu-id="d2016-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="d2016-157">Jednotka kvóty je zpráva.</span><span class="sxs-lookup"><span data-stu-id="d2016-157">The unit of the quota is a message.</span></span> <span data-ttu-id="d2016-158">Pokud vyrovnávací paměť je plná, zablokuje se další operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="d2016-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="d2016-159">Na straně příjmu tento atribut definuje maximální velikost vyrovnávací paměti používané kanál k ukládání příchozích zpráv do aplikace ještě nebyla odeslána.</span><span class="sxs-lookup"><span data-stu-id="d2016-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="d2016-160">Pokud vyrovnávací paměť je plná, další zprávy zařazují tiše příjemce a odesílaných klientem.</span><span class="sxs-lookup"><span data-stu-id="d2016-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="d2016-161">ordered</span><span class="sxs-lookup"><span data-stu-id="d2016-161">ordered</span></span>|<span data-ttu-id="d2016-162">Logická hodnota, která určuje, zda je zaručená zprávy doručeny v pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="d2016-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="d2016-163">Pokud je toto nastavení `false`, můžete k doručování zpráv mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2016-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="d2016-164">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d2016-164">The default is `true`.</span></span>|  
|<span data-ttu-id="d2016-165">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="d2016-165">reliableMessagingVersion</span></span>|<span data-ttu-id="d2016-166">Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , který určuje verzi WS-ReliableMessaging, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d2016-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2016-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d2016-167">Child Elements</span></span>  
 <span data-ttu-id="d2016-168">Žádná</span><span class="sxs-lookup"><span data-stu-id="d2016-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2016-169">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d2016-169">Parent Elements</span></span>  
  
|<span data-ttu-id="d2016-170">Prvek</span><span class="sxs-lookup"><span data-stu-id="d2016-170">Element</span></span>|<span data-ttu-id="d2016-171">Popis</span><span class="sxs-lookup"><span data-stu-id="d2016-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2016-172">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2016-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d2016-173">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d2016-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2016-174">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2016-174">Remarks</span></span>  
 <span data-ttu-id="d2016-175">Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="d2016-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="d2016-176">Spolehlivé zasílání zpráv pokusí znovu navázat komunikaci s selhání a umožňuje záruky doručení, jako je například v pořadí doručení zpráv zadání.</span><span class="sxs-lookup"><span data-stu-id="d2016-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="d2016-177">Relace uchování stavu pro klienty mezi voláními.</span><span class="sxs-lookup"><span data-stu-id="d2016-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="d2016-178">Tento element poskytuje také v případě potřeby doručování objednané zprávy.</span><span class="sxs-lookup"><span data-stu-id="d2016-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="d2016-179">Tato implementované relace můžete různé zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2016-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="d2016-180">Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="d2016-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="d2016-181">Za běhu elementy vazby vytvářet objekty pro vytváření kanálů a naslouchacích procesů, které jsou potřebné k vývoji odchozí a příchozí kanál zásobníky potřebné pro odesílání a příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="d2016-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="d2016-182">`reliableSession` Poskytuje volitelný vrstvy v zásobníku, který můžete vytvořit stabilní relaci mezi koncovými body a konfigurovat chování této relace.</span><span class="sxs-lookup"><span data-stu-id="d2016-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="d2016-183">Další informace najdete v tématu [spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="d2016-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2016-184">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2016-184">Example</span></span>  
 <span data-ttu-id="d2016-185">Následující příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenosu a zpráva kódování prvků, zejména povolení spolehlivé relace, která udržuje stavu klienta a určuje záruky doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2016-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="d2016-186">Tato funkce je nakonfigurován v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="d2016-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="d2016-187">Zobrazit příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="d2016-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="d2016-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2016-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="d2016-189">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="d2016-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="d2016-190">Vazby</span><span class="sxs-lookup"><span data-stu-id="d2016-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d2016-191">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d2016-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d2016-192">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d2016-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d2016-193">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="d2016-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
