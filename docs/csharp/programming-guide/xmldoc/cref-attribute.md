---
title: atribut cref – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 2a9b9966a28b62c41ac6091268ae172bae3a40d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793445"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="1b9ef-102">cref – atributC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="1b9ef-102">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="1b9ef-103">Atribut `cref` v dokumentaci XML označuje označení "odkaz na kód".</span><span class="sxs-lookup"><span data-stu-id="1b9ef-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="1b9ef-104">Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1b9ef-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="1b9ef-105">Nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , používají atributy `cref` k automatickému vygenerování hypertextových odkazů na stránku, kde je daný typ nebo člen dokumentován.</span><span class="sxs-lookup"><span data-stu-id="1b9ef-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="1b9ef-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b9ef-106">Example</span></span>

<span data-ttu-id="1b9ef-107">Následující příklad ukazuje `cref` atributy používané v [\<zobrazit značky >](./see.md) .</span><span class="sxs-lookup"><span data-stu-id="1b9ef-107">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="1b9ef-108">Při kompilaci program vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="1b9ef-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="1b9ef-109">Všimněte si, že atribut `cref` pro metodu `GetZero`, například, byl transformován kompilátorem na `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="1b9ef-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="1b9ef-110">Předpona "M:" znamená "metoda" a je konvence, kterou rozpoznávají nástroje dokumentace, jako jsou DocFX a Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="1b9ef-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="1b9ef-111">Úplný seznam předpon najdete v tématu [zpracování souboru XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ef-111">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
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
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="1b9ef-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b9ef-112">See also</span></span>

- [<span data-ttu-id="1b9ef-113">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="1b9ef-113">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="1b9ef-114">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="1b9ef-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
