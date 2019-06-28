---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 3c17184445aa5cec8a5121252934574add2b3db0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423161"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="703f1-102">\<connectionPoolSettings> of \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="703f1-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="703f1-103">Určuje další nastavení fondu připojení přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="703f1-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="703f1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="703f1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="703f1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="703f1-105">\<bindings></span></span>  
<span data-ttu-id="703f1-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="703f1-106">\<customBinding></span></span>  
<span data-ttu-id="703f1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="703f1-107">\<binding></span></span>  
<span data-ttu-id="703f1-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="703f1-108">\<tcpTransport></span></span>  
<span data-ttu-id="703f1-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="703f1-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703f1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="703f1-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="703f1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="703f1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="703f1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="703f1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="703f1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="703f1-113">Attributes</span></span>  
  
|<span data-ttu-id="703f1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="703f1-114">Attribute</span></span>|<span data-ttu-id="703f1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="703f1-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="703f1-116">Řetězec, který definuje název fondu připojení používaný pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="703f1-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="703f1-117">V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="703f1-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="703f1-118">Výchozí hodnota je řetězec "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="703f1-118">The default is a "default" string.</span></span> <span data-ttu-id="703f1-119">Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="703f1-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="703f1-120">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="703f1-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="703f1-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="703f1-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="703f1-122">A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí aktivní připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="703f1-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="703f1-123">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="703f1-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="703f1-124">Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="703f1-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="703f1-125">Mezipaměť připojení přenosu protokolu TCP používané vytvoří nové připojení pro každý koncový bod, až po limit mezipaměti, který je nastaven podle potřeby `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="703f1-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="703f1-126">Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou.</span><span class="sxs-lookup"><span data-stu-id="703f1-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="703f1-127">Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="703f1-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="703f1-128">`idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="703f1-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="703f1-129">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="703f1-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="703f1-130">Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="703f1-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="703f1-131">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="703f1-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="703f1-132">V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="703f1-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="703f1-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="703f1-133">Child Elements</span></span>  
 <span data-ttu-id="703f1-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="703f1-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="703f1-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="703f1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="703f1-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="703f1-136">Element</span></span>|<span data-ttu-id="703f1-137">Popis</span><span class="sxs-lookup"><span data-stu-id="703f1-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="703f1-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="703f1-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="703f1-139">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="703f1-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="703f1-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="703f1-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="703f1-141">Přenosy</span><span class="sxs-lookup"><span data-stu-id="703f1-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="703f1-142">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="703f1-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="703f1-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="703f1-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="703f1-144">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="703f1-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="703f1-145">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="703f1-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="703f1-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="703f1-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
