---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214050"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="d2fd3-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="d2fd3-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="d2fd3-102">Určuje, že se má použít jako překladač překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="d2fd3-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="d2fd3-103">Tento element je volitelný, protože je výchozí překladač PNRP.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="d2fd3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d2fd3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d2fd3-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d2fd3-105">\<bindings></span></span>  
<span data-ttu-id="d2fd3-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d2fd3-106">\<customBinding></span></span>  
<span data-ttu-id="d2fd3-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2fd3-107">\<binding></span></span>  
<span data-ttu-id="d2fd3-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="d2fd3-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fd3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2fd3-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2fd3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d2fd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2fd3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2fd3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2fd3-112">Attributes</span></span>  
  
|<span data-ttu-id="d2fd3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2fd3-113">Attribute</span></span>|<span data-ttu-id="d2fd3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d2fd3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2fd3-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="d2fd3-115">resolverType</span></span>|<span data-ttu-id="d2fd3-116">Řetězec, který určuje překladače, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="d2fd3-117">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-117">This attribute is optional.</span></span> <span data-ttu-id="d2fd3-118">Pokud není nastavená nebo pokud je nastavena na prázdný řetězec se používá PNRP.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2fd3-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d2fd3-119">Child Elements</span></span>  
 <span data-ttu-id="d2fd3-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d2fd3-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2fd3-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d2fd3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d2fd3-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d2fd3-122">Element</span></span>|<span data-ttu-id="d2fd3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d2fd3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2fd3-124">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2fd3-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d2fd3-125">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d2fd3-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d2fd3-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2fd3-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d2fd3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2fd3-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d2fd3-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="d2fd3-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d2fd3-129">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="d2fd3-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d2fd3-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d2fd3-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d2fd3-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d2fd3-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="d2fd3-132">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="d2fd3-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
