---
title: <list> – Průvodce programováním v C#
description: Další informace o XML <list> Inteligentní. Tato značka slouží k vytváření tabulek a definic, odrážek nebo číslovaných seznamů pomocí bloků Item.
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
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381863"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="fc909-105">\<list>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fc909-105">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc909-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc909-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="fc909-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc909-107">Parameters</span></span>

- `term`

  <span data-ttu-id="fc909-108">Pojem, který definuje, který bude definován v `description` .</span><span class="sxs-lookup"><span data-stu-id="fc909-108">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="fc909-109">Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term` .</span><span class="sxs-lookup"><span data-stu-id="fc909-109">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="fc909-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc909-110">Remarks</span></span>

<span data-ttu-id="fc909-111">Tento `<listheader>` blok slouží k definování řádku záhlaví seznamu tabulek nebo definic.</span><span class="sxs-lookup"><span data-stu-id="fc909-111">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="fc909-112">Při definování tabulky stačí zadat položku pro termín v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="fc909-112">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="fc909-113">Každá položka v seznamu je určena `<item>` blokem.</span><span class="sxs-lookup"><span data-stu-id="fc909-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="fc909-114">Při vytváření seznamu definic budete muset zadat i `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="fc909-114">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="fc909-115">U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description` .</span><span class="sxs-lookup"><span data-stu-id="fc909-115">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="fc909-116">Seznam nebo tabulka může mít tolik `<item>` bloků, kolik potřebujete.</span><span class="sxs-lookup"><span data-stu-id="fc909-116">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="fc909-117">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="fc909-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="fc909-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc909-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="fc909-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc909-119">See also</span></span>

- [<span data-ttu-id="fc909-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="fc909-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="fc909-121">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="fc909-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
