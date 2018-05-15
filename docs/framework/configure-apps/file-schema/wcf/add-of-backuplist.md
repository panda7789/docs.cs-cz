---
title: '&lt;add&gt; – &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="838b7-102">&lt;add&gt; – &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="838b7-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="838b7-103">Představuje element konfigurace, který definuje element zálohování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="838b7-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="838b7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="838b7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="838b7-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="838b7-105">\<routing></span></span>  
<span data-ttu-id="838b7-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="838b7-106">\<backupLists></span></span>  
<span data-ttu-id="838b7-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="838b7-107">\<backupList></span></span>  
<span data-ttu-id="838b7-108">\<add></span><span class="sxs-lookup"><span data-stu-id="838b7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838b7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="838b7-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="838b7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="838b7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="838b7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="838b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="838b7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="838b7-112">Attributes</span></span>  
  
|<span data-ttu-id="838b7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="838b7-113">Attribute</span></span>|<span data-ttu-id="838b7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="838b7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="838b7-115">name</span><span class="sxs-lookup"><span data-stu-id="838b7-115">name</span></span>|<span data-ttu-id="838b7-116">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="838b7-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="838b7-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="838b7-117">Child Elements</span></span>  
 <span data-ttu-id="838b7-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="838b7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="838b7-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="838b7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="838b7-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="838b7-120">Element</span></span>|<span data-ttu-id="838b7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="838b7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="838b7-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="838b7-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="838b7-123">Obsahuje seznam koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="838b7-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="838b7-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="838b7-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
