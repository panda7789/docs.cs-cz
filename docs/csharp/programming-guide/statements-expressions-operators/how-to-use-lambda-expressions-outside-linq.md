---
title: 'Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: eb9fea64b8aeb96a880b7e177673c1316b7aa4c1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45639169"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)
Výrazy lambda nejsou omezeny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Můžete je všude, kde je očekávána hodnota delegáta, to znamená, bez ohledu na to anonymní metoda se dá použít. Následující příklad ukazuje způsob použití lambda výrazů v obslužné rutině události Windows Forms. Všimněte si, že typy vstupy (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou odvozeny kompilátorem a není nutné explicitně zadat vstupní parametry lambda.  
  
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
  
## <a name="see-also"></a>Viz také

- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [Language Integrated Query (LINQ))](../../../csharp/programming-guide/concepts/linq/index.md)
