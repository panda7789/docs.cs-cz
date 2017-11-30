---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="f7bfe-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="f7bfe-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="f7bfe-103">Určuje, že překladač PNRP (protokolu Peer Name Resolution Protocol) se má použít jako překladač.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="f7bfe-104">Tento element je volitelný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="f7bfe-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f7bfe-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-106">\<bindings></span></span>  
<span data-ttu-id="f7bfe-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-107">\<customBinding></span></span>  
<span data-ttu-id="f7bfe-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-108">\<binding></span></span>  
<span data-ttu-id="f7bfe-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bfe-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7bfe-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7bfe-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f7bfe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f7bfe-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7bfe-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f7bfe-113">Attributes</span></span>  
  
|<span data-ttu-id="f7bfe-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f7bfe-114">Attribute</span></span>|<span data-ttu-id="f7bfe-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f7bfe-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7bfe-116">Třída resolverType</span><span class="sxs-lookup"><span data-stu-id="f7bfe-116">resolverType</span></span>|<span data-ttu-id="f7bfe-117">Řetězec, který určuje překladač k použití.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="f7bfe-118">Tento atribut je volitelné.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-118">This attribute is optional.</span></span> <span data-ttu-id="f7bfe-119">Pokud není nastaven, nebo pokud je nastavena na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7bfe-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f7bfe-120">Child Elements</span></span>  
 <span data-ttu-id="f7bfe-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="f7bfe-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7bfe-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f7bfe-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f7bfe-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f7bfe-123">Element</span></span>|<span data-ttu-id="f7bfe-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f7bfe-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7bfe-125">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f7bfe-126">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f7bfe-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7bfe-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7bfe-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7bfe-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f7bfe-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="f7bfe-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f7bfe-130">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="f7bfe-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f7bfe-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f7bfe-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f7bfe-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f7bfe-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="f7bfe-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="f7bfe-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
