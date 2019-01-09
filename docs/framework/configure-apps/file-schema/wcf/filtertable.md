---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147885"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="1ebf5-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="1ebf5-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="1ebf5-103">Představuje směrovací tabulku, která obsahuje seznam filtrů určených k vyhodnocení zpráv a koncový bod klienta pro směrování zpráv v případě ohodnocení filtru hodnotou true.</span><span class="sxs-lookup"><span data-stu-id="1ebf5-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="1ebf5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ebf5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1ebf5-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="1ebf5-105">\<routing></span></span>  
<span data-ttu-id="1ebf5-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="1ebf5-106">\<routingTables></span></span>  
<span data-ttu-id="1ebf5-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="1ebf5-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebf5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ebf5-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ebf5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ebf5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1ebf5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ebf5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ebf5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ebf5-111">Attributes</span></span>  
  
|<span data-ttu-id="1ebf5-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ebf5-112">Element</span></span>|<span data-ttu-id="1ebf5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1ebf5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ebf5-114">name</span><span class="sxs-lookup"><span data-stu-id="1ebf5-114">name</span></span>|<span data-ttu-id="1ebf5-115">Řetězec obsahující jedinečný název tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="1ebf5-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ebf5-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ebf5-116">Child Elements</span></span>  
  
|<span data-ttu-id="1ebf5-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ebf5-117">Element</span></span>|<span data-ttu-id="1ebf5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1ebf5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ebf5-119">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="1ebf5-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1ebf5-120">Mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="1ebf5-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ebf5-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ebf5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1ebf5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ebf5-122">Element</span></span>|<span data-ttu-id="1ebf5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1ebf5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ebf5-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="1ebf5-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1ebf5-125">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="1ebf5-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ebf5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ebf5-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
