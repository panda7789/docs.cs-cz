---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 2458cdd4d593637c2025047d5dd510f0f89b2a0f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423076"
---
# <a name="oneway"></a><span data-ttu-id="070e5-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="070e5-101">\<oneWay></span></span>
<span data-ttu-id="070e5-102">Umožňuje směrování paketů a použití jednosměrné metody pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="070e5-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="070e5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="070e5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="070e5-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="070e5-104">\<bindings></span></span>  
<span data-ttu-id="070e5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="070e5-105">\<customBinding></span></span>  
<span data-ttu-id="070e5-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="070e5-106">\<binding></span></span>  
<span data-ttu-id="070e5-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="070e5-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070e5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="070e5-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070e5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="070e5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="070e5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="070e5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070e5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="070e5-111">Attributes</span></span>  
  
|<span data-ttu-id="070e5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="070e5-112">Attribute</span></span>|<span data-ttu-id="070e5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="070e5-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="070e5-114">Logická hodnota určující, zda je povoleno směrování paketů.</span><span class="sxs-lookup"><span data-stu-id="070e5-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="070e5-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="070e5-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="070e5-116">Celé číslo určující maximální počet kanálů, které jdou přijmout.</span><span class="sxs-lookup"><span data-stu-id="070e5-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070e5-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="070e5-117">Child Elements</span></span>  
  
|<span data-ttu-id="070e5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="070e5-118">Element</span></span>|<span data-ttu-id="070e5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="070e5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070e5-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="070e5-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="070e5-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objekt, který obsahuje vlastnosti fondu kanálu pro current channel.</span><span class="sxs-lookup"><span data-stu-id="070e5-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="070e5-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="070e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="070e5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="070e5-123">Element</span></span>|<span data-ttu-id="070e5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="070e5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070e5-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="070e5-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="070e5-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="070e5-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="070e5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="070e5-127">Remarks</span></span>  
 <span data-ttu-id="070e5-128">Umožňuje směrování paketů jednosměrného převod vrstvy je nutné, který poskytuje tento element.</span><span class="sxs-lookup"><span data-stu-id="070e5-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="070e5-129">Uživatel může vytvořit vlastní vazby, které se za přenos s ohledem na relaci nebo požadavku a odpovědi k němu paketů směrovatelné vrstvy tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="070e5-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="070e5-130">Tento prvek je také užitečné, když chcete vystavit jednosměrné metody více nativní způsobem.</span><span class="sxs-lookup"><span data-stu-id="070e5-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="070e5-131">V této vrstvě, jako je například kompozitní duplexní a spolehlivé zasílání zpráv je možné použít dalších transformací.</span><span class="sxs-lookup"><span data-stu-id="070e5-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070e5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="070e5-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="070e5-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="070e5-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="070e5-134">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="070e5-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="070e5-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="070e5-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="070e5-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="070e5-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
