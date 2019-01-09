---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 1978c898039a6ff9ab3303427951c214cde96e24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145746"
---
# <a name="ltcustomgt"></a><span data-ttu-id="1ed40-102">&lt;custom&gt;</span><span class="sxs-lookup"><span data-stu-id="1ed40-102">&lt;custom&gt;</span></span>
<span data-ttu-id="1ed40-103">Určuje nastavení pro službu překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="1ed40-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="1ed40-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ed40-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1ed40-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1ed40-105">\<bindings></span></span>  
<span data-ttu-id="1ed40-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="1ed40-106">\<netPeerBinding></span></span>  
<span data-ttu-id="1ed40-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1ed40-107">\<binding></span></span>  
<span data-ttu-id="1ed40-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="1ed40-108">\<resolver></span></span>  
<span data-ttu-id="1ed40-109">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="1ed40-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed40-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ed40-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ed40-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ed40-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1ed40-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ed40-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ed40-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ed40-113">Attributes</span></span>  
  
|<span data-ttu-id="1ed40-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ed40-114">Attribute</span></span>|<span data-ttu-id="1ed40-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1ed40-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="1ed40-116">Identifikátor URI, který určuje adresu partnerského uzlu, který je hostitelem služby překladače vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="1ed40-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="1ed40-117">Řetězec, který určuje typ překladače vlastní sdílené služby.</span><span class="sxs-lookup"><span data-stu-id="1ed40-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ed40-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ed40-118">Child Elements</span></span>  
  
|<span data-ttu-id="1ed40-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ed40-119">Element</span></span>|<span data-ttu-id="1ed40-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1ed40-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ed40-121">\<identity ></span><span class="sxs-lookup"><span data-stu-id="1ed40-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1ed40-122">Určuje identitu pro nakonfigurovaný s tímto elementem překladače vlastní partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="1ed40-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="1ed40-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="1ed40-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="1ed40-124">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="1ed40-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="1ed40-125">Kolekce záhlaví adres, který slouží pro zprávy protokolu SOAP zpracovat rozpoznávání vlastní druhé strany.</span><span class="sxs-lookup"><span data-stu-id="1ed40-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ed40-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ed40-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1ed40-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ed40-127">Element</span></span>|<span data-ttu-id="1ed40-128">Popis</span><span class="sxs-lookup"><span data-stu-id="1ed40-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ed40-129">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="1ed40-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="1ed40-130">Mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.</span><span class="sxs-lookup"><span data-stu-id="1ed40-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ed40-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ed40-131">Remarks</span></span>  
 <span data-ttu-id="1ed40-132">Tento prvek definuje základního nastavení pro vlastní sdílené překladač služby, včetně koncového bodu adresy partnerského uzlu hostování služby a nastavení konkrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="1ed40-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="1ed40-133">Další informace o vytvoření vlastní mechanismus rozpoznávání najdete v tématu [přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="1ed40-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed40-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ed40-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="1ed40-135">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="1ed40-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="1ed40-136">Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci</span><span class="sxs-lookup"><span data-stu-id="1ed40-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
