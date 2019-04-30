---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909416"
---
# <a name="pick-activity"></a><span data-ttu-id="eb262-102">Výběr aktivity</span><span class="sxs-lookup"><span data-stu-id="eb262-102">Pick Activity</span></span>
<span data-ttu-id="eb262-103"><xref:System.Activities.Statements.Pick> Aktivity zjednodušuje modelování sadu triggerů událostí a jejich odpovídající obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="eb262-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="eb262-104">A <xref:System.Activities.Statements.Pick> aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivity, ve kterém každý <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivity a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivity.</span><span class="sxs-lookup"><span data-stu-id="eb262-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="eb262-105">V době spuštění aktivační události pro všechny větve spouští paralelně.</span><span class="sxs-lookup"><span data-stu-id="eb262-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="eb262-106">Po dokončení jednu aktivační událost, pak je její odpovídající akci provést, a další triggery se zruší.</span><span class="sxs-lookup"><span data-stu-id="eb262-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="eb262-107">Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity se podobá [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="eb262-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="eb262-108">Na následujícím snímku obrazovky z [pomocí aktivity vyberte](./samples/using-the-pick-activity.md) SDK – ukázka ukazuje aktivitě Pick se dvě větve.</span><span class="sxs-lookup"><span data-stu-id="eb262-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="eb262-109">Jedna větev obsahuje trigger s názvem **čtení vstup**, vlastní aktivitu, která načte vstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="eb262-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="eb262-110">Druhý větev <xref:System.Activities.Statements.Delay> aktivační událost pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="eb262-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="eb262-111">Pokud **čtení vstup** aktivita přijímá data před <xref:System.Activities.Statements.Delay> dokončení aktivity <xref:System.Activities.Statements.Delay> zruší zpoždění a pozdrav se zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="eb262-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="eb262-112">Jinak, pokud **čtení vstup** aktivity nedostane data v přiděleném čase, pak se zruší a časový limit zprávy, se zapíšou do konzoly.</span><span class="sxs-lookup"><span data-stu-id="eb262-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="eb262-113">To se běžně používá k přidání vypršení časového limitu na každou akci.</span><span class="sxs-lookup"><span data-stu-id="eb262-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="eb262-115">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="eb262-115">Best practices</span></span>  
 <span data-ttu-id="eb262-116">Při použití výběru, je větev, která spustí větev, jejíž aktivační událost dokončení první.</span><span class="sxs-lookup"><span data-stu-id="eb262-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="eb262-117">Koncepčně paralelně spustit všechny aktivační události a jedna aktivační událost může mít provedeny většinou svou logikou předtím, než ji zruší dokončení další trigger.</span><span class="sxs-lookup"><span data-stu-id="eb262-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="eb262-118">Myslete na to obecných pokynů při použití aktivity Pick se bude považovat aktivační událost jako jedna událost a vložit jako malé logikou, jako je to možné do něj.</span><span class="sxs-lookup"><span data-stu-id="eb262-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="eb262-119">V ideálním případě aktivační událost může obsahovat jenom dostatek logiku pro přijetí události a veškeré zpracování této události by měly patřit do akce větve.</span><span class="sxs-lookup"><span data-stu-id="eb262-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="eb262-120">Tato metoda minimalizuje množství překrytí spuštění aktivační události.</span><span class="sxs-lookup"><span data-stu-id="eb262-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="eb262-121">Představte si třeba <xref:System.Activities.Statements.Pick> s dvěma aktivačními procedurami, kde každá aktivační událost obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity za nímž následuje další logiku.</span><span class="sxs-lookup"><span data-stu-id="eb262-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="eb262-122">Pokud nečinnosti bodu zavádí další logiku, pak je možné obou <xref:System.ServiceModel.Activities.Receive> úspěšném dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="eb262-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="eb262-123">Jedna aktivační událost se plně kompletní při jiné se částečně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="eb262-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="eb262-124">V některých případech nepřijatelné přijímat zprávy a potom částečně dokončí zpracování.</span><span class="sxs-lookup"><span data-stu-id="eb262-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="eb262-125">Proto při použití předdefinovaných zasílání zpráv aktivity WF, jako <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používá v triggeru, <xref:System.ServiceModel.Activities.SendReply> a další logiky měly být umístěny v akci, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="eb262-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="eb262-126">Použití aktivity Pick v Návrháři</span><span class="sxs-lookup"><span data-stu-id="eb262-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="eb262-127">Použijte výběr v návrháři, Najít **vyberte** a **PickBranch** na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="eb262-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="eb262-128">Přetáhnout myší **vyberte** na plátno.</span><span class="sxs-lookup"><span data-stu-id="eb262-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="eb262-129">Ve výchozím nastavení nový **vyberte** aktivity v návrháři bude obsahovat dvě větve.</span><span class="sxs-lookup"><span data-stu-id="eb262-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="eb262-130">Chcete-li přidat další větve, přetáhněte **PickBranch** aktivity a umístěte ho vedle existující větve.</span><span class="sxs-lookup"><span data-stu-id="eb262-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="eb262-131">Aktivity může být přetaženy **vyberte** aktivitu buď **aktivační událost** oblasti nebo **akce** oblasti kterékoli **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="eb262-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="eb262-132">Použití aktivity vybrat v kódu</span><span class="sxs-lookup"><span data-stu-id="eb262-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="eb262-133"><xref:System.Activities.Statements.Pick> Aktivita používá naplnění jeho <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivity.</span><span class="sxs-lookup"><span data-stu-id="eb262-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="eb262-134"><xref:System.Activities.Statements.PickBranch> Každé aktivity mají <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="eb262-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="eb262-135">Po dokončení provádění, zadané aktivita <xref:System.Activities.Statements.PickBranch.Action%2A> spustí.</span><span class="sxs-lookup"><span data-stu-id="eb262-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="eb262-136">Následující příklad kódu ukazuje, jak používat <xref:System.Activities.Statements.Pick> aktivity k implementaci vypršení časového limitu pro aktivitu, která přečte řádek z konzoly.</span><span class="sxs-lookup"><span data-stu-id="eb262-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
