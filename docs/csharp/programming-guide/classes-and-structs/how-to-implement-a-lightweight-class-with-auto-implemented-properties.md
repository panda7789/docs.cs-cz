---
title: Postup implementace odlehčené třídy s automaticky implementovanými vlastnostmi – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: e9b2ab32fb79b80649305843abdd935b8c582bc0
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628212"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="752f5-102">Jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="752f5-102">How to implement a lightweight class with auto-implemented properties (C# Programming Guide)</span></span>

<span data-ttu-id="752f5-103">Tento příklad ukazuje, jak vytvořit neproměnlivou odlehčenou třídu, která slouží pouze k zapouzdření sady automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="752f5-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="752f5-104">Použijte tento druh konstrukce namísto struktury, pokud je nutné použít sémantiku typu reference.</span><span class="sxs-lookup"><span data-stu-id="752f5-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="752f5-105">Neměnné vlastnosti můžete vytvořit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="752f5-105">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="752f5-106">Přístupový objekt [set](../../language-reference/keywords/set.md) můžete deklarovat jako [soukromý](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="752f5-106">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="752f5-107">Vlastnost je nastavena pouze v rámci typu, ale je neměnná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="752f5-107">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="752f5-108">Při deklaraci privátního přístupového objektu `set` nelze použít inicializátor objektu pro inicializaci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="752f5-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="752f5-109">Je nutné použít konstruktor nebo metodu Factory.</span><span class="sxs-lookup"><span data-stu-id="752f5-109">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="752f5-110">Můžete deklarovat pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , který způsobí, že vlastnost není proměnlivá všude s výjimkou v konstruktoru typu.</span><span class="sxs-lookup"><span data-stu-id="752f5-110">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type's constructor.</span></span>

<span data-ttu-id="752f5-111">Následující příklad ukazuje, jak se vlastnost s přístupujícím objektem Get liší od typu s get a soukromou sadou.</span><span class="sxs-lookup"><span data-stu-id="752f5-111">The following example shows how a property with only get accessor differs than one with get and private set.</span></span>

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName; 

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a><span data-ttu-id="752f5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="752f5-112">Example</span></span>

<span data-ttu-id="752f5-113">Následující příklad ukazuje dva způsoby, jak implementovat neměnitelnou třídu, která má automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="752f5-113">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="752f5-114">Každý způsob deklaruje jednu vlastnost s privátní `set` a jednu z vlastností pouze `get`.</span><span class="sxs-lookup"><span data-stu-id="752f5-114">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="752f5-115">První třída používá konstruktor pouze k inicializaci vlastností a druhá třída používá statickou metodu objektu pro vytváření, která volá konstruktor.</span><span class="sxs-lookup"><span data-stu-id="752f5-115">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
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
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
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

<span data-ttu-id="752f5-116">Kompilátor vytvoří zálohovací pole pro každou automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="752f5-116">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="752f5-117">Pole nejsou k dispozici přímo ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="752f5-117">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="752f5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="752f5-118">See also</span></span>

- [<span data-ttu-id="752f5-119">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="752f5-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="752f5-120">struct</span><span class="sxs-lookup"><span data-stu-id="752f5-120">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="752f5-121">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="752f5-121">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
