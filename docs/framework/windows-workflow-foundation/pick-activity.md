---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 51caf020042212b570ae915ead00a4225df2c588
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283183"
---
# <a name="pick-activity"></a><span data-ttu-id="74dcb-102">Výběr aktivity</span><span class="sxs-lookup"><span data-stu-id="74dcb-102">Pick Activity</span></span>
<span data-ttu-id="74dcb-103">Aktivita <xref:System.Activities.Statements.Pick> zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.</span><span class="sxs-lookup"><span data-stu-id="74dcb-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="74dcb-104">Aktivita <xref:System.Activities.Statements.Pick> obsahuje kolekci aktivit <xref:System.Activities.Statements.PickBranch>, kde jsou jednotlivé <xref:System.Activities.Statements.PickBranch> párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivitou a aktivitou <xref:System.Activities.Statements.PickBranch.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="74dcb-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="74dcb-105">V době spuštění jsou triggery pro všechny větve spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="74dcb-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="74dcb-106">Po dokončení jedné triggeru se spustí jeho odpovídající akce a všechny ostatní triggery se zruší.</span><span class="sxs-lookup"><span data-stu-id="74dcb-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="74dcb-107">Chování aktivity [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> je podobné aktivitě .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity>.</span><span class="sxs-lookup"><span data-stu-id="74dcb-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="74dcb-108">Následující snímek obrazovky z ukázka [použití sady SDK pro výběr aktivity](./samples/using-the-pick-activity.md) zobrazuje aktivitu výběru se dvěma větvemi.</span><span class="sxs-lookup"><span data-stu-id="74dcb-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="74dcb-109">Jedna větev obsahuje aktivační událost s názvem **čtení vstupu**, vlastní aktivita, která čte vstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="74dcb-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="74dcb-110">Druhá větev má Trigger <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="74dcb-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="74dcb-111">Pokud aktivita **čtení vstupu** přijme data před dokončením <xref:System.Activities.Statements.Delay> aktivity, <xref:System.Activities.Statements.Delay> zpoždění se zruší a do konzoly se zapíše pozdrav.</span><span class="sxs-lookup"><span data-stu-id="74dcb-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="74dcb-112">V opačném případě, pokud aktivita **čtení vstupu** neobdrží data v přiděleném čase, bude zrušena a do konzoly bude zapsána zpráva s časovým limitem.</span><span class="sxs-lookup"><span data-stu-id="74dcb-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="74dcb-113">Toto je společný vzor, pomocí kterého lze přidat časový limit k jakékoli akci.</span><span class="sxs-lookup"><span data-stu-id="74dcb-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="74dcb-115">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="74dcb-115">Best practices</span></span>  
 <span data-ttu-id="74dcb-116">Při použití výběru je větev, která se spustí, větev, jejíž Trigger se dokončí jako první.</span><span class="sxs-lookup"><span data-stu-id="74dcb-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="74dcb-117">V koncepčním případě se všechny triggery spouštějí paralelně a jedna aktivační událost mohla provést většinu logiky předtím, než se zruší dokončením jiného triggeru.</span><span class="sxs-lookup"><span data-stu-id="74dcb-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="74dcb-118">S ohledem na to, že při použití aktivity výběru se má při použití aktivity výběru postupovat, je třeba se zacházet s triggerem, který představuje jedinou událost, a vložit do něj co nejmenší logiku.</span><span class="sxs-lookup"><span data-stu-id="74dcb-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="74dcb-119">V ideálním případě by měl aktivační událost obsahovat pouze dostatečnou logiku pro příjem události a všechny zpracování této události by měly přejít do akce větve.</span><span class="sxs-lookup"><span data-stu-id="74dcb-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="74dcb-120">Tato metoda minimalizuje velikost překryvu mezi spuštěním triggerů.</span><span class="sxs-lookup"><span data-stu-id="74dcb-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="74dcb-121">Představte si například <xref:System.Activities.Statements.Pick> se dvěma triggery, kde každá aktivační událost obsahuje aktivitu <xref:System.ServiceModel.Activities.Receive> následovanou další logikou.</span><span class="sxs-lookup"><span data-stu-id="74dcb-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="74dcb-122">Pokud další logika zavádí bod nečinnosti, existuje možnost, že obě <xref:System.ServiceModel.Activities.Receive> aktivity budou úspěšně dokončeny.</span><span class="sxs-lookup"><span data-stu-id="74dcb-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="74dcb-123">Jedna aktivační událost se kompletně dokončí, zatímco další se částečně dokončí.</span><span class="sxs-lookup"><span data-stu-id="74dcb-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="74dcb-124">V některých scénářích přijímá zprávu a pak částečně dokončuje zpracování je nepřijmoutelné.</span><span class="sxs-lookup"><span data-stu-id="74dcb-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="74dcb-125">Proto při použití integrovaných aktivit zasílání zpráv, jako jsou <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive> se běžně používá v triggeru, <xref:System.ServiceModel.Activities.SendReply> a další logiky by měly být vloženy do akce, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="74dcb-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="74dcb-126">Použití aktivity výběru v Návrháři</span><span class="sxs-lookup"><span data-stu-id="74dcb-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="74dcb-127">Chcete-li použít příkaz vybrat v návrháři, vyhledejte v sadě nástrojů příkaz **Vybrat** a **operace PickBranch** .</span><span class="sxs-lookup"><span data-stu-id="74dcb-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="74dcb-128">**Vyberte položku vybrat** a přetáhněte ji na plátno.</span><span class="sxs-lookup"><span data-stu-id="74dcb-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="74dcb-129">Ve výchozím nastavení bude nová aktivita **výběru** v Návrháři obsahovat dvě větve.</span><span class="sxs-lookup"><span data-stu-id="74dcb-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="74dcb-130">Chcete-li přidat další větve, přetáhněte aktivitu **operace PickBranch** a umístěte ji vedle existujících větví.</span><span class="sxs-lookup"><span data-stu-id="74dcb-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="74dcb-131">Aktivity mohou být do aktivity **výběru** přesunuty buď do oblasti **triggeru** , nebo do oblasti **akcí** všech **operace PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="74dcb-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="74dcb-132">Použití aktivity výběru v kódu</span><span class="sxs-lookup"><span data-stu-id="74dcb-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="74dcb-133"><xref:System.Activities.Statements.Pick> aktivita se používá k naplnění kolekce <xref:System.Activities.Statements.Pick.Branches%2A> s <xref:System.Activities.Statements.PickBranch> aktivitami.</span><span class="sxs-lookup"><span data-stu-id="74dcb-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="74dcb-134"><xref:System.Activities.Statements.PickBranch> aktivity mají vlastnost <xref:System.Activities.Statements.PickBranch.Trigger%2A> typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="74dcb-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="74dcb-135">Když zadaná aktivita dokončí provádění, <xref:System.Activities.Statements.PickBranch.Action%2A> se spustí.</span><span class="sxs-lookup"><span data-stu-id="74dcb-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="74dcb-136">Následující příklad kódu ukazuje, jak použít aktivitu <xref:System.Activities.Statements.Pick> k implementaci časového limitu aktivity, která čte řádek z konzoly.</span><span class="sxs-lookup"><span data-stu-id="74dcb-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
