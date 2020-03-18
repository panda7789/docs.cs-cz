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
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="4998a-102">Komentáře k dokumentaci XML (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4998a-102">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="4998a-103">V jazyce C# můžete vytvořit dokumentaci pro váš kód zahrnutím elementů XML do zvláštních polí komentářů (označených trojitými lomítky) ve zdrojovém kódu přímo před blokem kódu, na který odkazují komentáře.</span><span class="sxs-lookup"><span data-stu-id="4998a-103">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="4998a-104">Při kompilaci s volbou [-doc](../../language-reference/compiler-options/doc-compiler-option.md) kompilátor vyhledá všechny značky XML ve zdrojovém kódu a vytvoří soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="4998a-104">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="4998a-105">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="4998a-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="4998a-106">Chcete-li odkazovat na elementy XML (například vaše funkce zpracovává určité elementy XML, které chcete`<` `>`popsat v komentáři k dokumentaci XML), můžete použít standardní mechanismus citace ( a ).</span><span class="sxs-lookup"><span data-stu-id="4998a-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="4998a-107">Chcete-li odkazovat na obecné`cref`identifikátory v elementech odkazu na kód `cref="List&lt;T&gt;"`( ),`cref="List{T}"`můžete použít řídicí znaky (například) nebo závorky ( ).</span><span class="sxs-lookup"><span data-stu-id="4998a-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="4998a-108">Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.</span><span class="sxs-lookup"><span data-stu-id="4998a-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="4998a-109">Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="4998a-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4998a-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4998a-110">In this section</span></span>

- [<span data-ttu-id="4998a-111">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4998a-111">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="4998a-112">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="4998a-112">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="4998a-113">Oddělovače pro značky dokumentace</span><span class="sxs-lookup"><span data-stu-id="4998a-113">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="4998a-114">Jak používat funkce dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="4998a-114">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="4998a-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4998a-115">Related sections</span></span>

<span data-ttu-id="4998a-116">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="4998a-116">For more information, see:</span></span>

- [<span data-ttu-id="4998a-117">-doc (Komentáře k procesní dokumentaci)</span><span class="sxs-lookup"><span data-stu-id="4998a-117">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="4998a-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4998a-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4998a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4998a-119">See also</span></span>

- [<span data-ttu-id="4998a-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4998a-120">C# Programming Guide</span></span>](../index.md)
