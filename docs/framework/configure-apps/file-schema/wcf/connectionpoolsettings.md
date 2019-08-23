---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925965"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="61fcc-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="61fcc-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="61fcc-102">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="61fcc-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="61fcc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="61fcc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="61fcc-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="61fcc-104">\<bindings></span></span>  
<span data-ttu-id="61fcc-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="61fcc-105">\<customBinding></span></span>  
<span data-ttu-id="61fcc-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="61fcc-106">\<binding></span></span>  
<span data-ttu-id="61fcc-107">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="61fcc-107">\<namePipeTransport></span></span>  
<span data-ttu-id="61fcc-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="61fcc-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fcc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61fcc-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61fcc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61fcc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="61fcc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61fcc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61fcc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="61fcc-112">Attributes</span></span>  
  
|<span data-ttu-id="61fcc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="61fcc-113">Attribute</span></span>|<span data-ttu-id="61fcc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="61fcc-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="61fcc-115">Řetězec definující název fondu připojení, který se používá pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="61fcc-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="61fcc-116">V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="61fcc-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="61fcc-117">Výchozí hodnota je "výchozí" řetězec.</span><span class="sxs-lookup"><span data-stu-id="61fcc-117">The default is a "default" string.</span></span> <span data-ttu-id="61fcc-118">Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.</span><span class="sxs-lookup"><span data-stu-id="61fcc-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="61fcc-119">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno.</span><span class="sxs-lookup"><span data-stu-id="61fcc-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="61fcc-120">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="61fcc-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="61fcc-121">Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou.</span><span class="sxs-lookup"><span data-stu-id="61fcc-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="61fcc-122">Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="61fcc-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="61fcc-123">`idleTimeout` Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="61fcc-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="61fcc-124">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="61fcc-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="61fcc-125">Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="61fcc-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="61fcc-126">Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta.</span><span class="sxs-lookup"><span data-stu-id="61fcc-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="61fcc-127">V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="61fcc-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61fcc-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61fcc-128">Child Elements</span></span>  
 <span data-ttu-id="61fcc-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="61fcc-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61fcc-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61fcc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="61fcc-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="61fcc-131">Element</span></span>|<span data-ttu-id="61fcc-132">Popis</span><span class="sxs-lookup"><span data-stu-id="61fcc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61fcc-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="61fcc-133">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="61fcc-134">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="61fcc-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61fcc-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61fcc-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="61fcc-136">Přenosy</span><span class="sxs-lookup"><span data-stu-id="61fcc-136">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="61fcc-137">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="61fcc-137">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="61fcc-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="61fcc-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="61fcc-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="61fcc-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="61fcc-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="61fcc-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="61fcc-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="61fcc-141">\<customBinding></span></span>](custombinding.md)
