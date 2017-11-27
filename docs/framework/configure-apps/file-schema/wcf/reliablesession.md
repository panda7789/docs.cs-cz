---
title: '&lt;reliableSession&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 13421acf276f6fd98dc75bf7b53cd9f219ff0c0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="14c24-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="14c24-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="14c24-103">Definuje nastavení WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14c24-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="14c24-104">Pokud tento element je přidat do vlastní vazby, výsledná kanál může podporovat přesně-jednou záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="14c24-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="14c24-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="14c24-105">\<system.serviceModel></span></span>  
<span data-ttu-id="14c24-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="14c24-106">\<bindings></span></span>  
<span data-ttu-id="14c24-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="14c24-107">\<customBinding></span></span>  
<span data-ttu-id="14c24-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="14c24-108">\<binding></span></span>  
<span data-ttu-id="14c24-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="14c24-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c24-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14c24-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14c24-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14c24-111">Attributes and Elements</span></span>  
 <span data-ttu-id="14c24-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14c24-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14c24-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="14c24-113">Attributes</span></span>  
  
|<span data-ttu-id="14c24-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="14c24-114">Attribute</span></span>|<span data-ttu-id="14c24-115">Popis</span><span class="sxs-lookup"><span data-stu-id="14c24-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14c24-116">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="14c24-116">acknowledgementInterval</span></span>|<span data-ttu-id="14c24-117">A <xref:System.TimeSpan> obsahující maximální časový interval kanál se bude čekat na posílá potvrzení zprávy přijaté až tento bod.</span><span class="sxs-lookup"><span data-stu-id="14c24-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="14c24-118">Výchozí hodnota je 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="14c24-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="14c24-119">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="14c24-119">flowControlEnabled</span></span>|<span data-ttu-id="14c24-120">Logická hodnota, která určuje, zda je aktivován řízení toku na Upřesnit, specifické pro společnost Microsoft implementace toku řízení pro WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="14c24-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="14c24-121">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="14c24-121">The default is `true`.</span></span>|  
|<span data-ttu-id="14c24-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="14c24-122">inactivityTimeout</span></span>|<span data-ttu-id="14c24-123">A <xref:System.TimeSpan> , který určuje maximální dobu, po který se bude kanál povolit druhou stranou komunikace posílat žádné zprávy před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="14c24-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="14c24-124">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="14c24-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="14c24-125">Aktivity na kanál, který je definován jako přijímající aplikace nebo infrastruktury zprávy.</span><span class="sxs-lookup"><span data-stu-id="14c24-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="14c24-126">Tato vlastnost určuje maximální množství času, které k zachování neaktivní relace připojení.</span><span class="sxs-lookup"><span data-stu-id="14c24-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="14c24-127">Pokud se žádná aktivita úspěšně projde delší dobu, relace se přerušil infrastruktury a chyb kanálu.</span><span class="sxs-lookup"><span data-stu-id="14c24-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="14c24-128">**Poznámka:** není nutné pro aplikaci pravidelného zasílání zpráv pro zachování připojení připojení.</span><span class="sxs-lookup"><span data-stu-id="14c24-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="14c24-129">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="14c24-129">maxPendingChannels</span></span>|<span data-ttu-id="14c24-130">Celé číslo, které určuje maximální počet kanálů, které můžete čekat na naslouchací proces třeba přijmout.</span><span class="sxs-lookup"><span data-stu-id="14c24-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="14c24-131">Tato hodnota by měla být mezi 1 na 16384.</span><span class="sxs-lookup"><span data-stu-id="14c24-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="14c24-132">Výchozí hodnota je 4.</span><span class="sxs-lookup"><span data-stu-id="14c24-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="14c24-133">Kanály jsou čekající na vyřízení, když jsou čekání třeba přijmout.</span><span class="sxs-lookup"><span data-stu-id="14c24-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="14c24-134">Po dosažení tohoto limitu se vytvoří žádné kanály.</span><span class="sxs-lookup"><span data-stu-id="14c24-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="14c24-135">Místo toho jsou umístěny do čekající na vyřízení režimu dokud číslo dosáhne (přijetím čekající na vyřízení kanály).</span><span class="sxs-lookup"><span data-stu-id="14c24-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="14c24-136">To je limit na vytváření.</span><span class="sxs-lookup"><span data-stu-id="14c24-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="14c24-137">Když je dosaženo prahové hodnoty a vzdálené aplikace pokusí o vytvoření nové spolehlivé relace, požadavek se odmítne a otevřete operaci, která se zobrazí výzva této chyby.</span><span class="sxs-lookup"><span data-stu-id="14c24-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="14c24-138">Toto omezení se nevztahuje na počet čekajících odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="14c24-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="14c24-139">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="14c24-139">maxRetryCount</span></span>|<span data-ttu-id="14c24-140">Celé číslo, které určuje maximální počet nezdařených pokusů o spolehlivé kanál se pokusí znovu pošlou zprávu, že neobdržel potvrzení, voláním odeslat na jeho základní kanálu.</span><span class="sxs-lookup"><span data-stu-id="14c24-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="14c24-141">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="14c24-141">This value should be greater than zero.</span></span> <span data-ttu-id="14c24-142">Výchozí hodnota je 8.</span><span class="sxs-lookup"><span data-stu-id="14c24-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="14c24-143">Tato hodnota by měla být celé číslo větší než nula.</span><span class="sxs-lookup"><span data-stu-id="14c24-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="14c24-144">Není-li potvrzení přijata po poslední opakování přenosu, chyb kanálu.</span><span class="sxs-lookup"><span data-stu-id="14c24-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="14c24-145">Zpráva považuje za které se mají přenést, pokud jeho doručení na příjemce má byla potvrzena příjemce.</span><span class="sxs-lookup"><span data-stu-id="14c24-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="14c24-146">Pokud potvrzení nebyl přijat do určité doby pro zprávu, že bylo přeneseno, infrastrukturu automaticky odešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="14c24-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="14c24-147">Infrastruktury se pokusí znovu odeslat zprávu pro maximálně počet této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="14c24-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="14c24-148">Není-li potvrzení přijata po poslední opakování přenosu, chyb kanálu.</span><span class="sxs-lookup"><span data-stu-id="14c24-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="14c24-149">Infrastruktury používá nepodporovaný algoritmus exponenciální back vypnout k určení, kdy se mají přenést, znovu podle počítaný průměrný čas odezvy.</span><span class="sxs-lookup"><span data-stu-id="14c24-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="14c24-150">Čas začíná původně na 1 sekundu před opakování přenosu a zvýší zpoždění s všechny pokusy, což vede k přibližně šířka 8,5 minut předávání mezi první pokus o přenos a poslední pokus o opakování přenosu.</span><span class="sxs-lookup"><span data-stu-id="14c24-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="14c24-151">Čas první pokus o opakování přenosu je upravena podle počítané času jejich návratu a výsledný stretch dobu trvat těmito pokusy se liší podle toho.</span><span class="sxs-lookup"><span data-stu-id="14c24-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="14c24-152">To umožňuje dynamicky adaptovat podle aktuální na různých síťových podmínkách doba opakování přenosu.</span><span class="sxs-lookup"><span data-stu-id="14c24-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="14c24-153">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="14c24-153">maxTransferWindowSize</span></span>|<span data-ttu-id="14c24-154">Celé číslo, které určuje maximální velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14c24-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="14c24-155">Platné hodnoty jsou od 1 do 4096 (včetně).</span><span class="sxs-lookup"><span data-stu-id="14c24-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="14c24-156">Na klientovi tento atribut definuje maximální velikost vyrovnávací paměti používané spolehlivé kanál pro uložení ještě nebyla potvrzena příjemce zprávy.</span><span class="sxs-lookup"><span data-stu-id="14c24-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="14c24-157">Jednotka kvóty je zpráva.</span><span class="sxs-lookup"><span data-stu-id="14c24-157">The unit of the quota is a message.</span></span> <span data-ttu-id="14c24-158">Pokud vyrovnávací paměť je plná, jsou zablokované další operace ODESÍLÁNÍ.</span><span class="sxs-lookup"><span data-stu-id="14c24-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="14c24-159">Na příjemce tento atribut definuje maximální velikost vyrovnávací paměti používá kanál k ukládání příchozích zpráv ještě odeslat do aplikace.</span><span class="sxs-lookup"><span data-stu-id="14c24-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="14c24-160">Pokud vyrovnávací paměť je plná, další zprávy bezobslužně zahozených příjemce a odesílaných klientem.</span><span class="sxs-lookup"><span data-stu-id="14c24-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="14c24-161">ordered</span><span class="sxs-lookup"><span data-stu-id="14c24-161">ordered</span></span>|<span data-ttu-id="14c24-162">Logická hodnota, která určuje, zda jsou zprávy zaručené doručení v pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="14c24-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="14c24-163">Pokud toto nastavení je `false`, můžete k doručování zpráv mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="14c24-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="14c24-164">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="14c24-164">The default is `true`.</span></span>|  
|<span data-ttu-id="14c24-165">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="14c24-165">reliableMessagingVersion</span></span>|<span data-ttu-id="14c24-166">Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , určuje verzi protokolu WS-ReliableMessaging, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="14c24-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14c24-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14c24-167">Child Elements</span></span>  
 <span data-ttu-id="14c24-168">Žádné</span><span class="sxs-lookup"><span data-stu-id="14c24-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14c24-169">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14c24-169">Parent Elements</span></span>  
  
|<span data-ttu-id="14c24-170">Prvek</span><span class="sxs-lookup"><span data-stu-id="14c24-170">Element</span></span>|<span data-ttu-id="14c24-171">Popis</span><span class="sxs-lookup"><span data-stu-id="14c24-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14c24-172">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="14c24-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="14c24-173">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="14c24-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c24-174">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14c24-174">Remarks</span></span>  
 <span data-ttu-id="14c24-175">Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relace.</span><span class="sxs-lookup"><span data-stu-id="14c24-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="14c24-176">Spolehlivé zasílání zpráv opakování komunikace při selhání a umožňuje záruky doručení, jako je například v daném pořadí doručení zpráv, které mají být zadán.</span><span class="sxs-lookup"><span data-stu-id="14c24-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="14c24-177">Relace uchování stavu pro klienty mezi volání.</span><span class="sxs-lookup"><span data-stu-id="14c24-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="14c24-178">Tento element také volitelně poskytuje doručení seřazené zpráv.</span><span class="sxs-lookup"><span data-stu-id="14c24-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="14c24-179">Tuto relaci implementovaná můžete křížová zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="14c24-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="14c24-180">Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zprávy.</span><span class="sxs-lookup"><span data-stu-id="14c24-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="14c24-181">Prvky vazeb v době běhu vytvořit kanál továrny a naslouchací procesy, které jsou nezbytné k sestavení odchozí a příchozí kanál zásobníky potřeba odesílat a přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="14c24-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="14c24-182">`reliableSession` Poskytuje volitelné úroveň v zásobníku, která můžete vytvořit stabilní relaci mezi koncovými body a nakonfigurovat chování tuto relaci.</span><span class="sxs-lookup"><span data-stu-id="14c24-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="14c24-183">Další informace najdete v tématu [spolehlivé relace](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="14c24-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14c24-184">Příklad</span><span class="sxs-lookup"><span data-stu-id="14c24-184">Example</span></span>  
 <span data-ttu-id="14c24-185">Následující příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenosu a zprávu kódování elementy, zejména povolení spolehlivé relace, která udržuje stavu klienta a určuje záruky doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="14c24-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="14c24-186">Tato funkce je nakonfigurována v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="14c24-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="14c24-187">Příklad zobrazení konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="14c24-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14c24-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="14c24-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="14c24-189">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="14c24-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="14c24-190">Vazby</span><span class="sxs-lookup"><span data-stu-id="14c24-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="14c24-191">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="14c24-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="14c24-192">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="14c24-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="14c24-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="14c24-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
