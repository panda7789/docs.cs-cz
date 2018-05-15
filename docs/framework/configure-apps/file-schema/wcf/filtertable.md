---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="e8424-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="e8424-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="e8424-103">Představuje směrovací tabulku, která obsahuje seznam filtrů vyhodnocení zprávy proti a koncový bod klienta pro směrování zpráv do, pokud filtr se vyhodnotí jako true.</span><span class="sxs-lookup"><span data-stu-id="e8424-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="e8424-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8424-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e8424-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e8424-105">\<routing></span></span>  
<span data-ttu-id="e8424-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="e8424-106">\<routingTables></span></span>  
<span data-ttu-id="e8424-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="e8424-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8424-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8424-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8424-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8424-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8424-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8424-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8424-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8424-111">Attributes</span></span>  
  
|<span data-ttu-id="e8424-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8424-112">Element</span></span>|<span data-ttu-id="e8424-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e8424-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8424-114">name</span><span class="sxs-lookup"><span data-stu-id="e8424-114">name</span></span>|<span data-ttu-id="e8424-115">Řetězec, který obsahuje jedinečný název tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e8424-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8424-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8424-116">Child Elements</span></span>  
  
|<span data-ttu-id="e8424-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8424-117">Element</span></span>|<span data-ttu-id="e8424-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e8424-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8424-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="e8424-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e8424-120">Mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="e8424-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8424-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8424-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e8424-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8424-122">Element</span></span>|<span data-ttu-id="e8424-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e8424-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8424-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e8424-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e8424-125">Konfigurační oddíl, který obsahuje směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="e8424-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8424-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8424-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
