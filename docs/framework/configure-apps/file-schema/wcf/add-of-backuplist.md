---
title: <add> z <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926879"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="59148-102">\<Přidat > \<> backupList</span><span class="sxs-lookup"><span data-stu-id="59148-102">\<add> of \<backupList></span></span>
<span data-ttu-id="59148-103">Představuje prvek konfigurace, který definuje element záložního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59148-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="59148-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59148-104">\<system.serviceModel></span></span>  
<span data-ttu-id="59148-105">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="59148-105">\<routing></span></span>  
<span data-ttu-id="59148-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="59148-106">\<backupLists></span></span>  
<span data-ttu-id="59148-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="59148-107">\<backupList></span></span>  
<span data-ttu-id="59148-108">\<add></span><span class="sxs-lookup"><span data-stu-id="59148-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59148-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59148-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59148-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59148-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59148-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59148-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59148-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="59148-112">Attributes</span></span>  
  
|<span data-ttu-id="59148-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="59148-113">Attribute</span></span>|<span data-ttu-id="59148-114">Popis</span><span class="sxs-lookup"><span data-stu-id="59148-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59148-115">name</span><span class="sxs-lookup"><span data-stu-id="59148-115">name</span></span>|<span data-ttu-id="59148-116">Řetězec, který určuje název koncového bodu zálohy.</span><span class="sxs-lookup"><span data-stu-id="59148-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59148-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59148-117">Child Elements</span></span>  
 <span data-ttu-id="59148-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="59148-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59148-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59148-119">Parent Elements</span></span>  
  
|<span data-ttu-id="59148-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="59148-120">Element</span></span>|<span data-ttu-id="59148-121">Popis</span><span class="sxs-lookup"><span data-stu-id="59148-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59148-122">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="59148-122">\<routing></span></span>](routing.md)|<span data-ttu-id="59148-123">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="59148-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59148-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59148-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
