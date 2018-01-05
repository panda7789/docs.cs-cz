---
title: '&lt;tcpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f534bab962e83f76dab7e411cc3c2ca14779df9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttcptransportgt"></a><span data-ttu-id="bcb2e-102">&lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="bcb2e-102">&lt;tcpTransport&gt;</span></span>
<span data-ttu-id="bcb2e-103">Definuje přenos TCP, který lze použít pro vlastní vazby pomocí kanálu pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-103">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
 <span data-ttu-id="bcb2e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bcb2e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-105">\<bindings></span></span>  
<span data-ttu-id="bcb2e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-106">\<customBinding></span></span>  
<span data-ttu-id="bcb2e-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-107">\<binding></span></span>  
<span data-ttu-id="bcb2e-108">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-108">\<tcpTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb2e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcb2e-109">Syntax</span></span>  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcb2e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bcb2e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bcb2e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcb2e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bcb2e-112">Attributes</span></span>  
  
|<span data-ttu-id="bcb2e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bcb2e-113">Attribute</span></span>|<span data-ttu-id="bcb2e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bcb2e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcb2e-115">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bcb2e-115">channelInitializationTimeout</span></span>|<span data-ttu-id="bcb2e-116">Získá nebo nastaví časový limit pro inicializaci kanálu třeba přijmout.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-116">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="bcb2e-117">Maximální doba kanál, který může být ve stavu inicializace uplynutí dojde k odpojení v sekundách.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-117">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="bcb2e-118">Tato kvóta obsahuje dobu připojení protokolu TCP může trvat, kterými se ověří pomocí .net rámců zprávu protokolu.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-118">This quota includes the time a TCP connection can take to authenticate itself using the .Net Message Framing protocol.</span></span> <span data-ttu-id="bcb2e-119">Klient musí poslat některé počáteční data předtím, než má server dostatek informací k provedení ověřování.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-119">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="bcb2e-120">Výchozí hodnota je 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-120">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="bcb2e-121">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bcb2e-121">connectionBufferSize</span></span>|<span data-ttu-id="bcb2e-122">Získá nebo nastaví velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-122">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="bcb2e-123">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bcb2e-123">hostNameComparisonMode</span></span>|<span data-ttu-id="bcb2e-124">Získá nebo nastaví hodnotu, která určuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-124">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="bcb2e-125">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="bcb2e-125">listenBacklog</span></span>|<span data-ttu-id="bcb2e-126">Maximální počet požadavků ve frontě připojení, které mohou být čekající na vyřízení pro webovou službu.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-126">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="bcb2e-127">`connectionLeaseTimeout` Atribut omezuje trvání klient čekat, než se připojený. teprve potom vyvolání k výjimce připojení.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-127">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="bcb2e-128">Toto je soketu úrovně vlastnost, která určuje maximální počet požadavků ve frontě připojení, které mohou být čekající na vyřízení pro webovou službu.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-128">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="bcb2e-129">Když ListenBacklog příliš nízké, WCF zastaví přijímá žádosti a proto vyřadit nová připojení, dokud nebude server uznává některé z existujících připojení ve frontě. Výchozí hodnota je 16 * počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-129">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections .The default is 16 * number of processors.</span></span>|  
|<span data-ttu-id="bcb2e-130">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="bcb2e-130">manualAddressing</span></span>|<span data-ttu-id="bcb2e-131">Získá nebo nastaví hodnotu, která určuje, zda je vyžadováno ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-131">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="bcb2e-132">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bcb2e-132">maxBufferPoolSize</span></span>|<span data-ttu-id="bcb2e-133">Získá nebo nastaví maximální velikost všechny fondy vyrovnávací paměti používané přenosu.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-133">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="bcb2e-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bcb2e-134">maxBufferSize</span></span>|<span data-ttu-id="bcb2e-135">Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-135">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="bcb2e-136">Pro proudu zpráv tato hodnota by měla být alespoň maximální možná velikost záhlaví zprávy, které jsou přečíst v režim s vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-136">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="bcb2e-137">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bcb2e-137">maxOutputDelay</span></span>|<span data-ttu-id="bcb2e-138">Získá nebo nastaví maximální dobu, po kterou bloku zprávu nebo zprávu úplné může zůstat ve vyrovnávací paměti v paměti před odesláním interval.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-138">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="bcb2e-139">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bcb2e-139">maxPendingAccepts</span></span>|<span data-ttu-id="bcb2e-140">Získá nebo nastaví maximální počet čekající asynchronní přijmout operace, které jsou k dispozici pro zpracování příchozí připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-140">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="bcb2e-141">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bcb2e-141">maxPendingConnections</span></span>|<span data-ttu-id="bcb2e-142">Získá nebo nastaví maximální počet připojení, které čekají na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-142">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="bcb2e-143">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bcb2e-143">maxReceivedMessageSize</span></span>|<span data-ttu-id="bcb2e-144">Získá nebo nastaví maximální povolenou velikost zprávy, může být přijata.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-144">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="bcb2e-145">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="bcb2e-145">portSharingEnabled</span></span>|<span data-ttu-id="bcb2e-146">Logická hodnota, která určuje, zda je sdílení portů TCP povolený pro toto připojení.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-146">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="bcb2e-147">Pokud je to `false`, každou vazbu budou používat svůj vlastní výhradní port.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-147">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="bcb2e-148">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="bcb2e-149">Toto nastavení platí pouze pro služby.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-149">This setting is relevant only to services.</span></span> <span data-ttu-id="bcb2e-150">Ovlivněné nejsou klienty.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-150">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="bcb2e-151">Použití tohoto nastavení vyžaduje povolení změnou její typ spuštění ručně nebo automaticky pomocí technologie Windows Communication Foundation (WCF) TCP Port sdílení služby</span><span class="sxs-lookup"><span data-stu-id="bcb2e-151">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="bcb2e-152">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="bcb2e-152">teredoEnabled</span></span>|<span data-ttu-id="bcb2e-153">Logická hodnota, která určuje, zda je povoleno Teredo (technologie pro adresování klienty, kteří jsou za bránami firewall).</span><span class="sxs-lookup"><span data-stu-id="bcb2e-153">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="bcb2e-154">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-154">The default is `false`.</span></span><br /><br /> <span data-ttu-id="bcb2e-155">Tato vlastnost umožňuje Teredo základní soketu TCP.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-155">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="bcb2e-156">Další informace najdete v tématu [Teredo přehled](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="bcb2e-156">For more information, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span><br /><br /> <span data-ttu-id="bcb2e-157">Tato vlastnost se vztahuje pouze na [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] a [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bcb2e-157">This property is applicable only on [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] and [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span></span> [!INCLUDE[wv](../../../../../includes/wv-md.md)]<span data-ttu-id="bcb2e-158">má možnost konfigurace celého systému pro Teredo, takže když systém Vista, tato vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-158"> has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="bcb2e-159">Teredo vyžaduje, aby měl počítače klienta a služby Microsoft IPv6 zásobníku nainstalovaná a správně nakonfigurovaná pro použití Teredo.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-159">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span> <span data-ttu-id="bcb2e-160">Další informace o konfiguraci Teredo najdete v tématu [Teredo přehled](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="bcb2e-160">For more information about configuring Teredo, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span> <span data-ttu-id="bcb2e-161">Další informace najdete v tématu [Windows Server 2003 technologie centrech](http://go.microsoft.com/fwlink/?LinkId=49888).</span><span class="sxs-lookup"><span data-stu-id="bcb2e-161">For more information, see [Windows Server 2003 Technology Centers](http://go.microsoft.com/fwlink/?LinkId=49888).</span></span>|  
|<span data-ttu-id="bcb2e-162">transferMode</span><span class="sxs-lookup"><span data-stu-id="bcb2e-162">transferMode</span></span>|<span data-ttu-id="bcb2e-163">Získá nebo nastaví hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-163">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="bcb2e-164">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="bcb2e-164">connectionPoolSettings</span></span>|<span data-ttu-id="bcb2e-165">Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-165">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcb2e-166">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bcb2e-166">Child Elements</span></span>  
 <span data-ttu-id="bcb2e-167">Žádné</span><span class="sxs-lookup"><span data-stu-id="bcb2e-167">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcb2e-168">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bcb2e-168">Parent Elements</span></span>  
  
|<span data-ttu-id="bcb2e-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="bcb2e-169">Element</span></span>|<span data-ttu-id="bcb2e-170">Popis</span><span class="sxs-lookup"><span data-stu-id="bcb2e-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcb2e-171">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bcb2e-172">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-172">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb2e-173">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcb2e-173">Remarks</span></span>  
 <span data-ttu-id="bcb2e-174">Tento přenos používá identifikátory URI ve tvaru "net.tcp://hostname: port či cestu".</span><span class="sxs-lookup"><span data-stu-id="bcb2e-174">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="bcb2e-175">Ostatní součásti URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-175">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="bcb2e-176">`tcpTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-176">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="bcb2e-177">Tento přenos je optimalizovaná pro komunikaci WCF WCF.</span><span class="sxs-lookup"><span data-stu-id="bcb2e-177">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb2e-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcb2e-178">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bcb2e-179">Přenosy</span><span class="sxs-lookup"><span data-stu-id="bcb2e-179">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="bcb2e-180">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="bcb2e-180">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="bcb2e-181">Vazby</span><span class="sxs-lookup"><span data-stu-id="bcb2e-181">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bcb2e-182">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="bcb2e-182">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bcb2e-183">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="bcb2e-183">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bcb2e-184">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bcb2e-184">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
