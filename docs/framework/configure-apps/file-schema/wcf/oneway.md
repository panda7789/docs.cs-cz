---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738786"
---
# \<oneWay>
<span data-ttu-id="d5569-101">Povoluje směrování paketů a používání jednosměrných metod pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d5569-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="d5569-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5569-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5569-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d5569-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d5569-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d5569-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5569-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="d5569-105">Attributes</span></span>  
  
|<span data-ttu-id="d5569-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="d5569-106">Attribute</span></span>|<span data-ttu-id="d5569-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d5569-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="d5569-108">Logická hodnota, která určuje, zda je povoleno směrování paketů.</span><span class="sxs-lookup"><span data-stu-id="d5569-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="d5569-109">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="d5569-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="d5569-110">Celé číslo, které určuje maximální počet kanálů, které mohou být přijaty.</span><span class="sxs-lookup"><span data-stu-id="d5569-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5569-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d5569-111">Child Elements</span></span>  
  
|<span data-ttu-id="d5569-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5569-112">Element</span></span>|<span data-ttu-id="d5569-113">Description</span><span class="sxs-lookup"><span data-stu-id="d5569-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="d5569-114"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>Objekt, který obsahuje vlastnosti fondu kanálů pro aktuální kanál.</span><span class="sxs-lookup"><span data-stu-id="d5569-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5569-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d5569-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d5569-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5569-116">Element</span></span>|<span data-ttu-id="d5569-117">Description</span><span class="sxs-lookup"><span data-stu-id="d5569-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d5569-118">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d5569-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5569-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5569-119">Remarks</span></span>  
 <span data-ttu-id="d5569-120">Chcete-li povolit směrování paketů, je požadována jednosměrná konverzní vrstva, která tento prvek poskytuje.</span><span class="sxs-lookup"><span data-stu-id="d5569-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="d5569-121">Uživatel může vytvořit vlastní vazbu, která tuto vazbu navrství prostřednictvím přenosu, který je v relaci nebo požadavek-odpověď, aby bylo možné směrovat paket.</span><span class="sxs-lookup"><span data-stu-id="d5569-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="d5569-122">Tento prvek je také užitečný, pokud chcete zveřejnit jednosměrné metody v nativním režimu.</span><span class="sxs-lookup"><span data-stu-id="d5569-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="d5569-123">Pro tuto vrstvu lze použít více transformací, jako je kompozitní duplexní a spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="d5569-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5569-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5569-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d5569-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="d5569-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d5569-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d5569-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d5569-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d5569-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
