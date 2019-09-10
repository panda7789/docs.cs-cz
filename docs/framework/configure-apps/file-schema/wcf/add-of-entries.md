---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850505"
---
# <a name="add-of-entries"></a><span data-ttu-id="0eb24-102">\<Přidat > \<položek ></span><span class="sxs-lookup"><span data-stu-id="0eb24-102">\<add> of \<entries></span></span>
<span data-ttu-id="0eb24-103">Představuje položku směrování, která mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="0eb24-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="0eb24-104">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="0eb24-104">Messages matching this filter will be sent to this destination.</span></span>  
  
<span data-ttu-id="0eb24-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0eb24-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0eb24-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="0eb24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="0eb24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtru**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="0eb24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> položky**](entries.md)</span><span class="sxs-lookup"><span data-stu-id="0eb24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)</span></span>\
<span data-ttu-id="0eb24-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="0eb24-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb24-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eb24-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eb24-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0eb24-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0eb24-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0eb24-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eb24-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="0eb24-115">Attributes</span></span>  
  
|<span data-ttu-id="0eb24-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="0eb24-116">Attribute</span></span>|<span data-ttu-id="0eb24-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0eb24-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0eb24-118">backupList</span><span class="sxs-lookup"><span data-stu-id="0eb24-118">backupList</span></span>|<span data-ttu-id="0eb24-119">Řetězec, který určuje odkaz na záložní seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="0eb24-119">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="0eb24-120">endpoint</span><span class="sxs-lookup"><span data-stu-id="0eb24-120">endpoint</span></span>|<span data-ttu-id="0eb24-121">Řetězec, který určuje odkaz na koncový bod klienta, který obdrží zprávy, které odpovídají filtru zadanému `filterName` atributem.</span><span class="sxs-lookup"><span data-stu-id="0eb24-121">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="0eb24-122">filterName</span><span class="sxs-lookup"><span data-stu-id="0eb24-122">filterName</span></span>|<span data-ttu-id="0eb24-123">Řetězec, který určuje odkaz na element filtru.</span><span class="sxs-lookup"><span data-stu-id="0eb24-123">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="0eb24-124">priority</span><span class="sxs-lookup"><span data-stu-id="0eb24-124">priority</span></span>|<span data-ttu-id="0eb24-125">Celé číslo, které určuje prioritu této položky.</span><span class="sxs-lookup"><span data-stu-id="0eb24-125">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="0eb24-126">Položky v tabulce směrování budou vyhodnocovány na základě priority, přičemž 0 je nejnižší priorita.</span><span class="sxs-lookup"><span data-stu-id="0eb24-126">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="0eb24-127">Všechny položky pro konkrétní prioritu jsou vyhodnocovány současně, pokud se pro aktuální prioritu nenajde žádná vyhovující položka, bude vyhodnocena další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="0eb24-127">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="0eb24-128">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="0eb24-128">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eb24-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0eb24-129">Child Elements</span></span>  
 <span data-ttu-id="0eb24-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="0eb24-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eb24-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0eb24-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0eb24-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="0eb24-132">Element</span></span>|<span data-ttu-id="0eb24-133">Popis</span><span class="sxs-lookup"><span data-stu-id="0eb24-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eb24-134">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="0eb24-134">\<routing></span></span>](routing.md)|<span data-ttu-id="0eb24-135">Konfigurační oddíl, který obsahuje položky mapování směrování.</span><span class="sxs-lookup"><span data-stu-id="0eb24-135">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eb24-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0eb24-136">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
