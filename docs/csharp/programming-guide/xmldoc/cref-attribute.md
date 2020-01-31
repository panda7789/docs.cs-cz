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
# <a name="cref-attribute-c-programming-guide"></a>cref – atributC# (Průvodce programováním)

Atribut `cref` v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , používají atributy `cref` k automatickému vygenerování hypertextových odkazů na stránku, kde je daný typ nebo člen dokumentován.

## <a name="example"></a>Příklad

Následující příklad ukazuje `cref` atributy používané v [\<zobrazit značky >](./see.md) .

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Při kompilaci program vytvoří následující soubor XML. Všimněte si, že atribut `cref` pro metodu `GetZero`, například, byl transformován kompilátorem na `"M:TestNamespace.TestClass.GetZero"`. Předpona "M:" znamená "metoda" a je konvence, kterou rozpoznávají nástroje dokumentace, jako jsou DocFX a Sandcastle. Úplný seznam předpon najdete v tématu [zpracování souboru XML](./processing-the-xml-file.md).

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

- [Dokumentační komentáře XML](./index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)
