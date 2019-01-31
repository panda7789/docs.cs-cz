---
title: <list> (Visual Basic)
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
ms.openlocfilehash: 522450e4efcecaf74968ddb492b536aa98dc0b13
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260285"
---
# <a name="list-visual-basic"></a><span data-ttu-id="50447-102">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50447-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="50447-103">Definuje seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="50447-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50447-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50447-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="50447-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50447-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="50447-106">Typ seznamu.</span><span class="sxs-lookup"><span data-stu-id="50447-106">The type of the list.</span></span> <span data-ttu-id="50447-107">Pro seznam s odrážkami, "number" číslovaný seznam nebo "table" pro dva sloupce tabulky musí být "bullet".</span><span class="sxs-lookup"><span data-stu-id="50447-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="50447-108">Použije se pouze při `type` je "table".</span><span class="sxs-lookup"><span data-stu-id="50447-108">Only used when `type` is "table."</span></span> <span data-ttu-id="50447-109">Termín, který chcete definovat, která je definována v popisu značky.</span><span class="sxs-lookup"><span data-stu-id="50447-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="50447-110">Když `type` "bullet" nebo "number" `description` je položka v seznamu při `type` je "table" `description` je definice `term`.</span><span class="sxs-lookup"><span data-stu-id="50447-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50447-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50447-111">Remarks</span></span>  
 <span data-ttu-id="50447-112">`<listheader>` Bloku definuje záhlaví tabulky nebo definice seznamu.</span><span class="sxs-lookup"><span data-stu-id="50447-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="50447-113">Při definování tabulku, stačí jenom zadat položku pro `term` v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="50447-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="50447-114">Každá položka v seznamu není zadán s `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="50447-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="50447-115">Při vytváření definice seznamu, musíte zadat oba `term` a `description`.</span><span class="sxs-lookup"><span data-stu-id="50447-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="50447-116">Ale pro tabulku, seznam s odrážkami nebo číslovaného seznamu, stačí jenom zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="50447-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="50447-117">Seznam nebo tabulku můžete mít kolik `<item>` blokuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="50447-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="50447-118">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="50447-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50447-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="50447-119">Example</span></span>  
 <span data-ttu-id="50447-120">V tomto příkladu `<list>` značka, které definují seznam s odrážkami v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="50447-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50447-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50447-121">See also</span></span>
- [<span data-ttu-id="50447-122">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="50447-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
