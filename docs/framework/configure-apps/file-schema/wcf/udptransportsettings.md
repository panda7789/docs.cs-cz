---
title: '&lt;udpTransportSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f55d7bbedf764760ddc79622ce7ecf7fbbaa31d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltudptransportsettingsgt"></a><span data-ttu-id="5d3bd-102">&lt;udpTransportSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="5d3bd-102">&lt;udpTransportSettings&gt;</span></span>
<span data-ttu-id="5d3bd-103">Tento element konfigurace se zobrazí nastavení přenosu UDP pro [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span><span class="sxs-lookup"><span data-stu-id="5d3bd-103">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="5d3bd-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5d3bd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5d3bd-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5d3bd-105">\<standardEndpoints></span></span>  
<span data-ttu-id="5d3bd-106">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="5d3bd-106">\<udpDiscoveryEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3bd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d3bd-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer" 
                              maxBufferPoolSize="Integer" 
                              maxMulticastRetransmitCount="Integer" 
                              maxPendingMessageCount="Integer" 
                              maxReceivedMessageSize="Integer" 
                              maxUnicastRetransmitCount="Integer" 
                              multicastInterfaceId="String" 
                              socketReceiveBufferSize="Integer" 
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d3bd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5d3bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d3bd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d3bd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5d3bd-110">Attributes</span></span>  
  
|<span data-ttu-id="5d3bd-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5d3bd-111">Attribute</span></span>|<span data-ttu-id="5d3bd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5d3bd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d3bd-113">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="5d3bd-113">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="5d3bd-114">Celé číslo, které určuje maximální počet hodnotách hash zpráv, které používá přenos pro nalezení duplicitních zpráv.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-114">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="5d3bd-115">Duplicitní detekce se provádí na úrovni Správce TransportManager.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-115">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="5d3bd-116">Nastavení této vlastnosti na hodnotu 0 zakáže vyhledávání duplicit.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-116">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="5d3bd-117">Tento atribut umožňuje správcům systému a vývojářům vypnout algoritmy detekce duplicitních zpráv.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-117">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="5d3bd-118">To může být žádoucí, pokud chcete implementovat vlastní detekci duplikátů algoritmus.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-118">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="5d3bd-119">Výchozí hodnota je 4112.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-119">The default is 4112.</span></span>|  
|<span data-ttu-id="5d3bd-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5d3bd-120">maxBufferPoolSize</span></span>|<span data-ttu-id="5d3bd-121">Celé číslo, které určuje maximální velikost všechny fondy vyrovnávací paměti používané přenosu.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-121">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="5d3bd-122">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="5d3bd-122">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="5d3bd-123">Celé číslo, které určuje maximální počet, kolikrát zpráva by měla být přeneseny (kromě první odesílání).</span><span class="sxs-lookup"><span data-stu-id="5d3bd-123">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="5d3bd-124">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-124">The default is 2.</span></span>|  
|<span data-ttu-id="5d3bd-125">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="5d3bd-125">maxPendingMessageCount</span></span>|<span data-ttu-id="5d3bd-126">Celé číslo, které určuje maximální počet zpráv, které bylo přijato, ale ještě nebyla odebrána z InputQueue instance jednotlivých kanálu.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-126">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="5d3bd-127">Pokud InputQueue narazil na svůj limit počtu čeká na zprávu, zpráva se zahodí.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-127">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="5d3bd-128">Výchozí hodnota je 32.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-128">The default is 32.</span></span>|  
|<span data-ttu-id="5d3bd-129">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5d3bd-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="5d3bd-130">Celé číslo, které určuje maximální velikost zprávy, která může být zpracována vazbou.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-130">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="5d3bd-131">Výchozí hodnota je 65507.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-131">The default value is 65507.</span></span>|  
|<span data-ttu-id="5d3bd-132">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="5d3bd-132">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="5d3bd-133">Celé číslo, které určuje maximální počet, kolikrát zpráva by měla být přeneseny (kromě první odesílání).</span><span class="sxs-lookup"><span data-stu-id="5d3bd-133">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="5d3bd-134">Pokud je zpráva odeslána na adresu jednosměrového vysílání a příjmu zprávy odpovědi s odpovídající související s hlavičkou, může přenos ukončit již v rané fázi (před opětovným odesláním nakonfigurované stanovený počet).</span><span class="sxs-lookup"><span data-stu-id="5d3bd-134">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="5d3bd-135">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-135">The default value is 1.</span></span>|  
|<span data-ttu-id="5d3bd-136">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="5d3bd-136">multicastInterfaceId</span></span>|<span data-ttu-id="5d3bd-137">Řetězec, který jednoznačně identifikuje síťový adaptér, který se má použít při odesílání a příjem přenosů vícesměrového vysílání na počítačích s více adresami.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-137">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="5d3bd-138">Za běhu, bude přenos používat hodnota atributu k vyhledávání index rozhraní, které se pak použije k nastavení `IP_MULTICAST_IF` a `IPV6_MULTICAST_IF` soketu možnosti.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-138">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="5d3bd-139">Stejný index rozhraní se použije při připojení ke skupině vícesměrového vysílání, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-139">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="5d3bd-140">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-140">The default value is `null`.</span></span>|  
|<span data-ttu-id="5d3bd-141">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="5d3bd-141">socketReceiveBufferSize</span></span>|<span data-ttu-id="5d3bd-142">Celé číslo, které určuje velikost vyrovnávací paměti receive na základní soketu rozhraní WinSock.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-142">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="5d3bd-143">Může uživatel přijímající kanál používat tento atribut na vazby pro řízení chování při přijetí dat v systému.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-143">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="5d3bd-144">Například danou aplikaci, která spotřebovává příchozí zprávy WCF na maximální prahová hodnota, pomocí vyšší hodnota pro tento atribut by povolit zpráv zásobníku ve vyrovnávací paměti rozhraní WinSock při čekání na aplikaci, která bude moct jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-144">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="5d3bd-145">Pomocí na nižší hodnotu ve stejné situaci by způsobilo získávání ztracených zpráv. Tento atribut zpřístupňuje základní rozhraní WinSock `SO_RCVBUF` soketu možnost. Hodnota tohoto atributu musí být alespoň velikost `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-145">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="5d3bd-146">Jeho nastavení na hodnotu menší, než `maxReceivedMessageSize` způsobí výjimku modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-146">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="5d3bd-147">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-147">The default value is 65536.</span></span>|  
|<span data-ttu-id="5d3bd-148">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="5d3bd-148">timeToLive</span></span>|<span data-ttu-id="5d3bd-149">Celé číslo, které určuje počet síťové segment směrování, které mohou procházet paketů vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-149">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="5d3bd-150">Tento atribut zveřejňuje funkce související s `IP_MULTICAST_TTL` a `IP_TTL` soketu možnosti.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-150">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="5d3bd-151">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-151">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d3bd-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5d3bd-152">Child Elements</span></span>  
 <span data-ttu-id="5d3bd-153">Žádné</span><span class="sxs-lookup"><span data-stu-id="5d3bd-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d3bd-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5d3bd-154">Parent Elements</span></span>  
  
|<span data-ttu-id="5d3bd-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d3bd-155">Element</span></span>|<span data-ttu-id="5d3bd-156">Popis</span><span class="sxs-lookup"><span data-stu-id="5d3bd-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d3bd-157">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="5d3bd-157">\<udpDiscoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|<span data-ttu-id="5d3bd-158">Standardní koncový bod, který má pevnou zjišťování přenosu vazby kontraktu a UDP.</span><span class="sxs-lookup"><span data-stu-id="5d3bd-158">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d3bd-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d3bd-159">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
