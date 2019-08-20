---
title: <list> – C# Průvodce programováním
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
ms.openlocfilehash: aadb24c43d49acb3e71490efd156b14d9fc5f133
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587969"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="e457f-102">\<seznam > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="e457f-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e457f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e457f-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e457f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e457f-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="e457f-105">Pojem, který definuje, který bude definován v `description`.</span><span class="sxs-lookup"><span data-stu-id="e457f-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="e457f-106">Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term`.</span><span class="sxs-lookup"><span data-stu-id="e457f-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e457f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e457f-107">Remarks</span></span>  
 <span data-ttu-id="e457f-108">Blok \<listheader – > slouží k definování řádku záhlaví v seznamu tabulek nebo definic.</span><span class="sxs-lookup"><span data-stu-id="e457f-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="e457f-109">Při definování tabulky stačí zadat položku pro termín v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="e457f-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="e457f-110">Každá položka v seznamu je určena pomocí \<> blok položky.</span><span class="sxs-lookup"><span data-stu-id="e457f-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="e457f-111">Při vytváření seznamu definic budete muset zadat i `term`. `description`</span><span class="sxs-lookup"><span data-stu-id="e457f-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="e457f-112">U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="e457f-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="e457f-113">Seznam nebo tabulka může mít podle potřeby tolik \<> bloků položek.</span><span class="sxs-lookup"><span data-stu-id="e457f-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="e457f-114">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="e457f-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e457f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e457f-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e457f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e457f-116">See also</span></span>

- [<span data-ttu-id="e457f-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e457f-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e457f-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="e457f-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
