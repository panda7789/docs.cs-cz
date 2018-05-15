---
title: '&lt;add&gt; – &lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="43bba-102">&lt;add&gt; – &lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="43bba-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="43bba-103">Představuje směrování položku, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr.</span><span class="sxs-lookup"><span data-stu-id="43bba-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="43bba-104">Zprávy odpovídajících tomuto filtru budou odeslány do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="43bba-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="43bba-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="43bba-105">\<system.serviceModel></span></span>  
<span data-ttu-id="43bba-106">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="43bba-106">\<routing></span></span>  
<span data-ttu-id="43bba-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="43bba-107">\<routingTables></span></span>  
<span data-ttu-id="43bba-108">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="43bba-108">\<table></span></span>  
<span data-ttu-id="43bba-109">\<položky ></span><span class="sxs-lookup"><span data-stu-id="43bba-109">\<entries></span></span>  
<span data-ttu-id="43bba-110">\<add></span><span class="sxs-lookup"><span data-stu-id="43bba-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bba-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43bba-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43bba-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43bba-112">Attributes and Elements</span></span>  
 <span data-ttu-id="43bba-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43bba-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43bba-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="43bba-114">Attributes</span></span>  
  
|<span data-ttu-id="43bba-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="43bba-115">Attribute</span></span>|<span data-ttu-id="43bba-116">Popis</span><span class="sxs-lookup"><span data-stu-id="43bba-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43bba-117">backupList</span><span class="sxs-lookup"><span data-stu-id="43bba-117">backupList</span></span>|<span data-ttu-id="43bba-118">Řetězec, který určuje odkaz na zálohování seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="43bba-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="43bba-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="43bba-119">endpoint</span></span>|<span data-ttu-id="43bba-120">Řetězec, který určuje odkaz na koncový bod klienta, která bude přijímat zprávy, které odpovídají filtru určeného `filterName` atribut.</span><span class="sxs-lookup"><span data-stu-id="43bba-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="43bba-121">filterName</span><span class="sxs-lookup"><span data-stu-id="43bba-121">filterName</span></span>|<span data-ttu-id="43bba-122">Řetězec, který určuje odkaz na element filtru.</span><span class="sxs-lookup"><span data-stu-id="43bba-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="43bba-123">Priorita</span><span class="sxs-lookup"><span data-stu-id="43bba-123">priority</span></span>|<span data-ttu-id="43bba-124">Celé číslo, které určuje prioritu této položky.</span><span class="sxs-lookup"><span data-stu-id="43bba-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="43bba-125">Položky v tabulce směrování se vyhodnotí na základě priority, se 0 znamená nejnižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="43bba-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="43bba-126">Všechny záznamy pro určitou prioritou vyhodnocují současně, pokud neexistuje odpovídající položka je nalezena pro aktuální prioritu, se vyhodnotí další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="43bba-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="43bba-127">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="43bba-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43bba-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43bba-128">Child Elements</span></span>  
 <span data-ttu-id="43bba-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="43bba-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43bba-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43bba-130">Parent Elements</span></span>  
  
|<span data-ttu-id="43bba-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="43bba-131">Element</span></span>|<span data-ttu-id="43bba-132">Popis</span><span class="sxs-lookup"><span data-stu-id="43bba-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43bba-133">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="43bba-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="43bba-134">Konfigurační oddíl, který obsahuje položky směrování mapování.</span><span class="sxs-lookup"><span data-stu-id="43bba-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43bba-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="43bba-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
