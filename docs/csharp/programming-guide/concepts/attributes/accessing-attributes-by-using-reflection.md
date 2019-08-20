---
title: Přístup k atributům pomocí reflexe (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595505"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Přístup k atributům pomocí reflexe (C#)
Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu, by měl být malými hodnotami bez jakéhokoli způsobu, jak tyto informace načítat a na ni bude působit. Pomocí reflexe můžete načíst informace, které byly definovány s vlastními atributy. Klíčovou metodou je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty zdrojového kódu v době běhu. Tato metoda má několik přetížených verzí. Další informace naleznete v tématu <xref:System.Attribute>.  
  
 Specifikace atributu jako:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 je koncepční ekvivalent:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Kód však není proveden, dokud `SampleClass` není dotazován na atributy. Volání `GetCustomAttributes` `Author` na `SampleClass` způsobí, že se objekt sestrojí a inicializuje podle výše uvedeného. Pokud má třída jiné atributy, další objekty atributů jsou konstruovány podobně. `GetCustomAttributes`pak vrátí `Author` objekt a všechny objekty atributů v poli. Pak můžete iterovat přes toto pole, určit, jaké atributy byly aplikovány na základě typu každého prvku pole a extrahovat informace z objektů atributů.  
  
## <a name="example"></a>Příklad  
 Tady je kompletní příklad. Vlastní atribut je definován, aplikován na několik entit a načten prostřednictvím reflexe.  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce C#](../../index.md)
- [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](./index.md)
- [Vytváření vlastních atributů (C#)](./creating-custom-attributes.md)
