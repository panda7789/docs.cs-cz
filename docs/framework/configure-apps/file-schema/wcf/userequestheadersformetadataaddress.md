---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="53cea-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="53cea-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="53cea-103">Umožňuje načítání informací o adresu metadat ze záhlaví zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="53cea-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="53cea-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="53cea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="53cea-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="53cea-105">\<behaviors></span></span>  
<span data-ttu-id="53cea-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="53cea-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="53cea-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="53cea-107">\<behavior></span></span>  
<span data-ttu-id="53cea-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="53cea-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53cea-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53cea-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53cea-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53cea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="53cea-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53cea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53cea-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="53cea-112">Attributes</span></span>  
 <span data-ttu-id="53cea-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="53cea-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="53cea-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53cea-114">Child Elements</span></span>  
  
|<span data-ttu-id="53cea-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="53cea-115">Element</span></span>|<span data-ttu-id="53cea-116">Popis</span><span class="sxs-lookup"><span data-stu-id="53cea-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53cea-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="53cea-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="53cea-118">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="53cea-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53cea-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53cea-119">Parent Elements</span></span>  
  
|<span data-ttu-id="53cea-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="53cea-120">Element</span></span>|<span data-ttu-id="53cea-121">Popis</span><span class="sxs-lookup"><span data-stu-id="53cea-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53cea-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="53cea-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="53cea-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="53cea-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53cea-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="53cea-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
