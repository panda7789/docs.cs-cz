---
title: <add> of <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089533"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="b1fce-102">\<Přidat > z \<backupList ></span><span class="sxs-lookup"><span data-stu-id="b1fce-102">\<add> of \<backupList></span></span>
<span data-ttu-id="b1fce-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b1fce-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="b1fce-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1fce-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b1fce-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="b1fce-105">\<routing></span></span>  
<span data-ttu-id="b1fce-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="b1fce-106">\<backupLists></span></span>  
<span data-ttu-id="b1fce-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="b1fce-107">\<backupList></span></span>  
<span data-ttu-id="b1fce-108">\<add></span><span class="sxs-lookup"><span data-stu-id="b1fce-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1fce-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1fce-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1fce-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1fce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1fce-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1fce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1fce-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1fce-112">Attributes</span></span>  
  
|<span data-ttu-id="b1fce-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1fce-113">Attribute</span></span>|<span data-ttu-id="b1fce-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b1fce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1fce-115">name</span><span class="sxs-lookup"><span data-stu-id="b1fce-115">name</span></span>|<span data-ttu-id="b1fce-116">Řetězec určující název záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b1fce-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1fce-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1fce-117">Child Elements</span></span>  
 <span data-ttu-id="b1fce-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1fce-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1fce-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1fce-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b1fce-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1fce-120">Element</span></span>|<span data-ttu-id="b1fce-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b1fce-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1fce-122">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="b1fce-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b1fce-123">Obsahuje seznam koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b1fce-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1fce-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1fce-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
