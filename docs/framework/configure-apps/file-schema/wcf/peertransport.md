---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783348"
---
# <a name="peertransport"></a><span data-ttu-id="4b3be-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4b3be-101">\<peerTransport></span></span>
<span data-ttu-id="4b3be-102">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4b3be-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="4b3be-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4b3be-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4b3be-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4b3be-104">\<bindings></span></span>  
<span data-ttu-id="4b3be-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4b3be-105">\<customBinding></span></span>  
<span data-ttu-id="4b3be-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4b3be-106">\<binding></span></span>  
<span data-ttu-id="4b3be-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4b3be-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3be-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b3be-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b3be-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b3be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4b3be-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b3be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b3be-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b3be-111">Attributes</span></span>  
  
|<span data-ttu-id="4b3be-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b3be-112">Attribute</span></span>|<span data-ttu-id="4b3be-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4b3be-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b3be-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="4b3be-114">listenIpAddress</span></span>|<span data-ttu-id="4b3be-115">Řetězec, který určuje IP adresu, na které bude partnerský uzel přijímat zprávy TCP.</span><span class="sxs-lookup"><span data-stu-id="4b3be-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="4b3be-116">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="4b3be-116">The default is `null`.</span></span>|  
|<span data-ttu-id="4b3be-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4b3be-117">maxBufferPoolSize</span></span>|<span data-ttu-id="4b3be-118">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="4b3be-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="4b3be-119">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="4b3be-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="4b3be-120">Mnoho částí WCF pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3be-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="4b3be-121">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="4b3be-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4b3be-122">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="4b3be-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4b3be-123">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3be-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4b3be-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4b3be-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="4b3be-125">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4b3be-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="4b3be-126">Odesílatel zprávy obdrží chybu protokolu SOAP v případě, že zprávy je příliš velký pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="4b3be-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="4b3be-127">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="4b3be-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4b3be-128">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="4b3be-128">The default is 65536.</span></span>|  
|<span data-ttu-id="4b3be-129">port</span><span class="sxs-lookup"><span data-stu-id="4b3be-129">port</span></span>|<span data-ttu-id="4b3be-130">Celé číslo, které určuje portu síťového rozhraní, na které bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3be-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="4b3be-131">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="4b3be-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="4b3be-132">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="4b3be-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b3be-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b3be-133">Child Elements</span></span>  
  
|<span data-ttu-id="4b3be-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b3be-134">Element</span></span>|<span data-ttu-id="4b3be-135">Popis</span><span class="sxs-lookup"><span data-stu-id="4b3be-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b3be-136">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4b3be-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="4b3be-137">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="4b3be-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="4b3be-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4b3be-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b3be-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b3be-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4b3be-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b3be-140">Element</span></span>|<span data-ttu-id="4b3be-141">Popis</span><span class="sxs-lookup"><span data-stu-id="4b3be-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b3be-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4b3be-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4b3be-143">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4b3be-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b3be-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b3be-144">Remarks</span></span>  
 <span data-ttu-id="4b3be-145">Tento přenos nelze použít s smluv, které mají operace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4b3be-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3be-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b3be-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4b3be-147">Přenosy</span><span class="sxs-lookup"><span data-stu-id="4b3be-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="4b3be-148">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="4b3be-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4b3be-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="4b3be-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4b3be-150">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4b3be-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4b3be-151">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4b3be-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4b3be-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4b3be-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
