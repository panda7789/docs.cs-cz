---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: fc9c697aff2e9c26c7922a0acaf5577b0dea2dc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532367"
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="58559-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="58559-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="58559-103">Představuje konfigurační oddíl pro definování sady záložních služeb použitých při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="58559-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="58559-104">Každý podřízený prvek je záložní seznam, který uvádí sady koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="58559-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="58559-105">Pokud je první koncový bod v seznamu dolů, směrovací služba se automaticky převzetí služby při selhání k dalším objektem v seznamu.</span><span class="sxs-lookup"><span data-stu-id="58559-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="58559-106">To umožňuje rychlé přidání spolehlivosti do aplikace bez nutnosti představuje klientskou aplikaci, jak zpracovávat složité vzory nebo všechny služby, ve které jsou nasazené.</span><span class="sxs-lookup"><span data-stu-id="58559-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="58559-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58559-107">\<system.serviceModel></span></span>  
<span data-ttu-id="58559-108">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="58559-108">\<routing></span></span>  
<span data-ttu-id="58559-109">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="58559-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58559-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58559-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58559-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58559-111">Attributes and Elements</span></span>  
 <span data-ttu-id="58559-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58559-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58559-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="58559-113">Attributes</span></span>  
 <span data-ttu-id="58559-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="58559-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58559-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58559-115">Child Elements</span></span>  
  
|<span data-ttu-id="58559-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="58559-116">Element</span></span>|<span data-ttu-id="58559-117">Popis</span><span class="sxs-lookup"><span data-stu-id="58559-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58559-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="58559-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="58559-119">Obsahuje seznam koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="58559-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="58559-120">.</span><span class="sxs-lookup"><span data-stu-id="58559-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58559-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58559-121">Parent Elements</span></span>  
  
|<span data-ttu-id="58559-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="58559-122">Element</span></span>|<span data-ttu-id="58559-123">Popis</span><span class="sxs-lookup"><span data-stu-id="58559-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58559-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="58559-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="58559-125">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="58559-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58559-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58559-126">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
