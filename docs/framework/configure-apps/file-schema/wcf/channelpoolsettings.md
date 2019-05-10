---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 2ad1cba170a7ade06de4678651a8dfcb608d5c46
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607204"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="097a5-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="097a5-101">\<channelPoolSettings></span></span>
<span data-ttu-id="097a5-102">Určuje nastavení fondu kanálu pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="097a5-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="097a5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="097a5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="097a5-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="097a5-104">\<bindings></span></span>  
<span data-ttu-id="097a5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="097a5-105">\<customBinding></span></span>  
<span data-ttu-id="097a5-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="097a5-106">\<binding></span></span>  
<span data-ttu-id="097a5-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="097a5-107">\<oneWay></span></span>  
<span data-ttu-id="097a5-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="097a5-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097a5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="097a5-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="097a5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="097a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="097a5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="097a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="097a5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="097a5-112">Attributes</span></span>  
  
|<span data-ttu-id="097a5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="097a5-113">Attribute</span></span>|<span data-ttu-id="097a5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="097a5-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="097a5-115">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu kanály ve fondu může být neaktivní, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="097a5-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="097a5-116">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="097a5-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="097a5-117">A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí je kanál, když je vrácen do fondu, uzavřen.</span><span class="sxs-lookup"><span data-stu-id="097a5-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="097a5-118">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="097a5-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="097a5-119">Kladné celé číslo, určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="097a5-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="097a5-120">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="097a5-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="097a5-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="097a5-121">Child Elements</span></span>  
 <span data-ttu-id="097a5-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="097a5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="097a5-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="097a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="097a5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="097a5-124">Element</span></span>|<span data-ttu-id="097a5-125">Popis</span><span class="sxs-lookup"><span data-stu-id="097a5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="097a5-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="097a5-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="097a5-127">Umožňuje směrování paketů pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="097a5-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="097a5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="097a5-128">Remarks</span></span>  
 <span data-ttu-id="097a5-129">Kvóty slouží jako vhodný mechanismus zásady zabránit spotřebu nadměrné prostředků.</span><span class="sxs-lookup"><span data-stu-id="097a5-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="097a5-130">Brání tomu, aby útoků s cílem odepření služby (DOS), které jsou škodlivých aktivit nebo neúmyslným.</span><span class="sxs-lookup"><span data-stu-id="097a5-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="097a5-131">Při nastavování kvóty kanál ve vlastním kanálu pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="097a5-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="097a5-132">`ChannelPoolSettings` Určuje tři kvót:</span><span class="sxs-lookup"><span data-stu-id="097a5-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="097a5-133">`idleTimeout` Kvóty slouží ke zmírnění útoků s cílem odepření služby (DOS) na serveru, které využívají obsadit prostředků delší dobu.</span><span class="sxs-lookup"><span data-stu-id="097a5-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="097a5-134">Na straně klienta můžete nastavení správnou hodnotu zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="097a5-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="097a5-135">Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="097a5-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="097a5-136">Je vhodný pro vývojové prostředí a scénářů malé instalace.</span><span class="sxs-lookup"><span data-stu-id="097a5-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="097a5-137">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="097a5-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="097a5-138">`leaseTimeout` Kvóty slouží k integraci s nástroji pro vyrovnávání zatížení a zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="097a5-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="097a5-139">Výchozí hodnota je založena na konzervativní přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="097a5-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="097a5-140">Je vhodný pro vývojové prostředí a scénářů malé instalace.</span><span class="sxs-lookup"><span data-stu-id="097a5-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="097a5-141">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="097a5-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="097a5-142">`maxOutboundChannelsPerEndpoint` Kvóta nastavuje omezení mezipaměti na serveru a klienta a slouží ke zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="097a5-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="097a5-143">Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků, která je vhodná pro malé instalace scénáře a vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="097a5-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="097a5-144">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="097a5-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097a5-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="097a5-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="097a5-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="097a5-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="097a5-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="097a5-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="097a5-148">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="097a5-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="097a5-149">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="097a5-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="097a5-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="097a5-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
