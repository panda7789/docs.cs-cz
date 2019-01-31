---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264567"
---
# <a name="add-of-entries"></a><span data-ttu-id="e71b2-102">\<Přidat > z \<položky ></span><span class="sxs-lookup"><span data-stu-id="e71b2-102">\<add> of \<entries></span></span>
<span data-ttu-id="e71b2-103">Představuje položku směrování, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr.</span><span class="sxs-lookup"><span data-stu-id="e71b2-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e71b2-104">Tomuto filtru odpovídá zprávy se odešlou do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="e71b2-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="e71b2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e71b2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e71b2-106">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e71b2-106">\<routing></span></span>  
<span data-ttu-id="e71b2-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="e71b2-107">\<filterTables></span></span>  
<span data-ttu-id="e71b2-108">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="e71b2-108">\<filterTable></span></span>  
<span data-ttu-id="e71b2-109">\<položky ></span><span class="sxs-lookup"><span data-stu-id="e71b2-109">\<entries></span></span>  
<span data-ttu-id="e71b2-110">\<add></span><span class="sxs-lookup"><span data-stu-id="e71b2-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71b2-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e71b2-111">Syntax</span></span>  
  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e71b2-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e71b2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e71b2-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e71b2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e71b2-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e71b2-114">Attributes</span></span>  
  
|<span data-ttu-id="e71b2-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="e71b2-115">Attribute</span></span>|<span data-ttu-id="e71b2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e71b2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e71b2-117">backupList</span><span class="sxs-lookup"><span data-stu-id="e71b2-117">backupList</span></span>|<span data-ttu-id="e71b2-118">Řetězec, který určuje referenci na záložní seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e71b2-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="e71b2-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="e71b2-119">endpoint</span></span>|<span data-ttu-id="e71b2-120">Řetězec, který určuje referenci na koncový bod klienta, který bude přijímat zprávy, které odpovídají filtru určeném `filterName` atribut.</span><span class="sxs-lookup"><span data-stu-id="e71b2-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="e71b2-121">filterName</span><span class="sxs-lookup"><span data-stu-id="e71b2-121">filterName</span></span>|<span data-ttu-id="e71b2-122">Řetězec, který určuje odkaz na prvek filtru.</span><span class="sxs-lookup"><span data-stu-id="e71b2-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="e71b2-123">priorita</span><span class="sxs-lookup"><span data-stu-id="e71b2-123">priority</span></span>|<span data-ttu-id="e71b2-124">Celé číslo, které určuje priorita této položky.</span><span class="sxs-lookup"><span data-stu-id="e71b2-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="e71b2-125">Položky v tabulce směrování se vyhodnotí na základě priority, 0 je nejnižší priorita.</span><span class="sxs-lookup"><span data-stu-id="e71b2-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="e71b2-126">Všechny položky s konkrétní prioritou jsou vyhodnocovány současně, pokud neexistuje odpovídající položka nebyl nalezen aktuální priorita, se vyhodnotí na další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="e71b2-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="e71b2-127">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="e71b2-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e71b2-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e71b2-128">Child Elements</span></span>  
 <span data-ttu-id="e71b2-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="e71b2-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e71b2-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e71b2-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e71b2-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="e71b2-131">Element</span></span>|<span data-ttu-id="e71b2-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e71b2-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e71b2-133">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e71b2-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e71b2-134">Konfigurační oddíl, který obsahuje položky směrování mapování.</span><span class="sxs-lookup"><span data-stu-id="e71b2-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e71b2-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e71b2-135">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
