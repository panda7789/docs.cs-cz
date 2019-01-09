---
title: '&lt;Položky&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 8c442990ee736c17b71b625e06d961230a8ceed2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146430"
---
# <a name="ltentriesgt"></a><span data-ttu-id="664b9-102">&lt;Položky&gt;</span><span class="sxs-lookup"><span data-stu-id="664b9-102">&lt;entries&gt;</span></span>
<span data-ttu-id="664b9-103">Směrování položky, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="664b9-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="664b9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="664b9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="664b9-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="664b9-105">\<routing></span></span>  
<span data-ttu-id="664b9-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="664b9-106">\<routingTables></span></span>  
<span data-ttu-id="664b9-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="664b9-107">\<table></span></span>  
<span data-ttu-id="664b9-108">\<položky ></span><span class="sxs-lookup"><span data-stu-id="664b9-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664b9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="664b9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="664b9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="664b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="664b9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="664b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="664b9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="664b9-112">Attributes</span></span>  
 <span data-ttu-id="664b9-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="664b9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="664b9-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="664b9-114">Child Elements</span></span>  
  
|<span data-ttu-id="664b9-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="664b9-115">Element</span></span>|<span data-ttu-id="664b9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="664b9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="664b9-117">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="664b9-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="664b9-118">Filtr se mapuje na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="664b9-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="664b9-119">Tomuto filtru odpovídá zprávy se odešlou do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="664b9-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="664b9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="664b9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="664b9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="664b9-121">Element</span></span>|<span data-ttu-id="664b9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="664b9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="664b9-123">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="664b9-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="664b9-124">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="664b9-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="664b9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="664b9-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
