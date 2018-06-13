---
title: cref – atribut (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: a89c7170de956bae65f7018130ba27e61c076376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337022"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="f1703-102">cref – atribut (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f1703-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="f1703-103">`cref` Atribut ve značce XML dokumentace znamená "odkaz na kód."</span><span class="sxs-lookup"><span data-stu-id="f1703-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="f1703-104">Určuje, že vnitřní text značky je element kódu, například typ, metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f1703-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="f1703-105">Dokumentace nástroje, jako [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) použít `cref` atributy, které mají automaticky generovat hypertextové odkazy na stránku, kde je popsána typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="f1703-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1703-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1703-106">Example</span></span>  
 <span data-ttu-id="f1703-107">Následující příklad ukazuje `cref` atributy používané v [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md) značky.</span><span class="sxs-lookup"><span data-stu-id="f1703-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]  
  
 <span data-ttu-id="f1703-108">Při kompilaci, program vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="f1703-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="f1703-109">Všimněte si, že `cref` atribut pro `GetZero` metoda, například transformaci kompilátorem k `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="f1703-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="f1703-110">Předpona "M:" znamená "způsob" a je názvů, který rozpozná dokumentace nástrojů, například aplikaci Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="f1703-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="f1703-111">Úplný seznam předpon, najdete v části [zpracování souboru XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f1703-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1703-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1703-112">See Also</span></span>  
 [<span data-ttu-id="f1703-113">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="f1703-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="f1703-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="f1703-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
