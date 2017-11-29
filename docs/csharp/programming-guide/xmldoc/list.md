---
title: "&lt;seznam&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d997f3692d21959daa8eaec9eeeac8c0a1dc9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="204fe-102">&lt;seznam&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="204fe-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="204fe-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="204fe-103">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="204fe-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="204fe-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="204fe-105">Termín, definovat, které budou určené v `description`.</span><span class="sxs-lookup"><span data-stu-id="204fe-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="204fe-106">Buď položku v odrážku nebo číslovaný seznam nebo definice `term`.</span><span class="sxs-lookup"><span data-stu-id="204fe-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="204fe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="204fe-107">Remarks</span></span>  
 <span data-ttu-id="204fe-108">\<Listheader > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu.</span><span class="sxs-lookup"><span data-stu-id="204fe-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="204fe-109">Při definování tabulku, stačí zadat položku termín v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="204fe-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="204fe-110">Každá položka v seznamu je definován s \<položky > bloku.</span><span class="sxs-lookup"><span data-stu-id="204fe-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="204fe-111">Při vytváření definice seznamu, budete muset zadat oba seznamy `term` a `description`.</span><span class="sxs-lookup"><span data-stu-id="204fe-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="204fe-112">Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="204fe-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="204fe-113">Seznam nebo tabulka může mít jako mnoho \<položky > blokuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="204fe-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="204fe-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="204fe-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="204fe-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="204fe-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="204fe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="204fe-116">See Also</span></span>  
 [<span data-ttu-id="204fe-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="204fe-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="204fe-118">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="204fe-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
