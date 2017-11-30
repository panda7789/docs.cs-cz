---
title: "&lt;add&gt; – &lt;entries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="144cb-102">&lt;add&gt; – &lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="144cb-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="144cb-103">Představuje směrování položku, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr.</span><span class="sxs-lookup"><span data-stu-id="144cb-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="144cb-104">Zprávy odpovídajících tomuto filtru budou odeslány do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="144cb-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="144cb-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="144cb-105">\<system.serviceModel></span></span>  
<span data-ttu-id="144cb-106">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="144cb-106">\<routing></span></span>  
<span data-ttu-id="144cb-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="144cb-107">\<routingTables></span></span>  
<span data-ttu-id="144cb-108">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="144cb-108">\<table></span></span>  
<span data-ttu-id="144cb-109">\<položky ></span><span class="sxs-lookup"><span data-stu-id="144cb-109">\<entries></span></span>  
<span data-ttu-id="144cb-110">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="144cb-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144cb-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="144cb-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="144cb-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="144cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="144cb-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="144cb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="144cb-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="144cb-114">Attributes</span></span>  
  
|<span data-ttu-id="144cb-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="144cb-115">Attribute</span></span>|<span data-ttu-id="144cb-116">Popis</span><span class="sxs-lookup"><span data-stu-id="144cb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="144cb-117">backupList</span><span class="sxs-lookup"><span data-stu-id="144cb-117">backupList</span></span>|<span data-ttu-id="144cb-118">Řetězec, který určuje odkaz na zálohování seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="144cb-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="144cb-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="144cb-119">endpoint</span></span>|<span data-ttu-id="144cb-120">Řetězec, který určuje odkaz na koncový bod klienta, která bude přijímat zprávy, které odpovídají filtru určeného `filterName` atribut.</span><span class="sxs-lookup"><span data-stu-id="144cb-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="144cb-121">filterName</span><span class="sxs-lookup"><span data-stu-id="144cb-121">filterName</span></span>|<span data-ttu-id="144cb-122">Řetězec, který určuje odkaz na element filtru.</span><span class="sxs-lookup"><span data-stu-id="144cb-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="144cb-123">Priorita</span><span class="sxs-lookup"><span data-stu-id="144cb-123">priority</span></span>|<span data-ttu-id="144cb-124">Celé číslo, které určuje prioritu této položky.</span><span class="sxs-lookup"><span data-stu-id="144cb-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="144cb-125">Položky v tabulce směrování se vyhodnotí na základě priority, se 0 znamená nejnižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="144cb-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="144cb-126">Všechny záznamy pro určitou prioritou vyhodnocují současně, pokud neexistuje odpovídající položka je nalezena pro aktuální prioritu, se vyhodnotí další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="144cb-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="144cb-127">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="144cb-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="144cb-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="144cb-128">Child Elements</span></span>  
 <span data-ttu-id="144cb-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="144cb-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="144cb-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="144cb-130">Parent Elements</span></span>  
  
|<span data-ttu-id="144cb-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="144cb-131">Element</span></span>|<span data-ttu-id="144cb-132">Popis</span><span class="sxs-lookup"><span data-stu-id="144cb-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="144cb-133">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="144cb-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="144cb-134">Konfigurační oddíl, který obsahuje položky směrování mapování.</span><span class="sxs-lookup"><span data-stu-id="144cb-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="144cb-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="144cb-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
