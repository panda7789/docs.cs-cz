---
title: Komentáře k dokumentaci XML C# – Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789785"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Komentáře dokumentace XML (C# Průvodce programováním)

V C#aplikaci můžete vytvořit dokumentaci pro svůj kód zahrnutím prvků XML do speciálních polí komentářů (označených třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který komentáře odkazují, například.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Při kompilaci s možností [-doc](../../language-reference/compiler-options/doc-compiler-option.md) bude kompilátor hledat všechny značky XML ve zdrojovém kódu a vytvořit soubor dokumentace XML. Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

Chcete-li odkazovat na prvky XML (například vaše funkce zpracovává konkrétní prvky XML, které chcete popsat v komentáři k dokumentaci XML), můžete použít standardní mechanismus pro Quoting (`<` a `>`).  Chcete-li odkazovat na obecné identifikátory v prvcích referencí kódu (`cref`), můžete použít řídicí znaky (například `cref="List&lt;T&gt;"`) nebo složené závorky (`cref="List{T}"`).  Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.

> [!NOTE]
> Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.

## <a name="in-this-section"></a>V tomto oddílu

- [Doporučené značky pro dokumentační komentáře](./recommended-tags-for-documentation-comments.md)

- [Zpracování souboru XML](./processing-the-xml-file.md)

- [Oddělovače pro dokumentační značky](./delimiters-for-documentation-tags.md)

- [Jak používat funkce dokumentace XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Související oddíly

Další informace najdete v části .

- [-doc (zpracování dokumentačních komentářů)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
