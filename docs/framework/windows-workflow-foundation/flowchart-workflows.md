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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddfa98a8b9de0b362a27b55d4cd9a4c02ac8a761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="flowchart-workflows"></a>Vývojový diagram pracovních postupů
Vývojový diagram je dobře známé zlepší pro návrh programy. Vývojový diagram aktivity se obvykle používá k implementaci nesekvenční pracovní postupy, ale lze použít pro sekvenční pracovní postupy, pokud žádné `FlowDecision` uzly se používají.  
  
## <a name="flowchart-workflow-structure"></a>Vývojový diagram pracovního postupu struktura  
 Vývojový diagram aktivity je aktivitou, která obsahuje kolekci aktivit, které by šlo spustit.  Na vývojových diagramech také obsahovat toku ovládací prvky, jako například <xref:System.Activities.Statements.FlowDecision> a <xref:System.Activities.Statements.FlowSwitch%601> který přímé provádění mezi obsažené aktivity podle hodnoty proměnných.  
  
## <a name="types-of-flow-nodes"></a>Typy uzlů toku  
 V závislosti na typu řízení toku požadováno, když provádí elementu se používají různé typy elementů. Typy prvků vývojový diagram patří:  
  
-   `FlowStep`-Modely krok spouštění v vývojový diagram.  
  
-   `FlowDecision`-Větví provádění založené na podmínce logické, podobně jako <xref:System.Activities.Statements.If>.  
  
-   `FlowSwitch`– Spuštění větví podle výhradní přepínače, podobně jako <xref:System.Activities.Statements.Switch%601>.  
  
 Každé propojení nemá `Action` vlastnost, která definuje <xref:System.Activities.ActivityAction> , můžete použít ke spuštění podřízené aktivity a jednu nebo více `Next` vlastnosti, které definují, které element nebo elementy provést po dokončení provádění aktuálního elementu.  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Vytváření pořadí základní aktivity s uzlem FlowStep  
 Modelování základní pořadí, ve kterém se dvě aktivity spustit zase `FlowStep` element se používá. V následujícím příkladu dva `FlowStep` prvky se používají ke spouštění dvě aktivity v pořadí.  
  
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
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Vytvoření podmíněného vývojový diagram s uzlem FlowDecision  
 Modelování postup podmíněného uzel v pracovním postupu vývojový diagram (to znamená, chcete-li vytvořit odkaz, který funguje jako tradiční vývojový diagram rozhodování symbol), <xref:System.Activities.Statements.FlowDecision> uzel se používá. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Uzlu je nastavena na výraz, který definuje podmínku, a <xref:System.Activities.Statements.FlowDecision.True%2A> a <xref:System.Activities.Statements.FlowDecision.False%2A> vlastnosti jsou nastaveny na <xref:System.Activities.Statements.FlowNode> instance, které chcete provést, pokud je výsledkem výrazu `true` nebo `false`. Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowDecision> uzlu.  
  
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
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Vytváření výhradní přepínače s uzlem FlowSwitch  
 Pro modelování vývojový diagram, ve které jedna je vybrána výhradní cesta založené na odpovídající hodnotu <xref:System.Activities.Statements.FlowSwitch%601> uzel se používá. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Je nastavena na <xref:System.Activities.Activity%601> s parametrem typu <xref:System.Object> definuje hodnotu podle voleb proti. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Vlastnost definuje slovník klíčů a <xref:System.Activities.Statements.FlowNode> objekty, které se shodují s podmíněným výrazem a sadu <xref:System.Activities.Statements.FlowNode> objekty, které definují, jak by měla toku spuštění, pokud daný případ odpovídá podmíněným výrazem. <xref:System.Activities.Statements.FlowSwitch%601> Také definuje <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> vlastnost, která definuje, jak by měla toku spuštění, pokud žádné případy odpovídat výrazu podmínky. Následující příklad ukazuje, jak definovat pracovní postup, který používá <xref:System.Activities.Statements.FlowSwitch%601> elementu.  
  
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
