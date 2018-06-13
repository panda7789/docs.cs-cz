---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 556c00fa761a1bce5e922a304706c78893550901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599603"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="f54e0-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f54e0-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="f54e0-103">Označuje, že je text v rámci popis kódu.</span><span class="sxs-lookup"><span data-stu-id="f54e0-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f54e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f54e0-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f54e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f54e0-105">Parameters</span></span>  
  
|<span data-ttu-id="f54e0-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="f54e0-106">Parameter</span></span>|<span data-ttu-id="f54e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f54e0-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="f54e0-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="f54e0-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f54e0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f54e0-109">Remarks</span></span>  
 <span data-ttu-id="f54e0-110">`<c>` Značky poskytuje způsob, jak znamenat, že text v rámci popis by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="f54e0-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="f54e0-111">Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="f54e0-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="f54e0-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="f54e0-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f54e0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f54e0-113">Example</span></span>  
 <span data-ttu-id="f54e0-114">Tento příklad používá `<c>` značky v části Souhrn k označení, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="f54e0-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f54e0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f54e0-115">See Also</span></span>  
 [<span data-ttu-id="f54e0-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="f54e0-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
