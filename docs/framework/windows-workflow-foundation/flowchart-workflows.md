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
# <a name="flowchart-workflows"></a>Pracovní postupy vývojového diagramu

Vývojový diagram je dobře známé paradigma pro navrhování programů. Aktivita vývojového diagramu se obvykle používá k implementaci nesekvenčních `FlowDecision` pracovních postupů, ale lze ji použít pro sekvenční pracovní postupy, pokud se nepoužívají žádné uzly.

## <a name="flowchart-workflow-structure"></a>Struktura pracovního postupu vývojového diagramu

 Aktivita vývojového diagramu je aktivita, která obsahuje kolekci aktivit, které mají být provedeny.  Vývojové diagramy také obsahují <xref:System.Activities.Statements.FlowDecision> prvky řízení toku, jako je například <xref:System.Activities.Statements.FlowSwitch%601> přímé provádění mezi obsažené aktivity na základě hodnot proměnných.

## <a name="types-of-flow-nodes"></a>Typy uzlů toku

 Různé typy prvků se používají v závislosti na typu řízení toku požadované při spuštění prvku. Mezi typy prvků vývojového diagramu patří:

- `FlowStep`- Modely jeden krok provedení ve vývojovém diagramu.

- `FlowDecision`- Provádění větví na základě logické <xref:System.Activities.Statements.If>podmínky, podobně jako .

- `FlowSwitch`– Exekuce poboček založená <xref:System.Activities.Statements.Switch%601>na výhradním přepínači, podobně jako .

Každý odkaz `Action` má vlastnost, <xref:System.Activities.ActivityAction> která definuje, které lze použít ke `Next` spuštění podřízené aktivity a jeden nebo více vlastností, které definují, který prvek nebo prvky spustit při dokončení provádění aktuální prvek.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Vytvoření základní sekvence aktivit s uzlem FlowStep

Chcete-li modelovat základní pořadí, ve `FlowStep` kterém dvě aktivity spustit v pořadí, prvek se používá. V následujícím příkladu `FlowStep` dva prvky se používají k provedení dvou aktivit v pořadí.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Vytvoření podmíněného vývojového diagramu s uzly FlowDecision

Chcete-li modelovat uzel podmíněného toku v pracovním postupu vývojového diagramu (to znamená vytvořit <xref:System.Activities.Statements.FlowDecision> propojení, které funguje jako symbol rozhodnutí tradičního vývojového diagramu), použije se uzel. Vlastnost <xref:System.Activities.Statements.FlowDecision.Condition%2A> uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> vlastnosti a <xref:System.Activities.Statements.FlowDecision.False%2A> jsou nastaveny <xref:System.Activities.Statements.FlowNode> na `true` instance, které mají být provedeny, pokud výraz vyhodnotí nebo `false`. Následující příklad ukazuje, jak definovat pracovní <xref:System.Activities.Statements.FlowDecision> postup, který používá uzel.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Vytvoření výhradního přepínače s uzly FlowSwitch

Chcete-li modelovat vývojový diagram, ve kterém je <xref:System.Activities.Statements.FlowSwitch%601> vybrána jedna výhradní cesta na základě odpovídající hodnoty, použije se uzel. Vlastnost <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> je nastavena <xref:System.Activities.Activity%601> na parametr <xref:System.Object> typu, který definuje hodnotu, proti které mají odpovídat volbám. Vlastnost <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objektů tak, aby odpovídaly podmíněnému <xref:System.Activities.Statements.FlowNode> výrazu a sadu objektů, které definují, jak by mělo tok spuštění, pokud daný případ odpovídá podmíněnému výrazu. Také <xref:System.Activities.Statements.FlowSwitch%601> definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak by mělo tok spuštění, pokud žádné případy odpovídají výrazu podmínky. Následující příklad ukazuje, jak definovat pracovní <xref:System.Activities.Statements.FlowSwitch%601> postup, který používá prvek.

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
