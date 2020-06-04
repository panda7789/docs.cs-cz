---
title: 'Postupy: Vytvoření dotazu na metadata sestavení s reflexí (LINQ)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: a4f73bd2c8c01cbf92fac67991f01a1cb3dee932
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396451"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Postupy: vytvoření dotazu na metadata sestavení s reflexí (LINQ) (Visual Basic)
Následující příklad ukazuje, jak lze pomocí technologie LINQ použít s reflexí k načtení konkrétních metadat pro metody, které odpovídají zadanému vyhledávacímu kritériu. V tomto případě dotaz vyhledá názvy všech metod v sestavení, které vracejí výčtové typy jako pole.  
  
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
  
V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> Metoda k vrácení pole typů v zadaném sestavení. Filtr [klauzule WHERE](../../../language-reference/queries/where-clause.md) je použit, aby byly vráceny pouze veřejné typy. Pro každý veřejný typ je poddotaz generován pomocí <xref:System.Reflection.MethodInfo> pole, které je vráceno <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> voláním. Tyto výsledky jsou filtrovány tak, aby vracely pouze metody, jejichž návratový typ je pole nebo jiný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> . Nakonec jsou tyto výsledky seskupeny pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
