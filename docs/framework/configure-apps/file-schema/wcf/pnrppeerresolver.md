---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783276"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="3775e-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="3775e-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="3775e-102">Určuje, že se má použít jako překladač překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="3775e-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="3775e-103">Tento element je volitelný, protože je výchozí překladač PNRP.</span><span class="sxs-lookup"><span data-stu-id="3775e-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="3775e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3775e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3775e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3775e-105">\<bindings></span></span>  
<span data-ttu-id="3775e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3775e-106">\<customBinding></span></span>  
<span data-ttu-id="3775e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3775e-107">\<binding></span></span>  
<span data-ttu-id="3775e-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="3775e-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3775e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3775e-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3775e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3775e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3775e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3775e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3775e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3775e-112">Attributes</span></span>  
  
|<span data-ttu-id="3775e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3775e-113">Attribute</span></span>|<span data-ttu-id="3775e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3775e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3775e-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="3775e-115">resolverType</span></span>|<span data-ttu-id="3775e-116">Řetězec, který určuje překladače, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="3775e-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="3775e-117">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="3775e-117">This attribute is optional.</span></span> <span data-ttu-id="3775e-118">Pokud není nastavená nebo pokud je nastavena na prázdný řetězec se používá PNRP.</span><span class="sxs-lookup"><span data-stu-id="3775e-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3775e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3775e-119">Child Elements</span></span>  
 <span data-ttu-id="3775e-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="3775e-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3775e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3775e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3775e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="3775e-122">Element</span></span>|<span data-ttu-id="3775e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3775e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3775e-124">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3775e-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3775e-125">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3775e-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3775e-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="3775e-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3775e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3775e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3775e-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="3775e-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3775e-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3775e-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3775e-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3775e-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3775e-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3775e-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="3775e-132">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="3775e-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
