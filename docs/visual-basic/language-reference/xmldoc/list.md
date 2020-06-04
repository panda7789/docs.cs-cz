---
title: <list>
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
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400083"
---
# <a name="list-visual-basic"></a><span data-ttu-id="3fb87-101">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fb87-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="3fb87-102">Definuje seznam nebo tabulku.</span><span class="sxs-lookup"><span data-stu-id="3fb87-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb87-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb87-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3fb87-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fb87-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="3fb87-105">Typ seznamu</span><span class="sxs-lookup"><span data-stu-id="3fb87-105">The type of the list.</span></span> <span data-ttu-id="3fb87-106">U seznamu s odrážkami, "Number" pro číslovaný seznam nebo "Tabulka" pro tabulku se dvěma sloupci musí být "Bullet".</span><span class="sxs-lookup"><span data-stu-id="3fb87-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="3fb87-107">Používá se pouze v případě `type` , že je "Table".</span><span class="sxs-lookup"><span data-stu-id="3fb87-107">Only used when `type` is "table."</span></span> <span data-ttu-id="3fb87-108">Termín, který má definovat, který je definován ve značce Description.</span><span class="sxs-lookup"><span data-stu-id="3fb87-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="3fb87-109">Pokud je `type` "Bullet" nebo "Number", `description` je položka v seznamu, pokud `type` je "Table", `description` je definicí `term` .</span><span class="sxs-lookup"><span data-stu-id="3fb87-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb87-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fb87-110">Remarks</span></span>  
 <span data-ttu-id="3fb87-111">`<listheader>`Blok definuje nadpis buď tabulky, nebo seznamu definic.</span><span class="sxs-lookup"><span data-stu-id="3fb87-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="3fb87-112">Při definování tabulky stačí zadat položku pro `term` v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="3fb87-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="3fb87-113">Každá položka v seznamu je určena `<item>` blokem.</span><span class="sxs-lookup"><span data-stu-id="3fb87-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="3fb87-114">Při vytváření seznamu definic je nutné zadat i `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="3fb87-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="3fb87-115">U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description` .</span><span class="sxs-lookup"><span data-stu-id="3fb87-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3fb87-116">Seznam nebo tabulka může mít tolik `<item>` bloků, kolik potřebujete.</span><span class="sxs-lookup"><span data-stu-id="3fb87-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="3fb87-117">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="3fb87-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fb87-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fb87-118">Example</span></span>  
 <span data-ttu-id="3fb87-119">Tento příklad používá `<list>` značku k definování seznamu s odrážkami v oddílu poznámky.</span><span class="sxs-lookup"><span data-stu-id="3fb87-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3fb87-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb87-120">See also</span></span>

- [<span data-ttu-id="3fb87-121">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="3fb87-121">XML Comment Tags</span></span>](index.md)
