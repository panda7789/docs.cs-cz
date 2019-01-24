---
title: '&lt;OneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: c909bce5b54976a215a59ca8fd9f097f574acd80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600294"
---
# <a name="ltonewaygt"></a><span data-ttu-id="58b2c-102">&lt;OneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="58b2c-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="58b2c-103">Umožňuje směrování paketů a použití jednosměrné metody pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="58b2c-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="58b2c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58b2c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="58b2c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="58b2c-105">\<bindings></span></span>  
<span data-ttu-id="58b2c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="58b2c-106">\<customBinding></span></span>  
<span data-ttu-id="58b2c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="58b2c-107">\<binding></span></span>  
<span data-ttu-id="58b2c-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="58b2c-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b2c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58b2c-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58b2c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58b2c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58b2c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58b2c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58b2c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="58b2c-112">Attributes</span></span>  
  
|<span data-ttu-id="58b2c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="58b2c-113">Attribute</span></span>|<span data-ttu-id="58b2c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="58b2c-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="58b2c-115">Logická hodnota určující, zda je povoleno směrování paketů.</span><span class="sxs-lookup"><span data-stu-id="58b2c-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="58b2c-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="58b2c-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="58b2c-117">Celé číslo určující maximální počet kanálů, které jdou přijmout.</span><span class="sxs-lookup"><span data-stu-id="58b2c-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58b2c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58b2c-118">Child Elements</span></span>  
  
|<span data-ttu-id="58b2c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="58b2c-119">Element</span></span>|<span data-ttu-id="58b2c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="58b2c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58b2c-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="58b2c-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="58b2c-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objekt, který obsahuje vlastnosti fondu kanálu pro current channel.</span><span class="sxs-lookup"><span data-stu-id="58b2c-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58b2c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58b2c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58b2c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="58b2c-124">Element</span></span>|<span data-ttu-id="58b2c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="58b2c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58b2c-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="58b2c-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="58b2c-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="58b2c-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58b2c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58b2c-128">Remarks</span></span>  
 <span data-ttu-id="58b2c-129">Umožňuje směrování paketů jednosměrného převod vrstvy je nutné, který poskytuje tento element.</span><span class="sxs-lookup"><span data-stu-id="58b2c-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="58b2c-130">Uživatel může vytvořit vlastní vazby, které se za přenos s ohledem na relaci nebo požadavku a odpovědi k němu paketů směrovatelné vrstvy tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="58b2c-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="58b2c-131">Tento prvek je také užitečné, když chcete vystavit jednosměrné metody více nativní způsobem.</span><span class="sxs-lookup"><span data-stu-id="58b2c-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="58b2c-132">V této vrstvě, jako je například kompozitní duplexní a spolehlivé zasílání zpráv je možné použít dalších transformací.</span><span class="sxs-lookup"><span data-stu-id="58b2c-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b2c-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58b2c-133">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="58b2c-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="58b2c-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="58b2c-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="58b2c-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="58b2c-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="58b2c-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="58b2c-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="58b2c-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
