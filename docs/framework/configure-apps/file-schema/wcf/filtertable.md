---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229274"
---
# <a name="filtertable"></a><span data-ttu-id="0918c-101">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="0918c-101">\<filterTable></span></span>
<span data-ttu-id="0918c-102">Představuje směrovací tabulku, která obsahuje seznam filtrů určených k vyhodnocení zpráv a koncový bod klienta pro směrování zpráv v případě ohodnocení filtru hodnotou true.</span><span class="sxs-lookup"><span data-stu-id="0918c-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="0918c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0918c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0918c-104">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="0918c-104">\<routing></span></span>  
<span data-ttu-id="0918c-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="0918c-105">\<routingTables></span></span>  
<span data-ttu-id="0918c-106">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="0918c-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0918c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0918c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0918c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0918c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0918c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0918c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0918c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0918c-110">Attributes</span></span>  
  
|<span data-ttu-id="0918c-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="0918c-111">Element</span></span>|<span data-ttu-id="0918c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0918c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0918c-113">name</span><span class="sxs-lookup"><span data-stu-id="0918c-113">name</span></span>|<span data-ttu-id="0918c-114">Řetězec obsahující jedinečný název tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="0918c-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0918c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0918c-115">Child Elements</span></span>  
  
|<span data-ttu-id="0918c-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="0918c-116">Element</span></span>|<span data-ttu-id="0918c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0918c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0918c-118">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="0918c-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="0918c-119">Mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="0918c-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0918c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0918c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0918c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="0918c-121">Element</span></span>|<span data-ttu-id="0918c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="0918c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0918c-123">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="0918c-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0918c-124">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="0918c-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0918c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0918c-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
