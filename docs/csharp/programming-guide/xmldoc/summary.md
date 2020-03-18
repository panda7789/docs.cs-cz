---
title: <summary> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789677"
---
# <a name="summary-c-programming-guide"></a>\<souhrnný> (průvodce programováním jazyka C#)

## <a name="syntax"></a>Syntaxe

```xml
<summary>description</summary>
```

## <a name="parameters"></a>Parametry

- `description`

  Souhrn objektu.

## <a name="remarks"></a>Poznámky

Značka \<souhrnné> by měla být použita k popisu typu nebo člena typu. Pomocí [ \<poznámek>](./remarks.md) přidejte doplňující informace k popisu typu. Pomocí [atributu cref](./cref-attribute.md) povolte nástroje pro dokumentaci, jako jsou [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://github.com/EWSoftware/SHFB) k vytvoření interních hypertextových odkazů na stránky dokumentace pro prvky kódu.

Text souhrnné \<značky> je jediným zdrojem informací o typu v prostředí IntelliSense a zobrazuje se také v okně prohlížeče objektů.

Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru. Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

V předchozím příkladu se vytvoří následující soubor XML.

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `cref` vytvořit odkaz na obecný typ.

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

V předchozím příkladu se vytvoří následující soubor XML.

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
