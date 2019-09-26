---
title: Výrazy – WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 62b278825de6242075e89e3b243b6d6d8ef4d599
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306197"
---
# <a name="expressions"></a>Výrazy

Výraz programovací model Windows Workflow Foundation (WF) je jakákoli aktivita, která vrací výsledek. Všechny aktivity výrazů odvozují nepřímo <xref:System.Activities.Activity%601>z, který <xref:System.Activities.OutArgument> obsahuje vlastnost s <xref:System.Activities.Activity%601.Result%2A> názvem jako návratovou hodnotou aktivity. [!INCLUDE[wf1](../../../includes/wf1-md.md)]dodává <xref:System.Activities.Expressions.VariableValue%601> se široké škále aktivit výrazů od jednoduchých, jako je a <xref:System.Activities.Expressions.VariableReference%601>, která poskytuje přístup k proměnné s jedním pracovním postupem prostřednictvím aktivit operátora, složitým aktivitám, jako je například <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Tato nabídka přístup k celé šířce Visual Basic jazyka, aby vznikl výsledek. Další aktivity výrazu lze vytvořit odvozením z <xref:System.Activities.CodeActivity%601> nebo. <xref:System.Activities.NativeActivity%601>

## <a name="using-expressions"></a>Výrazy using
 Návrhář pracovních postupů <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> používá <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a pro všechny výrazy v <xref:Microsoft.CSharp.Activities.CSharpReference%601> Visual Basic projekty a <xref:Microsoft.CSharp.Activities.CSharpValue%601> pro výrazy v C# projektech pracovního postupu.

> [!NOTE]
> Podpora C# výrazů v projektech pracovního postupu byla představena v .NET Framework 4,5. Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).

 Pracovní postupy vytvořené návrhářem jsou uloženy v jazyce XAML, kde jsou výrazy zobrazeny v hranatých závorkách, jako v následujícím příkladu.

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

 Při definování pracovního postupu v kódu lze použít jakékoli aktivity výrazu. Následující příklad ukazuje použití složení aktivit operátoru pro přidání tří čísel:

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

 Stejný pracovní postup lze vyjádřit kompaktnější pomocí C# výrazů lambda, jak je znázorněno v následujícím příkladu:
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozšiřování dostupných výrazů pomocí aktivit vlastních výrazů

 Výrazy v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou rozšiřitelné, což umožňuje vytvořit další aktivity výrazů. Následující příklad ukazuje aktivitu, která vrací součet tří celočíselných hodnot.

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

 Další informace o použití výrazů v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).
