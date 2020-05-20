---
title: Výběr aktivity
description: V rámci Workflow Foundation aktivita výběru zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: eb59dc20919ed2d30a48f920ad154d4b0d99c41f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421459"
---
# <a name="pick-activity"></a><span data-ttu-id="d012d-103">Výběr aktivity</span><span class="sxs-lookup"><span data-stu-id="d012d-103">Pick Activity</span></span>
<span data-ttu-id="d012d-104"><xref:System.Activities.Statements.Pick>Aktivita zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.</span><span class="sxs-lookup"><span data-stu-id="d012d-104">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="d012d-105"><xref:System.Activities.Statements.Pick>Aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivit, kde každá <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivitou a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivitou.</span><span class="sxs-lookup"><span data-stu-id="d012d-105">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="d012d-106">V době spuštění jsou triggery pro všechny větve spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="d012d-106">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="d012d-107">Po dokončení jedné triggeru se spustí jeho odpovídající akce a všechny ostatní triggery se zruší.</span><span class="sxs-lookup"><span data-stu-id="d012d-107">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="d012d-108">Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity se podobá <xref:System.Workflow.Activities.ListenActivity> aktivitě .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="d012d-108">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="d012d-109">Následující snímek obrazovky z ukázka [použití sady SDK pro výběr aktivity](./samples/using-the-pick-activity.md) zobrazuje aktivitu výběru se dvěma větvemi.</span><span class="sxs-lookup"><span data-stu-id="d012d-109">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="d012d-110">Jedna větev obsahuje aktivační událost s názvem **čtení vstupu**, vlastní aktivita, která čte vstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d012d-110">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="d012d-111">Druhá větev obsahuje <xref:System.Activities.Statements.Delay> aktivační událost aktivity.</span><span class="sxs-lookup"><span data-stu-id="d012d-111">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="d012d-112">Pokud aktivita **čtení vstupu** přijme data před <xref:System.Activities.Statements.Delay> dokončením aktivity, <xref:System.Activities.Statements.Delay> zpoždění se zruší a do konzoly se zapíše pozdrav.</span><span class="sxs-lookup"><span data-stu-id="d012d-112">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="d012d-113">V opačném případě, pokud aktivita **čtení vstupu** neobdrží data v přiděleném čase, bude zrušena a do konzoly bude zapsána zpráva s časovým limitem.</span><span class="sxs-lookup"><span data-stu-id="d012d-113">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="d012d-114">Toto je společný vzor, pomocí kterého lze přidat časový limit k jakékoli akci.</span><span class="sxs-lookup"><span data-stu-id="d012d-114">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="d012d-116">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="d012d-116">Best practices</span></span>  
 <span data-ttu-id="d012d-117">Při použití výběru je větev, která se spustí, větev, jejíž Trigger se dokončí jako první.</span><span class="sxs-lookup"><span data-stu-id="d012d-117">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="d012d-118">V koncepčním případě se všechny triggery spouštějí paralelně a jedna aktivační událost mohla provést většinu logiky předtím, než se zruší dokončením jiného triggeru.</span><span class="sxs-lookup"><span data-stu-id="d012d-118">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="d012d-119">S ohledem na to, že při použití aktivity výběru se má při použití aktivity výběru postupovat, je třeba se zacházet s triggerem, který představuje jedinou událost, a vložit do něj co nejmenší logiku.</span><span class="sxs-lookup"><span data-stu-id="d012d-119">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="d012d-120">V ideálním případě by měl aktivační událost obsahovat pouze dostatečnou logiku pro příjem události a všechny zpracování této události by měly přejít do akce větve.</span><span class="sxs-lookup"><span data-stu-id="d012d-120">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="d012d-121">Tato metoda minimalizuje velikost překryvu mezi spuštěním triggerů.</span><span class="sxs-lookup"><span data-stu-id="d012d-121">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="d012d-122">Zvažte například <xref:System.Activities.Statements.Pick> se dvěma triggery, kde každá aktivační událost obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu následovanou další logikou.</span><span class="sxs-lookup"><span data-stu-id="d012d-122">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="d012d-123">Pokud další logika představuje bod nečinnosti, existuje možnost, že obě <xref:System.ServiceModel.Activities.Receive> aktivity budou úspěšně dokončeny.</span><span class="sxs-lookup"><span data-stu-id="d012d-123">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="d012d-124">Jedna aktivační událost se kompletně dokončí, zatímco další se částečně dokončí.</span><span class="sxs-lookup"><span data-stu-id="d012d-124">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="d012d-125">V některých scénářích přijímá zprávu a pak částečně dokončuje zpracování je nepřijmoutelné.</span><span class="sxs-lookup"><span data-stu-id="d012d-125">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="d012d-126">Proto při použití integrovaných aktivit zasílání zpráv, jako jsou <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> , zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používají v triggeru, <xref:System.ServiceModel.Activities.SendReply> a pokud je to možné, další logika by měla být vložena do akce.</span><span class="sxs-lookup"><span data-stu-id="d012d-126">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="d012d-127">Použití aktivity výběru v Návrháři</span><span class="sxs-lookup"><span data-stu-id="d012d-127">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="d012d-128">Chcete-li použít příkaz vybrat v návrháři, vyhledejte v sadě nástrojů příkaz **Vybrat** a **operace PickBranch** .</span><span class="sxs-lookup"><span data-stu-id="d012d-128">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="d012d-129">**Vyberte položku vybrat** a přetáhněte ji na plátno.</span><span class="sxs-lookup"><span data-stu-id="d012d-129">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="d012d-130">Ve výchozím nastavení bude nová aktivita **výběru** v Návrháři obsahovat dvě větve.</span><span class="sxs-lookup"><span data-stu-id="d012d-130">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="d012d-131">Chcete-li přidat další větve, přetáhněte aktivitu **operace PickBranch** a umístěte ji vedle existujících větví.</span><span class="sxs-lookup"><span data-stu-id="d012d-131">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="d012d-132">Aktivity mohou být do aktivity **výběru** přesunuty buď do oblasti **triggeru** , nebo do oblasti **akcí** všech **operace PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="d012d-132">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="d012d-133">Použití aktivity výběru v kódu</span><span class="sxs-lookup"><span data-stu-id="d012d-133">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="d012d-134"><xref:System.Activities.Statements.Pick>Aktivita se používá k naplnění <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivitami.</span><span class="sxs-lookup"><span data-stu-id="d012d-134">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="d012d-135"><xref:System.Activities.Statements.PickBranch>Jednotlivé aktivity mají <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity> .</span><span class="sxs-lookup"><span data-stu-id="d012d-135">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="d012d-136">Když zadaná aktivita dokončí provádění, <xref:System.Activities.Statements.PickBranch.Action%2A> provede se.</span><span class="sxs-lookup"><span data-stu-id="d012d-136">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="d012d-137">Následující příklad kódu ukazuje, jak použít <xref:System.Activities.Statements.Pick> aktivitu k implementaci časového limitu aktivity, která čte řádek z konzoly.</span><span class="sxs-lookup"><span data-stu-id="d012d-137">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine
                   {
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +
                           name.Get(ctx))
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
