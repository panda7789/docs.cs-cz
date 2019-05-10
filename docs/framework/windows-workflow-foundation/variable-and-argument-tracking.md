---
title: Sledování proměnných a argumentů
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 75ec8124200b146965214d161d0e6f246888542c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640985"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="daa82-102">Sledování proměnných a argumentů</span><span class="sxs-lookup"><span data-stu-id="daa82-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="daa82-103">Při sledování provádění pracovního postupu, je často užitečné extrahovat data.</span><span class="sxs-lookup"><span data-stu-id="daa82-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="daa82-104">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="daa82-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="daa82-105">V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], můžete extrahovat všechny viditelné proměnné nebo argumentu v rámci oboru žádnou aktivitu v pracovním postupu pomocí sledování.</span><span class="sxs-lookup"><span data-stu-id="daa82-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="daa82-106">Sledování profily umožňují snadno extrahovat data.</span><span class="sxs-lookup"><span data-stu-id="daa82-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="daa82-107">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="daa82-107">Variables and Arguments</span></span>  
 <span data-ttu-id="daa82-108">Pokud aktivita vyzařuje ActivityStateRecord se extrahují proměnné a argumenty.</span><span class="sxs-lookup"><span data-stu-id="daa82-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="daa82-109">Proměnná je k dispozici pro extrahování, pouze pokud je v rámci oboru aktivity.</span><span class="sxs-lookup"><span data-stu-id="daa82-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="daa82-110">Tímto způsobem je zadána proměnná extrahovaným v rámci aktivity:</span><span class="sxs-lookup"><span data-stu-id="daa82-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="daa82-111">Pokud proměnná je určen název proměnné, sledování vypadá pro proměnné v rámci aktuální aktivitu sledován a v nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="daa82-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="daa82-112">Proměnná vyhledává v aktuálním oboru aktivity a v nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="daa82-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="daa82-113">Pokud proměnné extrahovaným je určené vlastností name = "\*", pak se extrahují všechny proměnné v rámci aktuální aktivitu sledován.</span><span class="sxs-lookup"><span data-stu-id="daa82-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="daa82-114">V tomto případě proměnné, které jsou v oboru, ale definované v nadřazeném prvku, které nejsou extrahována aktivity.</span><span class="sxs-lookup"><span data-stu-id="daa82-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="daa82-115">Při extrahování argumenty, argumenty extrahovat závisí na stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="daa82-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="daa82-116">Když stav aktivity je zpracování, pak pouze `InArguments` jsou k dispozici pro extrakci.</span><span class="sxs-lookup"><span data-stu-id="daa82-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="daa82-117">Pro všechny ostatní aktivity stavu (uzavřeno, Faulted, zrušeno) všechny argumenty, InArguments a OutArguments, jsou k dispozici pro extrakci.</span><span class="sxs-lookup"><span data-stu-id="daa82-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="daa82-118">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="daa82-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="daa82-119">Proměnné a argumenty může být extrahována pouze pomocí <xref:System.Activities.Tracking.ActivityStateRecord> a tedy přihlášení k odběru v rámci sledovacích profilu pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="daa82-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="daa82-120">Ochrana informací uložených v proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="daa82-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="daa82-121">Sledované proměnné nebo argumentu je ve výchozím nastavení nastavena jako viditelná modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="daa82-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="daa82-122">Pracovní postup vývojář chránil přístup podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="daa82-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="daa82-123">Šifrování hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="daa82-123">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="daa82-124">Ovládací prvek pro vytváření profilu sledování, aby se zabránilo extrakce proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="daa82-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="daa82-125">Pro vlastní sledování účastníci Ujistěte se, že kód WF nesmí vyzradit citlivé informace, které je uložený v proměnných nebo argumentů.</span><span class="sxs-lookup"><span data-stu-id="daa82-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa82-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daa82-126">See also</span></span>

- [<span data-ttu-id="daa82-127">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="daa82-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="daa82-128">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="daa82-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
