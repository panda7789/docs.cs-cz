---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 652cb551fb318d43d4284dbee48aeb994f056692
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746794"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="01a5c-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="01a5c-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="01a5c-103">Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenované kanály, když je zahrnutý do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="01a5c-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="01a5c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01a5c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="01a5c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="01a5c-105">\<bindings></span></span>  
<span data-ttu-id="01a5c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="01a5c-106">\<customBinding></span></span>  
<span data-ttu-id="01a5c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="01a5c-107">\<binding></span></span>  
<span data-ttu-id="01a5c-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="01a5c-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a5c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01a5c-109">Syntax</span></span>  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01a5c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01a5c-110">Attributes and Elements</span></span>  
<span data-ttu-id="01a5c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="01a5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01a5c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="01a5c-112">Attributes</span></span>  
<span data-ttu-id="01a5c-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="01a5c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01a5c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01a5c-114">Child Elements</span></span>  
  
|<span data-ttu-id="01a5c-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="01a5c-115">Element</span></span>|<span data-ttu-id="01a5c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="01a5c-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01a5c-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="01a5c-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="01a5c-118">Získá nebo nastaví <xref:System.TimeSpan> který určuje maximální dobu, po kanál, který může být ve stavu inicializace uplynutí dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="01a5c-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="01a5c-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="01a5c-119">ConnectionBufferSize</span></span>|<span data-ttu-id="01a5c-120">Získá nebo nastaví velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="01a5c-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="01a5c-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="01a5c-121">hostNameComparisonMode</span></span>|<span data-ttu-id="01a5c-122">Získá nebo nastaví hodnotu, která určuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="01a5c-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="01a5c-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="01a5c-123">manualAddressing</span></span>|<span data-ttu-id="01a5c-124">Získá nebo nastaví hodnotu, která určuje, zda je vyžadováno ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="01a5c-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="01a5c-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="01a5c-125">maxBufferPoolSize</span></span>|<span data-ttu-id="01a5c-126">Získá nebo nastaví maximální velikost v bajtech všechny fondy vyrovnávací paměti používané přenosu.</span><span class="sxs-lookup"><span data-stu-id="01a5c-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="01a5c-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="01a5c-127">maxBufferSize</span></span>|<span data-ttu-id="01a5c-128">Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="01a5c-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="01a5c-129">Pro proudu zpráv tato hodnota by měla být alespoň maximální možná velikost záhlaví zprávy, které jsou přečíst v režim s vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="01a5c-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="01a5c-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="01a5c-130">maxOutputDelay</span></span>|<span data-ttu-id="01a5c-131">Získá nebo nastaví maximální dobu, po kterou bloku zprávu nebo zprávu úplné může zůstat ve vyrovnávací paměti v paměti před odesláním interval.</span><span class="sxs-lookup"><span data-stu-id="01a5c-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="01a5c-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="01a5c-132">maxPendingAccepts</span></span>|<span data-ttu-id="01a5c-133">Získá nebo nastaví maximální počet kanálů služby může mít čekání na naslouchací proces pro zpracování příchozí připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="01a5c-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="01a5c-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="01a5c-134">maxPendingConnections</span></span>|<span data-ttu-id="01a5c-135">Získá nebo nastaví maximální počet připojení, které čekají na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="01a5c-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="01a5c-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="01a5c-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="01a5c-137">Získá nebo nastaví maximální povolenou velikost zprávy, v bajtech, které můžou přijímat.</span><span class="sxs-lookup"><span data-stu-id="01a5c-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="01a5c-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="01a5c-138">transferMode</span></span>|<span data-ttu-id="01a5c-139">Získá nebo nastaví hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.</span><span class="sxs-lookup"><span data-stu-id="01a5c-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="01a5c-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="01a5c-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="01a5c-141">Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.</span><span class="sxs-lookup"><span data-stu-id="01a5c-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01a5c-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01a5c-142">Parent Elements</span></span>  
  
|<span data-ttu-id="01a5c-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="01a5c-143">Element</span></span>|<span data-ttu-id="01a5c-144">Popis</span><span class="sxs-lookup"><span data-stu-id="01a5c-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01a5c-145">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="01a5c-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="01a5c-146">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="01a5c-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01a5c-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01a5c-147">Remarks</span></span>  
<span data-ttu-id="01a5c-148">Tento přenos používá identifikátory URI ve tvaru "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="01a5c-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="01a5c-149">Ostatní součásti URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="01a5c-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="01a5c-150">`namedPipeTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="01a5c-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="01a5c-151">Tento přenos slouží serveru na počítači Windows Communication Foundation (WCF), - na - WCF komunikace.</span><span class="sxs-lookup"><span data-stu-id="01a5c-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a5c-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="01a5c-152">See Also</span></span>  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
<span data-ttu-id="01a5c-153">[Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="01a5c-153">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="01a5c-154">[Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="01a5c-154">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="01a5c-155">[Vazby](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="01a5c-155">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="01a5c-156">[Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="01a5c-156">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="01a5c-157">[Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="01a5c-157">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="01a5c-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="01a5c-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
