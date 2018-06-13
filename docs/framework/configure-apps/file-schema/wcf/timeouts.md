---
title: '&lt;časové limity&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752998"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="1c9d3-102">&lt;časové limity&gt;</span><span class="sxs-lookup"><span data-stu-id="1c9d3-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="1c9d3-103">Představuje konfiguraci element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.</span><span class="sxs-lookup"><span data-stu-id="1c9d3-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="1c9d3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1c9d3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c9d3-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="1c9d3-105">\<client></span></span>  
<span data-ttu-id="1c9d3-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="1c9d3-106">\<endpoint></span></span>  
<span data-ttu-id="1c9d3-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="1c9d3-107">\<host></span></span>  
<span data-ttu-id="1c9d3-108">\<časové limity ></span><span class="sxs-lookup"><span data-stu-id="1c9d3-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9d3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c9d3-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c9d3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c9d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1c9d3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c9d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c9d3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c9d3-112">Attributes</span></span>  
  
|<span data-ttu-id="1c9d3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c9d3-113">Attribute</span></span>|<span data-ttu-id="1c9d3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1c9d3-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1c9d3-115">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby zavřete povolená.</span><span class="sxs-lookup"><span data-stu-id="1c9d3-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="1c9d3-116">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro hostitele služby otevřete povolená.</span><span class="sxs-lookup"><span data-stu-id="1c9d3-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c9d3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c9d3-117">Child Elements</span></span>  
 <span data-ttu-id="1c9d3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1c9d3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c9d3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c9d3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1c9d3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c9d3-120">Element</span></span>|<span data-ttu-id="1c9d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1c9d3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c9d3-122">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="1c9d3-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="1c9d3-123">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="1c9d3-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c9d3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c9d3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="1c9d3-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="1c9d3-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
