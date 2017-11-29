---
title: "&lt;vlastní&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="32f50-102">&lt;vlastní&gt;</span><span class="sxs-lookup"><span data-stu-id="32f50-102">&lt;custom&gt;</span></span>
<span data-ttu-id="32f50-103">Určuje nastavení pro vlastní sdílené služby překladač.</span><span class="sxs-lookup"><span data-stu-id="32f50-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="32f50-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="32f50-104">\<system.serviceModel></span></span>  
<span data-ttu-id="32f50-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="32f50-105">\<bindings></span></span>  
<span data-ttu-id="32f50-106">\<netpeerbinding – ></span><span class="sxs-lookup"><span data-stu-id="32f50-106">\<netPeerBinding></span></span>  
<span data-ttu-id="32f50-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="32f50-107">\<binding></span></span>  
<span data-ttu-id="32f50-108">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="32f50-108">\<resolver></span></span>  
<span data-ttu-id="32f50-109">\<vlastní ></span><span class="sxs-lookup"><span data-stu-id="32f50-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f50-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32f50-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32f50-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32f50-111">Attributes and Elements</span></span>  
 <span data-ttu-id="32f50-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32f50-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32f50-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="32f50-113">Attributes</span></span>  
  
|<span data-ttu-id="32f50-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="32f50-114">Attribute</span></span>|<span data-ttu-id="32f50-115">Popis</span><span class="sxs-lookup"><span data-stu-id="32f50-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="32f50-116">Identifikátor URI, který určuje adresa koncového bodu sdílené uzlu, který je hostitelem služby vlastní sdílené překladač.</span><span class="sxs-lookup"><span data-stu-id="32f50-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="32f50-117">Řetězec, který určuje typ služby překladač vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="32f50-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32f50-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32f50-118">Child Elements</span></span>  
  
|<span data-ttu-id="32f50-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="32f50-119">Element</span></span>|<span data-ttu-id="32f50-120">Popis</span><span class="sxs-lookup"><span data-stu-id="32f50-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32f50-121">\<identity ></span><span class="sxs-lookup"><span data-stu-id="32f50-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="32f50-122">Určuje identitu pro vlastní sdílené překladače nakonfigurovaný s tímto elementem.</span><span class="sxs-lookup"><span data-stu-id="32f50-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="32f50-123">Tento element je typu <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="32f50-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="32f50-124">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="32f50-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="32f50-125">Kolekce adres hlavičky SOAP pro zprávy zpracovávaných překladač vlastní sdílené.</span><span class="sxs-lookup"><span data-stu-id="32f50-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32f50-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32f50-126">Parent Elements</span></span>  
  
|<span data-ttu-id="32f50-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="32f50-127">Element</span></span>|<span data-ttu-id="32f50-128">Popis</span><span class="sxs-lookup"><span data-stu-id="32f50-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32f50-129">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="32f50-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="32f50-130">Překladač partnera, který se používá k překladu sdílené OK ID pro sadu adres partnerských uzlů, která představuje několik uzlů, které jsou součástí OK.</span><span class="sxs-lookup"><span data-stu-id="32f50-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32f50-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32f50-131">Remarks</span></span>  
 <span data-ttu-id="32f50-132">Tento element definuje základního nastavení pro vlastní sdílené překladač služby, včetně adresa koncového bodu partnerského uzlu hostování služby a nastavení konkrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="32f50-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="32f50-133">Další informace o vytvoření vlastní překladač najdete v tématu [přidání vlastní překladač do aplikace PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="32f50-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f50-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="32f50-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="32f50-135">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="32f50-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="32f50-136">Přidání vlastní překladač do PeerChannel aplikace</span><span class="sxs-lookup"><span data-stu-id="32f50-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
