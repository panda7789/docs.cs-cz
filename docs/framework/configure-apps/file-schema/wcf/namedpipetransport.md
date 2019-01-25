---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: cdb2863ff376a92f7c4b679f4812b895ac3f2234
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518836"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="bc691-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="bc691-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="bc691-103">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="bc691-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="bc691-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc691-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc691-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bc691-105">\<bindings></span></span>  
<span data-ttu-id="bc691-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bc691-106">\<customBinding></span></span>  
<span data-ttu-id="bc691-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bc691-107">\<binding></span></span>  
<span data-ttu-id="bc691-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bc691-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc691-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc691-109">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc691-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc691-110">Attributes and Elements</span></span>  
<span data-ttu-id="bc691-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc691-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc691-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc691-112">Attributes</span></span>  
<span data-ttu-id="bc691-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc691-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc691-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc691-114">Child Elements</span></span>  
  
|<span data-ttu-id="bc691-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc691-115">Element</span></span>|<span data-ttu-id="bc691-116">Popis</span><span class="sxs-lookup"><span data-stu-id="bc691-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc691-117">třídě channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bc691-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="bc691-118">Získá nebo nastaví <xref:System.TimeSpan> , která určuje maximální dobu kanálu může být ve stavu inicializace před jeho odpojením.</span><span class="sxs-lookup"><span data-stu-id="bc691-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="bc691-119">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc691-119">ConnectionBufferSize</span></span>|<span data-ttu-id="bc691-120">Získá nebo nastaví velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="bc691-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="bc691-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bc691-121">hostNameComparisonMode</span></span>|<span data-ttu-id="bc691-122">Získá nebo nastaví hodnotu určující, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="bc691-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="bc691-123">Vlastnost manualAddressing</span><span class="sxs-lookup"><span data-stu-id="bc691-123">manualAddressing</span></span>|<span data-ttu-id="bc691-124">Získá nebo nastaví hodnotu určující, jestli je potřeba ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc691-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="bc691-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bc691-125">maxBufferPoolSize</span></span>|<span data-ttu-id="bc691-126">Získá nebo nastaví maximální velikost v bajtech, všechny fondy vyrovnávací paměti používané přenos.</span><span class="sxs-lookup"><span data-stu-id="bc691-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="bc691-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc691-127">maxBufferSize</span></span>|<span data-ttu-id="bc691-128">Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="bc691-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="bc691-129">Pro proudu zpráv tato hodnota by měla být aspoň maximální možná velikost záhlaví zpráv, které jsou v režimu vyrovnávací paměti pro čtení.</span><span class="sxs-lookup"><span data-stu-id="bc691-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="bc691-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bc691-130">maxOutputDelay</span></span>|<span data-ttu-id="bc691-131">Získá nebo nastaví maximální interval času, který blok zprávy, nebo celá zpráva může zůstat ve vyrovnávací paměti v paměti před odesláním navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="bc691-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="bc691-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bc691-132">maxPendingAccepts</span></span>|<span data-ttu-id="bc691-133">Získá nebo nastaví maximální počet kanálů služby může mít čekání na naslouchací proces pro zpracování příchozích připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="bc691-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="bc691-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bc691-134">maxPendingConnections</span></span>|<span data-ttu-id="bc691-135">Získá nebo nastaví maximální počet připojení čeká na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="bc691-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="bc691-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bc691-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="bc691-137">Získá nebo nastaví maximální povolenou velikost zprávy, v bajtech, které může být přijata.</span><span class="sxs-lookup"><span data-stu-id="bc691-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="bc691-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="bc691-138">transferMode</span></span>|<span data-ttu-id="bc691-139">Získá nebo nastaví hodnotu určující, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.</span><span class="sxs-lookup"><span data-stu-id="bc691-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="bc691-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bc691-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="bc691-141">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="bc691-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc691-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc691-142">Parent Elements</span></span>  
  
|<span data-ttu-id="bc691-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc691-143">Element</span></span>|<span data-ttu-id="bc691-144">Popis</span><span class="sxs-lookup"><span data-stu-id="bc691-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc691-145">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bc691-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bc691-146">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="bc691-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc691-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc691-147">Remarks</span></span>  
<span data-ttu-id="bc691-148">Tento přenos používá identifikátory URI ve tvaru "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="bc691-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="bc691-149">Ostatní součásti URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="bc691-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="bc691-150">`namedPipeTransport` Element je výchozí bod pro vytvoření vlastní vazby, který implementuje přenosový protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="bc691-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="bc691-151">Tento přenos se používá pro na počítači Windows Communication Foundation (WCF) - na - WCF komunikace.</span><span class="sxs-lookup"><span data-stu-id="bc691-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc691-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc691-152">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bc691-153">Přenosy</span><span class="sxs-lookup"><span data-stu-id="bc691-153">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="bc691-154">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="bc691-154">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bc691-155">Vazby</span><span class="sxs-lookup"><span data-stu-id="bc691-155">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bc691-156">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="bc691-156">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bc691-157">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="bc691-157">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bc691-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bc691-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
