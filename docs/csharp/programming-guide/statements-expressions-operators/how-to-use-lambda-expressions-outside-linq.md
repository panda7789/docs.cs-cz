---
title: 'Postupy: Použití výrazů Lambda mimo LINQ – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: d4dc0375552ef1fe00f629c22b5296399b4cc99d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243930"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="f8932-102">Postupy: Použití výrazů Lambda mimo LINQ (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="f8932-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="f8932-103">Výrazy lambda nejsou omezeny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="f8932-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="f8932-104">Můžete je všude, kde je očekávána hodnota delegáta, to znamená, bez ohledu na to anonymní metoda se dá použít.</span><span class="sxs-lookup"><span data-stu-id="f8932-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="f8932-105">Následující příklad ukazuje způsob použití lambda výrazů v obslužné rutině události Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f8932-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="f8932-106">Všimněte si, že typy vstupy (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou odvozeny kompilátorem a není nutné explicitně zadat vstupní parametry lambda.</span><span class="sxs-lookup"><span data-stu-id="f8932-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8932-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8932-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8932-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8932-108">See Also</span></span>

- [<span data-ttu-id="f8932-109">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="f8932-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="f8932-110">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="f8932-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="f8932-111">Language Integrated Query (LINQ))</span><span class="sxs-lookup"><span data-stu-id="f8932-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
