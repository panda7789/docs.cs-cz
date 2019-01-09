---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 2b537619a276f32c50576561aea03b5fbbb58e7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147782"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="02edf-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="02edf-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="02edf-103">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv, pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="02edf-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="02edf-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02edf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="02edf-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="02edf-105">\<routing></span></span>  
<span data-ttu-id="02edf-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="02edf-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02edf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02edf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02edf-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02edf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="02edf-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02edf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02edf-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="02edf-110">Attributes</span></span>  
 <span data-ttu-id="02edf-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="02edf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02edf-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02edf-112">Child Elements</span></span>  
  
|<span data-ttu-id="02edf-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="02edf-113">Element</span></span>|<span data-ttu-id="02edf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="02edf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02edf-115">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="02edf-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="02edf-116">Směrovací tabulky, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="02edf-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02edf-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02edf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="02edf-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="02edf-118">Element</span></span>|<span data-ttu-id="02edf-119">Popis</span><span class="sxs-lookup"><span data-stu-id="02edf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02edf-120">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="02edf-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="02edf-121">Konfigurační oddíl, který obsahuje směrovacími filtry a směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="02edf-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02edf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="02edf-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
