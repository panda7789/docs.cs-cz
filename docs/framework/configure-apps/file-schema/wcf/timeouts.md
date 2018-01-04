---
title: "&lt;časové limity&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04003584cf12355116d32cccffdcb2b9990b1b85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="4310e-102">&lt;časové limity&gt;</span><span class="sxs-lookup"><span data-stu-id="4310e-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="4310e-103">Představuje konfiguraci element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.</span><span class="sxs-lookup"><span data-stu-id="4310e-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="4310e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4310e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4310e-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="4310e-105">\<client></span></span>  
<span data-ttu-id="4310e-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="4310e-106">\<endpoint></span></span>  
<span data-ttu-id="4310e-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="4310e-107">\<host></span></span>  
<span data-ttu-id="4310e-108">\<časové limity ></span><span class="sxs-lookup"><span data-stu-id="4310e-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4310e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4310e-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4310e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4310e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4310e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4310e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4310e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4310e-112">Attributes</span></span>  
  
|<span data-ttu-id="4310e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4310e-113">Attribute</span></span>|<span data-ttu-id="4310e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4310e-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4310e-115">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby zavřete povolená.</span><span class="sxs-lookup"><span data-stu-id="4310e-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="4310e-116">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby otevřete povolená.</span><span class="sxs-lookup"><span data-stu-id="4310e-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4310e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4310e-117">Child Elements</span></span>  
 <span data-ttu-id="4310e-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4310e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4310e-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4310e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4310e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4310e-120">Element</span></span>|<span data-ttu-id="4310e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4310e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4310e-122">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="4310e-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="4310e-123">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4310e-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4310e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4310e-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="4310e-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="4310e-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
