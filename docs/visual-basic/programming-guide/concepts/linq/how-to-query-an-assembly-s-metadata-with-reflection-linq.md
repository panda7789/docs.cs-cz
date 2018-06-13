---
title: 'Postupy: sestavení dotazu&#39;s Metadata s reflexí (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: f465cccef2009bb9d8da1dc57c14eb09dc008f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643230"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Postupy: sestavení dotazu&#39;s Metadata s reflexí (LINQ) (Visual Basic)
Následující příklad ukazuje, jak lze použít LINQ s reflexí načíst konkrétní metadata o metodách, které splňují zadané kritérium. V takovém případě bude dotaz vrátí názvy ze všech metod sestavení, které vrací výčtové typy jako je například pole.  
  
## <a name="example"></a>Příklad  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
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
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A> metoda vrátí pole typů v zadaném sestavení. [Klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtr tak, aby se vrátí jenom veřejné typy. Pro každý typ veřejné poddotazu je generována pomocí <xref:System.Reflection.MethodInfo> pole, která je vrácena z <xref:System.Type.GetMethods%2A> volání. Tyto výsledky se filtrují vrátit pouze těch metod, jejichž návratový typ je nebo pole s jiným typem, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Nakonec jsou tyto výsledky seskupené podle pomocí názvu typu jako klíč.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
