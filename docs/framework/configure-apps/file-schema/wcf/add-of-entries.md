---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920132"
---
# <a name="add-of-entries"></a><span data-ttu-id="eb48f-102">\<Přidat > \<položek ></span><span class="sxs-lookup"><span data-stu-id="eb48f-102">\<add> of \<entries></span></span>
<span data-ttu-id="eb48f-103">Představuje položku směrování, která mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="eb48f-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="eb48f-104">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="eb48f-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="eb48f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb48f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="eb48f-106">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="eb48f-106">\<routing></span></span>  
<span data-ttu-id="eb48f-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="eb48f-107">\<filterTables></span></span>  
<span data-ttu-id="eb48f-108">\<> filtru</span><span class="sxs-lookup"><span data-stu-id="eb48f-108">\<filterTable></span></span>  
<span data-ttu-id="eb48f-109">\<> položky</span><span class="sxs-lookup"><span data-stu-id="eb48f-109">\<entries></span></span>  
<span data-ttu-id="eb48f-110">\<add></span><span class="sxs-lookup"><span data-stu-id="eb48f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb48f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb48f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb48f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eb48f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eb48f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb48f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb48f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb48f-114">Attributes</span></span>  
  
|<span data-ttu-id="eb48f-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="eb48f-115">Attribute</span></span>|<span data-ttu-id="eb48f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="eb48f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb48f-117">backupList</span><span class="sxs-lookup"><span data-stu-id="eb48f-117">backupList</span></span>|<span data-ttu-id="eb48f-118">Řetězec, který určuje odkaz na záložní seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="eb48f-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="eb48f-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="eb48f-119">endpoint</span></span>|<span data-ttu-id="eb48f-120">Řetězec, který určuje odkaz na koncový bod klienta, který obdrží zprávy, které odpovídají filtru zadanému `filterName` atributem.</span><span class="sxs-lookup"><span data-stu-id="eb48f-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="eb48f-121">filterName</span><span class="sxs-lookup"><span data-stu-id="eb48f-121">filterName</span></span>|<span data-ttu-id="eb48f-122">Řetězec, který určuje odkaz na element filtru.</span><span class="sxs-lookup"><span data-stu-id="eb48f-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="eb48f-123">priority</span><span class="sxs-lookup"><span data-stu-id="eb48f-123">priority</span></span>|<span data-ttu-id="eb48f-124">Celé číslo, které určuje prioritu této položky.</span><span class="sxs-lookup"><span data-stu-id="eb48f-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="eb48f-125">Položky v tabulce směrování budou vyhodnocovány na základě priority, přičemž 0 je nejnižší priorita.</span><span class="sxs-lookup"><span data-stu-id="eb48f-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="eb48f-126">Všechny položky pro konkrétní prioritu jsou vyhodnocovány současně, pokud se pro aktuální prioritu nenajde žádná vyhovující položka, bude vyhodnocena další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="eb48f-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="eb48f-127">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="eb48f-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb48f-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eb48f-128">Child Elements</span></span>  
 <span data-ttu-id="eb48f-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="eb48f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb48f-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eb48f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="eb48f-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb48f-131">Element</span></span>|<span data-ttu-id="eb48f-132">Popis</span><span class="sxs-lookup"><span data-stu-id="eb48f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb48f-133">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="eb48f-133">\<routing></span></span>](routing.md)|<span data-ttu-id="eb48f-134">Konfigurační oddíl, který obsahuje položky mapování směrování.</span><span class="sxs-lookup"><span data-stu-id="eb48f-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb48f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb48f-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
