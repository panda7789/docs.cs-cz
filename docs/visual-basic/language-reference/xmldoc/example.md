---
title: '&lt;Příklad&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598547"
---
# <a name="ltexamplegt-visual-basic"></a><span data-ttu-id="bbb88-102">&lt;Příklad&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbb88-102">&lt;example&gt; (Visual Basic)</span></span>
<span data-ttu-id="bbb88-103">Určuje příklad člena.</span><span class="sxs-lookup"><span data-stu-id="bbb88-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbb88-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbb88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbb88-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="bbb88-106">Popis ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="bbb88-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbb88-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbb88-107">Remarks</span></span>  
 <span data-ttu-id="bbb88-108">`<example>` Značka umožňuje určit příklad použití metody nebo jiné knihovny člen.</span><span class="sxs-lookup"><span data-stu-id="bbb88-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="bbb88-109">To obvykle zahrnuje použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) značky.</span><span class="sxs-lookup"><span data-stu-id="bbb88-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="bbb88-110">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="bbb88-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb88-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbb88-111">Example</span></span>  
 <span data-ttu-id="bbb88-112">Tento příklad používá `<example>` značka, které zahrnují příklad pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="bbb88-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bbb88-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbb88-113">See Also</span></span>  
 [<span data-ttu-id="bbb88-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="bbb88-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
