---
title: '&lt;překladač&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 48b6b6ca315f7ab63a8f7a64b97167fa04fe1e4e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133763"
---
# <a name="ltresolvergt"></a><span data-ttu-id="f23eb-102">&lt;překladač&gt;</span><span class="sxs-lookup"><span data-stu-id="f23eb-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="f23eb-103">Určuje mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="f23eb-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="f23eb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f23eb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f23eb-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f23eb-105">\<bindings></span></span>  
<span data-ttu-id="f23eb-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="f23eb-106">\<netPeerBinding></span></span>  
<span data-ttu-id="f23eb-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f23eb-107">\<binding></span></span>  
<span data-ttu-id="f23eb-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="f23eb-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23eb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f23eb-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f23eb-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f23eb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f23eb-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f23eb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f23eb-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f23eb-112">Attributes</span></span>  
  
|<span data-ttu-id="f23eb-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f23eb-113">Attribute</span></span>|<span data-ttu-id="f23eb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f23eb-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="f23eb-115">Řetězec, který určuje, jestli instance služby mechanismu rozpoznávání partnera přidružený k této službě je buď PNRP specifická, vlastní mechanismus rozpoznávání nebo je automaticky zjišťovaná.</span><span class="sxs-lookup"><span data-stu-id="f23eb-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="f23eb-116">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="f23eb-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="f23eb-117">Řetězec určující způsob odkazů jsou sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="f23eb-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="f23eb-118">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="f23eb-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f23eb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f23eb-119">Child Elements</span></span>  
  
|<span data-ttu-id="f23eb-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f23eb-120">Element</span></span>|<span data-ttu-id="f23eb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f23eb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f23eb-122">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="f23eb-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="f23eb-123">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="f23eb-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f23eb-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f23eb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f23eb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f23eb-125">Element</span></span>|<span data-ttu-id="f23eb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f23eb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f23eb-127">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f23eb-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f23eb-128">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f23eb-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f23eb-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f23eb-129">Remarks</span></span>  
 <span data-ttu-id="f23eb-130">Mechanismus rozpoznávání partnera název je služba zjišťování používají kanály peer najít partnerské uzly, které jsou součástí sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="f23eb-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="f23eb-131">Používá se také "zaregistrovat" uzlu sítě peer, mechanismus, pomocí kterého bude rovnocenný uzel stane známé a dostupné ze sítě peer.</span><span class="sxs-lookup"><span data-stu-id="f23eb-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="f23eb-132">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="f23eb-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23eb-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f23eb-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="f23eb-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="f23eb-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="f23eb-135">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="f23eb-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
