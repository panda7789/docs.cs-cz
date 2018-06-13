---
title: '&lt;ConnectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 87fcbf08d897cf8d9e1924a8a5ed2b5b20945638
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748149"
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="2b16c-102">&lt;ConnectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="2b16c-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="2b16c-103">Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.</span><span class="sxs-lookup"><span data-stu-id="2b16c-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="2b16c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2b16c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2b16c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2b16c-105">\<bindings></span></span>  
<span data-ttu-id="2b16c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b16c-106">\<customBinding></span></span>  
<span data-ttu-id="2b16c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="2b16c-107">\<binding></span></span>  
<span data-ttu-id="2b16c-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="2b16c-108">\<namePipeTransport></span></span>  
<span data-ttu-id="2b16c-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="2b16c-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b16c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b16c-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b16c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b16c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b16c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b16c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b16c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b16c-113">Attributes</span></span>  
  
|<span data-ttu-id="2b16c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b16c-114">Attribute</span></span>|<span data-ttu-id="2b16c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2b16c-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="2b16c-116">Řetězec, který definuje název fondu připojení používané pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="2b16c-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="2b16c-117">V přenášené datovými proudy režimu nejsou sdílené připojení – zakázáno sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="2b16c-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="2b16c-118">Výchozí hodnota je řetězec "default".</span><span class="sxs-lookup"><span data-stu-id="2b16c-118">The default is a "default" string.</span></span> <span data-ttu-id="2b16c-119">Tato hodnota izolovat připojení pro konkrétního klienta do samostatných skupin můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="2b16c-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="2b16c-120">U kladné <xref:System.TimeSpan> , určuje maximální dobu může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="2b16c-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="2b16c-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="2b16c-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="2b16c-122">Kladné celé číslo, které určuje maximální počet připojení, aby vzdálený koncový bod iniciovat službu.</span><span class="sxs-lookup"><span data-stu-id="2b16c-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="2b16c-123">Připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.</span><span class="sxs-lookup"><span data-stu-id="2b16c-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="2b16c-124">`idleTimeout` Omezí doba trvání, ve kterém připojení zůstat ve frontě, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2b16c-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="2b16c-125">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="2b16c-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="2b16c-126">Tento atribut omezuje počet souběžných aktivních připojení z klienta pro koncový bod konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="2b16c-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="2b16c-127">Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se mohou objevit reagovat na klienta služby.</span><span class="sxs-lookup"><span data-stu-id="2b16c-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="2b16c-128">V takovém případě je třeba upravit tuto hodnotu delší než maximální počet očekávané simultánních klientských připojení na konkrétní.</span><span class="sxs-lookup"><span data-stu-id="2b16c-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b16c-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b16c-129">Child Elements</span></span>  
 <span data-ttu-id="2b16c-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b16c-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b16c-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b16c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2b16c-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b16c-132">Element</span></span>|<span data-ttu-id="2b16c-133">Popis</span><span class="sxs-lookup"><span data-stu-id="2b16c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b16c-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="2b16c-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="2b16c-135">Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="2b16c-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b16c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b16c-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2b16c-137">Přenosy</span><span class="sxs-lookup"><span data-stu-id="2b16c-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="2b16c-138">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="2b16c-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="2b16c-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="2b16c-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2b16c-140">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2b16c-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2b16c-141">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2b16c-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2b16c-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b16c-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
