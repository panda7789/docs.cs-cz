---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 57fa67c9536d35775694c56c9053cffa4dea29ea
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257449"
---
# <a name="resolver"></a><span data-ttu-id="51656-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="51656-101">\<resolver></span></span>
<span data-ttu-id="51656-102">Určuje mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="51656-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="51656-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="51656-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="51656-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="51656-104">\<bindings></span></span>  
<span data-ttu-id="51656-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="51656-105">\<netPeerBinding></span></span>  
<span data-ttu-id="51656-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="51656-106">\<binding></span></span>  
<span data-ttu-id="51656-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="51656-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51656-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51656-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51656-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51656-109">Attributes and Elements</span></span>  
 <span data-ttu-id="51656-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51656-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51656-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="51656-111">Attributes</span></span>  
  
|<span data-ttu-id="51656-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="51656-112">Attribute</span></span>|<span data-ttu-id="51656-113">Popis</span><span class="sxs-lookup"><span data-stu-id="51656-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="51656-114">Řetězec, který určuje, jestli instance služby mechanismu rozpoznávání partnera přidružený k této službě je buď PNRP specifická, vlastní mechanismus rozpoznávání nebo je automaticky zjišťovaná.</span><span class="sxs-lookup"><span data-stu-id="51656-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="51656-115">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="51656-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="51656-116">Řetězec určující způsob odkazů jsou sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="51656-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="51656-117">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="51656-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51656-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51656-118">Child Elements</span></span>  
  
|<span data-ttu-id="51656-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="51656-119">Element</span></span>|<span data-ttu-id="51656-120">Popis</span><span class="sxs-lookup"><span data-stu-id="51656-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51656-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="51656-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="51656-122">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="51656-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51656-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51656-123">Parent Elements</span></span>  
  
|<span data-ttu-id="51656-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="51656-124">Element</span></span>|<span data-ttu-id="51656-125">Popis</span><span class="sxs-lookup"><span data-stu-id="51656-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51656-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="51656-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="51656-127">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="51656-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51656-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51656-128">Remarks</span></span>  
 <span data-ttu-id="51656-129">Mechanismus rozpoznávání partnera název je služba zjišťování používají kanály peer najít partnerské uzly, které jsou součástí sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="51656-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="51656-130">Používá se také "zaregistrovat" uzlu sítě peer, mechanismus, pomocí kterého bude rovnocenný uzel stane známé a dostupné ze sítě peer.</span><span class="sxs-lookup"><span data-stu-id="51656-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="51656-131">Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="51656-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51656-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51656-132">See also</span></span>
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="51656-133">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="51656-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="51656-134">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="51656-134">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
