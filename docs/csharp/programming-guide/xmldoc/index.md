---
title: Komentáře k dokumentaci XML – průvodce programováním jazyka C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76789785"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Komentáře k dokumentaci XML (průvodce programováním jazyka C#)

V jazyce C# můžete vytvořit dokumentaci pro váš kód zahrnutím elementů XML do zvláštních polí komentářů (označených trojitými lomítky) ve zdrojovém kódu přímo před blokem kódu, na který odkazují komentáře.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Při kompilaci s volbou [-doc](../../language-reference/compiler-options/doc-compiler-option.md) kompilátor vyhledá všechny značky XML ve zdrojovém kódu a vytvoří soubor dokumentace XML. Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

Chcete-li odkazovat na elementy XML (například vaše funkce zpracovává určité elementy XML, které chcete`<` `>`popsat v komentáři k dokumentaci XML), můžete použít standardní mechanismus citace ( a ).  Chcete-li odkazovat na obecné`cref`identifikátory v elementech odkazu na kód `cref="List&lt;T&gt;"`( ),`cref="List{T}"`můžete použít řídicí znaky (například) nebo závorky ( ).  Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.

> [!NOTE]
> Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.

## <a name="in-this-section"></a>V tomto oddílu

- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)

- [Zpracování souboru XML](./processing-the-xml-file.md)

- [Oddělovače pro značky dokumentace](./delimiters-for-documentation-tags.md)

- [Jak používat funkce dokumentace XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [-doc (Komentáře k procesní dokumentaci)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
