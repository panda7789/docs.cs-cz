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
ms.openlocfilehash: 46dd947ac6ff5a45c7d952acaa55e25c3a46969c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588054"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="8e574-102">Dokumentační komentáře XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8e574-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="8e574-103">V jazyce Visual C# můžete vytvářet dokumentaci ke kódu zadáním prvků XML do zvláštních polí komentáře (označeno třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který se komentáře vztahují, například:</span><span class="sxs-lookup"><span data-stu-id="8e574-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="8e574-104">Pokud kompilujete s možností [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , kompilátor bude hledat všechny značky XML ve zdrojovém kódu a vytvoří soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="8e574-104">When you compile with the [/doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="8e574-105">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="8e574-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="8e574-106">Chcete-li odkazovat na prvky XML (například vaše funkce zpracovává konkrétní prvky XML, které chcete popsat v komentáři k dokumentaci XML), můžete použít standardní mechanizmus quotes (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="8e574-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="8e574-107">Chcete-li odkazovat na obecné identifikátory v prvcích`cref`referencí kódu (), můžete použít řídicí znaky ( `cref="List&lt;T&gt;"`například) nebo závorky (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="8e574-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="8e574-108">Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.</span><span class="sxs-lookup"><span data-stu-id="8e574-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e574-109">Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="8e574-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e574-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8e574-110">In This Section</span></span>  
  
- [<span data-ttu-id="8e574-111">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="8e574-111">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)  
  
- [<span data-ttu-id="8e574-112">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="8e574-112">Processing the XML File</span></span>](./processing-the-xml-file.md)  
  
- [<span data-ttu-id="8e574-113">Oddělovače pro značky dokumentace</span><span class="sxs-lookup"><span data-stu-id="8e574-113">Delimiters for Documentation Tags</span></span>](./delimiters-for-documentation-tags.md)  
  
- [<span data-ttu-id="8e574-114">Postupy: Použití funkcí dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="8e574-114">How to: Use the XML Documentation Features</span></span>](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="8e574-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8e574-115">Related Sections</span></span>  
 <span data-ttu-id="8e574-116">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="8e574-116">For more information, see:</span></span>  
  
- [<span data-ttu-id="8e574-117">/doc (zpracování dokumentačních komentářů)</span><span class="sxs-lookup"><span data-stu-id="8e574-117">/doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="8e574-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e574-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e574-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e574-119">See also</span></span>

- [<span data-ttu-id="8e574-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8e574-120">C# Programming Guide</span></span>](../index.md)
