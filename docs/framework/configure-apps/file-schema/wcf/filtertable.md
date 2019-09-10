---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855188"
---
# <a name="filtertable"></a><span data-ttu-id="c4627-101">\<> filtru</span><span class="sxs-lookup"><span data-stu-id="c4627-101">\<filterTable></span></span>
<span data-ttu-id="c4627-102">Představuje směrovací tabulku, která obsahuje seznam filtrů pro vyhodnocení zpráv a koncový bod klienta pro směrování zpráv, pokud se filtr vyhodnotí jako true.</span><span class="sxs-lookup"><span data-stu-id="c4627-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="c4627-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4627-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4627-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c4627-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c4627-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="c4627-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="c4627-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="c4627-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="c4627-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> filtru**</span><span class="sxs-lookup"><span data-stu-id="c4627-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4627-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4627-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4627-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4627-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c4627-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4627-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4627-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4627-111">Attributes</span></span>  
  
|<span data-ttu-id="c4627-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4627-112">Element</span></span>|<span data-ttu-id="c4627-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c4627-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4627-114">name</span><span class="sxs-lookup"><span data-stu-id="c4627-114">name</span></span>|<span data-ttu-id="c4627-115">Řetězec, který obsahuje jedinečný název tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="c4627-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4627-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4627-116">Child Elements</span></span>  
  
|<span data-ttu-id="c4627-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4627-117">Element</span></span>|<span data-ttu-id="c4627-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c4627-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4627-119">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="c4627-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="c4627-120">Mapování mezi směrovacími filtry a cílovými koncovými body, které odesílají zprávy, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="c4627-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4627-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4627-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c4627-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4627-122">Element</span></span>|<span data-ttu-id="c4627-123">Popis</span><span class="sxs-lookup"><span data-stu-id="c4627-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4627-124">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="c4627-124">\<routing></span></span>](routing.md)|<span data-ttu-id="c4627-125">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="c4627-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4627-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4627-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
