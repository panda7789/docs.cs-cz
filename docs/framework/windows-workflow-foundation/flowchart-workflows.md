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
# <a name="flowchart-workflows"></a>Pracovní postupy vývojového diagramu

Vývojový diagram je dobře známé paradigma pro navrhování aplikací. Vývojový diagram aktivity se obvykle používá k implementaci – sekvenční pracovní postupy, ale lze použít pro sekvenční pracovní postupy, pokud žádné `FlowDecision` uzlů se používají.

## <a name="flowchart-workflow-structure"></a>Vývojový diagram Vyobrazený pracovního postupu

 Vývojový diagram aktivity je aktivitou, která obsahuje kolekce aktivit, který se spustí.  Na vývojových diagramech také obsahovat toku ovládacích prvků, jako například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> , který přímé provádění mezi obsažené aktivity na základě hodnot proměnných.

## <a name="types-of-flow-nodes"></a>Typy uzlů toku

 V závislosti na typu řízení toku požadováno, když spustí elementu se používají různé typy prvků. Vývojový diagram prvky mezi typy patří:

- `FlowStep` -Modely krok provádění ve vývojovém diagramu.

- `FlowDecision` -Provádění větve založené na logickou podmínku, podobně jako <xref:System.Activities.Statements.If>.

- `FlowSwitch` – Spuštění větve založené na exkluzivní přepínače, podobně jako <xref:System.Activities.Statements.Switch%601>.

Každé propojení má `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , který lze použít k provedení podřízených aktivit a jeden nebo více `Next` vlastnosti, které definují, který prvek nebo prvky, které mají provést po dokončení provádění aktuálního prvku.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Vytváření pořadí základní aktivity s uzlem FlowStep

Modelování základní pořadí, ve kterém dvě aktivity spuštění zase `FlowStep` element se používá. V následujícím příkladu dvě `FlowStep` elementy se používají ke spouštění dvě aktivity v sekvenci.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Vývojový diagram podmíněného vytváření s uzlem FlowDecision

Modelovat podmíněné tok uzel v pracovním postupu vývojového diagramu (to znamená, chcete-li vytvořit odkaz, který funguje jako symbol tradiční vývojový diagram rozhodování), <xref:System.Activities.Statements.FlowDecision> uzel se používá. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> a <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které chcete provést, pokud je výraz vyhodnocen `true` nebo `false`. Následující příklad ukazuje, jak definovat pracovní postup, který se používá <xref:System.Activities.Statements.FlowDecision> uzlu.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Vytváření exkluzivní přepínače s uzlem FlowSwitch

Modelování vývojový diagram, ve kterém jednoho vybraného exkluzivní cestu na základě odpovídající hodnotu <xref:System.Activities.Statements.FlowSwitch%601> uzel se používá. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Je nastavena na <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> , který definuje hodnoty tak, aby odpovídaly volby proti. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Vlastnost definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objekty tak, aby odpovídala podmíněný výraz a sadu <xref:System.Activities.Statements.FlowNode> objekty, které definují, jak provádění jakým způsobem se předávají pokud daný případ odpovídá podmíněný výraz. <xref:System.Activities.Statements.FlowSwitch%601> Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak provádění jakým způsobem se předávají pokud výraz podmínky odpovídat žádné případy. Následující příklad ukazuje, jak definovat pracovní postup, který se používá <xref:System.Activities.Statements.FlowSwitch%601> elementu.

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
