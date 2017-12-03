---
title: "&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b0bd7303f714847228bcd8bfed7134fe9942c1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="44134-102">&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="44134-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="44134-103">Určuje nastavení fondu další připojení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="44134-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="44134-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="44134-104">\<system.serviceModel></span></span>  
<span data-ttu-id="44134-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="44134-105">\<bindings></span></span>  
<span data-ttu-id="44134-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="44134-106">\<customBinding></span></span>  
<span data-ttu-id="44134-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="44134-107">\<binding></span></span>  
<span data-ttu-id="44134-108">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="44134-108">\<tcpTransport></span></span>  
<span data-ttu-id="44134-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="44134-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44134-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44134-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44134-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44134-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44134-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44134-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44134-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="44134-113">Attributes</span></span>  
  
|<span data-ttu-id="44134-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="44134-114">Attribute</span></span>|<span data-ttu-id="44134-115">Popis</span><span class="sxs-lookup"><span data-stu-id="44134-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="44134-116">Řetězec, který definuje název fondu připojení používané pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="44134-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="44134-117">V přenášené datovými proudy režimu nejsou sdílené připojení – zakázáno sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="44134-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="44134-118">Výchozí hodnota je řetězec "default".</span><span class="sxs-lookup"><span data-stu-id="44134-118">The default is a "default" string.</span></span> <span data-ttu-id="44134-119">Tato hodnota izolovat připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="44134-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="44134-120">U kladné <xref:System.TimeSpan> , určuje maximální dobu může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="44134-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="44134-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="44134-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="44134-122">A <xref:System.TimeSpan> určující dobu, po jejímž uplynutí je uzavřený aktivní připojení.</span><span class="sxs-lookup"><span data-stu-id="44134-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="44134-123">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="44134-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="44134-124">Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="44134-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="44134-125">Mezipaměť připojení používá přenos TCP vytvoří nové připojení podle potřeby pro každý koncový bod, až do limitu mezipaměti, kterou je nastavit`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="44134-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="44134-126">Kladné celé číslo, které určuje maximální počet připojení, aby vzdálený koncový bod iniciovat službu.</span><span class="sxs-lookup"><span data-stu-id="44134-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="44134-127">Připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.</span><span class="sxs-lookup"><span data-stu-id="44134-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="44134-128">`idleTimeout` Omezí doba trvání, ve kterém připojení zůstat ve frontě, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="44134-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="44134-129">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="44134-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="44134-130">Tento atribut omezuje počet souběžných aktivních připojení z klienta pro koncový bod konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="44134-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="44134-131">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se mohou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="44134-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="44134-132">V takovém případě je třeba upravit tuto hodnotu delší než maximální počet očekávané simultánních klientských připojení na konkrétní.</span><span class="sxs-lookup"><span data-stu-id="44134-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44134-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44134-133">Child Elements</span></span>  
 <span data-ttu-id="44134-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="44134-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44134-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44134-135">Parent Elements</span></span>  
  
|<span data-ttu-id="44134-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="44134-136">Element</span></span>|<span data-ttu-id="44134-137">Popis</span><span class="sxs-lookup"><span data-stu-id="44134-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44134-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="44134-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="44134-139">Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="44134-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44134-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="44134-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="44134-141">Přenosy</span><span class="sxs-lookup"><span data-stu-id="44134-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="44134-142">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="44134-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="44134-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="44134-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="44134-144">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="44134-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="44134-145">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="44134-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="44134-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="44134-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
