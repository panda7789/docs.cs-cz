---
title: '&lt;překladač&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 67afce36acc8e7c2ff1f176275f1d021a61cc603
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146261"
---
# <a name="ltresolvergt"></a><span data-ttu-id="c4990-102">&lt;překladač&gt;</span><span class="sxs-lookup"><span data-stu-id="c4990-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="c4990-103">Určuje mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="c4990-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="c4990-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4990-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4990-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="c4990-105">\<bindings></span></span>  
<span data-ttu-id="c4990-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="c4990-106">\<netPeerBinding></span></span>  
<span data-ttu-id="c4990-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="c4990-107">\<binding></span></span>  
<span data-ttu-id="c4990-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="c4990-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4990-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4990-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4990-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4990-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4990-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4990-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4990-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4990-112">Attributes</span></span>  
  
|<span data-ttu-id="c4990-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c4990-113">Attribute</span></span>|<span data-ttu-id="c4990-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c4990-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="c4990-115">Řetězec, který určuje, jestli instance služby mechanismu rozpoznávání partnera přidružený k této službě je buď PNRP specifická, vlastní mechanismus rozpoznávání nebo je automaticky zjišťovaná.</span><span class="sxs-lookup"><span data-stu-id="c4990-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="c4990-116">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="c4990-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="c4990-117">Řetězec určující způsob odkazů jsou sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="c4990-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="c4990-118">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="c4990-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4990-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4990-119">Child Elements</span></span>  
  
|<span data-ttu-id="c4990-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4990-120">Element</span></span>|<span data-ttu-id="c4990-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c4990-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4990-122">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="c4990-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="c4990-123">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="c4990-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4990-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4990-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c4990-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4990-125">Element</span></span>|<span data-ttu-id="c4990-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c4990-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4990-127">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="c4990-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c4990-128">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c4990-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4990-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4990-129">Remarks</span></span>  
 <span data-ttu-id="c4990-130">Mechanismus rozpoznávání partnera název je služba zjišťování používají kanály peer najít partnerské uzly, které jsou součástí sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="c4990-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="c4990-131">Používá se také "zaregistrovat" uzlu sítě peer, mechanismus, pomocí kterého bude rovnocenný uzel stane známé a dostupné ze sítě peer.</span><span class="sxs-lookup"><span data-stu-id="c4990-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="c4990-132">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="c4990-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4990-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4990-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="c4990-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="c4990-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="c4990-135">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="c4990-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
