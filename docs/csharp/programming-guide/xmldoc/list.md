---
title: <list> - C# Průvodce programováním
ms.custom: seodec18
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
ms.openlocfilehash: 9ac1d749d18a9d02ce28f8cf600495f345ec0e89
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489264"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="3c1c1-102">\<Seznam > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="3c1c1-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3c1c1-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c1c1-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3c1c1-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c1c1-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="3c1c1-105">Termín, který chcete definovat, které budou určené v `description`.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="3c1c1-106">Buď položku v odrážkami nebo číslovaný seznam nebo definici `term`.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c1c1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c1c1-107">Remarks</span></span>  
 <span data-ttu-id="3c1c1-108">\<Listheader – > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="3c1c1-109">Při definování tabulku, stačí zadat položky pro výraz v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="3c1c1-110">Každá položka v seznamu není zadán s \<položky > bloku.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="3c1c1-111">Při vytváření definice seznamu, budete muset zadat současně `term` a `description`.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="3c1c1-112">Ale pro tabulku, seznam s odrážkami nebo číslovaného seznamu, stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3c1c1-113">Seznam nebo tabulku můžete mít kolik \<položky > blokuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="3c1c1-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="3c1c1-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1c1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c1c1-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3c1c1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c1c1-116">See also</span></span>

- [<span data-ttu-id="3c1c1-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3c1c1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3c1c1-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="3c1c1-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
