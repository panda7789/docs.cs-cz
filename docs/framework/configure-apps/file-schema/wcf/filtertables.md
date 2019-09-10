---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855200"
---
# <a name="filtertables"></a><span data-ttu-id="197c4-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="197c4-101">\<filterTables></span></span>
<span data-ttu-id="197c4-102">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="197c4-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="197c4-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="197c4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="197c4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="197c4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="197c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="197c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="197c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="197c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197c4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="197c4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="197c4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="197c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="197c4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="197c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="197c4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="197c4-110">Attributes</span></span>  
 <span data-ttu-id="197c4-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="197c4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="197c4-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="197c4-112">Child Elements</span></span>  
  
|<span data-ttu-id="197c4-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="197c4-113">Element</span></span>|<span data-ttu-id="197c4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="197c4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="197c4-115">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="197c4-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="197c4-116">Směrovací tabulka obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje</span><span class="sxs-lookup"><span data-stu-id="197c4-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="197c4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="197c4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="197c4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="197c4-118">Element</span></span>|<span data-ttu-id="197c4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="197c4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="197c4-120">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="197c4-120">\<routing></span></span>](routing.md)|<span data-ttu-id="197c4-121">Konfigurační oddíl, který obsahuje filtry směrování a směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="197c4-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="197c4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="197c4-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
