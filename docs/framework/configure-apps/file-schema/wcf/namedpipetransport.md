---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: fd7dc38e229b6135f91fc159596ed1669d43701a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772356"
---
# <a name="namedpipetransport"></a><span data-ttu-id="dfdcd-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="dfdcd-101">\<namedPipeTransport></span></span>
<span data-ttu-id="dfdcd-102">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="dfdcd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dfdcd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="dfdcd-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="dfdcd-104">\<bindings></span></span>  
<span data-ttu-id="dfdcd-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dfdcd-105">\<customBinding></span></span>  
<span data-ttu-id="dfdcd-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="dfdcd-106">\<binding></span></span>  
<span data-ttu-id="dfdcd-107">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="dfdcd-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdcd-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfdcd-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfdcd-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dfdcd-109">Attributes and Elements</span></span>  
<span data-ttu-id="dfdcd-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfdcd-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dfdcd-111">Attributes</span></span>  
<span data-ttu-id="dfdcd-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="dfdcd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dfdcd-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dfdcd-113">Child Elements</span></span>  
  
|<span data-ttu-id="dfdcd-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="dfdcd-114">Element</span></span>|<span data-ttu-id="dfdcd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="dfdcd-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfdcd-116">třídě channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="dfdcd-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="dfdcd-117">Získá nebo nastaví <xref:System.TimeSpan> , která určuje maximální dobu kanálu může být ve stavu inicializace před jeho odpojením.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="dfdcd-118">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="dfdcd-118">ConnectionBufferSize</span></span>|<span data-ttu-id="dfdcd-119">Získá nebo nastaví velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="dfdcd-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="dfdcd-120">hostNameComparisonMode</span></span>|<span data-ttu-id="dfdcd-121">Získá nebo nastaví hodnotu určující, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="dfdcd-122">Vlastnost manualAddressing</span><span class="sxs-lookup"><span data-stu-id="dfdcd-122">manualAddressing</span></span>|<span data-ttu-id="dfdcd-123">Získá nebo nastaví hodnotu určující, jestli je potřeba ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="dfdcd-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="dfdcd-124">maxBufferPoolSize</span></span>|<span data-ttu-id="dfdcd-125">Získá nebo nastaví maximální velikost v bajtech, všechny fondy vyrovnávací paměti používané přenos.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="dfdcd-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="dfdcd-126">maxBufferSize</span></span>|<span data-ttu-id="dfdcd-127">Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="dfdcd-128">Pro proudu zpráv tato hodnota by měla být aspoň maximální možná velikost záhlaví zpráv, které jsou v režimu vyrovnávací paměti pro čtení.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="dfdcd-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="dfdcd-129">maxOutputDelay</span></span>|<span data-ttu-id="dfdcd-130">Získá nebo nastaví maximální interval času, který blok zprávy, nebo celá zpráva může zůstat ve vyrovnávací paměti v paměti před odesláním navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="dfdcd-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="dfdcd-131">maxPendingAccepts</span></span>|<span data-ttu-id="dfdcd-132">Získá nebo nastaví maximální počet kanálů služby může mít čekání na naslouchací proces pro zpracování příchozích připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="dfdcd-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="dfdcd-133">maxPendingConnections</span></span>|<span data-ttu-id="dfdcd-134">Získá nebo nastaví maximální počet připojení čeká na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="dfdcd-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="dfdcd-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="dfdcd-136">Získá nebo nastaví maximální povolenou velikost zprávy, v bajtech, které může být přijata.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="dfdcd-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="dfdcd-137">transferMode</span></span>|<span data-ttu-id="dfdcd-138">Získá nebo nastaví hodnotu určující, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="dfdcd-139">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="dfdcd-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="dfdcd-140">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dfdcd-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dfdcd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="dfdcd-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="dfdcd-142">Element</span></span>|<span data-ttu-id="dfdcd-143">Popis</span><span class="sxs-lookup"><span data-stu-id="dfdcd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfdcd-144">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="dfdcd-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="dfdcd-145">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfdcd-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfdcd-146">Remarks</span></span>  
<span data-ttu-id="dfdcd-147">Tento přenos používá identifikátory URI ve tvaru "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="dfdcd-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="dfdcd-148">Ostatní součásti URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="dfdcd-149">`namedPipeTransport` Element je výchozí bod pro vytvoření vlastní vazby, který implementuje přenosový protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="dfdcd-150">Tento přenos se používá pro na počítači Windows Communication Foundation (WCF) - na - WCF komunikace.</span><span class="sxs-lookup"><span data-stu-id="dfdcd-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdcd-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfdcd-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="dfdcd-152">Přenosy</span><span class="sxs-lookup"><span data-stu-id="dfdcd-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="dfdcd-153">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="dfdcd-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="dfdcd-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="dfdcd-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="dfdcd-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="dfdcd-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dfdcd-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="dfdcd-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="dfdcd-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dfdcd-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
