---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738748"
---
# \<reliableSession>
<span data-ttu-id="26f12-101">Definuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="26f12-101">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="26f12-102">Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou.</span><span class="sxs-lookup"><span data-stu-id="26f12-102">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
## <a name="syntax"></a><span data-ttu-id="26f12-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26f12-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26f12-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="26f12-104">Attributes and Elements</span></span>  
 <span data-ttu-id="26f12-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="26f12-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26f12-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="26f12-106">Attributes</span></span>  
  
|<span data-ttu-id="26f12-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="26f12-107">Attribute</span></span>|<span data-ttu-id="26f12-108">Popis</span><span class="sxs-lookup"><span data-stu-id="26f12-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26f12-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="26f12-109">acknowledgementInterval</span></span>|<span data-ttu-id="26f12-110">A <xref:System.TimeSpan> který obsahuje maximální časový interval, po který bude kanál čekat na odeslání potvrzení pro zprávy přijaté do tohoto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="26f12-110">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="26f12-111">Výchozí hodnota je 00:00:0,2.</span><span class="sxs-lookup"><span data-stu-id="26f12-111">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="26f12-112">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="26f12-112">flowControlEnabled</span></span>|<span data-ttu-id="26f12-113">Logická hodnota, která označuje, zda je aktivováno pokročilé řízení toku, což je implementace řízení toku pro zasílání zpráv WS-Reliable specifická pro společnost Microsoft.</span><span class="sxs-lookup"><span data-stu-id="26f12-113">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="26f12-114">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="26f12-114">The default is `true`.</span></span>|  
|<span data-ttu-id="26f12-115">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="26f12-115">inactivityTimeout</span></span>|<span data-ttu-id="26f12-116">A <xref:System.TimeSpan> Určuje maximální dobu, po kterou kanál povolí druhé straně komunikace, aby před chybou kanálu neodesílala žádné zprávy.</span><span class="sxs-lookup"><span data-stu-id="26f12-116">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="26f12-117">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="26f12-117">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="26f12-118">Aktivita na kanálu je definována jako příjem zpráv aplikace nebo infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="26f12-118">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="26f12-119">Tato vlastnost určuje maximální dobu, po kterou může zůstat neaktivní relace aktivní.</span><span class="sxs-lookup"><span data-stu-id="26f12-119">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="26f12-120">Pokud delší doba projde bez aktivity, je relace přerušená infrastrukturou a chybami kanálu.</span><span class="sxs-lookup"><span data-stu-id="26f12-120">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="26f12-121">**Poznámka:**  Není nutné, aby aplikace pravidelně odesílala zprávy pro zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="26f12-121">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="26f12-122">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="26f12-122">maxPendingChannels</span></span>|<span data-ttu-id="26f12-123">Celé číslo, které určuje maximální počet kanálů, které mohou čekat na přijetí naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="26f12-123">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="26f12-124">Tato hodnota by měla být mezi 1 a 16384 včetně.</span><span class="sxs-lookup"><span data-stu-id="26f12-124">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="26f12-125">Výchozí hodnota je 4.</span><span class="sxs-lookup"><span data-stu-id="26f12-125">The default is 4.</span></span><br /><br /> <span data-ttu-id="26f12-126">Kanály čekají na vyřízení, když čekají na přijetí.</span><span class="sxs-lookup"><span data-stu-id="26f12-126">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="26f12-127">Po dosažení tohoto limitu se nevytvoří žádné kanály.</span><span class="sxs-lookup"><span data-stu-id="26f12-127">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="26f12-128">Místo toho jsou vloženy do režimu čekání, dokud tento počet nezmizí (přijetím nevyřízených kanálů).</span><span class="sxs-lookup"><span data-stu-id="26f12-128">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="26f12-129">Toto je omezení podle továrny.</span><span class="sxs-lookup"><span data-stu-id="26f12-129">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="26f12-130">Když je dosaženo prahové hodnoty a Vzdálená aplikace se pokusí vytvořit novou spolehlivou relaci, je žádost zamítnuta a operace otevření, která se zobrazí po zobrazení této chyby.</span><span class="sxs-lookup"><span data-stu-id="26f12-130">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="26f12-131">Toto omezení se nevztahuje na počet nevyřízených odchozích kanálů.</span><span class="sxs-lookup"><span data-stu-id="26f12-131">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="26f12-132">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="26f12-132">maxRetryCount</span></span>|<span data-ttu-id="26f12-133">Celé číslo, které určuje maximální počet pokusů, kolikrát se spolehlivý kanál pokusí znovu přenést zprávu, pro kterou neobdržel potvrzení, voláním Send na svém základním kanálu.</span><span class="sxs-lookup"><span data-stu-id="26f12-133">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="26f12-134">Tato hodnota by měla být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="26f12-134">This value should be greater than zero.</span></span> <span data-ttu-id="26f12-135">Výchozí hodnota je 8.</span><span class="sxs-lookup"><span data-stu-id="26f12-135">The default is 8.</span></span><br /><br /> <span data-ttu-id="26f12-136">Tato hodnota by měla být celé číslo větší než nula.</span><span class="sxs-lookup"><span data-stu-id="26f12-136">This value should be an integer greater than zero.</span></span> <span data-ttu-id="26f12-137">Pokud po posledním opětovném přenosu neobdrží potvrzení, dojde k chybám kanálu.</span><span class="sxs-lookup"><span data-stu-id="26f12-137">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="26f12-138">Zpráva se považuje za přenesenou, pokud příjemce vaši dodávku od příjemce potvrdí.</span><span class="sxs-lookup"><span data-stu-id="26f12-138">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="26f12-139">Pokud se u zprávy, která byla přenesena do určité doby, nedostalo potvrzení, infrastruktura tuto zprávu automaticky znovu odešle.</span><span class="sxs-lookup"><span data-stu-id="26f12-139">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="26f12-140">Infrastruktura se pokusí zprávu znovu odeslat maximálně v počtu pokusů určených touto vlastností.</span><span class="sxs-lookup"><span data-stu-id="26f12-140">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="26f12-141">Pokud po posledním opětovném přenosu neobdrží potvrzení, dojde k chybám kanálu.</span><span class="sxs-lookup"><span data-stu-id="26f12-141">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="26f12-142">Infrastruktura používá exponenciální back-vypnutý algoritmus k určení, kdy se má znovu přenést na základě vypočtené průměrné doby odezvy.</span><span class="sxs-lookup"><span data-stu-id="26f12-142">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="26f12-143">Čas zpočátku začíná 1 sekundou před opakovaným přenosem a zdvojnásobuje se při každém pokusu, což má za následek přibližně 8,5 minut předávání mezi prvním pokusem o přenos a posledním pokusem o opakování přenosu.</span><span class="sxs-lookup"><span data-stu-id="26f12-143">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="26f12-144">Čas při prvním pokusu o opakování přenosu se upraví podle vypočtené doby odezvy a výsledným roztažením času se tyto pokusy budou měnit.</span><span class="sxs-lookup"><span data-stu-id="26f12-144">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="26f12-145">To umožňuje, aby se čas opětovného přenosu dynamicky přizpůsobil různým podmínkám sítě.</span><span class="sxs-lookup"><span data-stu-id="26f12-145">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="26f12-146">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="26f12-146">maxTransferWindowSize</span></span>|<span data-ttu-id="26f12-147">Celé číslo, které určuje maximální velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="26f12-147">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="26f12-148">Platné hodnoty jsou od 1 do 4096 včetně.</span><span class="sxs-lookup"><span data-stu-id="26f12-148">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="26f12-149">V klientovi tento atribut definuje maximální velikost vyrovnávací paměti používané spolehlivým kanálem pro uchovávání zpráv, které příjemce ještě nepřijal.</span><span class="sxs-lookup"><span data-stu-id="26f12-149">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="26f12-150">Jednotka kvóty je zpráva.</span><span class="sxs-lookup"><span data-stu-id="26f12-150">The unit of the quota is a message.</span></span> <span data-ttu-id="26f12-151">Pokud je vyrovnávací paměť plná, zablokují se další operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="26f12-151">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="26f12-152">Tento atribut na přijímači definuje maximální velikost vyrovnávací paměti, kterou kanál používá k ukládání příchozích zpráv, které ještě nebyly odeslány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="26f12-152">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="26f12-153">Pokud je vyrovnávací paměť plná, může příjemce tiše vyřadit další zprávy a vyžadovat opětovné odeslání klientem.</span><span class="sxs-lookup"><span data-stu-id="26f12-153">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="26f12-154">ordered</span><span class="sxs-lookup"><span data-stu-id="26f12-154">ordered</span></span>|<span data-ttu-id="26f12-155">Logická hodnota určující, zda mají být zprávy zaručeny pro doručení v pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="26f12-155">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="26f12-156">Pokud je toto nastavení `false` , zprávy mohou být doručeny mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="26f12-156">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="26f12-157">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="26f12-157">The default is `true`.</span></span>|  
|<span data-ttu-id="26f12-158">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="26f12-158">reliableMessagingVersion</span></span>|<span data-ttu-id="26f12-159">Platná hodnota z <xref:System.ServiceModel.ReliableMessagingVersion> , která určuje verzi WS-ReliableMessaging, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="26f12-159">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26f12-160">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="26f12-160">Child Elements</span></span>  
 <span data-ttu-id="26f12-161">Žádné</span><span class="sxs-lookup"><span data-stu-id="26f12-161">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26f12-162">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="26f12-162">Parent Elements</span></span>  
  
|<span data-ttu-id="26f12-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="26f12-163">Element</span></span>|<span data-ttu-id="26f12-164">Description</span><span class="sxs-lookup"><span data-stu-id="26f12-164">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="26f12-165">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="26f12-165">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26f12-166">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26f12-166">Remarks</span></span>  
 <span data-ttu-id="26f12-167">Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="26f12-167">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="26f12-168">Spolehlivé zasílání zpráv zopakuje komunikaci při selhání a umožňuje zasílat záruky doručování, jako je doručení zpráv v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="26f12-168">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="26f12-169">Relace uchovávají stav pro klienty mezi voláními.</span><span class="sxs-lookup"><span data-stu-id="26f12-169">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="26f12-170">Tento prvek také volitelně poskytuje objednané doručování zpráv.</span><span class="sxs-lookup"><span data-stu-id="26f12-170">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="26f12-171">Tato implementovaná relace může vzájemně přenášet zprostředkovatele SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="26f12-171">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="26f12-172">Každý prvek vazby představuje krok zpracování při posílání nebo přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="26f12-172">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="26f12-173">V době běhu vytvoří vazby prvky vytváření kanálů a naslouchací procesy, které jsou nezbytné pro vytváření odchozích a příchozích zásobníků kanálů potřebných pro odesílání a příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="26f12-173">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="26f12-174">`reliableSession`Poskytuje volitelnou vrstvu v zásobníku, která může navázat spolehlivou relaci mezi koncovými body a nakonfigurovat chování této relace.</span><span class="sxs-lookup"><span data-stu-id="26f12-174">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="26f12-175">Další informace najdete v tématu [spolehlivé relace](../../../wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="26f12-175">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f12-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="26f12-176">Example</span></span>  
 <span data-ttu-id="26f12-177">Následující příklad ukazuje, jak nakonfigurovat vlastní vazbu s různými prvky transportu a kódování zpráv, zejména povolením spolehlivých relací, které udržují stav klienta a určují záruku doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="26f12-177">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="26f12-178">Tato funkce je nakonfigurovaná v konfiguračních souborech aplikací pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="26f12-178">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="26f12-179">V příkladu se zobrazuje konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="26f12-179">The example show the service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26f12-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="26f12-180">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="26f12-181">Spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="26f12-181">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="26f12-182">Vazby</span><span class="sxs-lookup"><span data-stu-id="26f12-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="26f12-183">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="26f12-183">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="26f12-184">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="26f12-184">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
