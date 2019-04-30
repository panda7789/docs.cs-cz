---
title: Pracovní postupy vývojového diagramu
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: 1840f677929509e4902498c5aa8920f49cb13496
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773591"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="fb73d-102">Pracovní postupy vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="fb73d-102">Flowchart Workflows</span></span>

<span data-ttu-id="fb73d-103">Vývojový diagram je dobře známé paradigma pro navrhování aplikací.</span><span class="sxs-lookup"><span data-stu-id="fb73d-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="fb73d-104">Vývojový diagram aktivity se obvykle používá k implementaci – sekvenční pracovní postupy, ale lze použít pro sekvenční pracovní postupy, pokud žádné `FlowDecision` uzlů se používají.</span><span class="sxs-lookup"><span data-stu-id="fb73d-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="fb73d-105">Vývojový diagram Vyobrazený pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fb73d-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="fb73d-106">Vývojový diagram aktivity je aktivitou, která obsahuje kolekce aktivit, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="fb73d-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="fb73d-107">Na vývojových diagramech také obsahovat toku ovládacích prvků, jako například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> , který přímé provádění mezi obsažené aktivity na základě hodnot proměnných.</span><span class="sxs-lookup"><span data-stu-id="fb73d-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="fb73d-108">Typy uzlů toku</span><span class="sxs-lookup"><span data-stu-id="fb73d-108">Types of flow nodes</span></span>

 <span data-ttu-id="fb73d-109">V závislosti na typu řízení toku požadováno, když spustí elementu se používají různé typy prvků.</span><span class="sxs-lookup"><span data-stu-id="fb73d-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="fb73d-110">Vývojový diagram prvky mezi typy patří:</span><span class="sxs-lookup"><span data-stu-id="fb73d-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="fb73d-111">`FlowStep` -Modely krok provádění ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="fb73d-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="fb73d-112">`FlowDecision` -Provádění větve založené na logickou podmínku, podobně jako <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="fb73d-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="fb73d-113">`FlowSwitch` – Spuštění větve založené na exkluzivní přepínače, podobně jako <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="fb73d-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="fb73d-114">Každé propojení má `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , který lze použít k provedení podřízených aktivit a jeden nebo více `Next` vlastnosti, které definují, který prvek nebo prvky, které mají provést po dokončení provádění aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="fb73d-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="fb73d-115">Vytváření pořadí základní aktivity s uzlem FlowStep</span><span class="sxs-lookup"><span data-stu-id="fb73d-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="fb73d-116">Modelování základní pořadí, ve kterém dvě aktivity spuštění zase `FlowStep` element se používá.</span><span class="sxs-lookup"><span data-stu-id="fb73d-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="fb73d-117">V následujícím příkladu dvě `FlowStep` elementy se používají ke spouštění dvě aktivity v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fb73d-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="fb73d-118">Vývojový diagram podmíněného vytváření s uzlem FlowDecision</span><span class="sxs-lookup"><span data-stu-id="fb73d-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="fb73d-119">Modelovat podmíněné tok uzel v pracovním postupu vývojového diagramu (to znamená, chcete-li vytvořit odkaz, který funguje jako symbol tradiční vývojový diagram rozhodování), <xref:System.Activities.Statements.FlowDecision> uzel se používá.</span><span class="sxs-lookup"><span data-stu-id="fb73d-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="fb73d-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> a <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které chcete provést, pokud je výraz vyhodnocen `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="fb73d-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="fb73d-121">Následující příklad ukazuje, jak definovat pracovní postup, který se používá <xref:System.Activities.Statements.FlowDecision> uzlu.</span><span class="sxs-lookup"><span data-stu-id="fb73d-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="fb73d-122">Vytváření exkluzivní přepínače s uzlem FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="fb73d-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="fb73d-123">Modelování vývojový diagram, ve kterém jednoho vybraného exkluzivní cestu na základě odpovídající hodnotu <xref:System.Activities.Statements.FlowSwitch%601> uzel se používá.</span><span class="sxs-lookup"><span data-stu-id="fb73d-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="fb73d-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Je nastavena na <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> , který definuje hodnoty tak, aby odpovídaly volby proti.</span><span class="sxs-lookup"><span data-stu-id="fb73d-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="fb73d-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Vlastnost definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objekty tak, aby odpovídala podmíněný výraz a sadu <xref:System.Activities.Statements.FlowNode> objekty, které definují, jak provádění jakým způsobem se předávají pokud daný případ odpovídá podmíněný výraz.</span><span class="sxs-lookup"><span data-stu-id="fb73d-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="fb73d-126"><xref:System.Activities.Statements.FlowSwitch%601> Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak provádění jakým způsobem se předávají pokud výraz podmínky odpovídat žádné případy.</span><span class="sxs-lookup"><span data-stu-id="fb73d-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="fb73d-127">Následující příklad ukazuje, jak definovat pracovní postup, který se používá <xref:System.Activities.Statements.FlowSwitch%601> elementu.</span><span class="sxs-lookup"><span data-stu-id="fb73d-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
