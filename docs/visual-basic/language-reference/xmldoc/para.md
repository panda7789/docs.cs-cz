---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: fa11c713a5ed5793b50865753f8bcdeaabf56e83
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270549"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="dabba-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dabba-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="dabba-103">Určuje, že obsah je formátován jako odstavce.</span><span class="sxs-lookup"><span data-stu-id="dabba-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dabba-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dabba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dabba-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="dabba-106">Text odstavce.</span><span class="sxs-lookup"><span data-stu-id="dabba-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dabba-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dabba-107">Remarks</span></span>  
 <span data-ttu-id="dabba-108">`<para>` Značka je určen pro použití uvnitř značky, například [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidání struktury textu.</span><span class="sxs-lookup"><span data-stu-id="dabba-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="dabba-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="dabba-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dabba-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dabba-110">Example</span></span>  
 <span data-ttu-id="dabba-111">V tomto příkladu `<para>` značku k rozdělení v části poznámky `UpdateRecord` metoda do dvou odstavcích.</span><span class="sxs-lookup"><span data-stu-id="dabba-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dabba-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="dabba-112">See Also</span></span>  
 [<span data-ttu-id="dabba-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="dabba-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
