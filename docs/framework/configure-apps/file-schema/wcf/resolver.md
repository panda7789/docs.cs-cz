---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738737"
---
# <a name="resolver"></a><span data-ttu-id="d383f-101">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="d383f-101">\<resolver></span></span>
<span data-ttu-id="d383f-102">Určuje rovnocenný překladač, který se používá k překladu ID partnerské sítě na sadu adres partnerských uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="d383f-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="d383f-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d383f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d383f-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d383f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d383f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d383f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d383f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d383f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="d383f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="d383f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d383f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<překladač >**</span><span class="sxs-lookup"><span data-stu-id="d383f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d383f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d383f-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d383f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d383f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d383f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d383f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d383f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d383f-112">Attributes</span></span>  
  
|<span data-ttu-id="d383f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d383f-113">Attribute</span></span>|<span data-ttu-id="d383f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d383f-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d383f-115">Řetězec určující, zda je instance překladače partnerského vztahu přidružená k této službě buď specifická pro protokol PNRP, vlastního Překladači nebo automaticky určena.</span><span class="sxs-lookup"><span data-stu-id="d383f-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="d383f-116">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="d383f-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="d383f-117">Řetězec, který určuje způsob, jakým jsou odkazy sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="d383f-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="d383f-118">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="d383f-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d383f-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d383f-119">Child Elements</span></span>  
  
|<span data-ttu-id="d383f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d383f-120">Element</span></span>|<span data-ttu-id="d383f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d383f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d383f-122">\<hlaviček ></span><span class="sxs-lookup"><span data-stu-id="d383f-122">\<headers></span></span>](headers.md)|<span data-ttu-id="d383f-123">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="d383f-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d383f-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d383f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d383f-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="d383f-125">Element</span></span>|<span data-ttu-id="d383f-126">Popis</span><span class="sxs-lookup"><span data-stu-id="d383f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d383f-127">vazba \<</span><span class="sxs-lookup"><span data-stu-id="d383f-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="d383f-128">Definuje všechny schopnosti vazby [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d383f-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d383f-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d383f-129">Remarks</span></span>  
 <span data-ttu-id="d383f-130">Překladač názvů partnerů je služba zjišťování, kterou používají rovnocenné kanály k nalezení partnerských uzlů, které se účastní sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="d383f-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="d383f-131">Používá se také k registraci uzlu se sdílenou sítí, mechanizmus, který je partnerský uzel známý a dostupný z partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="d383f-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="d383f-132">Další informace o překladačích peer-to najdete v tématu věnovaném [překladačům](../../../wcf/feature-details/peer-resolvers.md)peer.</span><span class="sxs-lookup"><span data-stu-id="d383f-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d383f-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d383f-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="d383f-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="d383f-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="d383f-135">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d383f-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
