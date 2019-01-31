---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f98c358cc9891e9d7223d280fc8e50c19aad9759
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260645"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="05774-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="05774-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="05774-102">Určuje, že se má použít jako překladač překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="05774-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="05774-103">Tento element je volitelný, protože je výchozí překladač PNRP.</span><span class="sxs-lookup"><span data-stu-id="05774-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="05774-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="05774-104">\<system.serviceModel></span></span>  
<span data-ttu-id="05774-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="05774-105">\<bindings></span></span>  
<span data-ttu-id="05774-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="05774-106">\<customBinding></span></span>  
<span data-ttu-id="05774-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="05774-107">\<binding></span></span>  
<span data-ttu-id="05774-108">\<pnrpResolver></span><span class="sxs-lookup"><span data-stu-id="05774-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05774-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05774-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05774-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05774-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05774-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05774-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05774-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="05774-112">Attributes</span></span>  
  
|<span data-ttu-id="05774-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="05774-113">Attribute</span></span>|<span data-ttu-id="05774-114">Popis</span><span class="sxs-lookup"><span data-stu-id="05774-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05774-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="05774-115">resolverType</span></span>|<span data-ttu-id="05774-116">Řetězec, který určuje překladače, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="05774-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="05774-117">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="05774-117">This attribute is optional.</span></span> <span data-ttu-id="05774-118">Pokud není nastavená nebo pokud je nastavena na prázdný řetězec se používá PNRP.</span><span class="sxs-lookup"><span data-stu-id="05774-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05774-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05774-119">Child Elements</span></span>  
 <span data-ttu-id="05774-120">Žádná</span><span class="sxs-lookup"><span data-stu-id="05774-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05774-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05774-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05774-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="05774-122">Element</span></span>|<span data-ttu-id="05774-123">Popis</span><span class="sxs-lookup"><span data-stu-id="05774-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05774-124">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="05774-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="05774-125">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="05774-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05774-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="05774-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="05774-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05774-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="05774-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="05774-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="05774-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="05774-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="05774-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="05774-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="05774-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="05774-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="05774-132">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="05774-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
