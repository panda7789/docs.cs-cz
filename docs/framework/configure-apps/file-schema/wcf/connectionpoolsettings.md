---
title: '&lt;connectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 2d79b3e28d1a80011cba7c515d979ae0037785a5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149524"
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="033cd-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="033cd-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="033cd-103">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="033cd-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="033cd-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="033cd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="033cd-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="033cd-105">\<bindings></span></span>  
<span data-ttu-id="033cd-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="033cd-106">\<customBinding></span></span>  
<span data-ttu-id="033cd-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="033cd-107">\<binding></span></span>  
<span data-ttu-id="033cd-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="033cd-108">\<namePipeTransport></span></span>  
<span data-ttu-id="033cd-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="033cd-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="033cd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="033cd-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="033cd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="033cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="033cd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="033cd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="033cd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="033cd-113">Attributes</span></span>  
  
|<span data-ttu-id="033cd-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="033cd-114">Attribute</span></span>|<span data-ttu-id="033cd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="033cd-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="033cd-116">Řetězec, který definuje název fondu připojení používaný pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="033cd-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="033cd-117">V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="033cd-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="033cd-118">Výchozí hodnota je řetězec "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="033cd-118">The default is a "default" string.</span></span> <span data-ttu-id="033cd-119">Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="033cd-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="033cd-120">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="033cd-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="033cd-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="033cd-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="033cd-122">Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou.</span><span class="sxs-lookup"><span data-stu-id="033cd-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="033cd-123">Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="033cd-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="033cd-124">`idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="033cd-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="033cd-125">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="033cd-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="033cd-126">Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="033cd-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="033cd-127">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="033cd-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="033cd-128">V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="033cd-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="033cd-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="033cd-129">Child Elements</span></span>  
 <span data-ttu-id="033cd-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="033cd-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="033cd-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="033cd-131">Parent Elements</span></span>  
  
|<span data-ttu-id="033cd-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="033cd-132">Element</span></span>|<span data-ttu-id="033cd-133">Popis</span><span class="sxs-lookup"><span data-stu-id="033cd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="033cd-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="033cd-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="033cd-135">Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="033cd-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="033cd-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="033cd-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="033cd-137">Přenosy</span><span class="sxs-lookup"><span data-stu-id="033cd-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="033cd-138">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="033cd-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="033cd-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="033cd-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="033cd-140">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="033cd-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="033cd-141">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="033cd-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="033cd-142">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="033cd-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
