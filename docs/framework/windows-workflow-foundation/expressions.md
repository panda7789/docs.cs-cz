---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 047f0f5d0214926fde2fe21efd9a24c4b645ed8e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380171"
---
# <a name="expressions"></a>Výrazy
Výraz Windows Workflow Foundation (WF) je aktivit, které vrací výsledek. Všechny aktivity výrazů jsou nepřímo odvozeny z <xref:System.Activities.Activity%601>, které se nachází <xref:System.Activities.OutArgument> vlastnost s názvem <xref:System.Activities.Activity%601.Result%2A> jako návratovou hodnotu aktivity. [!INCLUDE[wf1](../../../includes/wf1-md.md)] se dodává s širokou škálu aktivity výrazů od těch, které jsou jako jednoduchý <xref:System.Activities.Expressions.VariableValue%601> a <xref:System.Activities.Expressions.VariableReference%601>, které poskytují přístup k proměnné pracovního postupu jeden prostřednictvím operátoru aktivitami, komplexní aktivity, jako <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> nabídku přístup k jeho plném rozsahu jazyka Visual Basic k vytvoření výsledku. Je možné vytvořit další výraz aktivity odvozené z <xref:System.Activities.CodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>Pomocí výrazů  
 Pomocí návrháře postupu provádění <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pro všechny výrazy v projektech Visual Basicu a <xref:Microsoft.CSharp.Activities.CSharpValue%601> a <xref:Microsoft.CSharp.Activities.CSharpReference%601> pro výrazy v C# projekty pracovního postupu.  
  
> [!NOTE]
>  Podpora pro C# výrazy v projekty pracovního postupu byla zavedena v rozhraní .NET Framework 4.5. Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).  
  
 Vytvořený pomocí návrháře pracovních postupů jsou uloženy v XAML, kde se zobrazí výrazy uzavřený v hranatých závorkách, jako v následujícím příkladu.  
  
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
  
 Při definování pracovního postupu v kódu, můžete použít všechny aktivity výrazů. Následující příklad ukazuje použití složení operátor aktivit pro přidání tří čísel.  
  
```  
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
  
 Stejný pracovní postup může být vyjádřena pomocí více kompaktně C# výrazů lambda, jak je znázorněno v následujícím příkladu.  
  
```  
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
  
 Pracovní postup lze také vyjádřit pomocí aktivity výrazů jazyka Visual Basic, jak je znázorněno v následujícím příkladu.  
  
```  
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
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozšíření k dispozici výrazy s aktivitami vlastní výraz  
 Výrazy v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] je rozšiřitelný, umožňuje další výraz aktivity, který se má vytvořit. Následující příklad ukazuje aktivitu, která vrací součet tři celočíselné hodnoty.  
  
```  
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
  
 Pomocí této nové aktivity můžete přepsat předchozí pracovní postup, který přidá tří hodnot, jak je znázorněno v následujícím příkladu.  
  
```  
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
  
 Další informace o použití výrazů v kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).
