---
title: '&lt;seznam&gt; (C# Průvodce programováním)'
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
ms.openlocfilehash: 768490424403f1235873a681ffba3367e3f128b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337727"
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="3ed7d-102">&lt;seznam&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="3ed7d-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3ed7d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ed7d-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
#### <a name="parameters"></a><span data-ttu-id="3ed7d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ed7d-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="3ed7d-105">Termín, definovat, které budou určené v `description`.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="3ed7d-106">Buď položku v odrážku nebo číslovaný seznam nebo definice `term`.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ed7d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ed7d-107">Remarks</span></span>  
 <span data-ttu-id="3ed7d-108">\<Listheader > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="3ed7d-109">Při definování tabulku, stačí zadat položku termín v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="3ed7d-110">Každá položka v seznamu je definován s \<položky > bloku.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="3ed7d-111">Při vytváření definice seznamu, budete muset zadat oba seznamy `term` a `description`.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="3ed7d-112">Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3ed7d-113">Seznam nebo tabulka může mít jako mnoho \<položky > blokuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="3ed7d-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="3ed7d-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed7d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ed7d-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3ed7d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ed7d-116">See Also</span></span>  
 [<span data-ttu-id="3ed7d-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3ed7d-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3ed7d-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="3ed7d-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
