---
title: Komentáře k dokumentaci XML C# – Průvodce programováním
ms.custom: seodec18
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
ms.openlocfilehash: 6405b094ccc50499bfeb4db4522f0ec9b01f68ad
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523482"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Dokumentační komentáře XML (Průvodce programováním v C#)
V jazyce Visual C# můžete vytvářet dokumentaci ke kódu zadáním prvků XML do zvláštních polí komentáře (označeno třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který se komentáře vztahují, například:  
  
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
  
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)  
  
- [Zpracování souboru XML](./processing-the-xml-file.md)  
  
- [Oddělovače pro značky dokumentace](./delimiters-for-documentation-tags.md)  
  
- [Postup: Používání funkcí dokumentace XML](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [-doc (zpracování dokumentačních komentářů)](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
