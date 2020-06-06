---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738737"
---
# \<resolver>
<span data-ttu-id="d8aaf-101">Určuje rovnocenný překladač, který se používá k překladu ID partnerské sítě na sadu adres partnerských uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="d8aaf-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8aaf-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8aaf-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8aaf-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d8aaf-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8aaf-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8aaf-105">Attributes</span></span>  
  
|<span data-ttu-id="d8aaf-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="d8aaf-106">Attribute</span></span>|<span data-ttu-id="d8aaf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d8aaf-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d8aaf-108">Řetězec určující, zda je instance překladače partnerského vztahu přidružená k této službě buď specifická pro protokol PNRP, vlastního Překladači nebo automaticky určena.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="d8aaf-109">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .</span><span class="sxs-lookup"><span data-stu-id="d8aaf-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="d8aaf-110">Řetězec, který určuje způsob, jakým jsou odkazy sdíleny mezi partnery.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="d8aaf-111">Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .</span><span class="sxs-lookup"><span data-stu-id="d8aaf-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8aaf-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8aaf-112">Child Elements</span></span>  
  
|<span data-ttu-id="d8aaf-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8aaf-113">Element</span></span>|<span data-ttu-id="d8aaf-114">Description</span><span class="sxs-lookup"><span data-stu-id="d8aaf-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="d8aaf-115">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8aaf-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8aaf-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d8aaf-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8aaf-117">Element</span></span>|<span data-ttu-id="d8aaf-118">Description</span><span class="sxs-lookup"><span data-stu-id="d8aaf-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d8aaf-119">Definuje všechny schopnosti vazby pro [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d8aaf-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8aaf-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8aaf-120">Remarks</span></span>  
 <span data-ttu-id="d8aaf-121">Překladač názvů partnerů je služba zjišťování, kterou používají rovnocenné kanály k nalezení partnerských uzlů, které se účastní sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="d8aaf-122">Používá se také k registraci uzlu se sdílenou sítí, mechanizmus, který je partnerský uzel známý a dostupný z partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="d8aaf-123">Další informace o překladačích peer-to najdete v tématu věnovaném [překladačům](../../../wcf/feature-details/peer-resolvers.md)peer.</span><span class="sxs-lookup"><span data-stu-id="d8aaf-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8aaf-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8aaf-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="d8aaf-125">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="d8aaf-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="d8aaf-126">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d8aaf-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
