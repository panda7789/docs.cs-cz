---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933799"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="09628-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="09628-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="09628-102">Určuje, že jako překladač se použije překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="09628-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="09628-103">Tento prvek je nepovinný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="09628-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="09628-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09628-104">\<system.serviceModel></span></span>  
<span data-ttu-id="09628-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="09628-105">\<bindings></span></span>  
<span data-ttu-id="09628-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="09628-106">\<customBinding></span></span>  
<span data-ttu-id="09628-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="09628-107">\<binding></span></span>  
<span data-ttu-id="09628-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="09628-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09628-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09628-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09628-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09628-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09628-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09628-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09628-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="09628-112">Attributes</span></span>  
  
|<span data-ttu-id="09628-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="09628-113">Attribute</span></span>|<span data-ttu-id="09628-114">Popis</span><span class="sxs-lookup"><span data-stu-id="09628-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09628-115">Typ překladače</span><span class="sxs-lookup"><span data-stu-id="09628-115">resolverType</span></span>|<span data-ttu-id="09628-116">Řetězec, který určuje překladač, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="09628-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="09628-117">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="09628-117">This attribute is optional.</span></span> <span data-ttu-id="09628-118">Pokud není nastavená, nebo pokud je nastavená na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="09628-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09628-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09628-119">Child Elements</span></span>  
 <span data-ttu-id="09628-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="09628-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09628-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09628-121">Parent Elements</span></span>  
  
|<span data-ttu-id="09628-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="09628-122">Element</span></span>|<span data-ttu-id="09628-123">Popis</span><span class="sxs-lookup"><span data-stu-id="09628-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09628-124">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="09628-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="09628-125">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="09628-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09628-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="09628-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="09628-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09628-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="09628-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="09628-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="09628-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="09628-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="09628-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="09628-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="09628-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="09628-131">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="09628-132">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="09628-132">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
