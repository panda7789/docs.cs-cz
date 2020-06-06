---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400456"
---
# \<custom>
<span data-ttu-id="c75b6-101">Určuje nastavení pro službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="c75b6-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="c75b6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c75b6-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c75b6-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c75b6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c75b6-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c75b6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c75b6-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c75b6-105">Attributes</span></span>  
  
|<span data-ttu-id="c75b6-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="c75b6-106">Attribute</span></span>|<span data-ttu-id="c75b6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c75b6-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="c75b6-108">Identifikátor URI, který určuje adresu koncového bodu partnerského uzlu, který hostuje službu Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="c75b6-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="c75b6-109">Řetězec, který určuje typ služby Custom peer resolver Service.</span><span class="sxs-lookup"><span data-stu-id="c75b6-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c75b6-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c75b6-110">Child Elements</span></span>  
  
|<span data-ttu-id="c75b6-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="c75b6-111">Element</span></span>|<span data-ttu-id="c75b6-112">Description</span><span class="sxs-lookup"><span data-stu-id="c75b6-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c75b6-113">Určuje identitu pro vlastní překladače rovnocenných uzlů nakonfigurované s tímto elementem.</span><span class="sxs-lookup"><span data-stu-id="c75b6-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="c75b6-114">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement> .</span><span class="sxs-lookup"><span data-stu-id="c75b6-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c75b6-115">Kolekce záhlaví adresy používané pro zprávy SOAP, které jsou zpracovávány vlastním překladačem peer.</span><span class="sxs-lookup"><span data-stu-id="c75b6-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c75b6-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c75b6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c75b6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c75b6-117">Element</span></span>|<span data-ttu-id="c75b6-118">Description</span><span class="sxs-lookup"><span data-stu-id="c75b6-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="c75b6-119">Peer resolver, který se používá k překladu ID partnerské sítě na sadu adres rovnocenných uzlů, které představují několik uzlů, které se účastní sítě.</span><span class="sxs-lookup"><span data-stu-id="c75b6-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c75b6-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c75b6-120">Remarks</span></span>  
 <span data-ttu-id="c75b6-121">Tento prvek definuje základní nastavení pro službu Custom peer resolver Service, včetně adresy koncového bodu partnerského zařízení, který hostuje službu, a všech specifických nastavení vazby.</span><span class="sxs-lookup"><span data-stu-id="c75b6-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="c75b6-122">Další informace o vytvoření vlastního překladače najdete v tématu [Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c75b6-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75b6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c75b6-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="c75b6-124">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="c75b6-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="c75b6-125">[Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c75b6-125">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
