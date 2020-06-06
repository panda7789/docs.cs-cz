---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736507"
---
# \<peerTransport>
<span data-ttu-id="0b111-101">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="0b111-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="0b111-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b111-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b111-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0b111-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0b111-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0b111-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b111-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="0b111-105">Attributes</span></span>  
  
|<span data-ttu-id="0b111-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="0b111-106">Attribute</span></span>|<span data-ttu-id="0b111-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0b111-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b111-108">Třída ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="0b111-108">listenIpAddress</span></span>|<span data-ttu-id="0b111-109">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="0b111-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="0b111-110">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="0b111-110">The default is `null`.</span></span>|  
|<span data-ttu-id="0b111-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0b111-111">maxBufferPoolSize</span></span>|<span data-ttu-id="0b111-112">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0b111-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="0b111-113">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="0b111-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="0b111-114">Mnoho částí služby WCF používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0b111-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="0b111-115">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="0b111-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0b111-116">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="0b111-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0b111-117">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="0b111-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0b111-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0b111-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="0b111-119">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="0b111-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="0b111-120">Odesílatel zprávy obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="0b111-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="0b111-121">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="0b111-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0b111-122">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="0b111-122">The default is 65536.</span></span>|  
|<span data-ttu-id="0b111-123">port</span><span class="sxs-lookup"><span data-stu-id="0b111-123">port</span></span>|<span data-ttu-id="0b111-124">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="0b111-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="0b111-125">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="0b111-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="0b111-126">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="0b111-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b111-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0b111-127">Child Elements</span></span>  
  
|<span data-ttu-id="0b111-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="0b111-128">Element</span></span>|<span data-ttu-id="0b111-129">Description</span><span class="sxs-lookup"><span data-stu-id="0b111-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="0b111-130">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="0b111-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="0b111-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="0b111-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b111-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0b111-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0b111-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="0b111-133">Element</span></span>|<span data-ttu-id="0b111-134">Description</span><span class="sxs-lookup"><span data-stu-id="0b111-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0b111-135">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="0b111-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b111-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b111-136">Remarks</span></span>  
 <span data-ttu-id="0b111-137">Tento přenos nelze použít u kontraktů, které mají operace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0b111-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b111-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b111-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0b111-139">Přenosy</span><span class="sxs-lookup"><span data-stu-id="0b111-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="0b111-140">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="0b111-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="0b111-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="0b111-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0b111-142">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="0b111-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0b111-143">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0b111-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
