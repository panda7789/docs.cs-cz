---
title: Přístup k atributům pomocí reflexe (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 05c051490dab5265309fd067dfb67f0ef7822541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318487"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Přístup k atributům pomocí reflexe (C#)
Nízké hodnoty bez nějakým způsobem načtení těchto informací a funguje na něm může být skutečnost, že můžete definovat vlastní atributy a umístěte je do vašeho zdrojového kódu. Pomocí reflexe můžete načíst informace, které je definovaný s vlastní atributy. Metoda klíče je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty běhu atributů zdrojového kódu. Tato metoda má několik přetížené verzí. Další informace naleznete v tématu <xref:System.Attribute>.  
  
 Specifikace atributu jako:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 je ekvivalentní k tomuto:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Však není kód spustí, dokud `SampleClass` je dotazován na atributy. Volání metody `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt, který má být vytvořená a inicializovat jako výše. Pokud třída má další atributy, se vytvářejí podobně jako jiné objekty atribut. `GetCustomAttributes` Vrátí `Author` objekt a všechny další objekty atribut v matici. Pak můžete Iterujte přes toto pole, určit atributy, které byly použity na základě typu jednotlivých prvků pole a extrahovat informace z atributů objektů.  
  
## <a name="example"></a>Příklad  
 Zde je kompletní příklad. Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
