---
title: 'Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 9612ec916481776691e85a84503ce5063c20b099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Postupy: Implementace lehké třídy s automaticky implementovanými vlastnostmi (Průvodce programováním v C#)
Tento příklad ukazuje postup vytvoření neměnné lehké třídy, která slouží pouze k zapouzdření sadu automaticky implementované vlastnosti. Použijte tento druh konstrukce místo struktury, pokud je nutné použít Sémantika typu odkaz.  
  
 Neměnné vlastnosti můžete provést dvěma způsoby.  Je možné deklarovat [nastavit](../../../csharp/language-reference/keywords/set.md) accessor.to být [privátní](../../../csharp/language-reference/keywords/private.md).  Vlastnost je nastavit v rámci typu, ale je neměnný k příjemce.  Můžete místo toho deklarovat jenom [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu, což může neměnné everywhere kromě v konstruktoru typu vlastnost.  
  
 Když je deklarovat privátního `set` přistupujícího objektu, nemůžete použít inicializátoru objektu k inicializaci vlastnosti. Je třeba použít konstruktor nebo metoda factory.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby, jak implementovat třídu neměnné automaticky implementované vlastnosti. Každý způsob deklaruje jednu z vlastností s privátního `set` a jedna z vlastností s `get` pouze.  První třídy používá konstruktor jenom k inicializaci vlastností a druhé třídy používá statické tovární metody, která volá konstruktor.  
  
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
  
 Kompilátor vytvoří základní pole pro každý automaticky implementované vlastnosti. Pole nejsou dostupné přímo z zdrojového kódu.  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
