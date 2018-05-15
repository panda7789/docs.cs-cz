---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="4112d-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="4112d-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="4112d-103">Představuje konfigurační oddíl pro definování sady zálohování služby použité při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="4112d-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="4112d-104">Každý podřízený element je zálohování seznam, který se zobrazí sada koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="4112d-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4112d-105">Pokud první koncový bod v seznamu je vypnutý, směrovací služby bude automaticky selhání na další stránku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4112d-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="4112d-106">To vám dává rychlý způsob, jak přidat spolehlivost k vaší aplikaci bez nutnosti naučit klientskou aplikaci, jak bude zpracováván komplexní vzory nebo všech služeb, kde jsou nasazeny.</span><span class="sxs-lookup"><span data-stu-id="4112d-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="4112d-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4112d-107">\<system.serviceModel></span></span>  
<span data-ttu-id="4112d-108">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4112d-108">\<routing></span></span>  
<span data-ttu-id="4112d-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="4112d-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4112d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4112d-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4112d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4112d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4112d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4112d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4112d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4112d-113">Attributes</span></span>  
 <span data-ttu-id="4112d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4112d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4112d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4112d-115">Child Elements</span></span>  
  
|<span data-ttu-id="4112d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4112d-116">Element</span></span>|<span data-ttu-id="4112d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="4112d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4112d-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="4112d-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="4112d-119">Obsahuje seznam koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="4112d-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4112d-120">.</span><span class="sxs-lookup"><span data-stu-id="4112d-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4112d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4112d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4112d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="4112d-122">Element</span></span>|<span data-ttu-id="4112d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4112d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4112d-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4112d-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="4112d-125">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k Pokud filtr odpovídá odesílat zprávy.</span><span class="sxs-lookup"><span data-stu-id="4112d-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4112d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4112d-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
