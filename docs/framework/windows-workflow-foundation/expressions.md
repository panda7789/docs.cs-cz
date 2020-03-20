---
title: Výrazy – wf
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93fe449e8fa6c50f715d842c2ef6a9ecbd31aff2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182930"
---
# <a name="expressions"></a>Výrazy

Výraz Nadace pracovního postupu systému Windows (WF) je jakákoli aktivita, která vrací výsledek. Všechny aktivity výrazu <xref:System.Activities.Activity%601>jsou odvozeny <xref:System.Activities.Activity%601.Result%2A> nepřímo z aplikace , která obsahuje vlastnost pojmenovanou <xref:System.Activities.OutArgument> jako vrácená hodnota aktivity. [!INCLUDE[wf1](../../../includes/wf1-md.md)]dodává se s širokou škálu výrazových <xref:System.Activities.Expressions.VariableValue%601> <xref:System.Activities.Expressions.VariableReference%601>aktivit od jednoduchých, jako je a , které <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> poskytují přístup k jedné proměnné pracovního postupu prostřednictvím operátora činnosti, na komplexní činnosti, jako je například a které nabízejí přístup k úplné šíři jazyka Visual Basic k vytvoření výsledku. Další aktivity výrazu lze vytvořit <xref:System.Activities.CodeActivity%601> odvozením z nebo <xref:System.Activities.NativeActivity%601>.

## <a name="using-expressions"></a>Použití výrazů
 Návrhář <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pracovních <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> postupů používá a pro všechny <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.CSharp.Activities.CSharpReference%601> výrazy v projektech jazyka Visual Basic a pro výrazy v projektech pracovního postupu jazyka C#.

> [!NOTE]
> Podpora výrazů jazyka C# v projektech pracovního postupu byla zavedena v rozhraní .NET Framework 4.5. Další informace naleznete v tématu [C# Výrazy](csharp-expressions.md).

 Pracovní postupy vytvořené návrhářem jsou uloženy v xaml, kde se výrazy zobrazují v hranatých závorkách, jako v následujícím příkladu.

```xml
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <Sequence.Variables>
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />
  </Sequence.Variables>
  <Assign>
    <Assign.To>
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>
    </Assign.To>
    <Assign.Value>
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>
    </Assign.Value>
  </Assign>
</Sequence>
```

 Při definování pracovního postupu v kódu lze použít všechny aktivity výrazu. Následující příklad ukazuje použití složení aktivit operátoru k přidání tří čísel:

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new Add<int, int, int> {
                    Left = new Add<int, int, int> {
                        Left = new InArgument<int>(a),
                        Right = new InArgument<int>(b)
                    },
                    Right = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Stejný pracovní postup lze vyjádřit kompaktněji pomocí výrazů c# lambda, jak je znázorněno v následujícím příkladu:
  
```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))
        }
    }
};
```

## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozšíření dostupných výrazů o aktivity vlastního výrazu

 Výrazy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v jsou rozšiřitelné umožňující vytvoření dalších aktivit výrazů. Následující příklad ukazuje aktivitu, která vrací součet tří celé hodnoty.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Activities;

namespace ExpressionsDemo
{
    public sealed class AddThreeValues : CodeActivity<int>
    {
        public InArgument<int> Value1 { get; set; }
        public InArgument<int> Value2 { get; set; }
        public InArgument<int> Value3 { get; set; }

        protected override int Execute(CodeActivityContext context)
        {
            return Value1.Get(context) +
                   Value2.Get(context) +
                   Value3.Get(context);
        }
    }
}
```

 Pomocí této nové aktivity můžete přepsat předchozí pracovní postup, který přidal tři hodnoty, jak je znázorněno v následujícím příkladu:

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new AddThreeValues() {
                    Value1 = new InArgument<int>(a),
                    Value2 = new InArgument<int>(b),
                    Value3 = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 Další informace o používání výrazů v kódu naleznete v [tématu Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).
