---
title: Přístup k atributům pomocí reflexe (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: aa8bf447fe0df81821a34b5a6d898980749921e1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216016"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Přístup k atributům pomocí reflexe (C#)
Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu by nízké hodnoty bez nějaký způsob načtení těchto informací a funguje na něj. Pomocí reflexe můžete načíst informace, které se definoval pomocí vlastních atributů. Metoda klíče `GetCustomAttributes`, která vrací pole objektů, které jsou za běhu ekvivalenty atributy zdrojového kódu. Tato metoda má několik přetížených verzí. Další informace naleznete v tématu <xref:System.Attribute>.  
  
 Specifikace atribut jako:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 je koncepčním ekvivalentem tohoto:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Však není spuštěn kód do `SampleClass` dotaz na atributy. Volání `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt má být vytvořen a inicializován, jak je uvedeno výše. Pokud třída má další atributy, dalších atributů objektů jsou vytvořeny podobně. `GetCustomAttributes` Vrátí `Author` objektu a dalších atributů objektů v poli. Můžete iterovat přes toto pole určit atributy, které byly použity na základě typu každý prvek pole a extrahovat informace z atributů objektů.  
  
## <a name="example"></a>Příklad  
 Tady je úplný příklad. Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.  
  
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

- <xref:System.Reflection>  
- <xref:System.Attribute>  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
- [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
