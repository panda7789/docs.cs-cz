---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: b0a344aa69085d50087eefc746236bc8ceacadaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918859"
---
# <a name="filtertables"></a><span data-ttu-id="f89d9-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="f89d9-101">\<filterTables></span></span>
<span data-ttu-id="f89d9-102">Představuje konfigurační oddíl pro definování směrovacích tabulek, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="f89d9-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="f89d9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f89d9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f89d9-104">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="f89d9-104">\<routing></span></span>  
<span data-ttu-id="f89d9-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f89d9-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f89d9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f89d9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f89d9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f89d9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f89d9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f89d9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f89d9-109">Attributes</span></span>  
 <span data-ttu-id="f89d9-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="f89d9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f89d9-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f89d9-111">Child Elements</span></span>  
  
|<span data-ttu-id="f89d9-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="f89d9-112">Element</span></span>|<span data-ttu-id="f89d9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f89d9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89d9-114">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="f89d9-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="f89d9-115">Směrovací tabulka obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se budou posílat zprávy, když se filtr shoduje</span><span class="sxs-lookup"><span data-stu-id="f89d9-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f89d9-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f89d9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f89d9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f89d9-117">Element</span></span>|<span data-ttu-id="f89d9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f89d9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89d9-119">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="f89d9-119">\<routing></span></span>](routing.md)|<span data-ttu-id="f89d9-120">Konfigurační oddíl, který obsahuje filtry směrování a směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="f89d9-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f89d9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f89d9-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
