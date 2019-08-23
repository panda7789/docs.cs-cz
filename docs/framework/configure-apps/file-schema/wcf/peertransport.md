---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 1ad05fd9125ecc8b3d5797e0dd335adbf808db84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933847"
---
# <a name="peertransport"></a><span data-ttu-id="5e138-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="5e138-101">\<peerTransport></span></span>
<span data-ttu-id="5e138-102">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="5e138-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="5e138-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e138-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5e138-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="5e138-104">\<bindings></span></span>  
<span data-ttu-id="5e138-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5e138-105">\<customBinding></span></span>  
<span data-ttu-id="5e138-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5e138-106">\<binding></span></span>  
<span data-ttu-id="5e138-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="5e138-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e138-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e138-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e138-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e138-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e138-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e138-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e138-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e138-111">Attributes</span></span>  
  
|<span data-ttu-id="5e138-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e138-112">Attribute</span></span>|<span data-ttu-id="5e138-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5e138-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e138-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="5e138-114">listenIpAddress</span></span>|<span data-ttu-id="5e138-115">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="5e138-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="5e138-116">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="5e138-116">The default is `null`.</span></span>|  
|<span data-ttu-id="5e138-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5e138-117">maxBufferPoolSize</span></span>|<span data-ttu-id="5e138-118">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5e138-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="5e138-119">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="5e138-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="5e138-120">Mnoho částí služby WCF používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5e138-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="5e138-121">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="5e138-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5e138-122">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="5e138-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5e138-123">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="5e138-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5e138-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5e138-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="5e138-125">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="5e138-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="5e138-126">Odesílatel zprávy obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="5e138-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="5e138-127">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="5e138-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5e138-128">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="5e138-128">The default is 65536.</span></span>|  
|<span data-ttu-id="5e138-129">port</span><span class="sxs-lookup"><span data-stu-id="5e138-129">port</span></span>|<span data-ttu-id="5e138-130">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="5e138-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="5e138-131">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="5e138-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="5e138-132">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="5e138-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e138-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e138-133">Child Elements</span></span>  
  
|<span data-ttu-id="5e138-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e138-134">Element</span></span>|<span data-ttu-id="5e138-135">Popis</span><span class="sxs-lookup"><span data-stu-id="5e138-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e138-136">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5e138-136">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="5e138-137">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="5e138-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="5e138-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5e138-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e138-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e138-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5e138-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e138-140">Element</span></span>|<span data-ttu-id="5e138-141">Popis</span><span class="sxs-lookup"><span data-stu-id="5e138-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e138-142">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5e138-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5e138-143">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5e138-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e138-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e138-144">Remarks</span></span>  
 <span data-ttu-id="5e138-145">Tento přenos nelze použít u kontraktů, které mají operace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5e138-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e138-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e138-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5e138-147">Přenosy</span><span class="sxs-lookup"><span data-stu-id="5e138-147">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5e138-148">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="5e138-148">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5e138-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="5e138-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5e138-150">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5e138-150">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5e138-151">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5e138-151">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5e138-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5e138-152">\<customBinding></span></span>](custombinding.md)
