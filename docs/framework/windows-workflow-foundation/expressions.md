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
# <a name="expressions"></a><span data-ttu-id="81508-102">Výrazy</span><span class="sxs-lookup"><span data-stu-id="81508-102">Expressions</span></span>

<span data-ttu-id="81508-103">Výraz Nadace pracovního postupu systému Windows (WF) je jakákoli aktivita, která vrací výsledek.</span><span class="sxs-lookup"><span data-stu-id="81508-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="81508-104">Všechny aktivity výrazu <xref:System.Activities.Activity%601>jsou odvozeny <xref:System.Activities.Activity%601.Result%2A> nepřímo z aplikace , která obsahuje vlastnost pojmenovanou <xref:System.Activities.OutArgument> jako vrácená hodnota aktivity.</span><span class="sxs-lookup"><span data-stu-id="81508-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="81508-105">dodává se s širokou škálu výrazových <xref:System.Activities.Expressions.VariableValue%601> <xref:System.Activities.Expressions.VariableReference%601>aktivit od jednoduchých, jako je a , které <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> poskytují přístup k jedné proměnné pracovního postupu prostřednictvím operátora činnosti, na komplexní činnosti, jako je například a které nabízejí přístup k úplné šíři jazyka Visual Basic k vytvoření výsledku.</span><span class="sxs-lookup"><span data-stu-id="81508-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="81508-106">Další aktivity výrazu lze vytvořit <xref:System.Activities.CodeActivity%601> odvozením z nebo <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="81508-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="81508-107">Použití výrazů</span><span class="sxs-lookup"><span data-stu-id="81508-107">Using Expressions</span></span>
 <span data-ttu-id="81508-108">Návrhář <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pracovních <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> postupů používá a pro všechny <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.CSharp.Activities.CSharpReference%601> výrazy v projektech jazyka Visual Basic a pro výrazy v projektech pracovního postupu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="81508-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="81508-109">Podpora výrazů jazyka C# v projektech pracovního postupu byla zavedena v rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="81508-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="81508-110">Další informace naleznete v tématu [C# Výrazy](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="81508-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="81508-111">Pracovní postupy vytvořené návrhářem jsou uloženy v xaml, kde se výrazy zobrazují v hranatých závorkách, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="81508-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="81508-112">Při definování pracovního postupu v kódu lze použít všechny aktivity výrazu.</span><span class="sxs-lookup"><span data-stu-id="81508-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="81508-113">Následující příklad ukazuje použití složení aktivit operátoru k přidání tří čísel:</span><span class="sxs-lookup"><span data-stu-id="81508-113">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

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

 <span data-ttu-id="81508-114">Stejný pracovní postup lze vyjádřit kompaktněji pomocí výrazů c# lambda, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="81508-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="81508-115">Rozšíření dostupných výrazů o aktivity vlastního výrazu</span><span class="sxs-lookup"><span data-stu-id="81508-115">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="81508-116">Výrazy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v jsou rozšiřitelné umožňující vytvoření dalších aktivit výrazů.</span><span class="sxs-lookup"><span data-stu-id="81508-116">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="81508-117">Následující příklad ukazuje aktivitu, která vrací součet tří celé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="81508-117">The following example shows an activity that returns a sum of three integer values.</span></span>

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

 <span data-ttu-id="81508-118">Pomocí této nové aktivity můžete přepsat předchozí pracovní postup, který přidal tři hodnoty, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="81508-118">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

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

 <span data-ttu-id="81508-119">Další informace o používání výrazů v kódu naleznete v [tématu Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="81508-119">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
