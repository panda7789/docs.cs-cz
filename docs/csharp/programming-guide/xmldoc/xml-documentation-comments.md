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
ms.openlocfilehash: ab4f8fae748455f96ca5ea0255658cc76dd14f97
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216656"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="4e9f0-102">Dokumentační komentáře XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4e9f0-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="4e9f0-103">V jazyce Visual C# můžete vytvářet dokumentaci ke kódu zadáním prvků XML do zvláštních polí komentáře (označeno třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který se komentáře vztahují, například:</span><span class="sxs-lookup"><span data-stu-id="4e9f0-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="4e9f0-104">Pokud kompilujete s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) možnost, začne kompilátor vyhledávat všechny značky XML ve zdrojovém kódu a vytváření souborů dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="4e9f0-105">Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="4e9f0-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="4e9f0-106">Chcete-li odkazovat na prvky XML (například vaší funkce zpracovává konkrétní prvky, které chcete popsat v komentáři XML dokumentace), můžete použít standardní mechanismus citací (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="4e9f0-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="4e9f0-107">K odkazování na obecné identifikátory v kódu – odkaz (`cref`) prvků, můžete použít buď řídicí znaky (například `cref="List&lt;T&gt;"`) nebo složené závorky (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="4e9f0-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="4e9f0-108">Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e9f0-109">Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="4e9f0-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e9f0-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4e9f0-110">In This Section</span></span>  
  
-   [<span data-ttu-id="4e9f0-111">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4e9f0-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="4e9f0-112">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="4e9f0-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="4e9f0-113">Oddělovače pro značky dokumentace</span><span class="sxs-lookup"><span data-stu-id="4e9f0-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="4e9f0-114">Postup: Používání funkcí dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="4e9f0-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="4e9f0-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4e9f0-115">Related Sections</span></span>  
 <span data-ttu-id="4e9f0-116">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="4e9f0-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="4e9f0-117">/ DOC (zpracování dokumentačních komentářů)</span><span class="sxs-lookup"><span data-stu-id="4e9f0-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="4e9f0-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e9f0-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e9f0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e9f0-119">See Also</span></span>

- [<span data-ttu-id="4e9f0-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4e9f0-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
