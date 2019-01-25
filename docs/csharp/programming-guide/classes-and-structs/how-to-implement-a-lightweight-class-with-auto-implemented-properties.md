---
title: 'Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: a987d0501e36232993a2f1a2b4ebda29d007afd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618643"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi (C# Průvodce programováním v)
Tento příklad ukazuje, jak vytvořit neměnné lehké třídy, která slouží pouze k zapouzdření sadu automaticky implementované vlastnosti. Použijte tento druh konstrukce místo struktury, pokud musíte použít odkazové sémantiky typu.  
  
 Neměnné vlastnosti můžete nastavit dvěma způsoby.  Lze deklarovat [nastavit](../../../csharp/language-reference/keywords/set.md) přístupového objektu bude [privátní](../../../csharp/language-reference/keywords/private.md).  Vlastnost je pouze nastavitelné v rámci typu, ale je neměnný spotřebitelům.  Můžete místo toho deklarovat pouze [získat](../../../csharp/language-reference/keywords/get.md) přístupový objekt, takže je vlastnost neměnné všude s výjimkou v konstruktoru typu.  
  
 Pokud deklarujete privátní `set` přístupový objekt, nelze použít inicializátor objektu k inicializaci vlastnosti. Je nutné použít konstruktor nebo výrobní metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby, jak implementovat neměnné třídy, která má automaticky implementované vlastnosti. Jednotlivé možnosti přinesou deklaruje jednu z vlastností s privátní `set` a jedna z vlastností s `get` pouze.  První třídy používá konstruktor pouze k inicializaci vlastností a druhá třída používá statický objekt pro vytváření metodu, která volá konstruktor.  
  
```csharp  
// This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // constructor to initialize its properties.   
    class Contact  
    {  
        // Read-only properties.   
        public string Name { get; }  
        public string Address { get; private set; }  
  
        // Public constructor.   
        public Contact(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
    }  
  
    // This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // static method and private constructor to initialize its properties.      
    public class Contact2  
    {  
        // Read-only properties.   
        public string Name { get; private set; }  
        public string Address { get; }  
  
        // Private constructor.   
        private Contact2(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
  
        // Public factory method.   
        public static Contact2 CreateContact(string name, string address)  
        {  
            return new Contact2(name, address);  
        }  
    }  
  
    public class Program  
    {   
        static void Main()  
        {  
            // Some simple data sources.   
            string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",   
                              "Cesar Garcia", "Debra Garcia"};  
            string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",  
                                  "12 108th St.", "89 E. 42nd St."};  
  
            // Simple query to demonstrate object creation in select clause.   
            // Create Contact objects by using a constructor.   
            var query1 = from i in Enumerable.Range(0, 5)  
                        select new Contact(names[i], addresses[i]);  
  
            // List elements cannot be modified by client code.   
            var list = query1.ToList();  
            foreach (var contact in list)  
            {  
                Console.WriteLine("{0}, {1}", contact.Name, contact.Address);  
            }  
  
            // Create Contact2 objects by using a static factory method.   
            var query2 = from i in Enumerable.Range(0, 5)  
                         select Contact2.CreateContact(names[i], addresses[i]);  
  
            // Console output is identical to query1.   
            var list2 = query2.ToList();  
  
            // List elements cannot be modified by client code.   
            // CS0272:   
            // list2[0].Name = "Eugene Zabokritski";   
  
            // Keep the console open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();                  
        }  
    }  
  
/* Output:  
    Terry Adams, 123 Main St.  
    Fadi Fakhouri, 345 Cypress Ave.  
    Hanying Feng, 678 1st Ave  
    Cesar Garcia, 12 108th St.  
    Debra Garcia, 89 E. 42nd St.  
*/  
```  
  
 Kompilátor vytvoří pole zálohování pro jednotlivé automaticky implementované vlastnosti. Pole nejsou přístupné přímo ze zdrojového kódu.  
  
## <a name="see-also"></a>Viz také:

- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
