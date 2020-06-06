---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855188"
---
# \<filterTable>
<span data-ttu-id="610d0-101">Představuje směrovací tabulku, která obsahuje seznam filtrů pro vyhodnocení zpráv a koncový bod klienta pro směrování zpráv, pokud se filtr vyhodnotí jako true.</span><span class="sxs-lookup"><span data-stu-id="610d0-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="610d0-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="610d0-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="610d0-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="610d0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="610d0-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="610d0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="610d0-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="610d0-105">Attributes</span></span>  
  
|<span data-ttu-id="610d0-106">Prvek</span><span class="sxs-lookup"><span data-stu-id="610d0-106">Element</span></span>|<span data-ttu-id="610d0-107">Description</span><span class="sxs-lookup"><span data-stu-id="610d0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="610d0-108">name</span><span class="sxs-lookup"><span data-stu-id="610d0-108">name</span></span>|<span data-ttu-id="610d0-109">Řetězec, který obsahuje jedinečný název tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="610d0-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="610d0-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="610d0-110">Child Elements</span></span>  
  
|<span data-ttu-id="610d0-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="610d0-111">Element</span></span>|<span data-ttu-id="610d0-112">Description</span><span class="sxs-lookup"><span data-stu-id="610d0-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="610d0-113">Mapování mezi směrovacími filtry a cílovými koncovými body, které odesílají zprávy, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="610d0-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="610d0-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="610d0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="610d0-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="610d0-115">Element</span></span>|<span data-ttu-id="610d0-116">Description</span><span class="sxs-lookup"><span data-stu-id="610d0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="610d0-117">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="610d0-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="610d0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="610d0-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
