---
title: Vyberte aktivitu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce650c931e94c76c669ee99068d2356f4b2ec32f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pick-activity"></a><span data-ttu-id="32012-102">Vyberte aktivitu</span><span class="sxs-lookup"><span data-stu-id="32012-102">Pick Activity</span></span>
<span data-ttu-id="32012-103"><xref:System.Activities.Statements.Pick> Aktivity zjednodušuje modelování sady aktivačních událostí a jejich odpovídající obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="32012-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="32012-104">A <xref:System.Activities.Statements.Pick> aktivity obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivity, kde každý <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivity a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivity.</span><span class="sxs-lookup"><span data-stu-id="32012-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="32012-105">V době provedení aktivačních událostí pro všechny větve provedení paralelně.</span><span class="sxs-lookup"><span data-stu-id="32012-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="32012-106">Po dokončení jedna aktivační událost, pak je jeho odpovídající akci provést, a všechny ostatní aktivační události došlo ke zrušení.</span><span class="sxs-lookup"><span data-stu-id="32012-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="32012-107">Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity je podobná [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="32012-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="32012-108">Následující snímek obrazovky [pomocí aktivity vyberte](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK – ukázka zobrazuje vybrat aktivitu se dvě větve.</span><span class="sxs-lookup"><span data-stu-id="32012-108">The following screenshot from the [Using the Pick Activity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="32012-109">Jeden větve je aktivační událost volá **vstup pro čtení**, vlastní aktivity, který čte vstupní z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="32012-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="32012-110">Má druhé větve <xref:System.Activities.Statements.Delay> aktivity aktivační události.</span><span class="sxs-lookup"><span data-stu-id="32012-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="32012-111">Pokud **vstup pro čtení** aktivita přijímá data před <xref:System.Activities.Statements.Delay> dokončení aktivity <xref:System.Activities.Statements.Delay> zpoždění, budou zrušeny a pohlednice zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="32012-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="32012-112">Jinak, pokud **vstup pro čtení** aktivity neobdrží data v přiděleném čase, pak budou zrušeny a zprávu vypršení časového limitu se zapíšou do konzoly.</span><span class="sxs-lookup"><span data-stu-id="32012-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="32012-113">Toto je běžný vzor použít k přidání vypršení časového limitu na každou akci.</span><span class="sxs-lookup"><span data-stu-id="32012-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 <span data-ttu-id="32012-114">![Vyberte aktivitu](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span><span class="sxs-lookup"><span data-stu-id="32012-114">![Pick Activity](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="32012-115">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="32012-115">Best practices</span></span>  
 <span data-ttu-id="32012-116">Při použití vybrat, větve, které provádí je větve, jejíž aktivační událost nejprve dokončí.</span><span class="sxs-lookup"><span data-stu-id="32012-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="32012-117">Koncepčně paralelně provádět všechny aktivační události a jedna aktivační událost může mít provést většinu svou logikou předtím, než je byla zrušena na dokončení jiné aktivační události.</span><span class="sxs-lookup"><span data-stu-id="32012-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="32012-118">Myslete na to obecných pokynů při používání vybrat aktivity je aktivační událost považovat za představující jednu událost a put jako málo logiku nejblíže do ní.</span><span class="sxs-lookup"><span data-stu-id="32012-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="32012-119">V ideálním případě aktivační událost musí obsahovat přesně akorát logiku přijímat události a veškeré zpracování této události by měli přejít do akce větve.</span><span class="sxs-lookup"><span data-stu-id="32012-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="32012-120">Tato metoda minimalizuje množství překryv mezi spuštění aktivačních událostí.</span><span class="sxs-lookup"><span data-stu-id="32012-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="32012-121">Představte si třeba <xref:System.Activities.Statements.Pick> s dvěma aktivačních událostí, kde jednotlivé aktivační události obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity následuje další logiku.</span><span class="sxs-lookup"><span data-stu-id="32012-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="32012-122">Pokud další logiku zavádí bod nečinnosti, pak je možné, i <xref:System.ServiceModel.Activities.Receive> úspěšném dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="32012-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="32012-123">Jedna aktivační událost se plně dokončení při jiné bude nedokončeným.</span><span class="sxs-lookup"><span data-stu-id="32012-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="32012-124">V některých případech nepřijatelná přijímá zprávy a částečně dokončení zpracování se.</span><span class="sxs-lookup"><span data-stu-id="32012-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="32012-125">Proto při používání předdefinovaných zasílání zpráv aktivity WF, jako <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, zatímco <xref:System.ServiceModel.Activities.Receive> se často používá v aktivační události, <xref:System.ServiceModel.Activities.SendReply> a jiné logiky měly být umístěny v akci, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="32012-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="32012-126">Pomocí vybrat aktivity v Návrháři</span><span class="sxs-lookup"><span data-stu-id="32012-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="32012-127">Pokud chcete použít vybrat v návrháři, Najít **vyberte** a **PickBranch** v panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="32012-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="32012-128">Přetáhnout myší **vyberte** na plátno.</span><span class="sxs-lookup"><span data-stu-id="32012-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="32012-129">Ve výchozím nastavení nový **vyberte** aktivity v návrháři bude obsahovat dvě větve.</span><span class="sxs-lookup"><span data-stu-id="32012-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="32012-130">Chcete-li přidat další větve, přetáhněte **PickBranch** aktivity a umístěte jej vedle existující větve.</span><span class="sxs-lookup"><span data-stu-id="32012-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="32012-131">Aktivity může být přetažen na **vyberte** aktivity do buď **aktivační událost** oblasti nebo **akce** oblasti kterékoli **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="32012-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="32012-132">Pomocí aktivity vyberte v kódu</span><span class="sxs-lookup"><span data-stu-id="32012-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="32012-133"><xref:System.Activities.Statements.Pick> Aktivita se používá naplněním jeho <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivity.</span><span class="sxs-lookup"><span data-stu-id="32012-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="32012-134"><xref:System.Activities.Statements.PickBranch> Aktivity každý mít <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="32012-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="32012-135">Po dokončení provádění zadaná aktivita <xref:System.Activities.Statements.PickBranch.Action%2A> provede.</span><span class="sxs-lookup"><span data-stu-id="32012-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="32012-136">Následující příklad kódu ukazuje, jak používat <xref:System.Activities.Statements.Pick> aktivity k implementaci vypršení časového limitu pro aktivitu, která přečte řádek z konzoly.</span><span class="sxs-lookup"><span data-stu-id="32012-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
