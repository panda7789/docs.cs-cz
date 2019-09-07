---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f12969d8b752e54916b45c3d0e64f114971b8944
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397651"
---
# <a name="oneway"></a><span data-ttu-id="2379e-101">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="2379e-101">\<oneWay></span></span>
<span data-ttu-id="2379e-102">Povoluje směrování paketů a používání jednosměrných metod pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2379e-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="2379e-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2379e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2379e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2379e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2379e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2379e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2379e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2379e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2379e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="2379e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2379e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oneWay**</span><span class="sxs-lookup"><span data-stu-id="2379e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2379e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2379e-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2379e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2379e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2379e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2379e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2379e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2379e-112">Attributes</span></span>  
  
|<span data-ttu-id="2379e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2379e-113">Attribute</span></span>|<span data-ttu-id="2379e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2379e-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="2379e-115">Logická hodnota, která určuje, zda je povoleno směrování paketů.</span><span class="sxs-lookup"><span data-stu-id="2379e-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="2379e-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2379e-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="2379e-117">Celé číslo, které určuje maximální počet kanálů, které mohou být přijaty.</span><span class="sxs-lookup"><span data-stu-id="2379e-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2379e-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2379e-118">Child Elements</span></span>  
  
|<span data-ttu-id="2379e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2379e-119">Element</span></span>|<span data-ttu-id="2379e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2379e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2379e-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="2379e-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="2379e-122"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> Objekt, který obsahuje vlastnosti fondu kanálů pro aktuální kanál.</span><span class="sxs-lookup"><span data-stu-id="2379e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2379e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2379e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2379e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2379e-124">Element</span></span>|<span data-ttu-id="2379e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2379e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2379e-126">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2379e-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="2379e-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2379e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2379e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2379e-128">Remarks</span></span>  
 <span data-ttu-id="2379e-129">Chcete-li povolit směrování paketů, je požadována jednosměrná konverzní vrstva, která tento prvek poskytuje.</span><span class="sxs-lookup"><span data-stu-id="2379e-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="2379e-130">Uživatel může vytvořit vlastní vazbu, která tuto vazbu navrství prostřednictvím přenosu, který je v relaci nebo požadavek-odpověď, aby bylo možné směrovat paket.</span><span class="sxs-lookup"><span data-stu-id="2379e-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="2379e-131">Tento prvek je také užitečný, pokud chcete zveřejnit jednosměrné metody v nativním režimu.</span><span class="sxs-lookup"><span data-stu-id="2379e-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="2379e-132">Pro tuto vrstvu lze použít více transformací, jako je kompozitní duplexní a spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="2379e-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2379e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2379e-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2379e-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="2379e-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2379e-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2379e-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2379e-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2379e-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2379e-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2379e-137">\<customBinding></span></span>](custombinding.md)
