---
title: '&lt;backupLists&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 437cb1320147d5d76a4df9c3a00b4ee27bf650b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="726e8-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="726e8-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="726e8-103">Představuje konfigurační oddíl pro definování sady zálohování služby použité při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="726e8-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="726e8-104">Každý podřízený element je zálohování seznam, který se zobrazí sada koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="726e8-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="726e8-105">Pokud první koncový bod v seznamu je vypnutý, směrovací služby bude automaticky selhání na další stránku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="726e8-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="726e8-106">To vám dává rychlý způsob, jak přidat spolehlivost k vaší aplikaci bez nutnosti naučit klientskou aplikaci, jak bude zpracováván komplexní vzory nebo všech služeb, kde jsou nasazeny.</span><span class="sxs-lookup"><span data-stu-id="726e8-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="726e8-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="726e8-107">\<system.serviceModel></span></span>  
<span data-ttu-id="726e8-108">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="726e8-108">\<routing></span></span>  
<span data-ttu-id="726e8-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="726e8-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726e8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="726e8-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="726e8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="726e8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="726e8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="726e8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="726e8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="726e8-113">Attributes</span></span>  
 <span data-ttu-id="726e8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="726e8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="726e8-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="726e8-115">Child Elements</span></span>  
  
|<span data-ttu-id="726e8-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="726e8-116">Element</span></span>|<span data-ttu-id="726e8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="726e8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="726e8-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="726e8-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="726e8-119">Obsahuje seznam koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="726e8-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="726e8-120">.</span><span class="sxs-lookup"><span data-stu-id="726e8-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="726e8-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="726e8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="726e8-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="726e8-122">Element</span></span>|<span data-ttu-id="726e8-123">Popis</span><span class="sxs-lookup"><span data-stu-id="726e8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="726e8-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="726e8-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="726e8-125">Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k odesílání zpráv do kdy odpovídá filtru.</span><span class="sxs-lookup"><span data-stu-id="726e8-125">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="726e8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="726e8-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
