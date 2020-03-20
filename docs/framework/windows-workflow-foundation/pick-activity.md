---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182897"
---
# <a name="pick-activity"></a><span data-ttu-id="c9078-102">Výběr aktivity</span><span class="sxs-lookup"><span data-stu-id="c9078-102">Pick Activity</span></span>
<span data-ttu-id="c9078-103">Aktivita <xref:System.Activities.Statements.Pick> zjednodušuje modelování sady aktivačních událostí následovaných odpovídajícími obslužnými rutinami.</span><span class="sxs-lookup"><span data-stu-id="c9078-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="c9078-104">Aktivita <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.PickBranch> obsahuje kolekci aktivit, <xref:System.Activities.Statements.PickBranch> kde každý je <xref:System.Activities.Statements.PickBranch.Trigger%2A> párování <xref:System.Activities.Statements.PickBranch.Action%2A> mezi aktivitou a aktivitou.</span><span class="sxs-lookup"><span data-stu-id="c9078-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="c9078-105">V době spuštění aktivační události pro všechny větve jsou prováděny paralelně.</span><span class="sxs-lookup"><span data-stu-id="c9078-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="c9078-106">Po dokončení jedné aktivační události je provedena odpovídající akce a všechny ostatní aktivační události jsou zrušeny.</span><span class="sxs-lookup"><span data-stu-id="c9078-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="c9078-107">Chování aktivity [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> je podobné aktivitě rozhraní .NET Framework 3.5. <xref:System.Workflow.Activities.ListenActivity></span><span class="sxs-lookup"><span data-stu-id="c9078-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="c9078-108">Následující snímek obrazovky z [ukázky Použití vyskladnění aktivity](./samples/using-the-pick-activity.md) SDK zobrazuje aktivitu vyskladnění se dvěma větvemi.</span><span class="sxs-lookup"><span data-stu-id="c9078-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="c9078-109">Jedna větev má aktivační událost nazvanou **Vstup pro čtení**, vlastní aktivitu, která čte vstup z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c9078-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="c9078-110">Druhá větev <xref:System.Activities.Statements.Delay> má aktivační událost aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9078-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="c9078-111">Pokud **čtení vstupní** aktivity obdrží <xref:System.Activities.Statements.Delay> data před <xref:System.Activities.Statements.Delay> dokončením aktivity Delay bude zrušena a bude zapsán pozdrav do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9078-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="c9078-112">V opačném případě pokud **čtení vstupní** aktivity nepřijímá data v přiděleném čase, pak bude zrušena a zpráva o časovém odhlášení bude zapsána do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9078-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="c9078-113">Toto je běžný vzor, který se používá k přidání časového opovce pro libovolnou akci.</span><span class="sxs-lookup"><span data-stu-id="c9078-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="c9078-115">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="c9078-115">Best practices</span></span>  
 <span data-ttu-id="c9078-116">Při použití Vyskladnění je větev, která se spustí, větev, jejíž aktivační událost se dokončí jako první.</span><span class="sxs-lookup"><span data-stu-id="c9078-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="c9078-117">Koncepčně všechny aktivační události spustit paralelně a jeden aktivační událost může mít provedeny většinu jeho logiky před zrušením dokončení jiné aktivační události.</span><span class="sxs-lookup"><span data-stu-id="c9078-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="c9078-118">S ohledem na to obecné vodítko následovat při použití pick aktivity je považovat aktivační událost jako představující jednu událost a dát co nejméně logiky, jak je to možné do něj.</span><span class="sxs-lookup"><span data-stu-id="c9078-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="c9078-119">V ideálním případě aktivační událost by měla obsahovat pouze dostatek logiky pro příjem události a všechny zpracování této události by měl přejít do akce větve.</span><span class="sxs-lookup"><span data-stu-id="c9078-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="c9078-120">Tato metoda minimalizuje množství překrytí mezi provádění aktivačních událostí.</span><span class="sxs-lookup"><span data-stu-id="c9078-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="c9078-121">Zvažte například <xref:System.Activities.Statements.Pick> s dvěma aktivačními událostmi, kde každá aktivační událost obsahuje aktivitu <xref:System.ServiceModel.Activities.Receive> následovanou další logikou.</span><span class="sxs-lookup"><span data-stu-id="c9078-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="c9078-122">Pokud další logika zavádí bod nečinnosti, pak <xref:System.ServiceModel.Activities.Receive> je možnost obě aktivity dokončení úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c9078-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="c9078-123">Jedna aktivační událost bude plně dokončena, zatímco druhá bude částečně dokončena.</span><span class="sxs-lookup"><span data-stu-id="c9078-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="c9078-124">V některých případech přijetí zprávy a potom částečné dokončení zpracování je nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="c9078-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="c9078-125">Proto při použití wf integrované zasílání zpráv <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>aktivity, jako je například a , zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používá v aktivační události <xref:System.ServiceModel.Activities.SendReply> a další logika by měla být uvedena v akci, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="c9078-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="c9078-126">Použití aktivity vyskladnění v návrháři</span><span class="sxs-lookup"><span data-stu-id="c9078-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="c9078-127">Chcete-li použít Pick v návrháři, **najděte** pick a **pickbranch** v panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c9078-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="c9078-128">Přetáhněte na plátno **vyberte.**</span><span class="sxs-lookup"><span data-stu-id="c9078-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="c9078-129">Ve výchozím nastavení bude nová aktivita **vyskladnění** v návrháři obsahovat dvě větve.</span><span class="sxs-lookup"><span data-stu-id="c9078-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="c9078-130">Chcete-li přidat další větve, přetáhněte aktivitu **PickBranch** a přetáhněte ji vedle existujících větví.</span><span class="sxs-lookup"><span data-stu-id="c9078-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="c9078-131">Aktivity mohou být vynechány na **aktivitu vyskladnění** do oblasti **Trigger** nebo do oblasti **akce** libovolné **větve pickbranch**.</span><span class="sxs-lookup"><span data-stu-id="c9078-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="c9078-132">Použití aktivity vyskladnění v kódu</span><span class="sxs-lookup"><span data-stu-id="c9078-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="c9078-133">Aktivita se <xref:System.Activities.Statements.Pick> používá vyplněním <xref:System.Activities.Statements.Pick.Branches%2A> své <xref:System.Activities.Statements.PickBranch> sbírky aktivitami.</span><span class="sxs-lookup"><span data-stu-id="c9078-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="c9078-134">Aktivity <xref:System.Activities.Statements.PickBranch> každý <xref:System.Activities.Statements.PickBranch.Trigger%2A> mají vlastnost <xref:System.Activities.Activity>typu .</span><span class="sxs-lookup"><span data-stu-id="c9078-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="c9078-135">Po dokončení provádění zadané aktivity provede. <xref:System.Activities.Statements.PickBranch.Action%2A></span><span class="sxs-lookup"><span data-stu-id="c9078-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="c9078-136">Následující příklad kódu ukazuje, jak <xref:System.Activities.Statements.Pick> použít aktivitu k implementaci časového období pro aktivitu, která čte řádek z konzoly.</span><span class="sxs-lookup"><span data-stu-id="c9078-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
