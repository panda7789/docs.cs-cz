---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 18359e871feed17a11006d0b2998907faf25c158
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106584"
---
# <a name="custom"></a><span data-ttu-id="11ac0-101">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="11ac0-101">\<custom></span></span>
<span data-ttu-id="11ac0-102">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="11ac0-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="11ac0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="11ac0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="11ac0-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="11ac0-104">\<bindings></span></span>  
<span data-ttu-id="11ac0-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="11ac0-105">\<netPeerBinding></span></span>  
<span data-ttu-id="11ac0-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="11ac0-106">\<binding></span></span>  
<span data-ttu-id="11ac0-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="11ac0-107">\<resolver></span></span>  
<span data-ttu-id="11ac0-108">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="11ac0-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ac0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11ac0-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11ac0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11ac0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11ac0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11ac0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11ac0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="11ac0-112">Attributes</span></span>  
  
|<span data-ttu-id="11ac0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="11ac0-113">Attribute</span></span>|<span data-ttu-id="11ac0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="11ac0-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="11ac0-115">Identifikátor URI, který určuje adresu partnerského uzlu, který je hostitelem služby překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="11ac0-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="11ac0-116">Řetězec, který určuje typ překladače vlastní sdílené služby.</span><span class="sxs-lookup"><span data-stu-id="11ac0-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11ac0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11ac0-117">Child Elements</span></span>  
  
|<span data-ttu-id="11ac0-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="11ac0-118">Element</span></span>|<span data-ttu-id="11ac0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="11ac0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11ac0-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="11ac0-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="11ac0-121">Určuje identitu pro nakonfigurovaný s tímto elementem překladače vlastní partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="11ac0-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="11ac0-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="11ac0-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="11ac0-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="11ac0-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="11ac0-124">Kolekce záhlaví adres, který slouží pro zprávy protokolu SOAP zpracovat rozpoznávání vlastní druhé strany.</span><span class="sxs-lookup"><span data-stu-id="11ac0-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11ac0-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11ac0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="11ac0-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="11ac0-126">Element</span></span>|<span data-ttu-id="11ac0-127">Popis</span><span class="sxs-lookup"><span data-stu-id="11ac0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11ac0-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="11ac0-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="11ac0-129">Mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="11ac0-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11ac0-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11ac0-130">Remarks</span></span>  
 <span data-ttu-id="11ac0-131">Tento prvek definuje základního nastavení pro vlastní sdílené překladač služby, včetně koncového bodu adresy partnerského uzlu hostování služby a nastavení konkrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="11ac0-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="11ac0-132">Další informace o vytvoření vlastní mechanismus rozpoznávání najdete v tématu [přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="11ac0-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ac0-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11ac0-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="11ac0-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="11ac0-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="11ac0-135">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="11ac0-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
