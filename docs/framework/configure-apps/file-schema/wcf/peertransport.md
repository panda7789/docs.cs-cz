---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 76c100c0ec793d6dc4e7e5385f9dcf4521d0039e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151940"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="4024a-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="4024a-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="4024a-103">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4024a-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="4024a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4024a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4024a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4024a-105">\<bindings></span></span>  
<span data-ttu-id="4024a-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4024a-106">\<customBinding></span></span>  
<span data-ttu-id="4024a-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4024a-107">\<binding></span></span>  
<span data-ttu-id="4024a-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4024a-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4024a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4024a-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4024a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4024a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4024a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4024a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4024a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4024a-112">Attributes</span></span>  
  
|<span data-ttu-id="4024a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4024a-113">Attribute</span></span>|<span data-ttu-id="4024a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4024a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4024a-115">Třída listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="4024a-115">listenIpAddress</span></span>|<span data-ttu-id="4024a-116">Řetězec, který určuje IP adresu, na které bude partnerský uzel přijímat zprávy TCP.</span><span class="sxs-lookup"><span data-stu-id="4024a-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="4024a-117">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="4024a-117">The default is `null`.</span></span>|  
|<span data-ttu-id="4024a-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4024a-118">maxBufferPoolSize</span></span>|<span data-ttu-id="4024a-119">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="4024a-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="4024a-120">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="4024a-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="4024a-121">Mnoho částí WCF pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4024a-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="4024a-122">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="4024a-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4024a-123">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="4024a-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4024a-124">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4024a-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4024a-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4024a-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="4024a-126">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4024a-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="4024a-127">Odesílatel zprávy obdrží chybu protokolu SOAP v případě, že zprávy je příliš velký pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="4024a-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="4024a-128">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="4024a-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4024a-129">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="4024a-129">The default is 65536.</span></span>|  
|<span data-ttu-id="4024a-130">port</span><span class="sxs-lookup"><span data-stu-id="4024a-130">port</span></span>|<span data-ttu-id="4024a-131">Celé číslo, které určuje portu síťového rozhraní, na které bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="4024a-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="4024a-132">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="4024a-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="4024a-133">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="4024a-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4024a-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4024a-134">Child Elements</span></span>  
  
|<span data-ttu-id="4024a-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="4024a-135">Element</span></span>|<span data-ttu-id="4024a-136">Popis</span><span class="sxs-lookup"><span data-stu-id="4024a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4024a-137">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4024a-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="4024a-138">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="4024a-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="4024a-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4024a-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4024a-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4024a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="4024a-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="4024a-141">Element</span></span>|<span data-ttu-id="4024a-142">Popis</span><span class="sxs-lookup"><span data-stu-id="4024a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4024a-143">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4024a-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4024a-144">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4024a-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4024a-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4024a-145">Remarks</span></span>  
 <span data-ttu-id="4024a-146">Tento přenos nelze použít s smluv, které mají operace požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4024a-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4024a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="4024a-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="4024a-148">Přenosy</span><span class="sxs-lookup"><span data-stu-id="4024a-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="4024a-149">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="4024a-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="4024a-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="4024a-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4024a-151">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4024a-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4024a-152">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4024a-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4024a-153">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4024a-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
