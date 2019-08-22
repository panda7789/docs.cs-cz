---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663374"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="af099-102">\<Přidat > \<> backupList</span><span class="sxs-lookup"><span data-stu-id="af099-102">\<add> of \<backupList></span></span>
<span data-ttu-id="af099-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="af099-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="af099-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="af099-104">\<system.serviceModel></span></span>  
<span data-ttu-id="af099-105">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="af099-105">\<routing></span></span>  
<span data-ttu-id="af099-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="af099-106">\<backupLists></span></span>  
<span data-ttu-id="af099-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="af099-107">\<backupList></span></span>  
<span data-ttu-id="af099-108">\<add></span><span class="sxs-lookup"><span data-stu-id="af099-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af099-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af099-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af099-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="af099-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af099-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="af099-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af099-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="af099-112">Attributes</span></span>  
  
|<span data-ttu-id="af099-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="af099-113">Attribute</span></span>|<span data-ttu-id="af099-114">Popis</span><span class="sxs-lookup"><span data-stu-id="af099-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af099-115">name</span><span class="sxs-lookup"><span data-stu-id="af099-115">name</span></span>|<span data-ttu-id="af099-116">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="af099-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af099-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="af099-117">Child Elements</span></span>  
 <span data-ttu-id="af099-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="af099-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af099-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="af099-119">Parent Elements</span></span>  
  
|<span data-ttu-id="af099-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="af099-120">Element</span></span>|<span data-ttu-id="af099-121">Popis</span><span class="sxs-lookup"><span data-stu-id="af099-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af099-122">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="af099-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="af099-123">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="af099-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af099-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af099-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
