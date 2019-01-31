---
title: 'Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 849244f1345966dbe198686f4f9024fc321b6ded
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263495"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (C#)
Následující příklad ukazuje, jak LINQ lze pomocí reflexe k načtení metadat konkrétní metody, které odpovídají zadanému vyhledávacímu kritériu. Dotaz v tomto případě se vyhledat názvy všechny metody v sestavení, které vrací vyčíslitelné typy například pole.  
  
## <a name="example"></a>Příklad  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
        {  
            Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
            var pubTypesQuery = from type in assembly.GetTypes()  
                        where type.IsPublic  
                            from method in type.GetMethods()  
                            where method.ReturnType.IsArray == true   
                                || ( method.ReturnType.GetInterface(  
                                    typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                                && method.ReturnType.FullName != "System.String" )  
                            group method.ToString() by type.ToString();  
  
            foreach (var groupOfMethods in pubTypesQuery)  
            {  
                Console.WriteLine("Type: {0}", groupOfMethods.Key);  
                foreach (var method in groupOfMethods)  
                {  
                    Console.WriteLine("  {0}", method);  
                }  
            }  
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A> metoda vrátí pole typů v zadaném sestavení. [Kde](../../../../csharp/language-reference/keywords/where-clause.md) filtr tak, aby se vrátí pouze veřejné typy. Pro každý veřejný typ poddotaz je generována pomocí <xref:System.Reflection.MethodInfo> pole, která je vrácena z <xref:System.Type.GetMethods%2A> volání. Tyto výsledky se filtrují pro vrácení pouze těch metod, jehož návratový typ je pole, jinak se typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. A konečně jsou tyto výsledky seskupené podle pomocí názvu typu jako klíč.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
