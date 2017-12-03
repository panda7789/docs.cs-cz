---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 028681acffcd93633807bdb1c6fa78aab98011c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="431b4-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="431b4-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="431b4-103">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv, když odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="431b4-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="431b4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="431b4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="431b4-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="431b4-105">\<routing></span></span>  
<span data-ttu-id="431b4-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="431b4-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431b4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431b4-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="431b4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="431b4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="431b4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="431b4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="431b4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="431b4-110">Attributes</span></span>  
 <span data-ttu-id="431b4-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="431b4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="431b4-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="431b4-112">Child Elements</span></span>  
  
|<span data-ttu-id="431b4-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="431b4-113">Element</span></span>|<span data-ttu-id="431b4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="431b4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="431b4-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="431b4-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="431b4-116">Směrovací tabulky, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="431b4-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="431b4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="431b4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="431b4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="431b4-118">Element</span></span>|<span data-ttu-id="431b4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="431b4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="431b4-120">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="431b4-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="431b4-121">Konfigurační oddíl, který obsahuje filtrech směrování a směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="431b4-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="431b4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="431b4-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
