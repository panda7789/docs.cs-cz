---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850505"
---
# <a name="add-of-entries"></a><span data-ttu-id="d5b02-102">\<add> z \<entries></span><span class="sxs-lookup"><span data-stu-id="d5b02-102">\<add> of \<entries></span></span>
<span data-ttu-id="d5b02-103">Představuje položku směrování, která mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="d5b02-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="d5b02-104">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="d5b02-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d5b02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5b02-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5b02-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d5b02-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d5b02-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d5b02-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5b02-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d5b02-108">Attributes</span></span>  
  
|<span data-ttu-id="d5b02-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d5b02-109">Attribute</span></span>|<span data-ttu-id="d5b02-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d5b02-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5b02-111">backupList</span><span class="sxs-lookup"><span data-stu-id="d5b02-111">backupList</span></span>|<span data-ttu-id="d5b02-112">Řetězec, který určuje odkaz na záložní seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d5b02-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="d5b02-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="d5b02-113">endpoint</span></span>|<span data-ttu-id="d5b02-114">Řetězec, který určuje odkaz na koncový bod klienta, který obdrží zprávy, které odpovídají filtru zadanému `filterName` atributem.</span><span class="sxs-lookup"><span data-stu-id="d5b02-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="d5b02-115">filterName</span><span class="sxs-lookup"><span data-stu-id="d5b02-115">filterName</span></span>|<span data-ttu-id="d5b02-116">Řetězec, který určuje odkaz na element filtru.</span><span class="sxs-lookup"><span data-stu-id="d5b02-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="d5b02-117">upřednostněn</span><span class="sxs-lookup"><span data-stu-id="d5b02-117">priority</span></span>|<span data-ttu-id="d5b02-118">Celé číslo, které určuje prioritu této položky.</span><span class="sxs-lookup"><span data-stu-id="d5b02-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="d5b02-119">Položky v tabulce směrování budou vyhodnocovány na základě priority, přičemž 0 je nejnižší priorita.</span><span class="sxs-lookup"><span data-stu-id="d5b02-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="d5b02-120">Všechny položky pro konkrétní prioritu jsou vyhodnocovány současně, pokud se pro aktuální prioritu nenajde žádná vyhovující položka, bude vyhodnocena další úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="d5b02-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="d5b02-121">Tato hodnota je volitelná.</span><span class="sxs-lookup"><span data-stu-id="d5b02-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5b02-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d5b02-122">Child Elements</span></span>  
 <span data-ttu-id="d5b02-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="d5b02-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5b02-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d5b02-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d5b02-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5b02-125">Element</span></span>|<span data-ttu-id="d5b02-126">Description</span><span class="sxs-lookup"><span data-stu-id="d5b02-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="d5b02-127">Konfigurační oddíl, který obsahuje položky mapování směrování.</span><span class="sxs-lookup"><span data-stu-id="d5b02-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5b02-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5b02-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
