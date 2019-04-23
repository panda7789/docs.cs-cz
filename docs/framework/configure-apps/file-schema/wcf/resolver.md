---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 39dcb868bd3ff25451509616e1dac7d41f94cfa1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075871"
---
# <a name="resolver"></a><span data-ttu-id="b9635-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="b9635-101">\<resolver></span></span>
<span data-ttu-id="b9635-102">Určuje mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="b9635-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="b9635-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b9635-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9635-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b9635-104">\<bindings></span></span>  
<span data-ttu-id="b9635-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="b9635-105">\<netPeerBinding></span></span>  
<span data-ttu-id="b9635-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b9635-106">\<binding></span></span>  
<span data-ttu-id="b9635-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="b9635-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9635-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9635-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9635-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9635-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b9635-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9635-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9635-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9635-111">Attributes</span></span>  
  
|<span data-ttu-id="b9635-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b9635-112">Attribute</span></span>|<span data-ttu-id="b9635-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b9635-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="b9635-114">Řetězec, který určuje, jestli instance služby mechanismu rozpoznávání partnera přidružený k této službě je buď PNRP specifická, vlastní mechanismus rozpoznávání nebo je automaticky zjišťovaná.</span><span class="sxs-lookup"><span data-stu-id="b9635-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="b9635-115">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="b9635-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="b9635-116">Řetězec určující způsob odkazů jsou sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="b9635-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="b9635-117">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="b9635-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9635-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9635-118">Child Elements</span></span>  
  
|<span data-ttu-id="b9635-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9635-119">Element</span></span>|<span data-ttu-id="b9635-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b9635-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9635-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="b9635-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="b9635-122">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="b9635-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9635-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9635-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b9635-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9635-124">Element</span></span>|<span data-ttu-id="b9635-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b9635-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9635-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b9635-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b9635-127">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b9635-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9635-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9635-128">Remarks</span></span>  
 <span data-ttu-id="b9635-129">Mechanismus rozpoznávání partnera název je služba zjišťování používají kanály peer najít partnerské uzly, které jsou součástí sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="b9635-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="b9635-130">Používá se také "zaregistrovat" uzlu sítě peer, mechanismus, pomocí kterého bude rovnocenný uzel stane známé a dostupné ze sítě peer.</span><span class="sxs-lookup"><span data-stu-id="b9635-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="b9635-131">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="b9635-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9635-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9635-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="b9635-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="b9635-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="b9635-134">[Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b9635-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
