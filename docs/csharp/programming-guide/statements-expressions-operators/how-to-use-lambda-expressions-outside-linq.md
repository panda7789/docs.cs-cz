---
title: 'Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: a7b7d25adab7ce1fc777b3bdbe581666ab952413
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328952"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="e3aaa-102">Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e3aaa-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="e3aaa-103">Lambda – výrazy nejsou omezeny na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="e3aaa-104">Můžete je všude, kde je očekávané hodnotu delegáta, který je bez ohledu na anonymní metodu je možné použít.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="e3aaa-105">Následující příklad ukazuje, jak pomocí výrazu lambda v obslužné rutině událostí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="e3aaa-106">Všimněte si, že typy vstupních hodnot (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou vyvozena na základě kompilátoru a není nutné mít explicitně lambda vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3aaa-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3aaa-107">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="e3aaa-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3aaa-108">See Also</span></span>  
 [<span data-ttu-id="e3aaa-109">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e3aaa-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="e3aaa-110">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="e3aaa-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="e3aaa-111">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e3aaa-111">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
