---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736582"
---
# <a name="namedpipetransport"></a><span data-ttu-id="aa40b-101">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="aa40b-101">\<namedPipeTransport></span></span>
<span data-ttu-id="aa40b-102">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="aa40b-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="aa40b-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aa40b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aa40b-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="aa40b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aa40b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="aa40b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="aa40b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="aa40b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="aa40b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="aa40b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="aa40b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedPipeTransport >**</span><span class="sxs-lookup"><span data-stu-id="aa40b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa40b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa40b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa40b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa40b-110">Attributes and Elements</span></span>  
<span data-ttu-id="aa40b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa40b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa40b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa40b-112">Attributes</span></span>  
<span data-ttu-id="aa40b-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="aa40b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aa40b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa40b-114">Child Elements</span></span>  
  
|<span data-ttu-id="aa40b-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa40b-115">Element</span></span>|<span data-ttu-id="aa40b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="aa40b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa40b-117">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="aa40b-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="aa40b-118">Získá nebo nastaví <xref:System.TimeSpan>, která určuje maximální dobu, po kterou může kanál ve stavu inicializace, než se odpojí.</span><span class="sxs-lookup"><span data-stu-id="aa40b-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="aa40b-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="aa40b-119">ConnectionBufferSize</span></span>|<span data-ttu-id="aa40b-120">Získá nebo nastaví velikost vyrovnávací paměti, která se používá k přenosu bloku serializované zprávy na lince z klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="aa40b-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="aa40b-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="aa40b-121">hostNameComparisonMode</span></span>|<span data-ttu-id="aa40b-122">Získává nebo nastavuje hodnotu, která indikuje, jestli se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="aa40b-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="aa40b-123">Jeho</span><span class="sxs-lookup"><span data-stu-id="aa40b-123">manualAddressing</span></span>|<span data-ttu-id="aa40b-124">Získává nebo nastavuje hodnotu, která indikuje, jestli se vyžaduje ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="aa40b-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="aa40b-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="aa40b-125">maxBufferPoolSize</span></span>|<span data-ttu-id="aa40b-126">Získá nebo nastaví maximální velikost všech fondů vyrovnávací paměti používaných při přenosu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="aa40b-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="aa40b-127">Třída</span><span class="sxs-lookup"><span data-stu-id="aa40b-127">maxBufferSize</span></span>|<span data-ttu-id="aa40b-128">Získá nebo nastaví maximální velikost vyrovnávací paměti, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="aa40b-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="aa40b-129">U zpráv v datových proudech by tato hodnota měla být alespoň maximální možná velikost záhlaví zprávy, která je čtena v režimu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa40b-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="aa40b-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="aa40b-130">maxOutputDelay</span></span>|<span data-ttu-id="aa40b-131">Získá nebo nastaví maximální časový interval, po který může blok zprávy nebo úplná zpráva zůstat v paměti před odesláním do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa40b-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="aa40b-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="aa40b-132">maxPendingAccepts</span></span>|<span data-ttu-id="aa40b-133">Získá nebo nastaví maximální počet kanálů, které může služba čekat na naslouchací proces pro zpracování příchozích připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="aa40b-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="aa40b-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="aa40b-134">maxPendingConnections</span></span>|<span data-ttu-id="aa40b-135">Získá nebo nastaví maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="aa40b-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="aa40b-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="aa40b-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="aa40b-137">Získá a nastaví maximální povolenou velikost zprávy (v bajtech), kterou lze přijmout.</span><span class="sxs-lookup"><span data-stu-id="aa40b-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="aa40b-138">Třídy TransferMode</span><span class="sxs-lookup"><span data-stu-id="aa40b-138">transferMode</span></span>|<span data-ttu-id="aa40b-139">Získává nebo nastavuje hodnotu, která indikuje, jestli se zprávy ukládají do vyrovnávací paměti nebo streamují s přenosem orientovaným na připojení.</span><span class="sxs-lookup"><span data-stu-id="aa40b-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="aa40b-140">\<connectionPoolSettings > > \<namedPipeTransport</span><span class="sxs-lookup"><span data-stu-id="aa40b-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="aa40b-141">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="aa40b-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa40b-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa40b-142">Parent Elements</span></span>  
  
|<span data-ttu-id="aa40b-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa40b-143">Element</span></span>|<span data-ttu-id="aa40b-144">Popis</span><span class="sxs-lookup"><span data-stu-id="aa40b-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa40b-145">vazba \<</span><span class="sxs-lookup"><span data-stu-id="aa40b-145">\<binding></span></span>](bindings.md)|<span data-ttu-id="aa40b-146">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="aa40b-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa40b-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa40b-147">Remarks</span></span>  
<span data-ttu-id="aa40b-148">Tento přenos používá identifikátory URI ve formátu "NET. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="aa40b-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="aa40b-149">Jiné součásti identifikátoru URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="aa40b-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="aa40b-150">`namedPipeTransport` element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="aa40b-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="aa40b-151">Tento přenos se používá pro komunikaci mezi počítači Windows Communication Foundation (WCF) a WCF.</span><span class="sxs-lookup"><span data-stu-id="aa40b-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa40b-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa40b-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="aa40b-153">Přenosy</span><span class="sxs-lookup"><span data-stu-id="aa40b-153">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="aa40b-154">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="aa40b-154">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="aa40b-155">Vazby</span><span class="sxs-lookup"><span data-stu-id="aa40b-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aa40b-156">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="aa40b-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="aa40b-157">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="aa40b-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="aa40b-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aa40b-158">\<customBinding></span></span>](custombinding.md)
