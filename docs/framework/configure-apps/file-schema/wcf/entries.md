---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925652"
---
# <a name="entries"></a><span data-ttu-id="a9791-101">\<> položky</span><span class="sxs-lookup"><span data-stu-id="a9791-101">\<entries></span></span>
<span data-ttu-id="a9791-102">Záznam směrování obsahující mapování mezi směrovacími filtry a cílovými koncovými body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="a9791-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="a9791-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a9791-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a9791-104">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="a9791-104">\<routing></span></span>  
<span data-ttu-id="a9791-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="a9791-105">\<routingTables></span></span>  
<span data-ttu-id="a9791-106">\<> tabulky</span><span class="sxs-lookup"><span data-stu-id="a9791-106">\<table></span></span>  
<span data-ttu-id="a9791-107">\<> položky</span><span class="sxs-lookup"><span data-stu-id="a9791-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9791-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9791-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9791-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a9791-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a9791-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a9791-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9791-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9791-111">Attributes</span></span>  
 <span data-ttu-id="a9791-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="a9791-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9791-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a9791-113">Child Elements</span></span>  
  
|<span data-ttu-id="a9791-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9791-114">Element</span></span>|<span data-ttu-id="a9791-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a9791-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9791-116">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="a9791-116">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="a9791-117">Mapuje filtr na koncový bod klienta, který byl dříve definován.</span><span class="sxs-lookup"><span data-stu-id="a9791-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="a9791-118">Zprávy, které odpovídají tomuto filtru, budou odeslány do tohoto cíle.</span><span class="sxs-lookup"><span data-stu-id="a9791-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9791-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a9791-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a9791-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9791-120">Element</span></span>|<span data-ttu-id="a9791-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a9791-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9791-122">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="a9791-122">\<routing></span></span>](routing.md)|<span data-ttu-id="a9791-123">Konfigurační oddíl, který obsahuje směrovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="a9791-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9791-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9791-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
