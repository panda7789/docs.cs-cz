---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398162"
---
# \<channelPoolSettings>
<span data-ttu-id="a2473-101">Určuje nastavení fondu kanálu pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a2473-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a2473-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2473-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2473-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a2473-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a2473-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a2473-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2473-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2473-105">Attributes</span></span>  
  
|<span data-ttu-id="a2473-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="a2473-106">Attribute</span></span>|<span data-ttu-id="a2473-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a2473-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="a2473-108">Kladná hodnota <xref:System.TimeSpan> , která určuje maximální dobu, po kterou můžou být kanály ve fondu nečinné, než se odpojí.</span><span class="sxs-lookup"><span data-stu-id="a2473-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="a2473-109">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="a2473-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="a2473-110">A <xref:System.TimeSpan> Určuje časový interval, po jehož uplynutí je kanál, který byl vrácen do fondu, uzavřen.</span><span class="sxs-lookup"><span data-stu-id="a2473-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="a2473-111">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a2473-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="a2473-112">Celé kladné číslo určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a2473-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="a2473-113">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="a2473-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2473-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a2473-114">Child Elements</span></span>  
 <span data-ttu-id="a2473-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="a2473-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2473-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a2473-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a2473-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a2473-117">Element</span></span>|<span data-ttu-id="a2473-118">Description</span><span class="sxs-lookup"><span data-stu-id="a2473-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="a2473-119">Povolí směrování paketů pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a2473-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2473-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2473-120">Remarks</span></span>  
 <span data-ttu-id="a2473-121">Kvóty se používají jako mechanismus zásad, aby se zabránilo vyčerpání nadměrných prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="a2473-122">Zabraňují útokům DOS (Denial of Service), které jsou buď škodlivé, nebo neúmyslné.</span><span class="sxs-lookup"><span data-stu-id="a2473-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="a2473-123">Tento prvek použijte při nastavování kvót kanálů na vlastním kanálu.</span><span class="sxs-lookup"><span data-stu-id="a2473-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="a2473-124">`ChannelPoolSettings`Určuje tři kvóty:</span><span class="sxs-lookup"><span data-stu-id="a2473-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="a2473-125">`idleTimeout`Kvóta se používá ke zmírnění útoků DOS (Denial of Service) na serveru, které se spoléhají na provázání prostředků po delší dobu.</span><span class="sxs-lookup"><span data-stu-id="a2473-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="a2473-126">Nastavení správné hodnoty na klientovi může zvýšit spolehlivost připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="a2473-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="a2473-127">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="a2473-128">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="a2473-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a2473-129">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="a2473-130">`leaseTimeout`Kvóta se používá pro integraci s nástroji pro vyrovnávání zatížení a za účelem zlepšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="a2473-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="a2473-131">Výchozí hodnota je založena na konzervativním přidělení prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="a2473-132">Je vhodný pro vývojové prostředí a malé scénáře instalace.</span><span class="sxs-lookup"><span data-stu-id="a2473-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a2473-133">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="a2473-134">`maxOutboundChannelsPerEndpoint`Omezení mezipaměti sad kvót nastavuje na serveru i v klientovi a slouží ke zvýšení spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="a2473-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="a2473-135">Výchozí hodnota vychází z konzervativního mírného přidělení prostředků, které jsou vhodné pro vývojové prostředí a malé instalace.</span><span class="sxs-lookup"><span data-stu-id="a2473-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a2473-136">Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.</span><span class="sxs-lookup"><span data-stu-id="a2473-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2473-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2473-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="a2473-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="a2473-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a2473-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a2473-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a2473-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a2473-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
