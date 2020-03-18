---
title: <list> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789743"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="adab6-102">\<seznam> (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="adab6-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="adab6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adab6-103">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="adab6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="adab6-104">Parameters</span></span>

- `term`

  <span data-ttu-id="adab6-105">Termín definovat, který bude definován `description`v .</span><span class="sxs-lookup"><span data-stu-id="adab6-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="adab6-106">Položka v odrážkách nebo číslovaném seznamu `term`nebo definice .</span><span class="sxs-lookup"><span data-stu-id="adab6-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="adab6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adab6-107">Remarks</span></span>

<span data-ttu-id="adab6-108">Blok \<> záhlaví seznamu se používá k definování řádku záhlaví tabulky nebo seznamu definic.</span><span class="sxs-lookup"><span data-stu-id="adab6-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="adab6-109">Při definování tabulky stačí zadat položku termínu v nadpisu.</span><span class="sxs-lookup"><span data-stu-id="adab6-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="adab6-110">Každá položka v seznamu je \<určena položkou> bloku.</span><span class="sxs-lookup"><span data-stu-id="adab6-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="adab6-111">Při vytváření seznamu definic bude nutné `term` zadat `description`obě a .</span><span class="sxs-lookup"><span data-stu-id="adab6-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="adab6-112">Pro tabulku, seznam s odrážkami nebo číslovaný seznam však `description`stačí zadat položku pro .</span><span class="sxs-lookup"><span data-stu-id="adab6-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="adab6-113">Seznam nebo tabulka může \<mít libovolný počet položek> bloky podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="adab6-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="adab6-114">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="adab6-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="adab6-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="adab6-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="adab6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="adab6-116">See also</span></span>

- [<span data-ttu-id="adab6-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="adab6-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="adab6-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="adab6-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
