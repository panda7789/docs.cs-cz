---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cb80f4b39bee128790b311732adf1202dbbc6993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601722"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="a8d91-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8d91-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="a8d91-103">Určuje, že obsah je formátován jako odstavec.</span><span class="sxs-lookup"><span data-stu-id="a8d91-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8d91-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8d91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8d91-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="a8d91-106">Text odstavce.</span><span class="sxs-lookup"><span data-stu-id="a8d91-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8d91-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8d91-107">Remarks</span></span>  
 <span data-ttu-id="a8d91-108">`<para>` Značka je pro použití uvnitř značky, jako například [ \<souhrnné >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidat struktura na text.</span><span class="sxs-lookup"><span data-stu-id="a8d91-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="a8d91-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="a8d91-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d91-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8d91-110">Example</span></span>  
 <span data-ttu-id="a8d91-111">Tento příklad používá `<para>` značka oddílu poznámky pro rozdělení `UpdateRecord` metoda do dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="a8d91-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a8d91-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8d91-112">See Also</span></span>  
 [<span data-ttu-id="a8d91-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a8d91-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
