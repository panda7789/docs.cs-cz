---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129971"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="d2447-102">\<connectionPoolSettings> of \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="d2447-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="d2447-103">Určuje další nastavení fondu připojení přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="d2447-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="d2447-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d2447-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d2447-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d2447-105">\<bindings></span></span>  
<span data-ttu-id="d2447-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d2447-106">\<customBinding></span></span>  
<span data-ttu-id="d2447-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2447-107">\<binding></span></span>  
<span data-ttu-id="d2447-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="d2447-108">\<tcpTransport></span></span>  
<span data-ttu-id="d2447-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="d2447-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2447-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2447-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2447-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d2447-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2447-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d2447-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2447-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2447-113">Attributes</span></span>  
  
|<span data-ttu-id="d2447-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2447-114">Attribute</span></span>|<span data-ttu-id="d2447-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d2447-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="d2447-116">Řetězec, který definuje název fondu připojení používaný pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="d2447-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="d2447-117">V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="d2447-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="d2447-118">Výchozí hodnota je řetězec "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="d2447-118">The default is a "default" string.</span></span> <span data-ttu-id="d2447-119">Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="d2447-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="d2447-120">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="d2447-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="d2447-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="d2447-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="d2447-122">A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí aktivní připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="d2447-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="d2447-123">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="d2447-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="d2447-124">Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="d2447-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="d2447-125">Mezipaměť připojení přenosu protokolu TCP používané vytvoří nové připojení pro každý koncový bod, až po limit mezipaměti, který je nastaven podle potřeby `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="d2447-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="d2447-126">Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou.</span><span class="sxs-lookup"><span data-stu-id="d2447-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="d2447-127">Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="d2447-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="d2447-128">`idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d2447-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="d2447-129">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="d2447-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="d2447-130">Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="d2447-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="d2447-131">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="d2447-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="d2447-132">V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d2447-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2447-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d2447-133">Child Elements</span></span>  
 <span data-ttu-id="d2447-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="d2447-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2447-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d2447-135">Parent Elements</span></span>  
  
|<span data-ttu-id="d2447-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="d2447-136">Element</span></span>|<span data-ttu-id="d2447-137">Popis</span><span class="sxs-lookup"><span data-stu-id="d2447-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2447-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="d2447-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="d2447-139">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="d2447-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2447-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2447-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d2447-141">Přenosy</span><span class="sxs-lookup"><span data-stu-id="d2447-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="d2447-142">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="d2447-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d2447-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="d2447-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d2447-144">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d2447-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d2447-145">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d2447-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d2447-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d2447-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
