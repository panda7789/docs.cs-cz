---
title: cref atribut - C# programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: b06d0c9d447124dec7d8cf3c0cbbfd0daca78fe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157010"
---
# <a name="cref-attribute-c-programming-guide"></a>cref atribut (C# programovací průvodce)

Atribut `cref` ve značce dokumentace XML znamená "odkaz na kód". Určuje, že vnitřní text značky je prvek kódu, například typ, metoda nebo vlastnost. Nástroje dokumentace, jako [je DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://github.com/EWSoftware/SHFB) používají `cref` atributy k automatickému generování hypertextových odkazů na stránku, kde je typ nebo člen dokumentován.

## <a name="example"></a>Příklad

Následující příklad `cref` ukazuje atributy použité v [ \<tématu>](./see.md) značky.

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Po kompilaci program vytvoří následující soubor XML. Všimněte `cref` si, `GetZero` že atribut metody, například, byl transformován kompilátorem na `"M:TestNamespace.TestClass.GetZero"`. Předpona "M:" znamená "metoda" a je konvence, která je rozpoznána dokumentačními nástroji, jako jsou DocFX a Sandcastle. Úplný seznam předpon naleznete [v tématu Zpracování souboru XML](./processing-the-xml-file.md).

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

## <a name="see-also"></a>Viz také

- [Komentáře dokumentace XML](./index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
