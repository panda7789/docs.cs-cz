---
title: '&lt;Položky&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: b9cc7f7736ffefaca68a0f197bd064a99c4dca9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746706"
---
# <a name="ltentriesgt"></a><span data-ttu-id="7d077-102">&lt;Položky&gt;</span><span class="sxs-lookup"><span data-stu-id="7d077-102">&lt;entries&gt;</span></span>
<span data-ttu-id="7d077-103">Směrování položku, která obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="7d077-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="7d077-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d077-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7d077-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="7d077-105">\<routing></span></span>  
<span data-ttu-id="7d077-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="7d077-106">\<routingTables></span></span>  
<span data-ttu-id="7d077-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="7d077-107">\<table></span></span>  
<span data-ttu-id="7d077-108">\<položky ></span><span class="sxs-lookup"><span data-stu-id="7d077-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d077-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d077-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d077-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d077-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d077-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d077-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d077-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d077-112">Attributes</span></span>  
 <span data-ttu-id="7d077-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d077-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d077-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d077-114">Child Elements</span></span>  
  
|<span data-ttu-id="7d077-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d077-115">Element</span></span>|<span data-ttu-id="7d077-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7d077-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d077-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="7d077-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="7d077-118">Filtr se mapuje na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="7d077-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="7d077-119">Zprávy odpovídajících tomuto filtru budou odeslány do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="7d077-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d077-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d077-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7d077-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d077-121">Element</span></span>|<span data-ttu-id="7d077-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7d077-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d077-123">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="7d077-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7d077-124">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="7d077-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d077-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d077-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
