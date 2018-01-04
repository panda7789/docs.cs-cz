---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7802bff708cb081aa9f54f76a35ff5842ad60544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="48ea2-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="48ea2-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="48ea2-103">Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenované kanály, když je zahrnutý do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="48ea2-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="48ea2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="48ea2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="48ea2-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="48ea2-105">\<bindings></span></span>  
<span data-ttu-id="48ea2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="48ea2-106">\<customBinding></span></span>  
<span data-ttu-id="48ea2-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="48ea2-107">\<binding></span></span>  
<span data-ttu-id="48ea2-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="48ea2-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ea2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48ea2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48ea2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48ea2-110">Attributes and Elements</span></span>  
<span data-ttu-id="48ea2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48ea2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48ea2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="48ea2-112">Attributes</span></span>  
<span data-ttu-id="48ea2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="48ea2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48ea2-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48ea2-114">Child Elements</span></span>  
  
|<span data-ttu-id="48ea2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="48ea2-115">Element</span></span>|<span data-ttu-id="48ea2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="48ea2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48ea2-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="48ea2-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="48ea2-118">Získá nebo nastaví <xref:System.TimeSpan> který určuje maximální dobu, po kanál, který může být ve stavu inicializace uplynutí dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="48ea2-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="48ea2-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="48ea2-119">ConnectionBufferSize</span></span>|<span data-ttu-id="48ea2-120">Získá nebo nastaví velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="48ea2-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="48ea2-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="48ea2-121">hostNameComparisonMode</span></span>|<span data-ttu-id="48ea2-122">Získá nebo nastaví hodnotu, která určuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="48ea2-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="48ea2-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="48ea2-123">manualAddressing</span></span>|<span data-ttu-id="48ea2-124">Získá nebo nastaví hodnotu, která určuje, zda je vyžadováno ruční adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="48ea2-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="48ea2-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="48ea2-125">maxBufferPoolSize</span></span>|<span data-ttu-id="48ea2-126">Získá nebo nastaví maximální velikost v bajtech všechny fondy vyrovnávací paměti používané přenosu.</span><span class="sxs-lookup"><span data-stu-id="48ea2-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="48ea2-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="48ea2-127">maxBufferSize</span></span>|<span data-ttu-id="48ea2-128">Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="48ea2-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="48ea2-129">Pro proudu zpráv tato hodnota by měla být alespoň maximální možná velikost záhlaví zprávy, které jsou přečíst v režim s vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="48ea2-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="48ea2-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="48ea2-130">maxOutputDelay</span></span>|<span data-ttu-id="48ea2-131">Získá nebo nastaví maximální dobu, po kterou bloku zprávu nebo zprávu úplné může zůstat ve vyrovnávací paměti v paměti před odesláním interval.</span><span class="sxs-lookup"><span data-stu-id="48ea2-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="48ea2-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="48ea2-132">maxPendingAccepts</span></span>|<span data-ttu-id="48ea2-133">Získá nebo nastaví maximální počet kanálů služby může mít čekání na naslouchací proces pro zpracování příchozí připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="48ea2-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="48ea2-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="48ea2-134">maxPendingConnections</span></span>|<span data-ttu-id="48ea2-135">Získá nebo nastaví maximální počet připojení, které čekají na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="48ea2-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="48ea2-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="48ea2-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="48ea2-137">Získá nebo nastaví maximální povolenou velikost zprávy, v bajtech, které můžou přijímat.</span><span class="sxs-lookup"><span data-stu-id="48ea2-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="48ea2-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="48ea2-138">transferMode</span></span>|<span data-ttu-id="48ea2-139">Získá nebo nastaví hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.</span><span class="sxs-lookup"><span data-stu-id="48ea2-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="48ea2-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="48ea2-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="48ea2-141">Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.</span><span class="sxs-lookup"><span data-stu-id="48ea2-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48ea2-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48ea2-142">Parent Elements</span></span>  
  
|<span data-ttu-id="48ea2-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="48ea2-143">Element</span></span>|<span data-ttu-id="48ea2-144">Popis</span><span class="sxs-lookup"><span data-stu-id="48ea2-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48ea2-145">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="48ea2-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="48ea2-146">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="48ea2-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48ea2-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48ea2-147">Remarks</span></span>  
<span data-ttu-id="48ea2-148">Tento přenos používá identifikátory URI ve tvaru "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="48ea2-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="48ea2-149">Ostatní součásti URI jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="48ea2-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="48ea2-150">`namedPipeTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="48ea2-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="48ea2-151">Tento přenos slouží serveru na počítači Windows Communication Foundation (WCF), - na - WCF komunikace.</span><span class="sxs-lookup"><span data-stu-id="48ea2-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ea2-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="48ea2-152">See Also</span></span>  
<span data-ttu-id="48ea2-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="48ea2-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="48ea2-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="48ea2-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="48ea2-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="48ea2-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="48ea2-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="48ea2-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="48ea2-157">[Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="48ea2-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="48ea2-158">[Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="48ea2-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="48ea2-159">[Vazby](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="48ea2-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="48ea2-160">[Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="48ea2-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="48ea2-161">[Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="48ea2-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="48ea2-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="48ea2-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
