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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d42249f19b2d9acebf547be9e590813d6bbf7a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="expressions"></a><span data-ttu-id="3a11c-102">Výrazy</span><span class="sxs-lookup"><span data-stu-id="3a11c-102">Expressions</span></span>
<span data-ttu-id="3a11c-103">A [!INCLUDE[wf](../../../includes/wf-md.md)] výraz je aktivit, které vrací výsledek.</span><span class="sxs-lookup"><span data-stu-id="3a11c-103">A [!INCLUDE[wf](../../../includes/wf-md.md)] expression is any activity that returns a result.</span></span> <span data-ttu-id="3a11c-104">Všechny aktivity výraz nepřímo odvozeny od <xref:System.Activities.Activity%601>, který obsahuje <xref:System.Activities.OutArgument> vlastnost s názvem <xref:System.Activities.Activity%601.Result%2A> jako návratová hodnota aktivity.</span><span class="sxs-lookup"><span data-stu-id="3a11c-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="3a11c-105">z jednoduché, jako jsou ty, které se dodává s širokou škálu aktivit výraz <xref:System.Activities.Expressions.VariableValue%601> a <xref:System.Activities.Expressions.VariableReference%601>, které poskytují přístup k proměnné jednoho pracovního postupu pomocí aktivity operátor pro komplexní aktivity, jako <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> v rámci této nabídky přístup k úplného spektra jazyka Visual Basic k vytvoření výsledku.</span><span class="sxs-lookup"><span data-stu-id="3a11c-105"> ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="3a11c-106">Lze vytvořit další výraz aktivity odvozené z <xref:System.Activities.CodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="3a11c-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="3a11c-107">Pomocí výrazů</span><span class="sxs-lookup"><span data-stu-id="3a11c-107">Using Expressions</span></span>  
 <span data-ttu-id="3a11c-108">Návrhář postupu provádění používá <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pro všechny výrazy v projektech Visual Basic a <xref:Microsoft.CSharp.Activities.CSharpValue%601> a <xref:Microsoft.CSharp.Activities.CSharpReference%601> pro výrazy v pracovním postupu projektů C#.</span><span class="sxs-lookup"><span data-stu-id="3a11c-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a11c-109">Podpora pro výrazy jazyka C# v projektech pracovního postupu byla zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a11c-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3a11c-110">[Výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3a11c-110"> [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="3a11c-111">V jazyce XAML, kde se zobrazí výrazy závorkách v hranatých závorkách, jako v následujícím příkladu se uloží vyprodukované návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3a11c-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3a11c-112">Při definování pracovního postupu v kódu, dá se žádné aktivity výraz.</span><span class="sxs-lookup"><span data-stu-id="3a11c-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="3a11c-113">Následující příklad ukazuje použití složení operátor aktivit a přidejte tři číslice.</span><span class="sxs-lookup"><span data-stu-id="3a11c-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
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
  
 <span data-ttu-id="3a11c-114">Témže pracovním postupu může být vyjádřený více kompaktně pomocí jazyka C# výrazy lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3a11c-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3a11c-115">Pracovní postup lze také vyjádřit pomocí aktivity výrazu jazyka Visual Basic, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3a11c-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="3a11c-116">Rozšíření k dispozici výrazy s aktivitami vlastního výrazu</span><span class="sxs-lookup"><span data-stu-id="3a11c-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="3a11c-117">Výrazy v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou extensible povolení pro další výraz aktivity, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="3a11c-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="3a11c-118">Následující příklad ukazuje aktivitu, která vrací součet tři celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a11c-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
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
  
 <span data-ttu-id="3a11c-119">Pomocí této nové aktivity je možné přepsat předchozí pracovního postupu, který přidat tři hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3a11c-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="3a11c-120">v kódu pomocí výrazů, najdete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kód](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="3a11c-120"> using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
