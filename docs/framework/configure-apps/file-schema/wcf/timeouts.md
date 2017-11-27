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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="65798-102">&lt;časové limity&gt;</span><span class="sxs-lookup"><span data-stu-id="65798-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="65798-103">Představuje konfiguraci element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.</span><span class="sxs-lookup"><span data-stu-id="65798-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="65798-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="65798-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65798-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="65798-105">\<client></span></span>  
<span data-ttu-id="65798-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="65798-106">\<endpoint></span></span>  
<span data-ttu-id="65798-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="65798-107">\<host></span></span>  
<span data-ttu-id="65798-108">\<časové limity ></span><span class="sxs-lookup"><span data-stu-id="65798-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65798-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65798-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65798-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65798-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65798-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65798-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65798-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="65798-112">Attributes</span></span>  
  
|<span data-ttu-id="65798-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="65798-113">Attribute</span></span>|<span data-ttu-id="65798-114">Popis</span><span class="sxs-lookup"><span data-stu-id="65798-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="65798-115">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby zavřete povolená.</span><span class="sxs-lookup"><span data-stu-id="65798-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="65798-116">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby otevřete povolená.</span><span class="sxs-lookup"><span data-stu-id="65798-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65798-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65798-117">Child Elements</span></span>  
 <span data-ttu-id="65798-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="65798-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65798-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65798-119">Parent Elements</span></span>  
  
|<span data-ttu-id="65798-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="65798-120">Element</span></span>|<span data-ttu-id="65798-121">Popis</span><span class="sxs-lookup"><span data-stu-id="65798-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65798-122">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="65798-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="65798-123">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="65798-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65798-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="65798-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="65798-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="65798-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
