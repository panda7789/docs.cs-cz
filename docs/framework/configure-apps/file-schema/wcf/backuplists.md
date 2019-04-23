---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6e44dbe3c0966c6d243db343b9f9b0dec2480cb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134443"
---
# <a name="backuplists"></a><span data-ttu-id="4ad58-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="4ad58-101">\<backupLists></span></span>
<span data-ttu-id="4ad58-102">Představuje konfigurační oddíl pro definování sady záložních služeb použitých při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="4ad58-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="4ad58-103">Každý podřízený prvek je záložní seznam, který uvádí sady koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4ad58-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4ad58-104">Pokud je první koncový bod v seznamu dolů, směrovací služba se automaticky převzetí služby při selhání k dalším objektem v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4ad58-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="4ad58-105">To umožňuje rychlé přidání spolehlivosti do aplikace bez nutnosti představuje klientskou aplikaci, jak zpracovávat složité vzory nebo všechny služby, ve které jsou nasazené.</span><span class="sxs-lookup"><span data-stu-id="4ad58-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="4ad58-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ad58-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4ad58-107">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4ad58-107">\<routing></span></span>  
<span data-ttu-id="4ad58-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="4ad58-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad58-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad58-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad58-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4ad58-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad58-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4ad58-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad58-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4ad58-112">Attributes</span></span>  
 <span data-ttu-id="4ad58-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4ad58-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ad58-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4ad58-114">Child Elements</span></span>  
  
|<span data-ttu-id="4ad58-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="4ad58-115">Element</span></span>|<span data-ttu-id="4ad58-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4ad58-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad58-117">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="4ad58-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="4ad58-118">Obsahuje seznam koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4ad58-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4ad58-119">.</span><span class="sxs-lookup"><span data-stu-id="4ad58-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad58-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4ad58-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad58-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4ad58-121">Element</span></span>|<span data-ttu-id="4ad58-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4ad58-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad58-123">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4ad58-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="4ad58-124">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> má být použit při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definujjí koncové body do odesílání zpráv do při shodě s filtrem.</span><span class="sxs-lookup"><span data-stu-id="4ad58-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ad58-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ad58-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
