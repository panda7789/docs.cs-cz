---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738776"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="7d8b7-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="7d8b7-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="7d8b7-102">Určuje, že jako překladač se použije překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="7d8b7-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="7d8b7-103">Tento prvek je nepovinný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="7d8b7-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7d8b7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d8b7-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7d8b7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7d8b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7d8b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7d8b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7d8b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7d8b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="7d8b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7d8b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="7d8b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8b7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d8b7-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d8b7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d8b7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7d8b7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d8b7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d8b7-113">Attributes</span></span>  
  
|<span data-ttu-id="7d8b7-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d8b7-114">Attribute</span></span>|<span data-ttu-id="7d8b7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7d8b7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d8b7-116">Typ překladače</span><span class="sxs-lookup"><span data-stu-id="7d8b7-116">resolverType</span></span>|<span data-ttu-id="7d8b7-117">Řetězec, který určuje překladač, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="7d8b7-118">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-118">This attribute is optional.</span></span> <span data-ttu-id="7d8b7-119">Pokud není nastavená, nebo pokud je nastavená na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d8b7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d8b7-120">Child Elements</span></span>  
 <span data-ttu-id="7d8b7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d8b7-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d8b7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d8b7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7d8b7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d8b7-123">Element</span></span>|<span data-ttu-id="7d8b7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7d8b7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d8b7-125">vazba \<</span><span class="sxs-lookup"><span data-stu-id="7d8b7-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="7d8b7-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7d8b7-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d8b7-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d8b7-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="7d8b7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d8b7-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7d8b7-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="7d8b7-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7d8b7-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7d8b7-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7d8b7-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7d8b7-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7d8b7-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7d8b7-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="7d8b7-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="7d8b7-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
