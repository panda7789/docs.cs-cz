---
title: Postup dotazování na metadata sestavení s reflexí (LINQ)C#()
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 65f27ae17d77553bfd7a78c1310febd337a55a6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345692"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Postup dotazování na metadata sestavení s reflexí (LINQ)C#()

Rozhraní API pro reflexi knihovny tříd .NET Framework lze použít k prozkoumávání metadat v sestavení .NET a vytvoření kolekcí typů, členů typu, parametrů a tak dále, které jsou v tomto sestavení. Vzhledem k tomu, že tyto kolekce podporují obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, mohou být dotazovány pomocí jazyka LINQ.  
  
Následující příklad ukazuje, jak lze pomocí technologie LINQ použít s reflexí k načtení konkrétních metadat pro metody, které odpovídají zadanému vyhledávacímu kritériu. V tomto případě dotaz vyhledá názvy všech metod v sestavení, které vracejí výčtové typy jako pole.  
  
## <a name="example"></a>Příklad  
  
```csharp  
using System;
using System.Linq;
using System.Reflection;  

class ReflectionHowTO  
{  
    static void Main()  
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

        Console.WriteLine("Press any key to exit... ");  
        Console.ReadKey();  
    }  
}
```  

V příkladu se používá metoda <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> k vrácení pole typů v zadaném sestavení. Filtr [WHERE](../../../language-reference/keywords/where-clause.md) je použit, aby byly vráceny pouze veřejné typy. Pro každý veřejný typ je poddotaz generován pomocí pole <xref:System.Reflection.MethodInfo>, které je vráceno z volání <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Tyto výsledky jsou filtrovány tak, aby vracely pouze metody, jejichž návratový typ je Array nebo else typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Nakonec jsou tyto výsledky seskupeny pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
