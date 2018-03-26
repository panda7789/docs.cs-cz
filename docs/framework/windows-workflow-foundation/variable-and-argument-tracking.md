---
title: Proměnné a Argument sledování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c0857830b52b2f71df5d81f4bd232b62b894da63
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="b588d-102">Proměnné a Argument sledování</span><span class="sxs-lookup"><span data-stu-id="b588d-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="b588d-103">Při spuštění pracovního postupu pro sledování, je často užitečné extrahovat data.</span><span class="sxs-lookup"><span data-stu-id="b588d-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="b588d-104">To poskytuje další kontext při přístupu k provádění sledování záznamů post.</span><span class="sxs-lookup"><span data-stu-id="b588d-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="b588d-105">V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], můžete rozbalit žádné viditelné proměnné nebo argumentu v rámci oboru všechny aktivity v pracovním postupu pomocí sledování.</span><span class="sxs-lookup"><span data-stu-id="b588d-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="b588d-106">Sledování profily usnadňují extrahovat data.</span><span class="sxs-lookup"><span data-stu-id="b588d-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="b588d-107">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="b588d-107">Variables and Arguments</span></span>  
 <span data-ttu-id="b588d-108">Proměnné a argumenty se extrahují, když aktivita vysílá ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="b588d-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="b588d-109">Proměnné je k dispozici pro extrakci, pouze pokud je v rámci oboru aktivity.</span><span class="sxs-lookup"><span data-stu-id="b588d-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="b588d-110">Proměnné v aktivitě extrahovat je určena následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b588d-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="b588d-111">Pokud je proměnná Určuje název proměnné, sledování vypadá pro proměnné v rámci aktuální aktivita sledovaných a v nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b588d-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="b588d-112">V aktuálním oboru aktivity a v nadřazeném oboru, prohledají se proměnná.</span><span class="sxs-lookup"><span data-stu-id="b588d-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="b588d-113">Pokud jsou zadané proměnné k extrakci pomocí názvu = "\*", pak všechny proměnné v rámci aktuální aktivita sledovaných extrahují.</span><span class="sxs-lookup"><span data-stu-id="b588d-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="b588d-114">V takovém případě proměnné, jsou v oboru ale definovaný v nadřazené aktivity nejsou extrahovány.</span><span class="sxs-lookup"><span data-stu-id="b588d-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="b588d-115">Při extrahování argumenty, argumenty extrahovat závisí na stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b588d-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="b588d-116">Pokud stav aktivity je zpracování, pak pouze `InArguments` jsou k dispozici pro extrakci.</span><span class="sxs-lookup"><span data-stu-id="b588d-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="b588d-117">Pro všechny ostatní aktivity stavu (uzavřeno, Faulted zrušená.) všechny argumenty, InArguments a OutArguments, jsou k dispozici pro extrakci.</span><span class="sxs-lookup"><span data-stu-id="b588d-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="b588d-118">Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="b588d-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b588d-119">Proměnné a argumenty lze extrahovat jenom s <xref:System.Activities.Tracking.ActivityStateRecord> a proto předplacené v rámci sledování profilu pomocí <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="b588d-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="b588d-120">Ochrana informace uložené v proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="b588d-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="b588d-121">Sledované proměnné nebo argument je ve výchozím nastavení dostupná modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b588d-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="b588d-122">Vývojář pracovního postupu chrání před přístupem provedením následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b588d-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="b588d-123">Hodnotu proměnné zašifrujte.</span><span class="sxs-lookup"><span data-stu-id="b588d-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="b588d-124">Ovládací prvek vytváření profilu sledování zabránit extrahování proměnné nebo argumentu.</span><span class="sxs-lookup"><span data-stu-id="b588d-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="b588d-125">Pro vlastní sledování účastníky ujistěte, že kód WF nesmí vyzradit citlivé informace, které je uložené v proměnné nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="b588d-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b588d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b588d-126">See Also</span></span>  
 [<span data-ttu-id="b588d-127">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="b588d-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="b588d-128">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="b588d-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
