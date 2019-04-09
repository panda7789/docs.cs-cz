---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: b1ff302a46605cb78fe567a63f66723ed757f147
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169985"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="a6810-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="a6810-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="a6810-102">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="a6810-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="a6810-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a6810-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a6810-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a6810-104">\<bindings></span></span>  
<span data-ttu-id="a6810-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6810-105">\<customBinding></span></span>  
<span data-ttu-id="a6810-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a6810-106">\<binding></span></span>  
<span data-ttu-id="a6810-107">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="a6810-107">\<namePipeTransport></span></span>  
<span data-ttu-id="a6810-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="a6810-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6810-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6810-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6810-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6810-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6810-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6810-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6810-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6810-112">Attributes</span></span>  
  
|<span data-ttu-id="a6810-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6810-113">Attribute</span></span>|<span data-ttu-id="a6810-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a6810-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="a6810-115">Řetězec, který definuje název fondu připojení používaný pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="a6810-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="a6810-116">V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="a6810-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="a6810-117">Výchozí hodnota je řetězec "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="a6810-117">The default is a "default" string.</span></span> <span data-ttu-id="a6810-118">Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="a6810-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="a6810-119">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="a6810-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="a6810-120">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="a6810-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="a6810-121">Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou.</span><span class="sxs-lookup"><span data-stu-id="a6810-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="a6810-122">Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="a6810-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="a6810-123">`idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="a6810-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="a6810-124">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="a6810-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="a6810-125">Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="a6810-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="a6810-126">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="a6810-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="a6810-127">V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a6810-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6810-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6810-128">Child Elements</span></span>  
 <span data-ttu-id="a6810-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6810-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6810-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6810-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a6810-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6810-131">Element</span></span>|<span data-ttu-id="a6810-132">Popis</span><span class="sxs-lookup"><span data-stu-id="a6810-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6810-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="a6810-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="a6810-134">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="a6810-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6810-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6810-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a6810-136">Přenosy</span><span class="sxs-lookup"><span data-stu-id="a6810-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="a6810-137">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="a6810-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a6810-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="a6810-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a6810-139">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="a6810-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a6810-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a6810-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a6810-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6810-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
