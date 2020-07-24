---
title: Postup dotazování na metadata sestavení s reflexí (LINQ) (C#)
description: Naučte se používat LINQ s rozhraními API pro reflexi .NET v jazyce C# k načtení konkrétních metadat pro metody, které odpovídají kritériím vyhledávání.
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: dc5352e9cb90e9ad2808fb027823174d07d69da6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104587"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Postup dotazování na metadata sestavení s reflexí (LINQ) (C#)

Rozhraní API pro reflexi rozhraní .NET lze použít k prohlédnutí metadat v sestavení .NET a vytvoření kolekcí typů, členů typu, parametrů a tak dále, které jsou v tomto sestavení. Vzhledem k tomu, že tyto kolekce podporují obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, mohou být dotazovány pomocí LINQ.  
  
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

V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> Metoda k vrácení pole typů v zadaném sestavení. Filtr [WHERE](../../../language-reference/keywords/where-clause.md) je použit, aby byly vráceny pouze veřejné typy. Pro každý veřejný typ je poddotaz generován pomocí <xref:System.Reflection.MethodInfo> pole, které je vráceno <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> voláním. Tyto výsledky jsou filtrovány tak, aby vracely pouze metody, jejichž návratový typ je pole nebo jiný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> . Nakonec jsou tyto výsledky seskupeny pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také

- [LINQ to Objects (C#)](./linq-to-objects.md)
