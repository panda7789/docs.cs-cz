---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089533"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="4c31f-102">\<Přidat > z \<backupList ></span><span class="sxs-lookup"><span data-stu-id="4c31f-102">\<add> of \<backupList></span></span>
<span data-ttu-id="4c31f-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4c31f-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="4c31f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4c31f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4c31f-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4c31f-105">\<routing></span></span>  
<span data-ttu-id="4c31f-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="4c31f-106">\<backupLists></span></span>  
<span data-ttu-id="4c31f-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="4c31f-107">\<backupList></span></span>  
<span data-ttu-id="4c31f-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4c31f-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c31f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c31f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c31f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c31f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4c31f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c31f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c31f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c31f-112">Attributes</span></span>  
  
|<span data-ttu-id="4c31f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c31f-113">Attribute</span></span>|<span data-ttu-id="4c31f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4c31f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c31f-115">name</span><span class="sxs-lookup"><span data-stu-id="4c31f-115">name</span></span>|<span data-ttu-id="4c31f-116">Řetězec určující název záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4c31f-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c31f-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c31f-117">Child Elements</span></span>  
 <span data-ttu-id="4c31f-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c31f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c31f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c31f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4c31f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c31f-120">Element</span></span>|<span data-ttu-id="4c31f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4c31f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c31f-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="4c31f-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="4c31f-123">Obsahuje seznam koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4c31f-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c31f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c31f-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
