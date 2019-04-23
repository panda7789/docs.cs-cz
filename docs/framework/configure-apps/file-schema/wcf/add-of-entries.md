---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 1324803d7c0f127cfee9eadebff2672955780eda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165409"
---
# <a name="add-of-entries"></a><span data-ttu-id="b8ad6-102">\<Přidat > z \<položky ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-102">\<add> of \<entries></span></span>
<span data-ttu-id="b8ad6-103">Představuje položku směrování, která se mapuje na koncový bod klienta, který byl předtím definovaný filtr.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="b8ad6-104">Tomuto filtru odpovídá zprávy se odešlou do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="b8ad6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b8ad6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b8ad6-106">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-106">\<routing></span></span>  
<span data-ttu-id="b8ad6-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-107">\<filterTables></span></span>  
<span data-ttu-id="b8ad6-108">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-108">\<filterTable></span></span>  
<span data-ttu-id="b8ad6-109">\<položky ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-109">\<entries></span></span>  
<span data-ttu-id="b8ad6-110">\<add></span><span class="sxs-lookup"><span data-stu-id="b8ad6-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ad6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8ad6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8ad6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8ad6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b8ad6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8ad6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8ad6-114">Attributes</span></span>  
  
|<span data-ttu-id="b8ad6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8ad6-115">Attribute</span></span>|<span data-ttu-id="b8ad6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b8ad6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8ad6-117">backupList</span><span class="sxs-lookup"><span data-stu-id="b8ad6-117">backupList</span></span>|<span data-ttu-id="b8ad6-118">Řetězec, který určuje referenci na záložní seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="b8ad6-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="b8ad6-119">endpoint</span></span>|<span data-ttu-id="b8ad6-120">Řetězec, který určuje referenci na koncový bod klienta, který bude přijímat zprávy, které odpovídají filtru určeném `filterName` atribut.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="b8ad6-121">filterName</span><span class="sxs-lookup"><span data-stu-id="b8ad6-121">filterName</span></span>|<span data-ttu-id="b8ad6-122">Řetězec, který určuje odkaz na prvek filtru.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="b8ad6-123">priorita</span><span class="sxs-lookup"><span data-stu-id="b8ad6-123">priority</span></span>|<span data-ttu-id="b8ad6-124">Celé číslo, které určuje priorita této položky.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="b8ad6-125">Položky v tabulce směrování se vyhodnotí na základě priority, 0 je nejnižší priorita.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="b8ad6-126">Všechny položky s konkrétní prioritou jsou vyhodnocovány současně, pokud neexistuje odpovídající položka nebyl nalezen aktuální priorita, se vyhodnotí na další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="b8ad6-127">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8ad6-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8ad6-128">Child Elements</span></span>  
 <span data-ttu-id="b8ad6-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8ad6-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8ad6-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8ad6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b8ad6-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8ad6-131">Element</span></span>|<span data-ttu-id="b8ad6-132">Popis</span><span class="sxs-lookup"><span data-stu-id="b8ad6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8ad6-133">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="b8ad6-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b8ad6-134">Konfigurační oddíl, který obsahuje položky směrování mapování.</span><span class="sxs-lookup"><span data-stu-id="b8ad6-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8ad6-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8ad6-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
