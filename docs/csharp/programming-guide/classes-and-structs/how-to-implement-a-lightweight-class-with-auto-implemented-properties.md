---
title: Postup implementace odlehčené třídy s automaticky implementovanými vlastnostmi – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: b5bf2e84ffe47cd1eaf17e877a20a700e98339ff
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970910"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi (C# Průvodce programováním)

Tento příklad ukazuje, jak vytvořit neproměnlivou odlehčenou třídu, která slouží pouze k zapouzdření sady automaticky implementovaných vlastností. Použijte tento druh konstrukce namísto struktury, pokud je nutné použít sémantiku typu reference.

Neměnné vlastnosti můžete vytvořit dvěma způsoby:

- Přístupový objekt [set](../../language-reference/keywords/set.md) můžete deklarovat jako [soukromý](../../language-reference/keywords/private.md).  Vlastnost je nastavena pouze v rámci typu, ale je neměnná pro příjemce.

  Při deklaraci privátního přístupového objektu `set` nelze použít inicializátor objektu pro inicializaci vlastnosti. Je nutné použít konstruktor nebo metodu Factory.
- Můžete deklarovat pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , který způsobí, že vlastnost není proměnlivá všude s výjimkou v konstruktoru typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje dva způsoby, jak implementovat neměnitelnou třídu, která má automaticky implementované vlastnosti. Každý způsob deklaruje jednu vlastnost s privátní `set` a jednu z vlastností pouze `get`.  První třída používá konstruktor pouze k inicializaci vlastností a druhá třída používá statickou metodu objektu pro vytváření, která volá konstruktor.

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

Kompilátor vytvoří zálohovací pole pro každou automaticky implementovanou vlastnost. Pole nejsou k dispozici přímo ze zdrojového kódu.

## <a name="see-also"></a>Viz také:

- [Vlastnosti](./properties.md)
- [struct](../../language-reference/keywords/struct.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
