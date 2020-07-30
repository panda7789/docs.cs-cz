---
title: XML – dokumentační komentáře – Průvodce programováním v C#
description: Přečtěte si o dokumentačních komentářích XML. Můžete vytvořit dokumentaci pro svůj kód zahrnutím prvků XML do speciálních polí komentářů.
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
ms.openlocfilehash: fbdeb53331d9fc63d24a3322ea13863d7c0a3630
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381876"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="a9e23-104">Komentáře dokumentace XML (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a9e23-104">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="a9e23-105">V jazyce C# můžete vytvořit dokumentaci pro svůj kód zahrnutím prvků XML do speciálních polí komentářů (označených třemi lomítky) ve zdrojovém kódu přímo před blok kódu, na který komentáře odkazují, například.</span><span class="sxs-lookup"><span data-stu-id="a9e23-105">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="a9e23-106">Při kompilaci s možností [-doc](../../language-reference/compiler-options/doc-compiler-option.md) bude kompilátor hledat všechny značky XML ve zdrojovém kódu a vytvořit soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="a9e23-106">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="a9e23-107">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="a9e23-107">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="a9e23-108">Chcete-li odkazovat na prvky XML (například vaše funkce zpracovává konkrétní prvky XML, které chcete popsat v komentáři k dokumentaci XML), můžete použít standardní mechanizmus quotes ( `<` a `>` ).</span><span class="sxs-lookup"><span data-stu-id="a9e23-108">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="a9e23-109">Chcete-li odkazovat na obecné identifikátory v prvcích referencí kódu ( `cref` ), můžete použít řídicí znaky (například `cref="List&lt;T&gt;"` ) nebo závorky ( `cref="List{T}"` ).</span><span class="sxs-lookup"><span data-stu-id="a9e23-109">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="a9e23-110">Ve zvláštním případě kompilátor analyzuje složené závorky jako lomené závorky, a to proto, aby komentáře v dokumentaci nebyly pro autora při vytváření odkazů na obecné identifikátory tak složité.</span><span class="sxs-lookup"><span data-stu-id="a9e23-110">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="a9e23-111">Komentáře dokumentace XML nejsou metadata; nejsou zahrnuty ve zkompilovaném sestavení, a proto nejsou přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="a9e23-111">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a9e23-112">V této části</span><span class="sxs-lookup"><span data-stu-id="a9e23-112">In this section</span></span>

- [<span data-ttu-id="a9e23-113">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a9e23-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="a9e23-114">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="a9e23-114">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="a9e23-115">Oddělovače pro značky dokumentace</span><span class="sxs-lookup"><span data-stu-id="a9e23-115">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="a9e23-116">Jak používat funkce dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="a9e23-116">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="a9e23-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a9e23-117">Related sections</span></span>

<span data-ttu-id="a9e23-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="a9e23-118">For more information, see:</span></span>

- [<span data-ttu-id="a9e23-119">-doc (zpracování dokumentačních komentářů)</span><span class="sxs-lookup"><span data-stu-id="a9e23-119">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="a9e23-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9e23-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a9e23-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9e23-121">See also</span></span>

- [<span data-ttu-id="a9e23-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a9e23-122">C# Programming Guide</span></span>](../index.md)
