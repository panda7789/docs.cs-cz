---
title: '&lt;add&gt; – &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151472"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="64aa0-102">&lt;add&gt; – &lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="64aa0-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="64aa0-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="64aa0-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="64aa0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="64aa0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="64aa0-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="64aa0-105">\<routing></span></span>  
<span data-ttu-id="64aa0-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="64aa0-106">\<backupLists></span></span>  
<span data-ttu-id="64aa0-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="64aa0-107">\<backupList></span></span>  
<span data-ttu-id="64aa0-108">\<add></span><span class="sxs-lookup"><span data-stu-id="64aa0-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64aa0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64aa0-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64aa0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="64aa0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="64aa0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="64aa0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64aa0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="64aa0-112">Attributes</span></span>  
  
|<span data-ttu-id="64aa0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="64aa0-113">Attribute</span></span>|<span data-ttu-id="64aa0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="64aa0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64aa0-115">name</span><span class="sxs-lookup"><span data-stu-id="64aa0-115">name</span></span>|<span data-ttu-id="64aa0-116">Řetězec určující název záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="64aa0-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64aa0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="64aa0-117">Child Elements</span></span>  
 <span data-ttu-id="64aa0-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="64aa0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64aa0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="64aa0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="64aa0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="64aa0-120">Element</span></span>|<span data-ttu-id="64aa0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="64aa0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64aa0-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="64aa0-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="64aa0-123">Obsahuje seznam koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="64aa0-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64aa0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="64aa0-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
