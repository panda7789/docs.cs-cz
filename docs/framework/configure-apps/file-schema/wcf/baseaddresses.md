---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bf698b64b528b0ea109223a2d94e6725c8ce6b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="0fdbe-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="0fdbe-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="0fdbe-103">Představuje kolekci `baseAddress` elementy, které jsou základní adresy pro hostitele služby v prostředí s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="0fdbe-104">Pokud základní adresa je k dispozici, může být koncové body nakonfigurované adresy relativně k základní adresu.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="0fdbe-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fdbe-106">\<klient ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-106">\<client></span></span>  
<span data-ttu-id="0fdbe-107">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-107">\<endpoint></span></span>  
<span data-ttu-id="0fdbe-108">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-108">\<host></span></span>  
<span data-ttu-id="0fdbe-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fdbe-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fdbe-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="0fdbe-111">Typ</span><span class="sxs-lookup"><span data-stu-id="0fdbe-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fdbe-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fdbe-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0fdbe-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fdbe-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fdbe-114">Attributes</span></span>  
 <span data-ttu-id="0fdbe-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fdbe-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fdbe-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fdbe-116">Child Elements</span></span>  
  
|<span data-ttu-id="0fdbe-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fdbe-117">Element</span></span>|<span data-ttu-id="0fdbe-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0fdbe-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fdbe-119">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="0fdbe-120">Konfigurace element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fdbe-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fdbe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0fdbe-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fdbe-122">Element</span></span>|<span data-ttu-id="0fdbe-123">Popis</span><span class="sxs-lookup"><span data-stu-id="0fdbe-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fdbe-124">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="0fdbe-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="0fdbe-125">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="0fdbe-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fdbe-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fdbe-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="0fdbe-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="0fdbe-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
