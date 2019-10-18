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
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524748"
---
# <a name="list-visual-basic"></a><span data-ttu-id="1e8a1-102">\<list > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e8a1-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="1e8a1-103">Definuje seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e8a1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1e8a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e8a1-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="1e8a1-106">Typ seznamu</span><span class="sxs-lookup"><span data-stu-id="1e8a1-106">The type of the list.</span></span> <span data-ttu-id="1e8a1-107">U seznamu s odrážkami, "Number" pro číslovaný seznam nebo "Tabulka" pro tabulku se dvěma sloupci musí být "Bullet".</span><span class="sxs-lookup"><span data-stu-id="1e8a1-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="1e8a1-108">Používá se pouze v případě, `type` je "Table".</span><span class="sxs-lookup"><span data-stu-id="1e8a1-108">Only used when `type` is "table."</span></span> <span data-ttu-id="1e8a1-109">Termín, který má definovat, který je definován ve značce Description.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="1e8a1-110">Pokud je `type` "Bullet" nebo "Number", "`description` je položka v seznamu, pokud `type` je" Table ", `description` je definice `term`.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e8a1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e8a1-111">Remarks</span></span>  
 <span data-ttu-id="1e8a1-112">Blok `<listheader>` definuje nadpis tabulky nebo seznamu definic.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="1e8a1-113">Při definování tabulky stačí zadat položku pro `term` v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="1e8a1-114">Každá položka v seznamu je určena pomocí `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="1e8a1-115">Při vytváření seznamu definic je nutné zadat jak `term`, tak `description`.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="1e8a1-116">U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="1e8a1-117">Seznam nebo tabulka může mít podle potřeby tolik `<item>` bloků.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="1e8a1-118">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-118">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e8a1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e8a1-119">Example</span></span>  
 <span data-ttu-id="1e8a1-120">Tento příklad používá značku `<list>` k definování seznamu s odrážkami v oddílu poznámky.</span><span class="sxs-lookup"><span data-stu-id="1e8a1-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1e8a1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e8a1-121">See also</span></span>

- [<span data-ttu-id="1e8a1-122">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="1e8a1-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
