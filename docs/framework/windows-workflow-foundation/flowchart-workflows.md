---
title: "Vývojový diagram pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 568725f9a112756a773eddab9f56411f4d4fa86e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="flowchart-workflows"></a><span data-ttu-id="9df59-102">Vývojový diagram pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9df59-102">Flowchart Workflows</span></span>
<span data-ttu-id="9df59-103">Vývojový diagram je dobře známé zlepší pro návrh programy.</span><span class="sxs-lookup"><span data-stu-id="9df59-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="9df59-104">Vývojový diagram aktivity se obvykle používá k implementaci nesekvenční pracovní postupy, ale lze použít pro sekvenční pracovní postupy, pokud žádné `FlowDecision` uzly se používají.</span><span class="sxs-lookup"><span data-stu-id="9df59-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>  
  
## <a name="flowchart-workflow-structure"></a><span data-ttu-id="9df59-105">Vývojový diagram pracovního postupu struktura</span><span class="sxs-lookup"><span data-stu-id="9df59-105">Flowchart Workflow Structure</span></span>  
 <span data-ttu-id="9df59-106">Vývojový diagram aktivity je aktivitou, která obsahuje kolekci aktivit, které by šlo spustit.</span><span class="sxs-lookup"><span data-stu-id="9df59-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="9df59-107">Na vývojových diagramech také obsahovat toku ovládací prvky, jako například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> který přímé provádění mezi obsažené aktivity podle hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="9df59-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>  
  
## <a name="types-of-flow-nodes"></a><span data-ttu-id="9df59-108">Typy uzlů toku</span><span class="sxs-lookup"><span data-stu-id="9df59-108">Types of Flow Nodes</span></span>  
 <span data-ttu-id="9df59-109">V závislosti na typu řízení toku požadováno, když provádí elementu se používají různé typy elementů.</span><span class="sxs-lookup"><span data-stu-id="9df59-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="9df59-110">Typy prvků vývojový diagram patří:</span><span class="sxs-lookup"><span data-stu-id="9df59-110">Types of flowchart elements include:</span></span>  
  
-   <span data-ttu-id="9df59-111">`FlowStep`-Modely krok spouštění v vývojový diagram.</span><span class="sxs-lookup"><span data-stu-id="9df59-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>  
  
-   <span data-ttu-id="9df59-112">`FlowDecision`-Větví provádění založené na podmínce logické, podobně jako <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="9df59-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>  
  
-   <span data-ttu-id="9df59-113">`FlowSwitch`– Spuštění větví podle výhradní přepínače, podobně jako <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="9df59-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>  
  
 <span data-ttu-id="9df59-114">Každé propojení nemá `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , můžete použít ke spuštění podřízené aktivity a jednu nebo více `Next` vlastnosti, které definují, které element nebo elementy provést po dokončení provádění aktuálního elementu.</span><span class="sxs-lookup"><span data-stu-id="9df59-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="9df59-115">Vytváření pořadí základní aktivity s uzlem FlowStep</span><span class="sxs-lookup"><span data-stu-id="9df59-115">Creating a Basic Activity Sequence with a FlowStep Node</span></span>  
 <span data-ttu-id="9df59-116">Modelování základní pořadí, ve kterém se dvě aktivity spustit zase `FlowStep` element se používá.</span><span class="sxs-lookup"><span data-stu-id="9df59-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="9df59-117">V následujícím příkladu dva `FlowStep` prvky se používají ke spouštění dvě aktivity v pořadí.</span><span class="sxs-lookup"><span data-stu-id="9df59-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="9df59-118">Vytvoření podmíněného vývojový diagram s uzlem FlowDecision</span><span class="sxs-lookup"><span data-stu-id="9df59-118">Creating a Conditional Flowchart with a FlowDecision Node</span></span>  
 <span data-ttu-id="9df59-119">Modelování postup podmíněného uzel v pracovním postupu vývojový diagram (to znamená, chcete-li vytvořit odkaz, který funguje jako tradiční vývojový diagram rozhodování symbol), <xref:System.Activities.Statements.FlowDecision> uzel se používá.</span><span class="sxs-lookup"><span data-stu-id="9df59-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="9df59-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> a <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které chcete provést, pokud je výsledkem výrazu `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="9df59-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="9df59-121">Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowDecision> uzlu.</span><span class="sxs-lookup"><span data-stu-id="9df59-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="9df59-122">Vytváření výhradní přepínače s uzlem FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="9df59-122">Creating an Exclusive Switch with a FlowSwitch Node</span></span>  
 <span data-ttu-id="9df59-123">Pro modelování vývojový diagram, ve které jedna je vybrána výhradní cesta založené na odpovídající hodnotu <xref:System.Activities.Statements.FlowSwitch%601> uzel se používá.</span><span class="sxs-lookup"><span data-stu-id="9df59-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="9df59-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Je nastavena na <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> definuje hodnotu podle voleb proti.</span><span class="sxs-lookup"><span data-stu-id="9df59-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="9df59-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Vlastnost definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objekty, které se shodují s podmíněným výrazem a sadu <xref:System.Activities.Statements.FlowNode> objekty, které definují, jak by měla toku spuštění, pokud daný případ odpovídá podmíněným výrazem.</span><span class="sxs-lookup"><span data-stu-id="9df59-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="9df59-126"><xref:System.Activities.Statements.FlowSwitch%601> Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak by měla toku spuštění, pokud žádné případy odpovídat výrazu podmínky.</span><span class="sxs-lookup"><span data-stu-id="9df59-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="9df59-127">Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowSwitch%601> elementu.</span><span class="sxs-lookup"><span data-stu-id="9df59-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
