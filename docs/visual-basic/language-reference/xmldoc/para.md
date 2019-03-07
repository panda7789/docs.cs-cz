---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cbb8e3b1e67150473159835ba2cd58d9ddf0c1c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479005"
---
# <a name="para-visual-basic"></a><span data-ttu-id="cba16-102">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cba16-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="cba16-103">Určuje, že obsah je formátován jako odstavce.</span><span class="sxs-lookup"><span data-stu-id="cba16-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cba16-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cba16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cba16-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="cba16-106">Text odstavce.</span><span class="sxs-lookup"><span data-stu-id="cba16-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cba16-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cba16-107">Remarks</span></span>  
 <span data-ttu-id="cba16-108">`<para>` Značka je určen pro použití uvnitř značky, například [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidání struktury textu.</span><span class="sxs-lookup"><span data-stu-id="cba16-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="cba16-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="cba16-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cba16-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="cba16-110">Example</span></span>  
 <span data-ttu-id="cba16-111">V tomto příkladu `<para>` značku k rozdělení v části poznámky `UpdateRecord` metoda do dvou odstavcích.</span><span class="sxs-lookup"><span data-stu-id="cba16-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cba16-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cba16-112">See also</span></span>
- [<span data-ttu-id="cba16-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="cba16-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
