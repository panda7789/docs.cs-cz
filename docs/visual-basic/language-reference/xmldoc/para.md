---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: fa11c713a5ed5793b50865753f8bcdeaabf56e83
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515012"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="6f4dd-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f4dd-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="6f4dd-103">Určuje, že obsah je formátován jako odstavce.</span><span class="sxs-lookup"><span data-stu-id="6f4dd-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f4dd-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f4dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f4dd-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="6f4dd-106">Text odstavce.</span><span class="sxs-lookup"><span data-stu-id="6f4dd-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f4dd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f4dd-107">Remarks</span></span>  
 <span data-ttu-id="6f4dd-108">`<para>` Značka je určen pro použití uvnitř značky, například [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidání struktury textu.</span><span class="sxs-lookup"><span data-stu-id="6f4dd-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="6f4dd-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="6f4dd-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4dd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f4dd-110">Example</span></span>  
 <span data-ttu-id="6f4dd-111">V tomto příkladu `<para>` značku k rozdělení v části poznámky `UpdateRecord` metoda do dvou odstavcích.</span><span class="sxs-lookup"><span data-stu-id="6f4dd-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6f4dd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f4dd-112">See Also</span></span>  
 [<span data-ttu-id="6f4dd-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6f4dd-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
