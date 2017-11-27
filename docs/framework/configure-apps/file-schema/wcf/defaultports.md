---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="bf7cc-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="bf7cc-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="bf7cc-103">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="bf7cc-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="bf7cc-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf7cc-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-105">\<behaviors></span></span>  
<span data-ttu-id="bf7cc-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf7cc-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-107">\<behavior></span></span>  
<span data-ttu-id="bf7cc-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="bf7cc-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf7cc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf7cc-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf7cc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf7cc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bf7cc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf7cc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf7cc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf7cc-113">Attributes</span></span>  
 <span data-ttu-id="bf7cc-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf7cc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf7cc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf7cc-115">Child Elements</span></span>  
  
|<span data-ttu-id="bf7cc-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf7cc-116">Element</span></span>|<span data-ttu-id="bf7cc-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bf7cc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf7cc-118">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="bf7cc-119">Koncový bod výchozí komunikace, která klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="bf7cc-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf7cc-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf7cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bf7cc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf7cc-121">Element</span></span>|<span data-ttu-id="bf7cc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bf7cc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf7cc-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="bf7cc-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="bf7cc-124">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="bf7cc-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf7cc-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf7cc-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
