---
title: 'Postupy: Použití výrazů lambda vně průvodce C# PROGRAMOVÁNÍm LINQ'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 947f80fdaa90b6b5f8176aac01dd8e3cf40e38cc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363781"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="07fa2-102">Postupy: Použití výrazů lambda mimo LINQ (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="07fa2-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="07fa2-103">Výrazy lambda nejsou omezené na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="07fa2-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="07fa2-104">Můžete je použít všude, kde je očekávána hodnota delegáta, to znamená, kde lze použít anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="07fa2-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="07fa2-105">Následující příklad ukazuje, jak použít výraz lambda v obslužné rutině události model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="07fa2-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="07fa2-106">Všimněte si, že typy vstupů (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou odvozeny kompilátorem a není nutné je explicitně předávat ve vstupních parametrech lambda.</span><span class="sxs-lookup"><span data-stu-id="07fa2-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07fa2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="07fa2-107">Example</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="07fa2-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07fa2-108">See also</span></span>

- [<span data-ttu-id="07fa2-109">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="07fa2-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="07fa2-110">LINQ (Language Integrated Query))</span><span class="sxs-lookup"><span data-stu-id="07fa2-110">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
