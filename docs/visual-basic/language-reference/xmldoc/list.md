---
title: '&lt;seznam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603610"
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="8dc37-102">&lt;seznam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8dc37-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="8dc37-103">Definuje seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="8dc37-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dc37-104">Syntax</span></span>  
  
```xml  
<list type="type">  
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
  
#### <a name="parameters"></a><span data-ttu-id="8dc37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dc37-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="8dc37-106">Typ seznamu.</span><span class="sxs-lookup"><span data-stu-id="8dc37-106">The type of the list.</span></span> <span data-ttu-id="8dc37-107">Musí být "bullet" pro "číslo" číslovaný seznam, nebo "tabulka" pro dva sloupce tabulky, seznamu s odrážkami.</span><span class="sxs-lookup"><span data-stu-id="8dc37-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="8dc37-108">Pouze použít, když `type` je "tabulky."</span><span class="sxs-lookup"><span data-stu-id="8dc37-108">Only used when `type` is "table."</span></span> <span data-ttu-id="8dc37-109">Termín, který chcete definovat, která je definovaná ve značce popis.</span><span class="sxs-lookup"><span data-stu-id="8dc37-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="8dc37-110">Když `type` "bullet" nebo "number" `description` položka v seznamu je při `type` je "tabulku" `description` je definice `term`.</span><span class="sxs-lookup"><span data-stu-id="8dc37-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dc37-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dc37-111">Remarks</span></span>  
 <span data-ttu-id="8dc37-112">`<listheader>` Bloku definuje záhlaví tabulky nebo definice seznamu.</span><span class="sxs-lookup"><span data-stu-id="8dc37-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="8dc37-113">Při definování tabulku, stačí zadat položku pro `term` v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8dc37-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="8dc37-114">Každá položka v seznamu je definován s `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="8dc37-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="8dc37-115">Při vytváření definice seznamu, musíte zadat oba `term` a `description`.</span><span class="sxs-lookup"><span data-stu-id="8dc37-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="8dc37-116">Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="8dc37-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="8dc37-117">Seznam nebo tabulka může mít jako mnoho `<item>` blokuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8dc37-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="8dc37-118">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="8dc37-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dc37-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dc37-119">Example</span></span>  
 <span data-ttu-id="8dc37-120">Tento příklad používá `<list>` značky k definování seznamu s odrážkami v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="8dc37-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8dc37-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dc37-121">See Also</span></span>  
 [<span data-ttu-id="8dc37-122">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8dc37-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
