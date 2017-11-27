---
title: Expressions1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: faf9e70cbe2c2a035874e5514ac04cf0f291661b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expressions"></a>Výrazy
A [!INCLUDE[wf](../../../includes/wf-md.md)] výraz je aktivit, které vrací výsledek. Všechny aktivity výraz nepřímo odvozeny od <xref:System.Activities.Activity%601>, který obsahuje <xref:System.Activities.OutArgument> vlastnost s názvem <xref:System.Activities.Activity%601.Result%2A> jako návratová hodnota aktivity. [!INCLUDE[wf1](../../../includes/wf1-md.md)]z jednoduché, jako jsou ty, které se dodává s širokou škálu aktivit výraz <xref:System.Activities.Expressions.VariableValue%601> a <xref:System.Activities.Expressions.VariableReference%601>, které poskytují přístup k proměnné jednoho pracovního postupu pomocí aktivity operátor pro komplexní aktivity, jako <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> v rámci této nabídky přístup k úplného spektra jazyka Visual Basic k vytvoření výsledku. Lze vytvořit další výraz aktivity odvozené z <xref:System.Activities.CodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>Pomocí výrazů  
 Návrhář postupu provádění používá <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pro všechny výrazy v projektech Visual Basic a <xref:Microsoft.CSharp.Activities.CSharpValue%601> a <xref:Microsoft.CSharp.Activities.CSharpReference%601> pro výrazy v pracovním postupu projektů C#.  
  
> [!NOTE]
>  Podpora pro výrazy jazyka C# v projektech pracovního postupu byla zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 V jazyce XAML, kde se zobrazí výrazy závorkách v hranatých závorkách, jako v následujícím příkladu se uloží vyprodukované návrháře pracovních postupů.  
  
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
  
 Při definování pracovního postupu v kódu, dá se žádné aktivity výraz. Následující příklad ukazuje použití složení operátor aktivit a přidejte tři číslice.  
  
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
  
 Témže pracovním postupu může být vyjádřený více kompaktně pomocí jazyka C# výrazy lambda, jak je znázorněno v následujícím příkladu.  
  
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
  
 Pracovní postup lze také vyjádřit pomocí aktivity výrazu jazyka Visual Basic, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozšíření k dispozici výrazy s aktivitami vlastního výrazu  
 Výrazy v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou extensible povolení pro další výraz aktivity, který se má vytvořit. Následující příklad ukazuje aktivitu, která vrací součet tři celočíselné hodnoty.  
  
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
  
 Pomocí této nové aktivity je možné přepsat předchozí pracovního postupu, který přidat tři hodnoty, jak je znázorněno v následujícím příkladu.  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]v kódu pomocí výrazů, najdete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kód](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).
