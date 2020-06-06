---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855200"
---
# \<filterTables>
<span data-ttu-id="7a822-101">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="7a822-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="7a822-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a822-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a822-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7a822-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7a822-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7a822-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a822-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7a822-105">Attributes</span></span>  
 <span data-ttu-id="7a822-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="7a822-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a822-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7a822-107">Child Elements</span></span>  
  
|<span data-ttu-id="7a822-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a822-108">Element</span></span>|<span data-ttu-id="7a822-109">Description</span><span class="sxs-lookup"><span data-stu-id="7a822-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="7a822-110">Směrovací tabulka obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje</span><span class="sxs-lookup"><span data-stu-id="7a822-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a822-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7a822-111">Parent Elements</span></span>  
  
|<span data-ttu-id="7a822-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a822-112">Element</span></span>|<span data-ttu-id="7a822-113">Description</span><span class="sxs-lookup"><span data-stu-id="7a822-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="7a822-114">Konfigurační oddíl, který obsahuje filtry směrování a směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="7a822-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a822-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a822-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
