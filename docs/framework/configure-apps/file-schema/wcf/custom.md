---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400456"
---
# <a name="custom"></a><span data-ttu-id="82c9d-101">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="82c9d-101">\<custom></span></span>
<span data-ttu-id="82c9d-102">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="82c9d-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="82c9d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="82c9d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="82c9d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="82c9d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="82c9d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="82c9d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="82c9d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="82c9d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="82c9d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="82c9d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="82c9d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> překladače**](resolver.md)</span><span class="sxs-lookup"><span data-stu-id="82c9d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)</span></span>\
<span data-ttu-id="82c9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vlastní >**</span><span class="sxs-lookup"><span data-stu-id="82c9d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c9d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82c9d-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82c9d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82c9d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="82c9d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82c9d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82c9d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="82c9d-113">Attributes</span></span>  
  
|<span data-ttu-id="82c9d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="82c9d-114">Attribute</span></span>|<span data-ttu-id="82c9d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="82c9d-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="82c9d-116">Identifikátor URI, který určuje adresu koncového bodu partnerského uzlu, který hostuje službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="82c9d-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="82c9d-117">Řetězec, který určuje typ služby Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="82c9d-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82c9d-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82c9d-118">Child Elements</span></span>  
  
|<span data-ttu-id="82c9d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="82c9d-119">Element</span></span>|<span data-ttu-id="82c9d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="82c9d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82c9d-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="82c9d-121">\<identity></span></span>](identity.md)|<span data-ttu-id="82c9d-122">Určuje identitu pro vlastní překladače rovnocenných uzlů nakonfigurované s tímto elementem.</span><span class="sxs-lookup"><span data-stu-id="82c9d-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="82c9d-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="82c9d-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="82c9d-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="82c9d-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="82c9d-125">Kolekce záhlaví adresy používané pro zprávy SOAP, které jsou zpracovávány vlastním překladačem peer.</span><span class="sxs-lookup"><span data-stu-id="82c9d-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82c9d-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82c9d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="82c9d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="82c9d-127">Element</span></span>|<span data-ttu-id="82c9d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="82c9d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82c9d-129">\<resolver></span><span class="sxs-lookup"><span data-stu-id="82c9d-129">\<resolver></span></span>](resolver.md)|<span data-ttu-id="82c9d-130">Peer resolver, který se používá k překladu ID partnerské sítě na sadu adres rovnocenných uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="82c9d-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82c9d-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82c9d-131">Remarks</span></span>  
 <span data-ttu-id="82c9d-132">Tento prvek definuje základní nastavení pro službu Custom peer resolver Service, včetně adresy koncového bodu partnerského zařízení, který hostuje službu, a všech specifických nastavení vazby.</span><span class="sxs-lookup"><span data-stu-id="82c9d-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="82c9d-133">Další informace o vytvoření vlastního překladače najdete v tématu [Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="82c9d-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c9d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82c9d-134">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="82c9d-135">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="82c9d-135">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="82c9d-136">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="82c9d-136">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
