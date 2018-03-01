---
title: "Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c99f6bc7c9db1f0e2341c31ec5bf60217723d4e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)
Lambda – výrazy nejsou omezeny na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Můžete je všude, kde je očekávané hodnotu delegáta, který je bez ohledu na anonymní metodu je možné použít. Následující příklad ukazuje, jak pomocí výrazu lambda v obslužné rutině událostí Windows Forms. Všimněte si, že typy vstupních hodnot (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou vyvozena na základě kompilátoru a není nutné mít explicitně lambda vstupní parametry.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
