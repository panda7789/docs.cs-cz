---
title: 'Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 6ba6c6f50b4d2f717de4325b5cd21434066b2899
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389181"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Postupy: Použití výrazů lambda mimo LINQ (Průvodce programováním v C#)
Výrazy lambda nejsou omezeny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Můžete je všude, kde je očekávána hodnota delegáta, to znamená, bez ohledu na to anonymní metoda se dá použít. Následující příklad ukazuje způsob použití lambda výrazů v obslužné rutině události Windows Forms. Všimněte si, že typy vstupy (<xref:System.Object> a <xref:System.Windows.Forms.MouseEventArgs>) jsou odvozeny kompilátorem a není nutné explicitně zadat vstupní parametry lambda.  
  
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
 [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
