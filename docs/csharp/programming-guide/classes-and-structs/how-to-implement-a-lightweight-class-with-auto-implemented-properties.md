---
title: Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 6d121f6be768d41d22ea01d871662913b2daae2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170270"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="ce575-102">Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ce575-102">How to implement a lightweight class with auto-implemented properties (C# Programming Guide)</span></span>

<span data-ttu-id="ce575-103">Tento příklad ukazuje, jak vytvořit neměnné zjednodušené třídy, která slouží pouze k zapouzdření sadu automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce575-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="ce575-104">Použijte tento druh konstrukce namísto struktury, když je nutné použít sémantiku typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="ce575-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="ce575-105">Neměnnou vlastnost můžete vytvořit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="ce575-105">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="ce575-106">Můžete deklarovat [nastavit](../../language-reference/keywords/set.md) přistupující ho jako [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="ce575-106">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="ce575-107">Vlastnost je pouze settable v rámci typu, ale je neměnné pro spotřebitele.</span><span class="sxs-lookup"><span data-stu-id="ce575-107">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="ce575-108">Při deklarování privátní `set` ho přistupujícího objektu nelze použít inicializační objekt inicializovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ce575-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="ce575-109">Je nutné použít konstruktor nebo metodu výroby.</span><span class="sxs-lookup"><span data-stu-id="ce575-109">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="ce575-110">Můžete deklarovat pouze [get](../../language-reference/keywords/get.md) přistupující objekt, který umožňuje vlastnost neměnné všude s výjimkou konstruktoru typu.</span><span class="sxs-lookup"><span data-stu-id="ce575-110">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type's constructor.</span></span>

<span data-ttu-id="ce575-111">Následující příklad ukazuje, jak se vlastnost s pouze get accessor liší než s get a private set.</span><span class="sxs-lookup"><span data-stu-id="ce575-111">The following example shows how a property with only get accessor differs than one with get and private set.</span></span>

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

## <a name="example"></a><span data-ttu-id="ce575-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce575-112">Example</span></span>

<span data-ttu-id="ce575-113">Následující příklad ukazuje dva způsoby implementace neměnné třídy, která má automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce575-113">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="ce575-114">Každý způsob deklaruje jednu z vlastností s privátní `set` a jednu z vlastností s `get` pouze.</span><span class="sxs-lookup"><span data-stu-id="ce575-114">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="ce575-115">První třída používá konstruktor pouze k inicializaci vlastností a druhá třída používá statickou metodu factory, která volá konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ce575-115">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

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

<span data-ttu-id="ce575-116">Kompilátor vytvoří záložní pole pro každou automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ce575-116">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="ce575-117">Pole nejsou přístupná přímo ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ce575-117">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce575-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce575-118">See also</span></span>

- [<span data-ttu-id="ce575-119">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ce575-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="ce575-120">Struct</span><span class="sxs-lookup"><span data-stu-id="ce575-120">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="ce575-121">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="ce575-121">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
