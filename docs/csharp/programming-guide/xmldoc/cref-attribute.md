---
title: cref – atribut – C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 9352718371226279f0a468913040e48cbeed984d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971361"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="325dc-102">cref – atribut (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="325dc-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="325dc-103">`cref` Atribut ve značce dokumentaci XML znamená "odkaz na kód."</span><span class="sxs-lookup"><span data-stu-id="325dc-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="325dc-104">Určuje, že vnitřní text značky je prvek kódu, jako je typ, metodu nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="325dc-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="325dc-105">Dokumentace ke službě nástroje, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) použít `cref` atributů, které mají automaticky generovat hypertextové odkazy na stránky, kde je zdokumentován tento typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="325dc-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="325dc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="325dc-106">Example</span></span>  
 <span data-ttu-id="325dc-107">Následující příklad ukazuje `cref` atributy použité v [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md) značky.</span><span class="sxs-lookup"><span data-stu-id="325dc-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]  
  
 <span data-ttu-id="325dc-108">Při kompilaci, program vygeneruje následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="325dc-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="325dc-109">Všimněte si, že `cref` atribut pro `GetZero` metody, například transformaci pomocí kompilátoru, aby `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="325dc-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="325dc-110">Předpona "M" znamená "method" a je konvence, který je rozpoznán dokumentace nástrojů, jako je DocFX a Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="325dc-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="325dc-111">Úplný seznam předpon, naleznete v tématu [zpracování souboru XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="325dc-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="325dc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="325dc-112">See also</span></span>

- [<span data-ttu-id="325dc-113">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="325dc-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [<span data-ttu-id="325dc-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="325dc-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
