---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398162"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="f3c8d-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="f3c8d-101">\<channelPoolSettings></span></span>
<span data-ttu-id="f3c8d-102">Určuje nastavení fondu kanálu pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
<span data-ttu-id="f3c8d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3c8d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3c8d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f3c8d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f3c8d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f3c8d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f3c8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3c8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f3c8d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="f3c8d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f3c8d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> oneWay**](oneway.md)</span><span class="sxs-lookup"><span data-stu-id="f3c8d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)</span></span>\
<span data-ttu-id="f3c8d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<channelPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="f3c8d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c8d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3c8d-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3c8d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3c8d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f3c8d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3c8d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3c8d-113">Attributes</span></span>  
  
|<span data-ttu-id="f3c8d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3c8d-114">Attribute</span></span>|<span data-ttu-id="f3c8d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f3c8d-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="f3c8d-116">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou můžou být kanály ve fondu nečinné, než se odpojí.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="f3c8d-117">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="f3c8d-118">A <xref:System.TimeSpan> určuje časový interval, po jehož uplynutí je kanál, který byl vrácen do fondu, uzavřen.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="f3c8d-119">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="f3c8d-120">Celé kladné číslo určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="f3c8d-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3c8d-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3c8d-122">Child Elements</span></span>  
 <span data-ttu-id="f3c8d-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3c8d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3c8d-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3c8d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f3c8d-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3c8d-125">Element</span></span>|<span data-ttu-id="f3c8d-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f3c8d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3c8d-127">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="f3c8d-127">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="f3c8d-128">Povolí směrování paketů pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3c8d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3c8d-129">Remarks</span></span>  
 <span data-ttu-id="f3c8d-130">Kvóty se používají jako mechanismus zásad, aby se zabránilo vyčerpání nadměrných prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="f3c8d-131">Zabraňují útokům DOS (Denial of Service), které jsou buď škodlivé, nebo neúmyslné.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="f3c8d-132">Tento prvek použijte při nastavování kvót kanálů na vlastním kanálu.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="f3c8d-133">`ChannelPoolSettings`Určuje tři kvóty:</span><span class="sxs-lookup"><span data-stu-id="f3c8d-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="f3c8d-134">`idleTimeout` Kvóta se používá ke zmírnění útoků DOS (Denial of Service) na serveru, které se spoléhají na provázání prostředků po delší dobu.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="f3c8d-135">Nastavení správné hodnoty na klientovi může zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="f3c8d-136">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="f3c8d-137">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f3c8d-138">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f3c8d-139">`leaseTimeout` Kvóta se používá pro integraci s nástroji pro vyrovnávání zatížení a za účelem zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="f3c8d-140">Výchozí hodnota je založena na konzervativním přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="f3c8d-141">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f3c8d-142">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="f3c8d-143">Omezení mezipaměti sad kvót nastavuje na serveru i v klientovi a slouží ke zvýšení spolehlivosti. `maxOutboundChannelsPerEndpoint`</span><span class="sxs-lookup"><span data-stu-id="f3c8d-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="f3c8d-144">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků, které jsou vhodné pro vývojové prostředí a malé instalace.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="f3c8d-145">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3c8d-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c8d-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3c8d-146">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f3c8d-147">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="f3c8d-147">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="f3c8d-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="f3c8d-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3c8d-149">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="f3c8d-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f3c8d-150">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f3c8d-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f3c8d-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f3c8d-151">\<customBinding></span></span>](custombinding.md)
