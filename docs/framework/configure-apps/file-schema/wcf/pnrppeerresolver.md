---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: cefd46d7810149264f9c431a212da0f3f51f8186
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577643"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="167c2-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="167c2-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="167c2-103">Určuje, že se má použít jako překladač překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="167c2-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="167c2-104">Tento element je volitelný, protože je výchozí překladač PNRP.</span><span class="sxs-lookup"><span data-stu-id="167c2-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="167c2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="167c2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="167c2-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="167c2-106">\<bindings></span></span>  
<span data-ttu-id="167c2-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="167c2-107">\<customBinding></span></span>  
<span data-ttu-id="167c2-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="167c2-108">\<binding></span></span>  
<span data-ttu-id="167c2-109">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="167c2-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167c2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="167c2-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="167c2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="167c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="167c2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="167c2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="167c2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="167c2-113">Attributes</span></span>  
  
|<span data-ttu-id="167c2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="167c2-114">Attribute</span></span>|<span data-ttu-id="167c2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="167c2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="167c2-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="167c2-116">resolverType</span></span>|<span data-ttu-id="167c2-117">Řetězec, který určuje překladače, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="167c2-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="167c2-118">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="167c2-118">This attribute is optional.</span></span> <span data-ttu-id="167c2-119">Pokud není nastavená nebo pokud je nastavena na prázdný řetězec se používá PNRP.</span><span class="sxs-lookup"><span data-stu-id="167c2-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="167c2-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="167c2-120">Child Elements</span></span>  
 <span data-ttu-id="167c2-121">Žádná</span><span class="sxs-lookup"><span data-stu-id="167c2-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="167c2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="167c2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="167c2-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="167c2-123">Element</span></span>|<span data-ttu-id="167c2-124">Popis</span><span class="sxs-lookup"><span data-stu-id="167c2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="167c2-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="167c2-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="167c2-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="167c2-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="167c2-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="167c2-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="167c2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="167c2-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="167c2-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="167c2-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="167c2-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="167c2-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="167c2-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="167c2-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="167c2-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="167c2-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="167c2-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="167c2-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
