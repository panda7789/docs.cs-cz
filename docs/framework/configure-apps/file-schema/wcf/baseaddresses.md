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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69a049e1daacce901685050ab9fbe99a9c4d3428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="78bdb-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="78bdb-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="78bdb-103">Představuje kolekci `baseAddress` elementy, které jsou základní adresy pro hostitele služby v prostředí s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="78bdb-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="78bdb-104">Pokud základní adresa je k dispozici, může být koncové body nakonfigurované adresy relativně k základní adresu.</span><span class="sxs-lookup"><span data-stu-id="78bdb-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="78bdb-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="78bdb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="78bdb-106">\<klient ></span><span class="sxs-lookup"><span data-stu-id="78bdb-106">\<client></span></span>  
<span data-ttu-id="78bdb-107">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="78bdb-107">\<endpoint></span></span>  
<span data-ttu-id="78bdb-108">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="78bdb-108">\<host></span></span>  
<span data-ttu-id="78bdb-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="78bdb-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bdb-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78bdb-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="78bdb-111">Typ</span><span class="sxs-lookup"><span data-stu-id="78bdb-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78bdb-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78bdb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="78bdb-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78bdb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78bdb-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="78bdb-114">Attributes</span></span>  
 <span data-ttu-id="78bdb-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="78bdb-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78bdb-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78bdb-116">Child Elements</span></span>  
  
|<span data-ttu-id="78bdb-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="78bdb-117">Element</span></span>|<span data-ttu-id="78bdb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="78bdb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78bdb-119">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="78bdb-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="78bdb-120">Konfigurace element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="78bdb-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78bdb-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78bdb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="78bdb-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="78bdb-122">Element</span></span>|<span data-ttu-id="78bdb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="78bdb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78bdb-124">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="78bdb-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="78bdb-125">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="78bdb-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78bdb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="78bdb-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="78bdb-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="78bdb-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
