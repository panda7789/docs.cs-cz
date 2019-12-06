---
title: Sledování proměnných a argumentů
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: c5d3fe6626c22184edd83de6aedad8589ab2ef35
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837542"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="e8ccc-102">Sledování proměnných a argumentů</span><span class="sxs-lookup"><span data-stu-id="e8ccc-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="e8ccc-103">Při sledování provádění pracovního postupu je často užitečné extrahovat data.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="e8ccc-104">To poskytuje další kontext při přístupu ke sledování záznamu po provedení.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="e8ccc-105">V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]můžete extrahovat všechny viditelné proměnné nebo argumenty v rámci rozsahu jakékoli aktivity pracovního postupu pomocí sledování.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="e8ccc-106">Sledování profilů usnadňuje extrahování dat.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="e8ccc-107">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="e8ccc-107">Variables and Arguments</span></span>  
 <span data-ttu-id="e8ccc-108">Proměnné a argumenty jsou extrahovány, když aktivita vygeneruje ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="e8ccc-109">Proměnná je k dispozici pro extrakci pouze v případě, že je v rámci rozsahu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="e8ccc-110">Proměnná, která se má extrahovat v rámci aktivity, je specifikována následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e8ccc-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="e8ccc-111">Pokud je proměnná určena názvem proměnné, pak sledování vyhledá proměnnou v rámci aktuální aktivity, která je sledována a v nadřazených aktivitách.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="e8ccc-112">Proměnná je prohledávána v oboru aktuální aktivity a v nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="e8ccc-113">Pokud proměnné, které mají být extrahovány, jsou určeny pomocí názvu = "\*", pak jsou extrahovány všechny proměnné v rámci aktuální aktivity, které jsou sledovány.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="e8ccc-114">V tomto případě proměnné, které jsou v oboru, ale nejsou definovány v nadřazených aktivitách, nejsou extrahovány.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="e8ccc-115">Při extrakci argumentů závisí argumenty, které jsou extrahovány, na stav aktivity.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="e8ccc-116">Když je spuštěn stav aktivity, jsou k extrakci k dispozici pouze `InArguments`.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="e8ccc-117">Pro extrakci jsou k dispozici všechny argumenty pro všechny ostatní stavy aktivity (uzavřeno, chyba, zrušeno).</span><span class="sxs-lookup"><span data-stu-id="e8ccc-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="e8ccc-118">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování záznamu sledování `Closed` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e8ccc-119">Proměnné a argumenty lze extrahovat pouze pomocí <xref:System.Activities.Tracking.ActivityStateRecord> a proto se přihlásí k odběru v rámci profilu sledování pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="e8ccc-120">Ochrana informací uložených v proměnných a argumentech</span><span class="sxs-lookup"><span data-stu-id="e8ccc-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="e8ccc-121">Sledovaná proměnná nebo argument je ve výchozím nastavení viditelná modulem runtime WF.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="e8ccc-122">Vývojář pracovního postupu může chránit před tím, že provádí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e8ccc-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="e8ccc-123">Zašifrujte hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-123">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="e8ccc-124">Řízení vytváření profilu sledování, aby se zabránilo extrakci proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="e8ccc-125">Pro vlastní účastníky sledování zajišťuje, že kód WF nezveřejňuje citlivé informace, které jsou uloženy v proměnných nebo argumentech.</span><span class="sxs-lookup"><span data-stu-id="e8ccc-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ccc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8ccc-126">See also</span></span>

- <span data-ttu-id="e8ccc-127">[Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e8ccc-127">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="e8ccc-128">[Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e8ccc-128">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
