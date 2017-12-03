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
ms.openlocfilehash: bfe66b499eb50a058ed8b6a46769893f6dc5fd6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="981e6-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="981e6-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="981e6-103">Představuje kolekci `baseAddress` elementy, které jsou základní adresy pro hostitele služby v prostředí s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="981e6-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="981e6-104">Pokud základní adresa je k dispozici, může být koncové body nakonfigurované adresy relativně k základní adresu.</span><span class="sxs-lookup"><span data-stu-id="981e6-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="981e6-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="981e6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="981e6-106">\<klient ></span><span class="sxs-lookup"><span data-stu-id="981e6-106">\<client></span></span>  
<span data-ttu-id="981e6-107">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="981e6-107">\<endpoint></span></span>  
<span data-ttu-id="981e6-108">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="981e6-108">\<host></span></span>  
<span data-ttu-id="981e6-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="981e6-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981e6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="981e6-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="981e6-111">Typ</span><span class="sxs-lookup"><span data-stu-id="981e6-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="981e6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="981e6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="981e6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="981e6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="981e6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="981e6-114">Attributes</span></span>  
 <span data-ttu-id="981e6-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="981e6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="981e6-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="981e6-116">Child Elements</span></span>  
  
|<span data-ttu-id="981e6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="981e6-117">Element</span></span>|<span data-ttu-id="981e6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="981e6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="981e6-119">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="981e6-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="981e6-120">Konfigurace element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="981e6-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="981e6-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="981e6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="981e6-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="981e6-122">Element</span></span>|<span data-ttu-id="981e6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="981e6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="981e6-124">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="981e6-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="981e6-125">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="981e6-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="981e6-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="981e6-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="981e6-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="981e6-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
