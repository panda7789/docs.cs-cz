---
title: Výrazy – WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 1c79d4294ce1e7d6f6fc13e8220f88919c8f6021
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989754"
---
# <a name="expressions"></a><span data-ttu-id="162c5-102">Výrazy</span><span class="sxs-lookup"><span data-stu-id="162c5-102">Expressions</span></span>
<span data-ttu-id="162c5-103">Výraz programovací model Windows Workflow Foundation (WF) je jakákoli aktivita, která vrací výsledek.</span><span class="sxs-lookup"><span data-stu-id="162c5-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="162c5-104">Všechny aktivity výrazů odvozují nepřímo <xref:System.Activities.Activity%601>z, který <xref:System.Activities.OutArgument> obsahuje vlastnost s <xref:System.Activities.Activity%601.Result%2A> názvem jako návratovou hodnotou aktivity.</span><span class="sxs-lookup"><span data-stu-id="162c5-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="162c5-105">dodává <xref:System.Activities.Expressions.VariableValue%601> se široké škále aktivit výrazů od jednoduchých, jako je a <xref:System.Activities.Expressions.VariableReference%601>, která poskytuje přístup k proměnné s jedním pracovním postupem prostřednictvím aktivit operátora, složitým aktivitám, jako je například <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Tato nabídka přístup k celé šířce Visual Basic jazyka, aby vznikl výsledek.</span><span class="sxs-lookup"><span data-stu-id="162c5-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="162c5-106">Další aktivity výrazu lze vytvořit odvozením z <xref:System.Activities.CodeActivity%601> nebo. <xref:System.Activities.NativeActivity%601></span><span class="sxs-lookup"><span data-stu-id="162c5-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="162c5-107">Výrazy using</span><span class="sxs-lookup"><span data-stu-id="162c5-107">Using Expressions</span></span>  
 <span data-ttu-id="162c5-108">Návrhář pracovních postupů <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> používá <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> a pro všechny výrazy v <xref:Microsoft.CSharp.Activities.CSharpReference%601> Visual Basic projekty a <xref:Microsoft.CSharp.Activities.CSharpValue%601> pro výrazy v C# projektech pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="162c5-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="162c5-109">Podpora C# výrazů v projektech pracovního postupu byla představena v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="162c5-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="162c5-110">Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="162c5-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="162c5-111">Pracovní postupy vytvořené návrhářem jsou uloženy v jazyce XAML, kde jsou výrazy zobrazeny v hranatých závorkách, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="162c5-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="162c5-112">Při definování pracovního postupu v kódu lze použít jakékoli aktivity výrazu.</span><span class="sxs-lookup"><span data-stu-id="162c5-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="162c5-113">Následující příklad ukazuje použití složení aktivit operátoru pro přidání tří čísel.</span><span class="sxs-lookup"><span data-stu-id="162c5-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
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
  
 <span data-ttu-id="162c5-114">Stejný pracovní postup lze vyjádřit kompaktnější pomocí C# výrazů lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="162c5-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="162c5-115">Pracovní postup lze také vyjádřit pomocí aktivit Visual Basic výrazů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="162c5-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```vb  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="162c5-116">Rozšiřování dostupných výrazů pomocí aktivit vlastních výrazů</span><span class="sxs-lookup"><span data-stu-id="162c5-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="162c5-117">Výrazy v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou rozšiřitelné, což umožňuje vytvořit další aktivity výrazů.</span><span class="sxs-lookup"><span data-stu-id="162c5-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="162c5-118">Následující příklad ukazuje aktivitu, která vrací součet tří celočíselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="162c5-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
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
  
 <span data-ttu-id="162c5-119">Pomocí této nové aktivity můžete přepsat předchozí pracovní postup, který přidal tři hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="162c5-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="162c5-120">Další informace o použití výrazů v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="162c5-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
