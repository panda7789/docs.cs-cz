---
title: '&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 1fbc4e179fa5f59a903dad51728638a1e182b23e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753076"
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="bfa48-102">&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="bfa48-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="bfa48-103">Určuje nastavení fondu další připojení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="bfa48-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="bfa48-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bfa48-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bfa48-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bfa48-105">\<bindings></span></span>  
<span data-ttu-id="bfa48-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bfa48-106">\<customBinding></span></span>  
<span data-ttu-id="bfa48-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="bfa48-107">\<binding></span></span>  
<span data-ttu-id="bfa48-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="bfa48-108">\<tcpTransport></span></span>  
<span data-ttu-id="bfa48-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="bfa48-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa48-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfa48-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfa48-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bfa48-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bfa48-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bfa48-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfa48-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bfa48-113">Attributes</span></span>  
  
|<span data-ttu-id="bfa48-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bfa48-114">Attribute</span></span>|<span data-ttu-id="bfa48-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bfa48-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="bfa48-116">Řetězec, který definuje název fondu připojení používané pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="bfa48-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="bfa48-117">V přenášené datovými proudy režimu nejsou sdílené připojení – zakázáno sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="bfa48-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="bfa48-118">Výchozí hodnota je řetězec "default".</span><span class="sxs-lookup"><span data-stu-id="bfa48-118">The default is a "default" string.</span></span> <span data-ttu-id="bfa48-119">Tato hodnota izolovat připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="bfa48-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="bfa48-120">U kladné <xref:System.TimeSpan> , určuje maximální dobu může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="bfa48-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="bfa48-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="bfa48-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="bfa48-122">A <xref:System.TimeSpan> určující dobu, po jejímž uplynutí je uzavřený aktivní připojení.</span><span class="sxs-lookup"><span data-stu-id="bfa48-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="bfa48-123">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="bfa48-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="bfa48-124">Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="bfa48-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="bfa48-125">Mezipaměť připojení používá přenos TCP vytvoří nové připojení podle potřeby pro každý koncový bod, až do limitu mezipaměti, kterou je nastavit `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="bfa48-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="bfa48-126">Kladné celé číslo, které určuje maximální počet připojení, aby vzdálený koncový bod iniciovat službu.</span><span class="sxs-lookup"><span data-stu-id="bfa48-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="bfa48-127">Připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.</span><span class="sxs-lookup"><span data-stu-id="bfa48-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="bfa48-128">`idleTimeout` Omezí doba trvání, ve kterém připojení zůstat ve frontě, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bfa48-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="bfa48-129">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="bfa48-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="bfa48-130">Tento atribut omezuje počet souběžných aktivních připojení z klienta pro koncový bod konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="bfa48-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="bfa48-131">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se mohou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="bfa48-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="bfa48-132">V takovém případě je třeba upravit tuto hodnotu delší než maximální počet očekávané simultánních klientských připojení na konkrétní.</span><span class="sxs-lookup"><span data-stu-id="bfa48-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfa48-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bfa48-133">Child Elements</span></span>  
 <span data-ttu-id="bfa48-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="bfa48-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfa48-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bfa48-135">Parent Elements</span></span>  
  
|<span data-ttu-id="bfa48-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="bfa48-136">Element</span></span>|<span data-ttu-id="bfa48-137">Popis</span><span class="sxs-lookup"><span data-stu-id="bfa48-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfa48-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bfa48-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="bfa48-139">Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="bfa48-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfa48-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfa48-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bfa48-141">Přenosy</span><span class="sxs-lookup"><span data-stu-id="bfa48-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="bfa48-142">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="bfa48-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="bfa48-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="bfa48-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bfa48-144">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="bfa48-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bfa48-145">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="bfa48-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bfa48-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bfa48-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
