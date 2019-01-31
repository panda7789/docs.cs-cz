---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 8962a0c018442ed590b62e53ea8323d80e334df7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290092"
---
# <a name="peertransport"></a><span data-ttu-id="1c5ce-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-101">\<peerTransport></span></span>
<span data-ttu-id="1c5ce-102">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="1c5ce-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1c5ce-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1c5ce-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-104">\<bindings></span></span>  
<span data-ttu-id="1c5ce-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1c5ce-105">\<customBinding></span></span>  
<span data-ttu-id="1c5ce-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-106">\<binding></span></span>  
<span data-ttu-id="1c5ce-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c5ce-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c5ce-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c5ce-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c5ce-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c5ce-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c5ce-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c5ce-111">Attributes</span></span>  
  
|<span data-ttu-id="1c5ce-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c5ce-112">Attribute</span></span>|<span data-ttu-id="1c5ce-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1c5ce-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c5ce-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="1c5ce-114">listenIpAddress</span></span>|<span data-ttu-id="1c5ce-115">Řetězec, který určuje IP adresu, na které bude partnerský uzel přijímat zprávy TCP.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="1c5ce-116">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-116">The default is `null`.</span></span>|  
|<span data-ttu-id="1c5ce-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1c5ce-117">maxBufferPoolSize</span></span>|<span data-ttu-id="1c5ce-118">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="1c5ce-119">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="1c5ce-120">Mnoho částí WCF pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="1c5ce-121">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1c5ce-122">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1c5ce-123">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="1c5ce-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1c5ce-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="1c5ce-125">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="1c5ce-126">Odesílatel zprávy obdrží chybu protokolu SOAP v případě, že zprávy je příliš velký pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="1c5ce-127">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1c5ce-128">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-128">The default is 65536.</span></span>|  
|<span data-ttu-id="1c5ce-129">port</span><span class="sxs-lookup"><span data-stu-id="1c5ce-129">port</span></span>|<span data-ttu-id="1c5ce-130">Celé číslo, které určuje portu síťového rozhraní, na které bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="1c5ce-131">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="1c5ce-132">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c5ce-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c5ce-133">Child Elements</span></span>  
  
|<span data-ttu-id="1c5ce-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c5ce-134">Element</span></span>|<span data-ttu-id="1c5ce-135">Popis</span><span class="sxs-lookup"><span data-stu-id="1c5ce-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c5ce-136">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="1c5ce-137">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="1c5ce-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c5ce-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c5ce-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1c5ce-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c5ce-140">Element</span></span>|<span data-ttu-id="1c5ce-141">Popis</span><span class="sxs-lookup"><span data-stu-id="1c5ce-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c5ce-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1c5ce-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1c5ce-143">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c5ce-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c5ce-144">Remarks</span></span>  
 <span data-ttu-id="1c5ce-145">Tento přenos nelze použít s smluv, které mají operace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1c5ce-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5ce-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c5ce-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1c5ce-147">Přenosy</span><span class="sxs-lookup"><span data-stu-id="1c5ce-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="1c5ce-148">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="1c5ce-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="1c5ce-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="1c5ce-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1c5ce-150">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1c5ce-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1c5ce-151">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1c5ce-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1c5ce-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1c5ce-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
