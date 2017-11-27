---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04780d51cfd1d1d0049fc608cf7bd304be382b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="f876c-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="f876c-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="f876c-103">Představuje směrovací tabulku, která obsahuje seznam filtrů vyhodnocení zprávy proti a koncový bod klienta pro směrování zpráv do, pokud filtr se vyhodnotí jako true.</span><span class="sxs-lookup"><span data-stu-id="f876c-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="f876c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f876c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f876c-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="f876c-105">\<routing></span></span>  
<span data-ttu-id="f876c-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f876c-106">\<routingTables></span></span>  
<span data-ttu-id="f876c-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="f876c-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f876c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f876c-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f876c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f876c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f876c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f876c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f876c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f876c-111">Attributes</span></span>  
  
|<span data-ttu-id="f876c-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="f876c-112">Element</span></span>|<span data-ttu-id="f876c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f876c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f876c-114">name</span><span class="sxs-lookup"><span data-stu-id="f876c-114">name</span></span>|<span data-ttu-id="f876c-115">Řetězec, který obsahuje jedinečný název tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f876c-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f876c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f876c-116">Child Elements</span></span>  
  
|<span data-ttu-id="f876c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f876c-117">Element</span></span>|<span data-ttu-id="f876c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f876c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f876c-119">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="f876c-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f876c-120">Mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="f876c-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f876c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f876c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f876c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="f876c-122">Element</span></span>|<span data-ttu-id="f876c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f876c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f876c-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="f876c-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f876c-125">Konfigurační oddíl, který obsahuje směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="f876c-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f876c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f876c-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
