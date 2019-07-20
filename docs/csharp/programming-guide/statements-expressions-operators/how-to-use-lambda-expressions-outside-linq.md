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
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Postupy: Použití výrazů lambda mimo LINQ (C# Průvodce programováním)
Výrazy lambda nejsou omezené na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Můžete je použít všude, kde je očekávána hodnota delegáta, to znamená, kde lze použít anonymní metodu. Následující příklad ukazuje, jak použít výraz lambda v obslužné rutině události model Windows Forms. Všimněte si, že typy vstupů (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou odvozeny kompilátorem a není nutné je explicitně předávat ve vstupních parametrech lambda.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [LINQ (Language Integrated Query))](../../../csharp/programming-guide/concepts/linq/index.md)
