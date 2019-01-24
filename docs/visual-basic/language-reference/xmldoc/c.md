---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 0e3ed08a62e9a52efa231c573a8061ff92d3cee0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604154"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="e8e3e-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e3e-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="e8e3e-103">Označuje, že je text v rámci popis kódu.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8e3e-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8e3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8e3e-105">Parameters</span></span>  
  
|<span data-ttu-id="e8e3e-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="e8e3e-106">Parameter</span></span>|<span data-ttu-id="e8e3e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e8e3e-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="e8e3e-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8e3e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8e3e-109">Remarks</span></span>  
 <span data-ttu-id="e8e3e-110">`<c>` Značky poskytuje způsob, jak určit, že text v popisu musí být označené jako kód.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="e8e3e-111">Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="e8e3e-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8e3e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8e3e-113">Example</span></span>  
 <span data-ttu-id="e8e3e-114">V tomto příkladu `<c>` značky v souhrnné části, která označuje, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="e8e3e-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e8e3e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8e3e-115">See also</span></span>
- [<span data-ttu-id="e8e3e-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e8e3e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
