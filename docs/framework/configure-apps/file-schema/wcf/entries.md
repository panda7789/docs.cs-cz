---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855275"
---
# <a name="entries"></a><span data-ttu-id="49f12-101">\<> položky</span><span class="sxs-lookup"><span data-stu-id="49f12-101">\<entries></span></span>
<span data-ttu-id="49f12-102">Záznam směrování obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="49f12-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="49f12-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="49f12-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="49f12-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="49f12-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="49f12-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="49f12-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="49f12-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="49f12-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="49f12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtru**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="49f12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="49f12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> položky**</span><span class="sxs-lookup"><span data-stu-id="49f12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f12-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49f12-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49f12-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="49f12-110">Attributes and Elements</span></span>  
 <span data-ttu-id="49f12-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="49f12-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49f12-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="49f12-112">Attributes</span></span>  
 <span data-ttu-id="49f12-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="49f12-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="49f12-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="49f12-114">Child Elements</span></span>  
  
|<span data-ttu-id="49f12-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="49f12-115">Element</span></span>|<span data-ttu-id="49f12-116">Popis</span><span class="sxs-lookup"><span data-stu-id="49f12-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49f12-117">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="49f12-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="49f12-118">Mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="49f12-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="49f12-119">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="49f12-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49f12-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="49f12-120">Parent Elements</span></span>  
  
|<span data-ttu-id="49f12-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="49f12-121">Element</span></span>|<span data-ttu-id="49f12-122">Popis</span><span class="sxs-lookup"><span data-stu-id="49f12-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49f12-123">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="49f12-123">\<routing></span></span>](routing.md)|<span data-ttu-id="49f12-124">Konfigurační oddíl, který obsahuje směrovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="49f12-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49f12-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49f12-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
