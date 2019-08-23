---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919561"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3d1ba-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3d1ba-101">\<channelPoolSettings></span></span>
<span data-ttu-id="3d1ba-102">Určuje nastavení fondu kanálu pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="3d1ba-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3d1ba-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3d1ba-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3d1ba-104">\<bindings></span></span>  
<span data-ttu-id="3d1ba-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3d1ba-105">\<customBinding></span></span>  
<span data-ttu-id="3d1ba-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3d1ba-106">\<binding></span></span>  
<span data-ttu-id="3d1ba-107">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="3d1ba-107">\<oneWay></span></span>  
<span data-ttu-id="3d1ba-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3d1ba-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d1ba-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d1ba-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d1ba-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d1ba-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d1ba-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d1ba-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d1ba-112">Attributes</span></span>  
  
|<span data-ttu-id="3d1ba-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3d1ba-113">Attribute</span></span>|<span data-ttu-id="3d1ba-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3d1ba-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="3d1ba-115">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou můžou být kanály ve fondu nečinné, než se odpojí.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="3d1ba-116">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3d1ba-117">A <xref:System.TimeSpan> určuje časový interval, po jehož uplynutí je kanál, který byl vrácen do fondu, uzavřen.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="3d1ba-118">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="3d1ba-119">Celé kladné číslo určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="3d1ba-120">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d1ba-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d1ba-121">Child Elements</span></span>  
 <span data-ttu-id="3d1ba-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d1ba-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d1ba-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d1ba-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3d1ba-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3d1ba-124">Element</span></span>|<span data-ttu-id="3d1ba-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3d1ba-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d1ba-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="3d1ba-126">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="3d1ba-127">Povolí směrování paketů pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d1ba-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d1ba-128">Remarks</span></span>  
 <span data-ttu-id="3d1ba-129">Kvóty se používají jako mechanismus zásad, aby se zabránilo vyčerpání nadměrných prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="3d1ba-130">Zabraňují útokům DOS (Denial of Service), které jsou buď škodlivé, nebo neúmyslné.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="3d1ba-131">Tento prvek použijte při nastavování kvót kanálů na vlastním kanálu.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="3d1ba-132">`ChannelPoolSettings`Určuje tři kvóty:</span><span class="sxs-lookup"><span data-stu-id="3d1ba-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="3d1ba-133">`idleTimeout` Kvóta se používá ke zmírnění útoků DOS (Denial of Service) na serveru, které se spoléhají na provázání prostředků po delší dobu.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="3d1ba-134">Nastavení správné hodnoty na klientovi může zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="3d1ba-135">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="3d1ba-136">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3d1ba-137">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="3d1ba-138">`leaseTimeout` Kvóta se používá pro integraci s nástroji pro vyrovnávání zatížení a za účelem zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="3d1ba-139">Výchozí hodnota je založena na konzervativním přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="3d1ba-140">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3d1ba-141">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="3d1ba-142">Omezení mezipaměti sad kvót nastavuje na serveru i v klientovi a slouží ke zvýšení spolehlivosti. `maxOutboundChannelsPerEndpoint`</span><span class="sxs-lookup"><span data-stu-id="3d1ba-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="3d1ba-143">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků, které jsou vhodné pro vývojové prostředí a malé instalace.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3d1ba-144">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d1ba-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1ba-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d1ba-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3d1ba-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="3d1ba-146">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="3d1ba-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="3d1ba-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3d1ba-148">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3d1ba-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3d1ba-149">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3d1ba-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3d1ba-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3d1ba-150">\<customBinding></span></span>](custombinding.md)
