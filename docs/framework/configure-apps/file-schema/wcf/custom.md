---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925954"
---
# <a name="custom"></a><span data-ttu-id="27fcd-101">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="27fcd-101">\<custom></span></span>
<span data-ttu-id="27fcd-102">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="27fcd-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="27fcd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="27fcd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="27fcd-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="27fcd-104">\<bindings></span></span>  
<span data-ttu-id="27fcd-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="27fcd-105">\<netPeerBinding></span></span>  
<span data-ttu-id="27fcd-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="27fcd-106">\<binding></span></span>  
<span data-ttu-id="27fcd-107">\<> překladače</span><span class="sxs-lookup"><span data-stu-id="27fcd-107">\<resolver></span></span>  
<span data-ttu-id="27fcd-108">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="27fcd-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fcd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27fcd-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27fcd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27fcd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27fcd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27fcd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27fcd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="27fcd-112">Attributes</span></span>  
  
|<span data-ttu-id="27fcd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="27fcd-113">Attribute</span></span>|<span data-ttu-id="27fcd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="27fcd-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="27fcd-115">Identifikátor URI, který určuje adresu koncového bodu partnerského uzlu, který hostuje službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="27fcd-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="27fcd-116">Řetězec, který určuje typ služby Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="27fcd-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27fcd-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27fcd-117">Child Elements</span></span>  
  
|<span data-ttu-id="27fcd-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="27fcd-118">Element</span></span>|<span data-ttu-id="27fcd-119">Popis</span><span class="sxs-lookup"><span data-stu-id="27fcd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27fcd-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="27fcd-120">\<identity></span></span>](identity.md)|<span data-ttu-id="27fcd-121">Určuje identitu pro vlastní překladače rovnocenných uzlů nakonfigurované s tímto elementem.</span><span class="sxs-lookup"><span data-stu-id="27fcd-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="27fcd-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="27fcd-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="27fcd-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="27fcd-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="27fcd-124">Kolekce záhlaví adresy používané pro zprávy SOAP, které jsou zpracovávány vlastním překladačem peer.</span><span class="sxs-lookup"><span data-stu-id="27fcd-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27fcd-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27fcd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="27fcd-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="27fcd-126">Element</span></span>|<span data-ttu-id="27fcd-127">Popis</span><span class="sxs-lookup"><span data-stu-id="27fcd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27fcd-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="27fcd-128">\<resolver></span></span>](resolver.md)|<span data-ttu-id="27fcd-129">Peer resolver, který se používá k překladu ID partnerské sítě na sadu adres rovnocenných uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="27fcd-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27fcd-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27fcd-130">Remarks</span></span>  
 <span data-ttu-id="27fcd-131">Tento prvek definuje základní nastavení pro službu Custom peer resolver Service, včetně adresy koncového bodu partnerského zařízení, který hostuje službu, a všech specifických nastavení vazby.</span><span class="sxs-lookup"><span data-stu-id="27fcd-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="27fcd-132">Další informace o vytvoření vlastního překladače najdete v tématu [Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="27fcd-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fcd-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27fcd-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="27fcd-134">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="27fcd-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="27fcd-135">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="27fcd-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
