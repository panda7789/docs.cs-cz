---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="919be-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="919be-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="919be-103">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv, když odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="919be-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="919be-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="919be-104">\<system.serviceModel></span></span>  
<span data-ttu-id="919be-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="919be-105">\<routing></span></span>  
<span data-ttu-id="919be-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="919be-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919be-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="919be-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="919be-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="919be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="919be-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="919be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="919be-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="919be-110">Attributes</span></span>  
 <span data-ttu-id="919be-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="919be-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="919be-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="919be-112">Child Elements</span></span>  
  
|<span data-ttu-id="919be-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="919be-113">Element</span></span>|<span data-ttu-id="919be-114">Popis</span><span class="sxs-lookup"><span data-stu-id="919be-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="919be-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="919be-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="919be-116">Směrovací tabulky, které obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="919be-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="919be-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="919be-117">Parent Elements</span></span>  
  
|<span data-ttu-id="919be-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="919be-118">Element</span></span>|<span data-ttu-id="919be-119">Popis</span><span class="sxs-lookup"><span data-stu-id="919be-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="919be-120">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="919be-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="919be-121">Konfigurační oddíl, který obsahuje filtrech směrování a směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="919be-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="919be-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="919be-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
