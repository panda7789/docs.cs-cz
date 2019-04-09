---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 39dcb868bd3ff25451509616e1dac7d41f94cfa1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075871"
---
# <a name="resolver"></a><span data-ttu-id="6eb8b-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="6eb8b-101">\<resolver></span></span>
<span data-ttu-id="6eb8b-102">Určuje mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="6eb8b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6eb8b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6eb8b-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6eb8b-104">\<bindings></span></span>  
<span data-ttu-id="6eb8b-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="6eb8b-105">\<netPeerBinding></span></span>  
<span data-ttu-id="6eb8b-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6eb8b-106">\<binding></span></span>  
<span data-ttu-id="6eb8b-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="6eb8b-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb8b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb8b-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6eb8b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6eb8b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6eb8b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6eb8b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6eb8b-111">Attributes</span></span>  
  
|<span data-ttu-id="6eb8b-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6eb8b-112">Attribute</span></span>|<span data-ttu-id="6eb8b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb8b-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6eb8b-114">Řetězec, který určuje, jestli instance služby mechanismu rozpoznávání partnera přidružený k této službě je buď PNRP specifická, vlastní mechanismus rozpoznávání nebo je automaticky zjišťovaná.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="6eb8b-115">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="6eb8b-116">Řetězec určující způsob odkazů jsou sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="6eb8b-117">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6eb8b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6eb8b-118">Child Elements</span></span>  
  
|<span data-ttu-id="6eb8b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="6eb8b-119">Element</span></span>|<span data-ttu-id="6eb8b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb8b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6eb8b-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="6eb8b-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="6eb8b-122">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6eb8b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6eb8b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6eb8b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6eb8b-124">Element</span></span>|<span data-ttu-id="6eb8b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb8b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6eb8b-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6eb8b-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6eb8b-127">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6eb8b-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eb8b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eb8b-128">Remarks</span></span>  
 <span data-ttu-id="6eb8b-129">Mechanismus rozpoznávání partnera název je služba zjišťování používají kanály peer najít partnerské uzly, které jsou součástí sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="6eb8b-130">Používá se také "zaregistrovat" uzlu sítě peer, mechanismus, pomocí kterého bude rovnocenný uzel stane známé a dostupné ze sítě peer.</span><span class="sxs-lookup"><span data-stu-id="6eb8b-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="6eb8b-131">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="6eb8b-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb8b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eb8b-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="6eb8b-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="6eb8b-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="6eb8b-134">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="6eb8b-134">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
