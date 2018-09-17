---
title: '&lt;Vlastní&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 7d558be66b8a1e46d9743c5f8bf0bb9a8b4c349e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743570"
---
# <a name="ltcustomgt"></a><span data-ttu-id="80a90-102">&lt;Vlastní&gt;</span><span class="sxs-lookup"><span data-stu-id="80a90-102">&lt;custom&gt;</span></span>
<span data-ttu-id="80a90-103">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="80a90-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="80a90-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80a90-104">\<system.serviceModel></span></span>  
<span data-ttu-id="80a90-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="80a90-105">\<bindings></span></span>  
<span data-ttu-id="80a90-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="80a90-106">\<netPeerBinding></span></span>  
<span data-ttu-id="80a90-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="80a90-107">\<binding></span></span>  
<span data-ttu-id="80a90-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="80a90-108">\<resolver></span></span>  
<span data-ttu-id="80a90-109">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="80a90-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a90-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80a90-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80a90-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80a90-111">Attributes and Elements</span></span>  
 <span data-ttu-id="80a90-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80a90-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80a90-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="80a90-113">Attributes</span></span>  
  
|<span data-ttu-id="80a90-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="80a90-114">Attribute</span></span>|<span data-ttu-id="80a90-115">Popis</span><span class="sxs-lookup"><span data-stu-id="80a90-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="80a90-116">Identifikátor URI, který určuje adresu partnerského uzlu, který je hostitelem služby překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="80a90-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="80a90-117">Řetězec, který určuje typ překladače vlastní sdílené služby.</span><span class="sxs-lookup"><span data-stu-id="80a90-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80a90-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80a90-118">Child Elements</span></span>  
  
|<span data-ttu-id="80a90-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="80a90-119">Element</span></span>|<span data-ttu-id="80a90-120">Popis</span><span class="sxs-lookup"><span data-stu-id="80a90-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80a90-121">\<identity ></span><span class="sxs-lookup"><span data-stu-id="80a90-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="80a90-122">Určuje identitu pro nakonfigurovaný s tímto elementem překladače vlastní partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="80a90-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="80a90-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="80a90-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="80a90-124">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="80a90-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="80a90-125">Kolekce záhlaví adres, který slouží pro zprávy protokolu SOAP zpracovat rozpoznávání vlastní druhé strany.</span><span class="sxs-lookup"><span data-stu-id="80a90-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80a90-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80a90-126">Parent Elements</span></span>  
  
|<span data-ttu-id="80a90-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="80a90-127">Element</span></span>|<span data-ttu-id="80a90-128">Popis</span><span class="sxs-lookup"><span data-stu-id="80a90-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80a90-129">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="80a90-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="80a90-130">Mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="80a90-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80a90-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80a90-131">Remarks</span></span>  
 <span data-ttu-id="80a90-132">Tento prvek definuje základního nastavení pro vlastní sdílené překladač služby, včetně koncového bodu adresy partnerského uzlu hostování služby a nastavení konkrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="80a90-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="80a90-133">Další informace o vytvoření vlastní mechanismus rozpoznávání najdete v tématu [přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="80a90-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a90-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="80a90-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="80a90-135">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="80a90-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="80a90-136">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="80a90-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
