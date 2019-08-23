---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933209"
---
# <a name="namedpipetransport"></a><span data-ttu-id="02cbf-101">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="02cbf-101">\<namedPipeTransport></span></span>
<span data-ttu-id="02cbf-102">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="02cbf-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="02cbf-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02cbf-103">\<system.serviceModel></span></span>  
<span data-ttu-id="02cbf-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="02cbf-104">\<bindings></span></span>  
<span data-ttu-id="02cbf-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="02cbf-105">\<customBinding></span></span>  
<span data-ttu-id="02cbf-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="02cbf-106">\<binding></span></span>  
<span data-ttu-id="02cbf-107">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="02cbf-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02cbf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02cbf-108">Syntax</span></span>  
  
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
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02cbf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02cbf-109">Attributes and Elements</span></span>  
<span data-ttu-id="02cbf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02cbf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02cbf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="02cbf-111">Attributes</span></span>  
<span data-ttu-id="02cbf-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="02cbf-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02cbf-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02cbf-113">Child Elements</span></span>  
  
|<span data-ttu-id="02cbf-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="02cbf-114">Element</span></span>|<span data-ttu-id="02cbf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="02cbf-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02cbf-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="02cbf-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="02cbf-117">Získá nebo nastaví <xref:System.TimeSpan> , který určuje maximální dobu, po kterou může kanál ve stavu inicializace, než bude odpojen.</span><span class="sxs-lookup"><span data-stu-id="02cbf-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="02cbf-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="02cbf-118">ConnectionBufferSize</span></span>|<span data-ttu-id="02cbf-119">Získá nebo nastaví velikost vyrovnávací paměti, která se používá k přenosu bloku serializované zprávy na lince z klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="02cbf-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="02cbf-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="02cbf-120">hostNameComparisonMode</span></span>|<span data-ttu-id="02cbf-121">Získává nebo nastavuje hodnotu, která indikuje, jestli se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="02cbf-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="02cbf-122">Jeho</span><span class="sxs-lookup"><span data-stu-id="02cbf-122">manualAddressing</span></span>|<span data-ttu-id="02cbf-123">Získává nebo nastavuje hodnotu, která indikuje, jestli se vyžaduje ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="02cbf-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="02cbf-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="02cbf-124">maxBufferPoolSize</span></span>|<span data-ttu-id="02cbf-125">Získá nebo nastaví maximální velikost všech fondů vyrovnávací paměti používaných při přenosu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="02cbf-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="02cbf-126">Třída</span><span class="sxs-lookup"><span data-stu-id="02cbf-126">maxBufferSize</span></span>|<span data-ttu-id="02cbf-127">Získá nebo nastaví maximální velikost vyrovnávací paměti, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="02cbf-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="02cbf-128">U zpráv v datových proudech by tato hodnota měla být alespoň maximální možná velikost záhlaví zprávy, která je čtena v režimu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="02cbf-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="02cbf-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="02cbf-129">maxOutputDelay</span></span>|<span data-ttu-id="02cbf-130">Získá nebo nastaví maximální časový interval, po který může blok zprávy nebo úplná zpráva zůstat v paměti před odesláním do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="02cbf-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="02cbf-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="02cbf-131">maxPendingAccepts</span></span>|<span data-ttu-id="02cbf-132">Získá nebo nastaví maximální počet kanálů, které může služba čekat na naslouchací proces pro zpracování příchozích připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="02cbf-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="02cbf-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="02cbf-133">maxPendingConnections</span></span>|<span data-ttu-id="02cbf-134">Získá nebo nastaví maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="02cbf-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="02cbf-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="02cbf-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="02cbf-136">Získá a nastaví maximální povolenou velikost zprávy (v bajtech), kterou lze přijmout.</span><span class="sxs-lookup"><span data-stu-id="02cbf-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="02cbf-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="02cbf-137">transferMode</span></span>|<span data-ttu-id="02cbf-138">Získává nebo nastavuje hodnotu, která indikuje, jestli se zprávy ukládají do vyrovnávací paměti nebo streamují s přenosem orientovaným na připojení.</span><span class="sxs-lookup"><span data-stu-id="02cbf-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="02cbf-139">\<connectionPoolSettings > \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="02cbf-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="02cbf-140">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="02cbf-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02cbf-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02cbf-141">Parent Elements</span></span>  
  
|<span data-ttu-id="02cbf-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="02cbf-142">Element</span></span>|<span data-ttu-id="02cbf-143">Popis</span><span class="sxs-lookup"><span data-stu-id="02cbf-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02cbf-144">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="02cbf-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="02cbf-145">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="02cbf-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02cbf-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02cbf-146">Remarks</span></span>  
<span data-ttu-id="02cbf-147">Tento přenos používá identifikátory URI ve formátu "NET. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="02cbf-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="02cbf-148">Jiné součásti identifikátoru URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="02cbf-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="02cbf-149">`namedPipeTransport` Element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="02cbf-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="02cbf-150">Tento přenos se používá pro komunikaci mezi počítači Windows Communication Foundation (WCF) a WCF.</span><span class="sxs-lookup"><span data-stu-id="02cbf-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02cbf-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02cbf-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="02cbf-152">Přenosy</span><span class="sxs-lookup"><span data-stu-id="02cbf-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="02cbf-153">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="02cbf-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="02cbf-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="02cbf-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02cbf-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="02cbf-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="02cbf-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="02cbf-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="02cbf-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="02cbf-157">\<customBinding></span></span>](custombinding.md)
