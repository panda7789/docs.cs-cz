---
title: <summary> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789677"
---
# <a name="summary-c-programming-guide"></a>> \<souhrnuC# (Průvodce programováním)

## <a name="syntax"></a>Syntaxe

```xml
<summary>description</summary>
```

## <a name="parameters"></a>Parametry

- `description`

  Souhrn objektu.

## <a name="remarks"></a>Poznámky

K popisu typu nebo členu typu by měla být použita značka \<Summary >. Pomocí [\<poznámky >](./remarks.md) přidat doplňující informace k popisu typu. Pomocí [atributu cref](./cref-attribute.md) můžete povolit nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , a vytvářet interní hypertextové odkazy na stránky dokumentace pro prvky kódu.

Text > Značka \<Summary je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v okně Prohlížeč objektů.

Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru. Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

Předchozí příklad vytvoří následující soubor XML.

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

Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecný typ.

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

Předchozí příklad vytvoří následující soubor XML.

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

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../index.md)
- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)
