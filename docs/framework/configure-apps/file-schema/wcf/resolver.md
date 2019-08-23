---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934214"
---
# <a name="resolver"></a><span data-ttu-id="3cf2d-101">\<> překladače</span><span class="sxs-lookup"><span data-stu-id="3cf2d-101">\<resolver></span></span>
<span data-ttu-id="3cf2d-102">Určuje rovnocenný překladač, který se používá k překladu ID partnerské sítě na sadu adres partnerských uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="3cf2d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3cf2d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3cf2d-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3cf2d-104">\<bindings></span></span>  
<span data-ttu-id="3cf2d-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="3cf2d-105">\<netPeerBinding></span></span>  
<span data-ttu-id="3cf2d-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3cf2d-106">\<binding></span></span>  
<span data-ttu-id="3cf2d-107">\<> překladače</span><span class="sxs-lookup"><span data-stu-id="3cf2d-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf2d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cf2d-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cf2d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3cf2d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3cf2d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cf2d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3cf2d-111">Attributes</span></span>  
  
|<span data-ttu-id="3cf2d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3cf2d-112">Attribute</span></span>|<span data-ttu-id="3cf2d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf2d-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="3cf2d-114">Řetězec určující, zda je instance překladače partnerského vztahu přidružená k této službě buď specifická pro protokol PNRP, vlastního Překladači nebo automaticky určena.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="3cf2d-115">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="3cf2d-116">Řetězec, který určuje způsob, jakým jsou odkazy sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="3cf2d-117">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cf2d-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf2d-118">Child Elements</span></span>  
  
|<span data-ttu-id="3cf2d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cf2d-119">Element</span></span>|<span data-ttu-id="3cf2d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf2d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cf2d-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="3cf2d-121">\<headers></span></span>](headers.md)|<span data-ttu-id="3cf2d-122">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cf2d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3cf2d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3cf2d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3cf2d-124">Element</span></span>|<span data-ttu-id="3cf2d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf2d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cf2d-126">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3cf2d-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="3cf2d-127">Definuje všechny schopnosti [ \<vazby NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3cf2d-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf2d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cf2d-128">Remarks</span></span>  
 <span data-ttu-id="3cf2d-129">Překladač názvů partnerů je služba zjišťování, kterou používají rovnocenné kanály k nalezení partnerských uzlů, které se účastní sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="3cf2d-130">Používá se také k registraci uzlu se sdílenou sítí, mechanizmus, který je partnerský uzel známý a dostupný z partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="3cf2d-131">Další informace o překladačích peer-to najdete [](../../../wcf/feature-details/peer-resolvers.md)v tématu věnovaném překladačům peer.</span><span class="sxs-lookup"><span data-stu-id="3cf2d-131">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf2d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cf2d-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="3cf2d-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="3cf2d-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="3cf2d-134">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3cf2d-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
