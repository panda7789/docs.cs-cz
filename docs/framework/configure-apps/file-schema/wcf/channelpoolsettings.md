---
title: '&lt;channelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 666602bde75cd21b5b3d16bd4d5e6cf63c12d593
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554956"
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="fc140-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="fc140-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="fc140-103">Určuje nastavení fondu kanálu pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="fc140-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="fc140-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fc140-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fc140-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="fc140-105">\<bindings></span></span>  
<span data-ttu-id="fc140-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fc140-106">\<customBinding></span></span>  
<span data-ttu-id="fc140-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="fc140-107">\<binding></span></span>  
<span data-ttu-id="fc140-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="fc140-108">\<oneWay></span></span>  
<span data-ttu-id="fc140-109">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="fc140-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc140-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc140-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc140-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc140-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fc140-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc140-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc140-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc140-113">Attributes</span></span>  
  
|<span data-ttu-id="fc140-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc140-114">Attribute</span></span>|<span data-ttu-id="fc140-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fc140-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="fc140-116">Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu kanály ve fondu může být neaktivní, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="fc140-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="fc140-117">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="fc140-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="fc140-118">A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí je kanál, když je vrácen do fondu, uzavřen.</span><span class="sxs-lookup"><span data-stu-id="fc140-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="fc140-119">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fc140-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="fc140-120">Kladné celé číslo, určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fc140-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="fc140-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="fc140-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc140-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc140-122">Child Elements</span></span>  
 <span data-ttu-id="fc140-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc140-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc140-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc140-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fc140-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc140-125">Element</span></span>|<span data-ttu-id="fc140-126">Popis</span><span class="sxs-lookup"><span data-stu-id="fc140-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc140-127">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="fc140-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="fc140-128">Umožňuje směrování paketů pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="fc140-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc140-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc140-129">Remarks</span></span>  
 <span data-ttu-id="fc140-130">Kvóty slouží jako vhodný mechanismus zásady zabránit spotřebu nadměrné prostředků.</span><span class="sxs-lookup"><span data-stu-id="fc140-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="fc140-131">Brání tomu, aby útoků s cílem odepření služby (DOS), které jsou škodlivých aktivit nebo neúmyslným.</span><span class="sxs-lookup"><span data-stu-id="fc140-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="fc140-132">Při nastavování kvóty kanál ve vlastním kanálu pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="fc140-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="fc140-133">`ChannelPoolSettings` Určuje tři kvót:</span><span class="sxs-lookup"><span data-stu-id="fc140-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="fc140-134">`idleTimeout` Kvóty slouží ke zmírnění útoků s cílem odepření služby (DOS) na serveru, které využívají obsadit prostředků delší dobu.</span><span class="sxs-lookup"><span data-stu-id="fc140-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="fc140-135">Na straně klienta můžete nastavení správnou hodnotu zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="fc140-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="fc140-136">Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="fc140-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="fc140-137">Je vhodný pro vývojové prostředí a scénářů malé instalace.</span><span class="sxs-lookup"><span data-stu-id="fc140-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fc140-138">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="fc140-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fc140-139">`leaseTimeout` Kvóty slouží k integraci s nástroji pro vyrovnávání zatížení a zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="fc140-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="fc140-140">Výchozí hodnota je založena na konzervativní přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="fc140-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="fc140-141">Je vhodný pro vývojové prostředí a scénářů malé instalace.</span><span class="sxs-lookup"><span data-stu-id="fc140-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fc140-142">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="fc140-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fc140-143">`maxOutboundChannelsPerEndpoint` Kvóta nastavuje omezení mezipaměti na serveru a klienta a slouží ke zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="fc140-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="fc140-144">Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků, která je vhodná pro malé instalace scénáře a vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="fc140-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fc140-145">Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="fc140-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc140-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc140-146">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fc140-147">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="fc140-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="fc140-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="fc140-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fc140-149">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="fc140-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fc140-150">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="fc140-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fc140-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fc140-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
