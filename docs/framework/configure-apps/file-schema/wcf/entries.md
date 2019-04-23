---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201790"
---
# <a name="entries"></a><span data-ttu-id="75a9a-101">\<položky ></span><span class="sxs-lookup"><span data-stu-id="75a9a-101">\<entries></span></span>
<span data-ttu-id="75a9a-102">Směrování položky, které obsahují mapování mezi směrovacími filtry a cílovými koncovými body pro odesílání zpráv do pokud bod odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="75a9a-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="75a9a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75a9a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="75a9a-104">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="75a9a-104">\<routing></span></span>  
<span data-ttu-id="75a9a-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="75a9a-105">\<routingTables></span></span>  
<span data-ttu-id="75a9a-106">\<Tabulka ></span><span class="sxs-lookup"><span data-stu-id="75a9a-106">\<table></span></span>  
<span data-ttu-id="75a9a-107">\<položky ></span><span class="sxs-lookup"><span data-stu-id="75a9a-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a9a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75a9a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75a9a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="75a9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="75a9a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="75a9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75a9a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="75a9a-111">Attributes</span></span>  
 <span data-ttu-id="75a9a-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="75a9a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75a9a-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="75a9a-113">Child Elements</span></span>  
  
|<span data-ttu-id="75a9a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="75a9a-114">Element</span></span>|<span data-ttu-id="75a9a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="75a9a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75a9a-116">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="75a9a-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="75a9a-117">Filtr se mapuje na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="75a9a-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="75a9a-118">Tomuto filtru odpovídá zprávy se odešlou do tohoto cílového místa.</span><span class="sxs-lookup"><span data-stu-id="75a9a-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75a9a-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="75a9a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="75a9a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="75a9a-120">Element</span></span>|<span data-ttu-id="75a9a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="75a9a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75a9a-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="75a9a-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="75a9a-123">Konfigurační oddíl, který obsahuje směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="75a9a-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75a9a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75a9a-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
