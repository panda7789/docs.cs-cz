---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925607"
---
# <a name="filtertable"></a><span data-ttu-id="96981-101">\<> filtru</span><span class="sxs-lookup"><span data-stu-id="96981-101">\<filterTable></span></span>
<span data-ttu-id="96981-102">Představuje směrovací tabulku, která obsahuje seznam filtrů pro vyhodnocení zpráv a koncový bod klienta pro směrování zpráv, pokud se filtr vyhodnotí jako true.</span><span class="sxs-lookup"><span data-stu-id="96981-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="96981-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96981-103">\<system.serviceModel></span></span>  
<span data-ttu-id="96981-104">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="96981-104">\<routing></span></span>  
<span data-ttu-id="96981-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="96981-105">\<routingTables></span></span>  
<span data-ttu-id="96981-106">\<> tabulky</span><span class="sxs-lookup"><span data-stu-id="96981-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96981-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96981-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96981-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96981-108">Attributes and Elements</span></span>  
 <span data-ttu-id="96981-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96981-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96981-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="96981-110">Attributes</span></span>  
  
|<span data-ttu-id="96981-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="96981-111">Element</span></span>|<span data-ttu-id="96981-112">Popis</span><span class="sxs-lookup"><span data-stu-id="96981-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96981-113">name</span><span class="sxs-lookup"><span data-stu-id="96981-113">name</span></span>|<span data-ttu-id="96981-114">Řetězec, který obsahuje jedinečný název tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="96981-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96981-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96981-115">Child Elements</span></span>  
  
|<span data-ttu-id="96981-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="96981-116">Element</span></span>|<span data-ttu-id="96981-117">Popis</span><span class="sxs-lookup"><span data-stu-id="96981-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96981-118">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="96981-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="96981-119">Mapování mezi směrovacími filtry a cílovými koncovými body, které odesílají zprávy, když filtr odpovídá.</span><span class="sxs-lookup"><span data-stu-id="96981-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96981-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96981-120">Parent Elements</span></span>  
  
|<span data-ttu-id="96981-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="96981-121">Element</span></span>|<span data-ttu-id="96981-122">Popis</span><span class="sxs-lookup"><span data-stu-id="96981-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96981-123">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="96981-123">\<routing></span></span>](routing.md)|<span data-ttu-id="96981-124">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="96981-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96981-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96981-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
