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
# <a name="flowchart-workflows"></a>Pracovní postupy vývojového diagramu

Vývojový diagram je dobře známé paradigma pro navrhování programů. Aktivita vývojového diagramu se obvykle používá k implementaci nesekvenčních pracovních postupů, ale je možné ji použít pro sekvenční pracovní postupy, pokud `FlowDecision` se nepoužívají žádné uzly.

## <a name="flowchart-workflow-structure"></a>Struktura pracovního postupu vývojového diagramu

 Aktivita vývojového diagramu je aktivita, která obsahuje kolekci aktivit, které mají být provedeny.  Vývojové diagramy také obsahují prvky řízení toku, například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> , které přímo vykonává mezi obsaženými aktivitami na základě hodnot proměnných.

## <a name="types-of-flow-nodes"></a>Typy uzlů toků

 Různé typy prvků jsou používány v závislosti na typu řízení toku vyžadovaného při spuštění elementu. Mezi typy prvků vývojového diagramu patří:

- `FlowStep`– Modeluje jeden krok provádění ve vývojovém diagramu.

- `FlowDecision`– Spouštění větví na základě logické podmínky, podobně jako <xref:System.Activities.Statements.If> .

- `FlowSwitch`– Spuštění větví na základě výhradního přepínače, podobně jako <xref:System.Activities.Statements.Switch%601> .

Každé propojení má `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , který lze použít ke spouštění podřízených aktivit, a jednu nebo více `Next` vlastností, které definují, který prvek nebo prvky mají být provedeny, když aktuální element dokončí provádění.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Vytvoření sekvence základní aktivity pomocí uzlu FlowStep

Chcete-li modelovat základní pořadí, ve kterém jsou dvě aktivity spouštěny, `FlowStep` je použit element. V následujícím příkladu `FlowStep` se dva prvky používají ke spuštění dvou aktivit v sekvenci.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Vytvoření podmíněného vývojového diagramu pomocí uzlu použitím objektu FlowDecision

Pokud chcete modelovat uzel podmíněného toku v pracovním postupu vývojového diagramu (to znamená, že chcete vytvořit odkaz, který funguje jako tradiční symbol rozhodnutí vývojového diagramu), <xref:System.Activities.Statements.FlowDecision> použije se uzel. <xref:System.Activities.Statements.FlowDecision.Condition%2A>Vlastnost uzlu je nastavena na výraz definující podmínku a <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti a jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které mají být provedeny, pokud je výraz vyhodnocen jako `true` nebo `false` . Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowDecision> uzel.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Vytvoření výhradního přepínače pomocí uzlu FlowSwitch

Chcete-li modelovat vývojový diagram, ve kterém je vybrána jedna exkluzivní cesta na základě vyhovující hodnoty, <xref:System.Activities.Statements.FlowSwitch%601> je použit uzel. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Vlastnost je nastavena na hodnotu <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> , který definuje hodnotu pro porovnání volby s. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Vlastnost definuje slovník klíčů a objektů, které <xref:System.Activities.Statements.FlowNode> mají být porovnány s podmíněným výrazem, a sadou <xref:System.Activities.Statements.FlowNode> objektů, které definují, jak by měl tok provádět, pokud daný případ odpovídá podmíněnému výrazu. <xref:System.Activities.Statements.FlowSwitch%601>Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje způsob, jakým by měl být provádění tok, pokud žádné případy neodpovídají výrazu podmínky. Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowSwitch%601> prvek.

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
