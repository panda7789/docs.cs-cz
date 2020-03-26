---
title: Pracovní postupy vývojového diagramu
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: b84b0de34f8869d9775fe0694e74c340cc16a6b3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249061"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="c0728-102">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="c0728-102">Flowchart Workflows</span></span>

<span data-ttu-id="c0728-103">Vývojový diagram je dobře známé paradigma pro navrhování programů.</span><span class="sxs-lookup"><span data-stu-id="c0728-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="c0728-104">Aktivita vývojového diagramu se obvykle používá k implementaci nesekvenčních `FlowDecision` pracovních postupů, ale lze ji použít pro sekvenční pracovní postupy, pokud se nepoužívají žádné uzly.</span><span class="sxs-lookup"><span data-stu-id="c0728-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="c0728-105">Struktura pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="c0728-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="c0728-106">Aktivita vývojového diagramu je aktivita, která obsahuje kolekci aktivit, které mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="c0728-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="c0728-107">Vývojové diagramy také obsahují <xref:System.Activities.Statements.FlowDecision> prvky řízení toku, jako je například <xref:System.Activities.Statements.FlowSwitch%601> přímé provádění mezi obsažené aktivity na základě hodnot proměnných.</span><span class="sxs-lookup"><span data-stu-id="c0728-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="c0728-108">Typy uzlů toku</span><span class="sxs-lookup"><span data-stu-id="c0728-108">Types of flow nodes</span></span>

 <span data-ttu-id="c0728-109">Různé typy prvků se používají v závislosti na typu řízení toku požadované při spuštění prvku.</span><span class="sxs-lookup"><span data-stu-id="c0728-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="c0728-110">Mezi typy prvků vývojového diagramu patří:</span><span class="sxs-lookup"><span data-stu-id="c0728-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="c0728-111">`FlowStep`- Modely jeden krok provedení ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="c0728-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="c0728-112">`FlowDecision`- Provádění větví na základě logické <xref:System.Activities.Statements.If>podmínky, podobně jako .</span><span class="sxs-lookup"><span data-stu-id="c0728-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="c0728-113">`FlowSwitch`– Exekuce poboček založená <xref:System.Activities.Statements.Switch%601>na výhradním přepínači, podobně jako .</span><span class="sxs-lookup"><span data-stu-id="c0728-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="c0728-114">Každý odkaz `Action` má vlastnost, <xref:System.Activities.ActivityAction> která definuje, které lze použít ke `Next` spuštění podřízené aktivity a jeden nebo více vlastností, které definují, který prvek nebo prvky spustit při dokončení provádění aktuální prvek.</span><span class="sxs-lookup"><span data-stu-id="c0728-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="c0728-115">Vytvoření základní sekvence aktivit s uzlem FlowStep</span><span class="sxs-lookup"><span data-stu-id="c0728-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="c0728-116">Chcete-li modelovat základní pořadí, ve `FlowStep` kterém dvě aktivity spustit v pořadí, prvek se používá.</span><span class="sxs-lookup"><span data-stu-id="c0728-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="c0728-117">V následujícím příkladu `FlowStep` dva prvky se používají k provedení dvou aktivit v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c0728-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="c0728-118">Vytvoření podmíněného vývojového diagramu s uzly FlowDecision</span><span class="sxs-lookup"><span data-stu-id="c0728-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="c0728-119">Chcete-li modelovat uzel podmíněného toku v pracovním postupu vývojového diagramu (to znamená vytvořit <xref:System.Activities.Statements.FlowDecision> propojení, které funguje jako symbol rozhodnutí tradičního vývojového diagramu), použije se uzel.</span><span class="sxs-lookup"><span data-stu-id="c0728-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="c0728-120">Vlastnost <xref:System.Activities.Statements.FlowDecision.Condition%2A> uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> vlastnosti a <xref:System.Activities.Statements.FlowDecision.False%2A> jsou nastaveny <xref:System.Activities.Statements.FlowNode> na `true` instance, které mají být provedeny, pokud výraz vyhodnotí nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c0728-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="c0728-121">Následující příklad ukazuje, jak definovat pracovní <xref:System.Activities.Statements.FlowDecision> postup, který používá uzel.</span><span class="sxs-lookup"><span data-stu-id="c0728-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="c0728-122">Vytvoření výhradního přepínače s uzly FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="c0728-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="c0728-123">Chcete-li modelovat vývojový diagram, ve kterém je <xref:System.Activities.Statements.FlowSwitch%601> vybrána jedna výhradní cesta na základě odpovídající hodnoty, použije se uzel.</span><span class="sxs-lookup"><span data-stu-id="c0728-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="c0728-124">Vlastnost <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> je nastavena <xref:System.Activities.Activity%601> na parametr <xref:System.Object> typu, který definuje hodnotu, proti které mají odpovídat volbám.</span><span class="sxs-lookup"><span data-stu-id="c0728-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="c0728-125">Vlastnost <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objektů tak, aby odpovídaly podmíněnému <xref:System.Activities.Statements.FlowNode> výrazu a sadu objektů, které definují, jak by mělo tok spuštění, pokud daný případ odpovídá podmíněnému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c0728-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="c0728-126">Také <xref:System.Activities.Statements.FlowSwitch%601> definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak by mělo tok spuštění, pokud žádné případy odpovídají výrazu podmínky.</span><span class="sxs-lookup"><span data-stu-id="c0728-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="c0728-127">Následující příklad ukazuje, jak definovat pracovní <xref:System.Activities.Statements.FlowSwitch%601> postup, který používá prvek.</span><span class="sxs-lookup"><span data-stu-id="c0728-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
