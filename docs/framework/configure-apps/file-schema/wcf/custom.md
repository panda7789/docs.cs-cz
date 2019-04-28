---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 18359e871feed17a11006d0b2998907faf25c158
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704190"
---
# <a name="custom"></a><span data-ttu-id="3ff80-101">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="3ff80-101">\<custom></span></span>
<span data-ttu-id="3ff80-102">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="3ff80-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="3ff80-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ff80-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3ff80-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3ff80-104">\<bindings></span></span>  
<span data-ttu-id="3ff80-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="3ff80-105">\<netPeerBinding></span></span>  
<span data-ttu-id="3ff80-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ff80-106">\<binding></span></span>  
<span data-ttu-id="3ff80-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="3ff80-107">\<resolver></span></span>  
<span data-ttu-id="3ff80-108">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="3ff80-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff80-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ff80-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ff80-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ff80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ff80-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ff80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ff80-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ff80-112">Attributes</span></span>  
  
|<span data-ttu-id="3ff80-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ff80-113">Attribute</span></span>|<span data-ttu-id="3ff80-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff80-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="3ff80-115">Identifikátor URI, který určuje adresu partnerského uzlu, který je hostitelem služby překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="3ff80-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="3ff80-116">Řetězec, který určuje typ překladače vlastní sdílené služby.</span><span class="sxs-lookup"><span data-stu-id="3ff80-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ff80-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ff80-117">Child Elements</span></span>  
  
|<span data-ttu-id="3ff80-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ff80-118">Element</span></span>|<span data-ttu-id="3ff80-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff80-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ff80-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="3ff80-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3ff80-121">Určuje identitu pro nakonfigurovaný s tímto elementem překladače vlastní partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="3ff80-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="3ff80-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="3ff80-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="3ff80-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="3ff80-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="3ff80-124">Kolekce záhlaví adres, který slouží pro zprávy protokolu SOAP zpracovat rozpoznávání vlastní druhé strany.</span><span class="sxs-lookup"><span data-stu-id="3ff80-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ff80-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ff80-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3ff80-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ff80-126">Element</span></span>|<span data-ttu-id="3ff80-127">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff80-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ff80-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="3ff80-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="3ff80-129">Mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="3ff80-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ff80-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ff80-130">Remarks</span></span>  
 <span data-ttu-id="3ff80-131">Tento prvek definuje základního nastavení pro vlastní sdílené překladač služby, včetně koncového bodu adresy partnerského uzlu hostování služby a nastavení konkrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="3ff80-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="3ff80-132">Další informace o vytvoření vlastní mechanismus rozpoznávání najdete v tématu [přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3ff80-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff80-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ff80-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="3ff80-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="3ff80-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="3ff80-135">[Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3ff80-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
