---
title: '&lt;channelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ad722fbc34617ef7f424d5f1c4418e1e1cb45344
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747233"
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="45b26-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="45b26-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="45b26-103">Určuje nastavení fondu kanálu pro vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="45b26-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="45b26-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="45b26-104">\<system.serviceModel></span></span>  
<span data-ttu-id="45b26-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="45b26-105">\<bindings></span></span>  
<span data-ttu-id="45b26-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="45b26-106">\<customBinding></span></span>  
<span data-ttu-id="45b26-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="45b26-107">\<binding></span></span>  
<span data-ttu-id="45b26-108">\<Typ oneWay ></span><span class="sxs-lookup"><span data-stu-id="45b26-108">\<oneWay></span></span>  
<span data-ttu-id="45b26-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="45b26-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b26-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45b26-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45b26-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="45b26-111">Attributes and Elements</span></span>  
 <span data-ttu-id="45b26-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="45b26-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45b26-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="45b26-113">Attributes</span></span>  
  
|<span data-ttu-id="45b26-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="45b26-114">Attribute</span></span>|<span data-ttu-id="45b26-115">Popis</span><span class="sxs-lookup"><span data-stu-id="45b26-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="45b26-116">U kladné <xref:System.TimeSpan> , určuje maximální dobu může být kanály ve fondu nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="45b26-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="45b26-117">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="45b26-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="45b26-118">A <xref:System.TimeSpan> který určuje, po jejímž uplynutí je uzavřený kanál, pokud vrátí do fondu, časový interval.</span><span class="sxs-lookup"><span data-stu-id="45b26-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="45b26-119">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="45b26-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="45b26-120">Kladné celé číslo, které určuje maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="45b26-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="45b26-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="45b26-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45b26-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="45b26-122">Child Elements</span></span>  
 <span data-ttu-id="45b26-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="45b26-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45b26-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="45b26-124">Parent Elements</span></span>  
  
|<span data-ttu-id="45b26-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="45b26-125">Element</span></span>|<span data-ttu-id="45b26-126">Popis</span><span class="sxs-lookup"><span data-stu-id="45b26-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45b26-127">\<Typ oneWay ></span><span class="sxs-lookup"><span data-stu-id="45b26-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="45b26-128">Umožňuje směrování paketů pro vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="45b26-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45b26-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45b26-129">Remarks</span></span>  
 <span data-ttu-id="45b26-130">Kvóty slouží jako mechanismus zásad aby spotřeba nadměrné zdrojů.</span><span class="sxs-lookup"><span data-stu-id="45b26-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="45b26-131">Brání tomu, aby útok na dostupnost služby (DOS) útoků, které jsou škodlivý nebo nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="45b26-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="45b26-132">Při nastavení kvót kanál ve vlastním kanálu pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="45b26-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="45b26-133">`ChannelPoolSettings` Určuje tři kvót:</span><span class="sxs-lookup"><span data-stu-id="45b26-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="45b26-134">`idleTimeout` Kvóty se používá k zmírnit útok na dostupnost služby (DOS) útoky na serveru, které jsou závislé na příkazů systémové prostředky pro delší dobu.</span><span class="sxs-lookup"><span data-stu-id="45b26-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="45b26-135">Na straně klienta správnou hodnotu nastavení zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="45b26-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="45b26-136">Výchozí hodnota je založena na můžete mírné přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="45b26-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="45b26-137">Je vhodná pro prostředí pro vývoj a scénáře malé instalace.</span><span class="sxs-lookup"><span data-stu-id="45b26-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="45b26-138">Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="45b26-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="45b26-139">`leaseTimeout` Kvóty slouží k integraci s nástroje pro vyrovnávání zatížení a pro zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="45b26-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="45b26-140">Výchozí hodnota je založena na konzervativní přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="45b26-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="45b26-141">Je vhodná pro prostředí pro vývoj a scénáře malé instalace.</span><span class="sxs-lookup"><span data-stu-id="45b26-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="45b26-142">Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="45b26-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="45b26-143">`maxOutboundChannelsPerEndpoint` Kvóty nastaví limity mezipaměti na serveru a klienta a slouží k vylepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="45b26-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="45b26-144">Výchozí hodnota je založená na můžete mírné přidělení prostředků, který je vhodný pro malé instalace scénáře a vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="45b26-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="45b26-145">Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.</span><span class="sxs-lookup"><span data-stu-id="45b26-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b26-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="45b26-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="45b26-147">\<Typ oneWay ></span><span class="sxs-lookup"><span data-stu-id="45b26-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="45b26-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="45b26-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="45b26-149">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="45b26-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="45b26-150">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="45b26-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="45b26-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="45b26-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
