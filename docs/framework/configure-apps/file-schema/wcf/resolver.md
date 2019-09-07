---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: fb974492dee6b2a4244cedc06e3f5e40334dd02a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399986"
---
# <a name="resolver"></a><span data-ttu-id="5cf44-101">\<> překladače</span><span class="sxs-lookup"><span data-stu-id="5cf44-101">\<resolver></span></span>
<span data-ttu-id="5cf44-102">Určuje rovnocenný překladač, který se používá k překladu ID partnerské sítě na sadu adres partnerských uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="5cf44-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="5cf44-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cf44-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5cf44-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5cf44-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5cf44-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5cf44-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5cf44-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5cf44-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="5cf44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="5cf44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5cf44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> překladače**</span><span class="sxs-lookup"><span data-stu-id="5cf44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf44-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cf44-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cf44-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5cf44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5cf44-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5cf44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cf44-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5cf44-112">Attributes</span></span>  
  
|<span data-ttu-id="5cf44-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5cf44-113">Attribute</span></span>|<span data-ttu-id="5cf44-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5cf44-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="5cf44-115">Řetězec určující, zda je instance překladače partnerského vztahu přidružená k této službě buď specifická pro protokol PNRP, vlastního Překladači nebo automaticky určena.</span><span class="sxs-lookup"><span data-stu-id="5cf44-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="5cf44-116">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="5cf44-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="5cf44-117">Řetězec, který určuje způsob, jakým jsou odkazy sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="5cf44-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="5cf44-118">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="5cf44-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cf44-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5cf44-119">Child Elements</span></span>  
  
|<span data-ttu-id="5cf44-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="5cf44-120">Element</span></span>|<span data-ttu-id="5cf44-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5cf44-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cf44-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="5cf44-122">\<headers></span></span>](headers.md)|<span data-ttu-id="5cf44-123">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="5cf44-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5cf44-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5cf44-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5cf44-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5cf44-125">Element</span></span>|<span data-ttu-id="5cf44-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5cf44-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cf44-127">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5cf44-127">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5cf44-128">Definuje všechny schopnosti [ \<vazby NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5cf44-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cf44-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cf44-129">Remarks</span></span>  
 <span data-ttu-id="5cf44-130">Překladač názvů partnerů je služba zjišťování, kterou používají rovnocenné kanály k nalezení partnerských uzlů, které se účastní sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="5cf44-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="5cf44-131">Používá se také k registraci uzlu se sdílenou sítí, mechanizmus, který je partnerský uzel známý a dostupný z partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="5cf44-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="5cf44-132">Další informace o překladačích peer-to najdete v tématu věnovaném [překladačům](../../../wcf/feature-details/peer-resolvers.md)peer.</span><span class="sxs-lookup"><span data-stu-id="5cf44-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf44-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cf44-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="5cf44-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="5cf44-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="5cf44-135">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5cf44-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
