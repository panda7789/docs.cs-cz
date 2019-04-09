---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c49c7cf3a196595556c2bf1b4ed4365bfe1e4cbf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075727"
---
# <a name="filtertables"></a><span data-ttu-id="e8de3-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="e8de3-101">\<filterTables></span></span>
<span data-ttu-id="e8de3-102">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv, pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="e8de3-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e8de3-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8de3-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e8de3-104">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e8de3-104">\<routing></span></span>  
<span data-ttu-id="e8de3-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="e8de3-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8de3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8de3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8de3-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8de3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e8de3-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8de3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8de3-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8de3-109">Attributes</span></span>  
 <span data-ttu-id="e8de3-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="e8de3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8de3-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8de3-111">Child Elements</span></span>  
  
|<span data-ttu-id="e8de3-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8de3-112">Element</span></span>|<span data-ttu-id="e8de3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e8de3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8de3-114">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="e8de3-114">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e8de3-115">Směrovací tabulky, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="e8de3-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8de3-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8de3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e8de3-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8de3-117">Element</span></span>|<span data-ttu-id="e8de3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e8de3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8de3-119">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e8de3-119">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e8de3-120">Konfigurační oddíl, který obsahuje směrovacími filtry a směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="e8de3-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8de3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8de3-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
