---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f0874d38c3432f066d1bec5cc84f53e1f3730180
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747977"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="9f75b-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="9f75b-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="9f75b-103">Určuje, že překladač PNRP (protokolu Peer Name Resolution Protocol) se má použít jako překladač.</span><span class="sxs-lookup"><span data-stu-id="9f75b-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="9f75b-104">Tento element je volitelný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="9f75b-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="9f75b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9f75b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9f75b-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="9f75b-106">\<bindings></span></span>  
<span data-ttu-id="9f75b-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9f75b-107">\<customBinding></span></span>  
<span data-ttu-id="9f75b-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="9f75b-108">\<binding></span></span>  
<span data-ttu-id="9f75b-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="9f75b-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f75b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f75b-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f75b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f75b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f75b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f75b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f75b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f75b-113">Attributes</span></span>  
  
|<span data-ttu-id="9f75b-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f75b-114">Attribute</span></span>|<span data-ttu-id="9f75b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9f75b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f75b-116">Třída resolverType</span><span class="sxs-lookup"><span data-stu-id="9f75b-116">resolverType</span></span>|<span data-ttu-id="9f75b-117">Řetězec, který určuje překladač k použití.</span><span class="sxs-lookup"><span data-stu-id="9f75b-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="9f75b-118">Tento atribut je volitelné.</span><span class="sxs-lookup"><span data-stu-id="9f75b-118">This attribute is optional.</span></span> <span data-ttu-id="9f75b-119">Pokud není nastaven, nebo pokud je nastavena na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="9f75b-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f75b-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f75b-120">Child Elements</span></span>  
 <span data-ttu-id="9f75b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f75b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f75b-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f75b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9f75b-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f75b-123">Element</span></span>|<span data-ttu-id="9f75b-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9f75b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f75b-125">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="9f75b-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9f75b-126">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="9f75b-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f75b-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f75b-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f75b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f75b-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9f75b-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="9f75b-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9f75b-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="9f75b-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9f75b-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9f75b-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9f75b-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9f75b-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="9f75b-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="9f75b-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
