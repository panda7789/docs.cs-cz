---
title: 'Postupy: Dotazování na metadata sestavení s reflexí (LINQC#) ()'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: fb0fb118eaabbd9d66c5c4a445b0393a69dd2355
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592909"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Postupy: Dotazování na metadata sestavení s reflexí (LINQC#) ()

Rozhraní API pro reflexi knihovny tříd .NET Framework lze použít k prozkoumávání metadat v sestavení .NET a vytvoření kolekcí typů, členů typu, parametrů a tak dále, které jsou v tomto sestavení. Vzhledem k tomu, že tyto <xref:System.Collections.Generic.IEnumerable%601> kolekce podporují obecné rozhraní, mohou být dotazovány pomocí LINQ.  
  
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

V příkladu se používá <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> metoda k vrácení pole typů v zadaném sestavení. Filtr [WHERE](../../../language-reference/keywords/where-clause.md) je použit, aby byly vráceny pouze veřejné typy. Pro každý veřejný typ je poddotaz generován pomocí <xref:System.Reflection.MethodInfo> pole, které je vráceno <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> voláním. Tyto výsledky jsou filtrovány tak, aby vracely pouze metody, jejichž návratový typ je pole nebo jiný typ <xref:System.Collections.Generic.IEnumerable%601>, který implementuje. Nakonec jsou tyto výsledky seskupeny pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](./linq-to-objects.md)
