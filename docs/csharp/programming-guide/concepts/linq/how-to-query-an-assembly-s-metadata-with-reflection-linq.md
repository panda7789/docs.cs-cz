---
title: Jak dotazovat metadata sestavení s reflexe (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 6e68cfea2bf3e03aed9de3e4a18cf9941ece34e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168918"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Jak dotazovat metadata sestavení s reflexe (LINQ) (C#)

Rozhraní API pro reflexi třídy rozhraní .NET Framework lze použít ke kontrole metadat v sestavení .NET a k vytvoření kolekcí typů, členů typu, parametrů a tak dále, které jsou v tomto sestavení. Vzhledem k tomu, <xref:System.Collections.Generic.IEnumerable%601> že tyto kolekce podporují obecné rozhraní, mohou být dotazovány pomocí LINQ.  
  
Následující příklad ukazuje, jak linq lze použít s odrazem načíst konkrétní metadata o metodách, které odpovídají zadané vyhledávací kritérium. V takovém případě dotaz najde názvy všech metod v sestavení, které vracejí výčet typů, jako jsou pole.  
  
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

Příklad používá <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> metodu k vrácení pole typů v zadaném sestavení. Kde [where](../../../language-reference/keywords/where-clause.md) je použit filtr tak, aby byly vráceny pouze veřejné typy. Pro každý veřejný typ je generován poddotaz <xref:System.Reflection.MethodInfo> pomocí pole, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> které je vráceno z volání. Tyto výsledky jsou filtrovány vrátit pouze ty metody, jejichž návratový <xref:System.Collections.Generic.IEnumerable%601>typ je pole nebo jiný typ, který implementuje . Nakonec tyto výsledky jsou seskupeny pomocí názvu typu jako klíč.  
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (C#)](./linq-to-objects.md)
