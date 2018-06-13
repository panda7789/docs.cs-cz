---
title: Dokumentační komentáře XML (Průvodce programováním v C#)
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
ms.openlocfilehash: 2f3bc5780e202bc5905cc027821f937b75335454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359167"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Dokumentační komentáře XML (Průvodce programováním v C#)
V jazyce Visual C# můžete vytvářet dokumentaci ke kódu zadáním prvků XML do zvláštních polí komentáře (označeno třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který se komentáře vztahují, například:  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 Když kompilujete s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) možnost, bude kompilátor hledat pro všechny značky XML ve zdrojovém kódu a vytváření souborů dokumentace XML. K vytvoření konečné dokumentaci založenou na soubor generované kompilátorem, můžete vytvořit vlastní nástroj nebo pomocí nástroje, jako například [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Odkázat na elementy XML (například vaše funkce procesy konkrétní elementy XML, který chcete popisují v dokumentaci komentáře jazyka XML), můžete použít standardní citací mechanismus (`<` a `>`).  K odkazování na obecné identifikátory v kódu – odkaz (`cref`) elementy, můžete použít buď řídicí znaky (například `cref="List&lt;T&gt;"`) nebo složené závorky (`cref="List{T}"`).  Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.  
  
> [!NOTE]
>  Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [Zpracování souboru XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Oddělovače pro značky dokumentace](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Postup: Používání funkcí dokumentace XML](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [/ DOC (zpracování dokumentačních komentářů)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
