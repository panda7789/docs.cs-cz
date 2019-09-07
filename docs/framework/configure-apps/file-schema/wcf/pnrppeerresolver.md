---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400051"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="9d42f-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="9d42f-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="9d42f-102">Určuje, že jako překladač se použije překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="9d42f-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="9d42f-103">Tento prvek je nepovinný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="9d42f-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="9d42f-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d42f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d42f-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9d42f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9d42f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9d42f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9d42f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9d42f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="9d42f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="9d42f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9d42f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="9d42f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d42f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d42f-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d42f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d42f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9d42f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d42f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d42f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d42f-113">Attributes</span></span>  
  
|<span data-ttu-id="9d42f-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d42f-114">Attribute</span></span>|<span data-ttu-id="9d42f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9d42f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d42f-116">Typ překladače</span><span class="sxs-lookup"><span data-stu-id="9d42f-116">resolverType</span></span>|<span data-ttu-id="9d42f-117">Řetězec, který určuje překladač, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="9d42f-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="9d42f-118">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="9d42f-118">This attribute is optional.</span></span> <span data-ttu-id="9d42f-119">Pokud není nastavená, nebo pokud je nastavená na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="9d42f-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d42f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d42f-120">Child Elements</span></span>  
 <span data-ttu-id="9d42f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d42f-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d42f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d42f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9d42f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d42f-123">Element</span></span>|<span data-ttu-id="9d42f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9d42f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d42f-125">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="9d42f-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9d42f-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="9d42f-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d42f-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d42f-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9d42f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d42f-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9d42f-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="9d42f-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9d42f-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="9d42f-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9d42f-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9d42f-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9d42f-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9d42f-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="9d42f-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="9d42f-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
