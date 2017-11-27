---
title: "cref – atribut (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cffba9083b22813be3dd0379b244f4d078f8549
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="6608c-102">cref – atribut (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6608c-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="6608c-103">`cref` Atribut ve značce XML dokumentace znamená "odkaz na kód."</span><span class="sxs-lookup"><span data-stu-id="6608c-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="6608c-104">Určuje, že vnitřní text značky je element kódu, například typ, metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6608c-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="6608c-105">Dokumentace nástroje, jako [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) použít `cref` atributy, které mají automaticky generovat hypertextové odkazy na stránku, kde je popsána typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="6608c-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6608c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6608c-106">Example</span></span>  
 <span data-ttu-id="6608c-107">Následující příklad ukazuje `cref` atributy používané v [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md) značky.</span><span class="sxs-lookup"><span data-stu-id="6608c-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]  
  
 <span data-ttu-id="6608c-108">Při kompilaci, program vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="6608c-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="6608c-109">Všimněte si, že `cref` atribut pro `GetZero` metoda, například transformaci kompilátorem k `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="6608c-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="6608c-110">Předpona "M:" znamená "způsob" a je názvů, který rozpozná dokumentace nástrojů, například aplikaci Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="6608c-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="6608c-111">Úplný seznam předpon, najdete v části [zpracování souboru XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="6608c-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor">  
            <summary>  
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">  
            <summary>  
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example>   
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6608c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6608c-112">See Also</span></span>  
 [<span data-ttu-id="6608c-113">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6608c-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="6608c-114">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="6608c-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
