---
title: "&lt;add&gt; – &lt;backupList&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="c41d9-102">&lt;add&gt; – &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="c41d9-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="c41d9-103">Představuje element konfigurace, který definuje element zálohování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c41d9-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="c41d9-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c41d9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c41d9-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="c41d9-105">\<routing></span></span>  
<span data-ttu-id="c41d9-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="c41d9-106">\<backupLists></span></span>  
<span data-ttu-id="c41d9-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="c41d9-107">\<backupList></span></span>  
<span data-ttu-id="c41d9-108">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="c41d9-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41d9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c41d9-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c41d9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c41d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c41d9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c41d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c41d9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c41d9-112">Attributes</span></span>  
  
|<span data-ttu-id="c41d9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c41d9-113">Attribute</span></span>|<span data-ttu-id="c41d9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c41d9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c41d9-115">name</span><span class="sxs-lookup"><span data-stu-id="c41d9-115">name</span></span>|<span data-ttu-id="c41d9-116">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="c41d9-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c41d9-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c41d9-117">Child Elements</span></span>  
 <span data-ttu-id="c41d9-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="c41d9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c41d9-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c41d9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c41d9-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c41d9-120">Element</span></span>|<span data-ttu-id="c41d9-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c41d9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c41d9-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="c41d9-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c41d9-123">Obsahuje seznam koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="c41d9-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c41d9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c41d9-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
