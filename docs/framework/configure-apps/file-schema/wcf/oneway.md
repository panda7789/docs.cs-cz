---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932942"
---
# <a name="oneway"></a><span data-ttu-id="7001e-101">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="7001e-101">\<oneWay></span></span>
<span data-ttu-id="7001e-102">Povoluje směrování paketů a používání jednosměrných metod pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="7001e-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="7001e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7001e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7001e-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="7001e-104">\<bindings></span></span>  
<span data-ttu-id="7001e-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7001e-105">\<customBinding></span></span>  
<span data-ttu-id="7001e-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="7001e-106">\<binding></span></span>  
<span data-ttu-id="7001e-107">\<> oneWay</span><span class="sxs-lookup"><span data-stu-id="7001e-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7001e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7001e-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7001e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7001e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7001e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7001e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7001e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7001e-111">Attributes</span></span>  
  
|<span data-ttu-id="7001e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="7001e-112">Attribute</span></span>|<span data-ttu-id="7001e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7001e-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="7001e-114">Logická hodnota, která určuje, zda je povoleno směrování paketů.</span><span class="sxs-lookup"><span data-stu-id="7001e-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="7001e-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="7001e-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="7001e-116">Celé číslo, které určuje maximální počet kanálů, které mohou být přijaty.</span><span class="sxs-lookup"><span data-stu-id="7001e-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7001e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7001e-117">Child Elements</span></span>  
  
|<span data-ttu-id="7001e-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7001e-118">Element</span></span>|<span data-ttu-id="7001e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7001e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7001e-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="7001e-120">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="7001e-121"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> Objekt, který obsahuje vlastnosti fondu kanálů pro aktuální kanál.</span><span class="sxs-lookup"><span data-stu-id="7001e-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7001e-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7001e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7001e-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7001e-123">Element</span></span>|<span data-ttu-id="7001e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7001e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7001e-125">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="7001e-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7001e-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7001e-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7001e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7001e-127">Remarks</span></span>  
 <span data-ttu-id="7001e-128">Chcete-li povolit směrování paketů, je požadována jednosměrná konverzní vrstva, která tento prvek poskytuje.</span><span class="sxs-lookup"><span data-stu-id="7001e-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="7001e-129">Uživatel může vytvořit vlastní vazbu, která tuto vazbu navrství prostřednictvím přenosu, který je v relaci nebo požadavek-odpověď, aby bylo možné směrovat paket.</span><span class="sxs-lookup"><span data-stu-id="7001e-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="7001e-130">Tento prvek je také užitečný, pokud chcete zveřejnit jednosměrné metody v nativním režimu.</span><span class="sxs-lookup"><span data-stu-id="7001e-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="7001e-131">Pro tuto vrstvu lze použít více transformací, jako je kompozitní duplexní a spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="7001e-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7001e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7001e-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7001e-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="7001e-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7001e-134">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7001e-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7001e-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7001e-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7001e-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7001e-136">\<customBinding></span></span>](custombinding.md)
