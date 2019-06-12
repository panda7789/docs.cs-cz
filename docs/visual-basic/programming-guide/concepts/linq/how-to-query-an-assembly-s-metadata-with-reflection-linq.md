---
title: 'Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: fd9fa5fcbd1f02cec4e96511fa8c4e60d77ce965
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026057"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (Visual Basic)
Následující příklad ukazuje, jak LINQ lze pomocí reflexe k načtení metadat konkrétní metody, které odpovídají zadanému vyhledávacímu kritériu. Dotaz v tomto případě se vyhledat názvy všechny metody v sestavení, které vrací vyčíslitelné typy například pole.  
  
## <a name="example"></a>Příklad  
  
```vb
Imports System.Linq
Imports System.Reflection  

Module Module1  
    Sub Main()  
        Dim asmbly As Assembly =
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()
                            Where type.IsPublic
                            From method In type.GetMethods()
                            Where method.ReturnType.IsArray = True
                            Let name = method.ToString()
                            Let typeName = type.ToString()
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.WriteLine("Press any key to exit... ")  
        Console.ReadKey()  
    End Sub  
End Module  
```  
  
V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> metoda vrátí pole typů v zadaném sestavení. [Klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtr tak, aby se vrátí pouze veřejné typy. Pro každý veřejný typ poddotaz je generována pomocí <xref:System.Reflection.MethodInfo> pole, která je vrácena z <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> volání. Tyto výsledky se filtrují pro vrácení pouze těch metod, jehož návratový typ je pole, jinak se typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. A konečně jsou tyto výsledky seskupené podle pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
