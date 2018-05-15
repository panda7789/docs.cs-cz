---
title: '&lt;Řešitel&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltresolvergt"></a><span data-ttu-id="b90cc-102">&lt;Řešitel&gt;</span><span class="sxs-lookup"><span data-stu-id="b90cc-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="b90cc-103">Určuje sdílené překladače, který se používá k překladu sdílené OK ID sítě pro sadu adres partnerských uzlů, která představuje několik uzlů, které jsou součástí OK.</span><span class="sxs-lookup"><span data-stu-id="b90cc-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="b90cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b90cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b90cc-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b90cc-105">\<bindings></span></span>  
<span data-ttu-id="b90cc-106">\<netpeerbinding – ></span><span class="sxs-lookup"><span data-stu-id="b90cc-106">\<netPeerBinding></span></span>  
<span data-ttu-id="b90cc-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b90cc-107">\<binding></span></span>  
<span data-ttu-id="b90cc-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="b90cc-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90cc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b90cc-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b90cc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b90cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b90cc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b90cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b90cc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b90cc-112">Attributes</span></span>  
  
|<span data-ttu-id="b90cc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b90cc-113">Attribute</span></span>|<span data-ttu-id="b90cc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b90cc-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="b90cc-115">Řetězec, který určuje, zda instance překladače sdílené přidruženého k této službě je buď PNRP konkrétní, vlastní překladač, nebo automaticky určeno.</span><span class="sxs-lookup"><span data-stu-id="b90cc-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="b90cc-116">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="b90cc-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="b90cc-117">Řetězec, který určuje způsobu, jakým odkazy jsou sdílena mezi partnerské uzly.</span><span class="sxs-lookup"><span data-stu-id="b90cc-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="b90cc-118">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="b90cc-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b90cc-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b90cc-119">Child Elements</span></span>  
  
|<span data-ttu-id="b90cc-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b90cc-120">Element</span></span>|<span data-ttu-id="b90cc-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b90cc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b90cc-122">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="b90cc-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="b90cc-123">Určuje nastavení pro vlastní sdílené služby překladač.</span><span class="sxs-lookup"><span data-stu-id="b90cc-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b90cc-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b90cc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b90cc-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b90cc-125">Element</span></span>|<span data-ttu-id="b90cc-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b90cc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b90cc-127">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b90cc-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b90cc-128">Definuje všechny možnosti vazby [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b90cc-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b90cc-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b90cc-129">Remarks</span></span>  
 <span data-ttu-id="b90cc-130">Překladač název sdílené je služba zjišťování používá sdílené kanály najít sdílené uzly, které jsou součástí sdílené mřížku.</span><span class="sxs-lookup"><span data-stu-id="b90cc-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="b90cc-131">Slouží také "register" uzlu s sdílené mřížky mechanismus, pomocí kterého uzlu sdílené stane známé a dostupné z mřížky sdílené.</span><span class="sxs-lookup"><span data-stu-id="b90cc-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="b90cc-132">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="b90cc-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90cc-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b90cc-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="b90cc-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="b90cc-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="b90cc-135">Přidání vlastní překladač do PeerChannel aplikace</span><span class="sxs-lookup"><span data-stu-id="b90cc-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
