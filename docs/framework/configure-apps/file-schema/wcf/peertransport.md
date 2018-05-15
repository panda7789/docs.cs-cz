---
title: '&lt;– peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: df192c6a602aa073f48fab4229b4be3fbeb2349d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="448d3-102">&lt;– peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="448d3-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="448d3-103">Definuje sdílené přenos vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="448d3-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="448d3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="448d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="448d3-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="448d3-105">\<bindings></span></span>  
<span data-ttu-id="448d3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="448d3-106">\<customBinding></span></span>  
<span data-ttu-id="448d3-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="448d3-107">\<binding></span></span>  
<span data-ttu-id="448d3-108">\<– peerTransport ></span><span class="sxs-lookup"><span data-stu-id="448d3-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="448d3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="448d3-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="448d3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="448d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="448d3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="448d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="448d3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="448d3-112">Attributes</span></span>  
  
|<span data-ttu-id="448d3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="448d3-113">Attribute</span></span>|<span data-ttu-id="448d3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="448d3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="448d3-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="448d3-115">listenIpAddress</span></span>|<span data-ttu-id="448d3-116">Řetězec, který určuje IP adresu, na kterém bude uzlu sdílené naslouchat zpráv TCP.</span><span class="sxs-lookup"><span data-stu-id="448d3-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="448d3-117">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="448d3-117">The default is `null`.</span></span>|  
|<span data-ttu-id="448d3-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="448d3-118">maxBufferPoolSize</span></span>|<span data-ttu-id="448d3-119">Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="448d3-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="448d3-120">Výchozí hodnota je 524288.</span><span class="sxs-lookup"><span data-stu-id="448d3-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="448d3-121">Mnoho části služby WCF pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="448d3-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="448d3-122">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="448d3-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="448d3-123">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="448d3-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="448d3-124">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="448d3-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="448d3-125">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="448d3-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="448d3-126">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlavičky.</span><span class="sxs-lookup"><span data-stu-id="448d3-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="448d3-127">Odesílatel zprávy obdrží chybu protokolu SOAP po příliš velké vzhledem k příjemce zprávy.</span><span class="sxs-lookup"><span data-stu-id="448d3-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="448d3-128">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="448d3-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="448d3-129">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="448d3-129">The default is 65536.</span></span>|  
|<span data-ttu-id="448d3-130">port</span><span class="sxs-lookup"><span data-stu-id="448d3-130">port</span></span>|<span data-ttu-id="448d3-131">Celé číslo, které určuje, na které tato vazba zpracuje rovnocenné zprávy TCP port síťového rozhraní.</span><span class="sxs-lookup"><span data-stu-id="448d3-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="448d3-132">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="448d3-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="448d3-133">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="448d3-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="448d3-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="448d3-134">Child Elements</span></span>  
  
|<span data-ttu-id="448d3-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="448d3-135">Element</span></span>|<span data-ttu-id="448d3-136">Popis</span><span class="sxs-lookup"><span data-stu-id="448d3-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="448d3-137">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="448d3-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="448d3-138">Definuje nastavení zabezpečení pro tento přenos.</span><span class="sxs-lookup"><span data-stu-id="448d3-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="448d3-139">Tento element je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="448d3-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="448d3-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="448d3-140">Parent Elements</span></span>  
  
|<span data-ttu-id="448d3-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="448d3-141">Element</span></span>|<span data-ttu-id="448d3-142">Popis</span><span class="sxs-lookup"><span data-stu-id="448d3-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="448d3-143">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="448d3-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="448d3-144">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="448d3-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="448d3-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="448d3-145">Remarks</span></span>  
 <span data-ttu-id="448d3-146">Tento přenos nelze použít s smluv, které mají požadavek nebo odpověď operace.</span><span class="sxs-lookup"><span data-stu-id="448d3-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="448d3-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="448d3-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="448d3-148">Přenosy</span><span class="sxs-lookup"><span data-stu-id="448d3-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="448d3-149">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="448d3-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="448d3-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="448d3-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="448d3-151">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="448d3-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="448d3-152">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="448d3-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="448d3-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="448d3-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
