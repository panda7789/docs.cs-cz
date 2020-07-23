---
title: Přístup k atributům pomocí reflexe (C#)
description: Pomocí reflexe získáte informace definované pomocí vlastních atributů v jazyce C# pomocí metody GetCustomAttributes.
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 9425141d64fd061d0c1f628228693cce02f7bfa0
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925095"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="79962-103">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="79962-103">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="79962-104">Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu, by měl být malými hodnotami bez jakéhokoli způsobu, jak tyto informace načítat a na ni bude působit.</span><span class="sxs-lookup"><span data-stu-id="79962-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="79962-105">Pomocí reflexe můžete načíst informace, které byly definovány s vlastními atributy.</span><span class="sxs-lookup"><span data-stu-id="79962-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="79962-106">Klíčovou metodou je `GetCustomAttributes` , která vrací pole objektů, které jsou ekvivalenty zdrojového kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="79962-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="79962-107">Tato metoda má několik přetížených verzí.</span><span class="sxs-lookup"><span data-stu-id="79962-107">This method has several overloaded versions.</span></span> <span data-ttu-id="79962-108">Další informace naleznete v tématu <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="79962-108">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="79962-109">Specifikace atributu jako:</span><span class="sxs-lookup"><span data-stu-id="79962-109">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="79962-110">je koncepční ekvivalent:</span><span class="sxs-lookup"><span data-stu-id="79962-110">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="79962-111">Kód však není proveden, dokud `SampleClass` není dotazován na atributy.</span><span class="sxs-lookup"><span data-stu-id="79962-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="79962-112">Volání `GetCustomAttributes` na způsobí, že se objekt sestrojí `SampleClass` `Author` a inicializuje podle výše uvedeného.</span><span class="sxs-lookup"><span data-stu-id="79962-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="79962-113">Pokud má třída jiné atributy, další objekty atributů jsou konstruovány podobně.</span><span class="sxs-lookup"><span data-stu-id="79962-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="79962-114">`GetCustomAttributes`pak vrátí `Author` objekt a všechny objekty atributů v poli.</span><span class="sxs-lookup"><span data-stu-id="79962-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="79962-115">Pak můžete iterovat přes toto pole, určit, jaké atributy byly aplikovány na základě typu každého prvku pole a extrahovat informace z objektů atributů.</span><span class="sxs-lookup"><span data-stu-id="79962-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79962-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="79962-116">Example</span></span>  
 <span data-ttu-id="79962-117">Tady je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="79962-117">Here is a complete example.</span></span> <span data-ttu-id="79962-118">Vlastní atribut je definován, aplikován na několik entit a načten prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="79962-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79962-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="79962-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="79962-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="79962-120">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="79962-121">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="79962-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="79962-122">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="79962-122">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="79962-123">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="79962-123">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="79962-124">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="79962-124">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
