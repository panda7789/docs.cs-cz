---
title: Pracovní postupy vývojového diagramu
description: Tento článek popisuje aktivitu vývojového diagramu, která se obvykle používá k implementaci nesekvenčních pracovních postupů v rámci Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: ce0661653a1d50b3f7264246b810faabbd12bf5f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419912"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="76e92-103">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="76e92-103">Flowchart Workflows</span></span>

<span data-ttu-id="76e92-104">Vývojový diagram je dobře známé paradigma pro navrhování programů.</span><span class="sxs-lookup"><span data-stu-id="76e92-104">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="76e92-105">Aktivita vývojového diagramu se obvykle používá k implementaci nesekvenčních pracovních postupů, ale je možné ji použít pro sekvenční pracovní postupy, pokud `FlowDecision` se nepoužívají žádné uzly.</span><span class="sxs-lookup"><span data-stu-id="76e92-105">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="76e92-106">Struktura pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="76e92-106">Flowchart workflow structure</span></span>

 <span data-ttu-id="76e92-107">Aktivita vývojového diagramu je aktivita, která obsahuje kolekci aktivit, které mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="76e92-107">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="76e92-108">Vývojové diagramy také obsahují prvky řízení toku, například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> , které přímo vykonává mezi obsaženými aktivitami na základě hodnot proměnných.</span><span class="sxs-lookup"><span data-stu-id="76e92-108">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="76e92-109">Typy uzlů toků</span><span class="sxs-lookup"><span data-stu-id="76e92-109">Types of flow nodes</span></span>

 <span data-ttu-id="76e92-110">Různé typy prvků jsou používány v závislosti na typu řízení toku vyžadovaného při spuštění elementu.</span><span class="sxs-lookup"><span data-stu-id="76e92-110">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="76e92-111">Mezi typy prvků vývojového diagramu patří:</span><span class="sxs-lookup"><span data-stu-id="76e92-111">Types of flowchart elements include:</span></span>

- <span data-ttu-id="76e92-112">`FlowStep`– Modeluje jeden krok provádění ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="76e92-112">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="76e92-113">`FlowDecision`– Spouštění větví na základě logické podmínky, podobně jako <xref:System.Activities.Statements.If> .</span><span class="sxs-lookup"><span data-stu-id="76e92-113">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="76e92-114">`FlowSwitch`– Spuštění větví na základě výhradního přepínače, podobně jako <xref:System.Activities.Statements.Switch%601> .</span><span class="sxs-lookup"><span data-stu-id="76e92-114">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="76e92-115">Každé propojení má `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , který lze použít ke spouštění podřízených aktivit, a jednu nebo více `Next` vlastností, které definují, který prvek nebo prvky mají být provedeny, když aktuální element dokončí provádění.</span><span class="sxs-lookup"><span data-stu-id="76e92-115">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="76e92-116">Vytvoření sekvence základní aktivity pomocí uzlu FlowStep</span><span class="sxs-lookup"><span data-stu-id="76e92-116">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="76e92-117">Chcete-li modelovat základní pořadí, ve kterém jsou dvě aktivity spouštěny, `FlowStep` je použit element.</span><span class="sxs-lookup"><span data-stu-id="76e92-117">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="76e92-118">V následujícím příkladu `FlowStep` se dva prvky používají ke spuštění dvou aktivit v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="76e92-118">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="76e92-119">Vytvoření podmíněného vývojového diagramu pomocí uzlu použitím objektu FlowDecision</span><span class="sxs-lookup"><span data-stu-id="76e92-119">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="76e92-120">Pokud chcete modelovat uzel podmíněného toku v pracovním postupu vývojového diagramu (to znamená, že chcete vytvořit odkaz, který funguje jako tradiční symbol rozhodnutí vývojového diagramu), <xref:System.Activities.Statements.FlowDecision> použije se uzel.</span><span class="sxs-lookup"><span data-stu-id="76e92-120">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="76e92-121"><xref:System.Activities.Statements.FlowDecision.Condition%2A>Vlastnost uzlu je nastavena na výraz definující podmínku a <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti a jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které mají být provedeny, pokud je výraz vyhodnocen jako `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="76e92-121">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="76e92-122">Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowDecision> uzel.</span><span class="sxs-lookup"><span data-stu-id="76e92-122">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="76e92-123">Vytvoření výhradního přepínače pomocí uzlu FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="76e92-123">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="76e92-124">Chcete-li modelovat vývojový diagram, ve kterém je vybrána jedna exkluzivní cesta na základě vyhovující hodnoty, <xref:System.Activities.Statements.FlowSwitch%601> je použit uzel.</span><span class="sxs-lookup"><span data-stu-id="76e92-124">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="76e92-125"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Vlastnost je nastavena na hodnotu <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> , který definuje hodnotu pro porovnání volby s.</span><span class="sxs-lookup"><span data-stu-id="76e92-125">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="76e92-126"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Vlastnost definuje slovník klíčů a objektů, které <xref:System.Activities.Statements.FlowNode> mají být porovnány s podmíněným výrazem, a sadou <xref:System.Activities.Statements.FlowNode> objektů, které definují, jak by měl tok provádět, pokud daný případ odpovídá podmíněnému výrazu.</span><span class="sxs-lookup"><span data-stu-id="76e92-126">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="76e92-127"><xref:System.Activities.Statements.FlowSwitch%601>Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje způsob, jakým by měl být provádění tok, pokud žádné případy neodpovídají výrazu podmínky.</span><span class="sxs-lookup"><span data-stu-id="76e92-127">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="76e92-128">Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowSwitch%601> prvek.</span><span class="sxs-lookup"><span data-stu-id="76e92-128">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
