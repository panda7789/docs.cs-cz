---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 787b50296b7ed4f6fdceef244a99dffffae63c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919404"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="58baa-102">\<connectionPoolSettings > \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="58baa-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="58baa-103">Určuje další nastavení fondu připojení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="58baa-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="58baa-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58baa-104">\<system.serviceModel></span></span>  
<span data-ttu-id="58baa-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="58baa-105">\<bindings></span></span>  
<span data-ttu-id="58baa-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="58baa-106">\<customBinding></span></span>  
<span data-ttu-id="58baa-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="58baa-107">\<binding></span></span>  
<span data-ttu-id="58baa-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="58baa-108">\<tcpTransport></span></span>  
<span data-ttu-id="58baa-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="58baa-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58baa-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58baa-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58baa-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58baa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="58baa-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58baa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58baa-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="58baa-113">Attributes</span></span>  
  
|<span data-ttu-id="58baa-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="58baa-114">Attribute</span></span>|<span data-ttu-id="58baa-115">Popis</span><span class="sxs-lookup"><span data-stu-id="58baa-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="58baa-116">Řetězec definující název fondu připojení, který se používá pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="58baa-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="58baa-117">V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="58baa-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="58baa-118">Výchozí hodnota je "výchozí" řetězec.</span><span class="sxs-lookup"><span data-stu-id="58baa-118">The default is a "default" string.</span></span> <span data-ttu-id="58baa-119">Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.</span><span class="sxs-lookup"><span data-stu-id="58baa-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="58baa-120">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno.</span><span class="sxs-lookup"><span data-stu-id="58baa-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="58baa-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="58baa-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="58baa-122">A <xref:System.TimeSpan> určuje dobu, po jejímž uplynutí je aktivní připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="58baa-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="58baa-123">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="58baa-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="58baa-124">Po návratu do mezipaměti připojení a při aktivním přenosu se připojení zavře.</span><span class="sxs-lookup"><span data-stu-id="58baa-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="58baa-125">Mezipaměť připojení, kterou přenos TCP používá, vytvoří nová připojení podle požadavků pro každý koncový bod až do limitu mezipaměti, který nastaví.`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="58baa-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="58baa-126">Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou.</span><span class="sxs-lookup"><span data-stu-id="58baa-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="58baa-127">Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="58baa-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="58baa-128">`idleTimeout` Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="58baa-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="58baa-129">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="58baa-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="58baa-130">Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="58baa-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="58baa-131">Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta.</span><span class="sxs-lookup"><span data-stu-id="58baa-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="58baa-132">V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="58baa-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58baa-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58baa-133">Child Elements</span></span>  
 <span data-ttu-id="58baa-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="58baa-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58baa-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58baa-135">Parent Elements</span></span>  
  
|<span data-ttu-id="58baa-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="58baa-136">Element</span></span>|<span data-ttu-id="58baa-137">Popis</span><span class="sxs-lookup"><span data-stu-id="58baa-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58baa-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="58baa-138">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="58baa-139">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="58baa-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58baa-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58baa-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="58baa-141">Přenosy</span><span class="sxs-lookup"><span data-stu-id="58baa-141">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="58baa-142">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="58baa-142">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="58baa-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="58baa-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="58baa-144">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="58baa-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="58baa-145">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="58baa-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="58baa-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="58baa-146">\<customBinding></span></span>](custombinding.md)
