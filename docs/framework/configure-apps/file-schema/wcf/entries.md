---
title: "&lt;položky&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef9c58a9b4ecd6db8b4efe116f6fafba01c3f6f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="786a7-102">&lt;položky&gt;</span><span class="sxs-lookup"><span data-stu-id="786a7-102">&lt;entries&gt;</span></span>
<span data-ttu-id="786a7-103">Směrování položku, která obsahují mapování mezi směrování filtry a cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="786a7-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="786a7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="786a7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="786a7-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="786a7-105">\<routing></span></span>  
<span data-ttu-id="786a7-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="786a7-106">\<routingTables></span></span>  
<span data-ttu-id="786a7-107">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="786a7-107">\<table></span></span>  
<span data-ttu-id="786a7-108">\<položky ></span><span class="sxs-lookup"><span data-stu-id="786a7-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="786a7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="786a7-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="786a7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="786a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="786a7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="786a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="786a7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="786a7-112">Attributes</span></span>  
 <span data-ttu-id="786a7-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="786a7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="786a7-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="786a7-114">Child Elements</span></span>  
  
|<span data-ttu-id="786a7-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="786a7-115">Element</span></span>|<span data-ttu-id="786a7-116">Popis</span><span class="sxs-lookup"><span data-stu-id="786a7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="786a7-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="786a7-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="786a7-118">Filtr se mapuje na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="786a7-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="786a7-119">Zprávy odpovídajících tomuto filtru budou odeslány do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="786a7-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="786a7-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="786a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="786a7-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="786a7-121">Element</span></span>|<span data-ttu-id="786a7-122">Popis</span><span class="sxs-lookup"><span data-stu-id="786a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="786a7-123">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="786a7-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="786a7-124">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="786a7-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="786a7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="786a7-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
