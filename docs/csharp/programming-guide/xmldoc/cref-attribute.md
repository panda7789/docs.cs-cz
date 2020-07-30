---
title: cref – atribut – Průvodce programováním v C#
description: Přečtěte si o atributu cref. Atribut cref znamená "odkaz na kód" a určuje, zda je vnitřní text značky prvkem kódu.
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 31fa1a3f182d7b72a1dfbe1ce47386f87fbbff75
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381993"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="7fe84-104">cref – atribut (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7fe84-104">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="7fe84-105">`cref`Atribut v dokumentaci XML označuje označení "odkaz na kód".</span><span class="sxs-lookup"><span data-stu-id="7fe84-105">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="7fe84-106">Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7fe84-106">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="7fe84-107">Nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , používají `cref` atributy k automatickému vygenerování hypertextových odkazů na stránku, kde je daný typ nebo člen dokumentován.</span><span class="sxs-lookup"><span data-stu-id="7fe84-107">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="7fe84-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fe84-108">Example</span></span>

<span data-ttu-id="7fe84-109">Následující příklad ukazuje `cref` atributy používané v [\<see>](./see.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="7fe84-109">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="7fe84-110">Při kompilaci program vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="7fe84-110">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="7fe84-111">Všimněte si, že `cref` atribut `GetZero` metody, například, byl transformován kompilátorem na `"M:TestNamespace.TestClass.GetZero"` .</span><span class="sxs-lookup"><span data-stu-id="7fe84-111">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="7fe84-112">Předpona "M:" znamená "metoda" a je konvence, kterou rozpoznávají nástroje dokumentace, jako jsou DocFX a Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="7fe84-112">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="7fe84-113">Úplný seznam předpon najdete v tématu [zpracování souboru XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="7fe84-113">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7fe84-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fe84-114">See also</span></span>

- [<span data-ttu-id="7fe84-115">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="7fe84-115">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="7fe84-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="7fe84-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
