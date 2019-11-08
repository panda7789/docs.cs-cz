---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736507"
---
# <a name="peertransport"></a><span data-ttu-id="62bc7-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="62bc7-101">\<peerTransport></span></span>
<span data-ttu-id="62bc7-102">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="62bc7-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="62bc7-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="62bc7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62bc7-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="62bc7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62bc7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="62bc7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="62bc7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="62bc7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="62bc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="62bc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="62bc7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**</span><span class="sxs-lookup"><span data-stu-id="62bc7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62bc7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62bc7-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62bc7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="62bc7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62bc7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="62bc7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62bc7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="62bc7-112">Attributes</span></span>  
  
|<span data-ttu-id="62bc7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="62bc7-113">Attribute</span></span>|<span data-ttu-id="62bc7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="62bc7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62bc7-115">Třída ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="62bc7-115">listenIpAddress</span></span>|<span data-ttu-id="62bc7-116">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="62bc7-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="62bc7-117">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="62bc7-117">The default is `null`.</span></span>|  
|<span data-ttu-id="62bc7-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="62bc7-118">maxBufferPoolSize</span></span>|<span data-ttu-id="62bc7-119">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62bc7-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="62bc7-120">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="62bc7-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="62bc7-121">Mnoho částí služby WCF používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62bc7-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="62bc7-122">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="62bc7-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="62bc7-123">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="62bc7-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="62bc7-124">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="62bc7-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="62bc7-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="62bc7-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="62bc7-126">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="62bc7-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="62bc7-127">Odesílatel zprávy obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="62bc7-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="62bc7-128">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="62bc7-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="62bc7-129">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="62bc7-129">The default is 65536.</span></span>|  
|<span data-ttu-id="62bc7-130">port</span><span class="sxs-lookup"><span data-stu-id="62bc7-130">port</span></span>|<span data-ttu-id="62bc7-131">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="62bc7-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="62bc7-132">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="62bc7-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="62bc7-133">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="62bc7-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62bc7-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="62bc7-134">Child Elements</span></span>  
  
|<span data-ttu-id="62bc7-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="62bc7-135">Element</span></span>|<span data-ttu-id="62bc7-136">Popis</span><span class="sxs-lookup"><span data-stu-id="62bc7-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62bc7-137">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="62bc7-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="62bc7-138">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="62bc7-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="62bc7-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="62bc7-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62bc7-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="62bc7-140">Parent Elements</span></span>  
  
|<span data-ttu-id="62bc7-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="62bc7-141">Element</span></span>|<span data-ttu-id="62bc7-142">Popis</span><span class="sxs-lookup"><span data-stu-id="62bc7-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62bc7-143">vazba \<</span><span class="sxs-lookup"><span data-stu-id="62bc7-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="62bc7-144">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="62bc7-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62bc7-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62bc7-145">Remarks</span></span>  
 <span data-ttu-id="62bc7-146">Tento přenos nelze použít u kontraktů, které mají operace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="62bc7-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bc7-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62bc7-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="62bc7-148">Přenosy</span><span class="sxs-lookup"><span data-stu-id="62bc7-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="62bc7-149">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="62bc7-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="62bc7-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="62bc7-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62bc7-151">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="62bc7-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="62bc7-152">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="62bc7-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="62bc7-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="62bc7-153">\<customBinding></span></span>](custombinding.md)
