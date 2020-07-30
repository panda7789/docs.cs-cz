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
# <a name="cref-attribute-c-programming-guide"></a>cref – atribut (Průvodce programováním v C#)

`cref`Atribut v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , používají `cref` atributy k automatickému vygenerování hypertextových odkazů na stránku, kde je daný typ nebo člen dokumentován.

## <a name="example"></a>Příklad

Následující příklad ukazuje `cref` atributy používané v [\<see>](./see.md) tagu.

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Při kompilaci program vytvoří následující soubor XML. Všimněte si, že `cref` atribut `GetZero` metody, například, byl transformován kompilátorem na `"M:TestNamespace.TestClass.GetZero"` . Předpona "M:" znamená "metoda" a je konvence, kterou rozpoznávají nástroje dokumentace, jako jsou DocFX a Sandcastle. Úplný seznam předpon najdete v tématu [zpracování souboru XML](./processing-the-xml-file.md).

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

## <a name="see-also"></a>Viz také:

- [Komentáře dokumentace XML](./index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
