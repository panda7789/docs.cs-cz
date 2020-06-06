---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736582"
---
# \<namedPipeTransport>
<span data-ttu-id="76908-101">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="76908-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="76908-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76908-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76908-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76908-103">Attributes and Elements</span></span>  
<span data-ttu-id="76908-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76908-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76908-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="76908-105">Attributes</span></span>  
<span data-ttu-id="76908-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="76908-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76908-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76908-107">Child Elements</span></span>  
  
|<span data-ttu-id="76908-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="76908-108">Element</span></span>|<span data-ttu-id="76908-109">Description</span><span class="sxs-lookup"><span data-stu-id="76908-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76908-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="76908-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="76908-111">Získá nebo nastaví <xref:System.TimeSpan> , který určuje maximální dobu, po kterou může kanál ve stavu inicializace, než bude odpojen.</span><span class="sxs-lookup"><span data-stu-id="76908-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="76908-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="76908-112">ConnectionBufferSize</span></span>|<span data-ttu-id="76908-113">Získá nebo nastaví velikost vyrovnávací paměti, která se používá k přenosu bloku serializované zprávy na lince z klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="76908-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="76908-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="76908-114">hostNameComparisonMode</span></span>|<span data-ttu-id="76908-115">Získává nebo nastavuje hodnotu, která indikuje, jestli se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="76908-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="76908-116">Jeho</span><span class="sxs-lookup"><span data-stu-id="76908-116">manualAddressing</span></span>|<span data-ttu-id="76908-117">Získává nebo nastavuje hodnotu, která indikuje, jestli se vyžaduje ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="76908-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="76908-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="76908-118">maxBufferPoolSize</span></span>|<span data-ttu-id="76908-119">Získá nebo nastaví maximální velikost všech fondů vyrovnávací paměti používaných při přenosu (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="76908-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="76908-120">Třída</span><span class="sxs-lookup"><span data-stu-id="76908-120">maxBufferSize</span></span>|<span data-ttu-id="76908-121">Získá nebo nastaví maximální velikost vyrovnávací paměti, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="76908-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="76908-122">U zpráv v datových proudech by tato hodnota měla být alespoň maximální možná velikost záhlaví zprávy, která je čtena v režimu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="76908-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="76908-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="76908-123">maxOutputDelay</span></span>|<span data-ttu-id="76908-124">Získá nebo nastaví maximální časový interval, po který může blok zprávy nebo úplná zpráva zůstat v paměti před odesláním do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="76908-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="76908-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="76908-125">maxPendingAccepts</span></span>|<span data-ttu-id="76908-126">Získá nebo nastaví maximální počet kanálů, které může služba čekat na naslouchací proces pro zpracování příchozích připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="76908-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="76908-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="76908-127">maxPendingConnections</span></span>|<span data-ttu-id="76908-128">Získá nebo nastaví maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="76908-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="76908-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="76908-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="76908-130">Získá a nastaví maximální povolenou velikost zprávy (v bajtech), kterou lze přijmout.</span><span class="sxs-lookup"><span data-stu-id="76908-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="76908-131">Třídy TransferMode</span><span class="sxs-lookup"><span data-stu-id="76908-131">transferMode</span></span>|<span data-ttu-id="76908-132">Získává nebo nastavuje hodnotu, která indikuje, jestli se zprávy ukládají do vyrovnávací paměti nebo streamují s přenosem orientovaným na připojení.</span><span class="sxs-lookup"><span data-stu-id="76908-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="76908-133">\<connectionPoolSettings>tohoto\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="76908-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="76908-134">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="76908-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76908-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76908-135">Parent Elements</span></span>  
  
|<span data-ttu-id="76908-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="76908-136">Element</span></span>|<span data-ttu-id="76908-137">Description</span><span class="sxs-lookup"><span data-stu-id="76908-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="76908-138">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="76908-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76908-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76908-139">Remarks</span></span>  
<span data-ttu-id="76908-140">Tento přenos používá identifikátory URI ve formátu "NET. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="76908-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="76908-141">Jiné součásti identifikátoru URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="76908-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="76908-142">`namedPipeTransport`Element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="76908-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="76908-143">Tento přenos se používá pro komunikaci mezi počítači Windows Communication Foundation (WCF) a WCF.</span><span class="sxs-lookup"><span data-stu-id="76908-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76908-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="76908-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="76908-145">Přenosy</span><span class="sxs-lookup"><span data-stu-id="76908-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="76908-146">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="76908-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="76908-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="76908-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="76908-148">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="76908-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="76908-149">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="76908-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
