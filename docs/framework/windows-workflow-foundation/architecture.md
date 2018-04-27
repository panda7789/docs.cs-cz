---
title: Architektura pracovního postupu systému Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a3a59369738ada0c6b770d272afa9c6c79c2ce01
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="windows-workflow-architecture"></a><span data-ttu-id="9281d-102">Architektura pracovního postupu systému Windows</span><span class="sxs-lookup"><span data-stu-id="9281d-102">Windows Workflow Architecture</span></span>
<span data-ttu-id="9281d-103">Windows Workflow Foundation (WF) zvýší úroveň abstrakce pro vývoj aplikací interaktivní časově náročné.</span><span class="sxs-lookup"><span data-stu-id="9281d-103">Windows Workflow Foundation (WF) raises the abstraction level for developing interactive long-running applications.</span></span> <span data-ttu-id="9281d-104">Pracovní jednotky se zapouzdřené jako aktivity.</span><span class="sxs-lookup"><span data-stu-id="9281d-104">Units of work are encapsulated as activities.</span></span> <span data-ttu-id="9281d-105">Aktivity spustit v prostředí, které poskytuje možnosti pro řízení toku, výjimek, chyb šíření, trvalosti dat o stavu, načítání a uvolňování probíhající pracovních postupů z paměti, sledování a toku transakcí.</span><span class="sxs-lookup"><span data-stu-id="9281d-105">Activities run in an environment that provides facilities for flow control, exception handling, fault propagation, persistence of state data, loading and unloading of in-progress workflows from memory, tracking, and transaction flow.</span></span>  
  
## <a name="activity-architecture"></a><span data-ttu-id="9281d-106">Architektura aktivity</span><span class="sxs-lookup"><span data-stu-id="9281d-106">Activity Architecture</span></span>  
 <span data-ttu-id="9281d-107">Aktivity jsou vyvinutý jako typy CLR, které jsou odvozeny od buď <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>, nebo jejich varianty, které vrací hodnotu, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, nebo <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="9281d-107">Activities are developed as CLR types that derive from either <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>, or their variants that return a value, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, or <xref:System.Activities.NativeActivity%601>.</span></span> <span data-ttu-id="9281d-108">Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.Activity> umožňuje uživateli sestavte existující aktivity rychle vytvořit pracovní jednotky, které jsou spuštěny v prostředí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9281d-108">Developing activities that derive from <xref:System.Activities.Activity> allows the user to assemble pre-existing activities to quickly create units of work that execute in the workflow environment.</span></span> <span data-ttu-id="9281d-109"><xref:System.Activities.CodeActivity>, na druhé straně umožňuje logiky provádění vytvářet spravovaného kódu pomocí <xref:System.Activities.CodeActivityContext> především pro přístup k argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="9281d-109"><xref:System.Activities.CodeActivity>, on the other hand, enables execution logic to be authored in managed code using <xref:System.Activities.CodeActivityContext> primarily for access to activity arguments.</span></span> <span data-ttu-id="9281d-110"><xref:System.Activities.AsyncCodeActivity> je podobná <xref:System.Activities.CodeActivity> s tím rozdílem, že ho můžete použít k implementaci asynchronních úloh.</span><span class="sxs-lookup"><span data-stu-id="9281d-110"><xref:System.Activities.AsyncCodeActivity> is similar to <xref:System.Activities.CodeActivity> except that it can be used to implement asynchronous tasks.</span></span> <span data-ttu-id="9281d-111">Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.NativeActivity> umožňuje uživatelům přistupovat k běhu programu prostřednictvím <xref:System.Activities.NativeActivityContext> pro fungování jako podřízené objekty, vytváření záložek, plánování vyvolání asynchronní pracovní, registraci transakce a další.</span><span class="sxs-lookup"><span data-stu-id="9281d-111">Developing activities that derive from <xref:System.Activities.NativeActivity> allows users to access the runtime through the <xref:System.Activities.NativeActivityContext> for functionality like scheduling children, creating bookmarks, invoking asynchronous work, registering transactions, and more.</span></span>  
  
 <span data-ttu-id="9281d-112">Vytváření aktivit, které jsou odvozeny od <xref:System.Activities.Activity> je deklarativní a tyto aktivity mohou být vytvořené v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="9281d-112">Authoring activities that derive from <xref:System.Activities.Activity> is declarative and these activities can be authored in XAML.</span></span> <span data-ttu-id="9281d-113">V následujícím příkladu aktivity volá `Prompt` je vytvořený pomocí jiné aktivity pro spuštění textu.</span><span class="sxs-lookup"><span data-stu-id="9281d-113">In the following example, an activity called `Prompt` is created using other activities for the execution body.</span></span>  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a><span data-ttu-id="9281d-114">Kontext aktivity</span><span class="sxs-lookup"><span data-stu-id="9281d-114">Activity Context</span></span>  
 <span data-ttu-id="9281d-115"><xref:System.Activities.ActivityContext> Je rozhraní Autor aktivita pro modul runtime pracovního postupu a poskytuje přístup k modulu runtime zadávané funkcí.</span><span class="sxs-lookup"><span data-stu-id="9281d-115">The <xref:System.Activities.ActivityContext> is the activity author's interface to the workflow runtime and provides access to the runtime's wealth of features.</span></span> <span data-ttu-id="9281d-116">V následujícím příkladu je definován aktivitu využívající kontext provádění na vytvoření záložky (mechanismus, který umožňuje aktivitu registrace bodu pokračování v jeho spuštění, který může být obnoven, hostitel předávání dat do aktivity).</span><span class="sxs-lookup"><span data-stu-id="9281d-116">In the following example, an activity is defined that uses the execution context to create a bookmark (the mechanism that allows an activity to register a continuation point in its execution that can be resumed by a host passing data into the activity).</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a><span data-ttu-id="9281d-117">Životní cyklus aktivity</span><span class="sxs-lookup"><span data-stu-id="9281d-117">Activity Life Cycle</span></span>  
 <span data-ttu-id="9281d-118">Instance aktivity spustí v <xref:System.Activities.ActivityInstanceState.Executing> stavu.</span><span class="sxs-lookup"><span data-stu-id="9281d-118">An instance of an activity starts out in the <xref:System.Activities.ActivityInstanceState.Executing> state.</span></span> <span data-ttu-id="9281d-119">Pokud nedojde k výjimky, zůstane v tomto stavu, dokud všechny podřízené aktivity dokončení provádění a všemi ostatními čekající na vyřízení pracovní (<xref:System.Activities.Bookmark> objekty, například) bylo dokončeno, v okamžiku ho přechodů k <xref:System.Activities.ActivityInstanceState.Closed> stavu.</span><span class="sxs-lookup"><span data-stu-id="9281d-119">Unless exceptions are encountered, it remains in this state until all child activities are finished executing and any other pending work (<xref:System.Activities.Bookmark> objects, for instance) is completed, at which point it transitions to the <xref:System.Activities.ActivityInstanceState.Closed> state.</span></span> <span data-ttu-id="9281d-120">Nadřazená aktivita instance může požádat o podřízené zrušit; je-li dítě moct zrušit dokončí za <xref:System.Activities.ActivityInstanceState.Canceled> stavu.</span><span class="sxs-lookup"><span data-stu-id="9281d-120">The parent of an activity instance can request a child to cancel; if the child is able to be canceled it completes in the <xref:System.Activities.ActivityInstanceState.Canceled> state.</span></span> <span data-ttu-id="9281d-121">Pokud během provádění je vyvolána výjimka, modul runtime vloží do aktivity <xref:System.Activities.ActivityInstanceState.Faulted> stavu a rozšíří výjimka řetězem nadřazené aktivit.</span><span class="sxs-lookup"><span data-stu-id="9281d-121">If an exception is thrown during execution, the runtime puts the activity into the <xref:System.Activities.ActivityInstanceState.Faulted> state and propagates the exception up the parent chain of activities.</span></span> <span data-ttu-id="9281d-122">Toto jsou tři dokončení stav aktivity:</span><span class="sxs-lookup"><span data-stu-id="9281d-122">Following are the three completion states of an activity:</span></span>  
  
-   <span data-ttu-id="9281d-123">**Ukončit:** aktivity dokončil svou práci a byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="9281d-123">**Closed:** The activity has completed its work and exited.</span></span>  
  
-   <span data-ttu-id="9281d-124">**Došlo ke zrušení:** řádně aktivity opuštění svou práci a byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="9281d-124">**Canceled:** The activity has gracefully abandoned its work and exited.</span></span> <span data-ttu-id="9281d-125">Pracovní není explicitně vrácena zpět, když se zadá tento stav.</span><span class="sxs-lookup"><span data-stu-id="9281d-125">Work is not explicitly rolled back when this state is entered.</span></span>  
  
-   <span data-ttu-id="9281d-126">**Došlo k chybě:** aktivity došlo k chybě a byl ukončen bez dokončení svou práci.</span><span class="sxs-lookup"><span data-stu-id="9281d-126">**Faulted:** The activity has encountered an error and has exited without completing its work.</span></span>  
  
 <span data-ttu-id="9281d-127">Aktivity zůstat v <xref:System.Activities.ActivityInstanceState.Executing> stav, když jsou nastavené jako trvalé nebo odpojeno.</span><span class="sxs-lookup"><span data-stu-id="9281d-127">Activities remain in the <xref:System.Activities.ActivityInstanceState.Executing> state when they are persisted or unloaded.</span></span>
