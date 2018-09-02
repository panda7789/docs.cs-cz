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
ms.openlocfilehash: 4a8b6395209e95f3156354c4ee919291e05c7471
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417775"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="92981-102">Dokumentační komentáře XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="92981-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="92981-103">V jazyce Visual C# můžete vytvářet dokumentaci ke kódu zadáním prvků XML do zvláštních polí komentáře (označeno třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který se komentáře vztahují, například:</span><span class="sxs-lookup"><span data-stu-id="92981-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="92981-104">Pokud kompilujete s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) možnost, začne kompilátor vyhledávat všechny značky XML ve zdrojovém kódu a vytváření souborů dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="92981-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="92981-105">Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="92981-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="92981-106">Chcete-li odkazovat na prvky XML (například vaší funkce zpracovává konkrétní prvky, které chcete popsat v komentáři XML dokumentace), můžete použít standardní mechanismus citací (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="92981-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="92981-107">K odkazování na obecné identifikátory v kódu – odkaz (`cref`) prvků, můžete použít buď řídicí znaky (například `cref="List&lt;T&gt;"`) nebo složené závorky (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="92981-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="92981-108">Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.</span><span class="sxs-lookup"><span data-stu-id="92981-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92981-109">Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="92981-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92981-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="92981-110">In This Section</span></span>  
  
-   [<span data-ttu-id="92981-111">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="92981-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="92981-112">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="92981-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="92981-113">Oddělovače pro značky dokumentace</span><span class="sxs-lookup"><span data-stu-id="92981-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="92981-114">Postup: Používání funkcí dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="92981-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="92981-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="92981-115">Related Sections</span></span>  
 <span data-ttu-id="92981-116">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="92981-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="92981-117">/ DOC (zpracování dokumentačních komentářů)</span><span class="sxs-lookup"><span data-stu-id="92981-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="92981-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92981-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92981-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="92981-119">See Also</span></span>  
 [<span data-ttu-id="92981-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="92981-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
