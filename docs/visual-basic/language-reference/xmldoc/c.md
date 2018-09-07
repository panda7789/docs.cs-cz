---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854727"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="93835-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93835-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="93835-103">Označuje, že je text v rámci popis kódu.</span><span class="sxs-lookup"><span data-stu-id="93835-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93835-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93835-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93835-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93835-105">Parameters</span></span>  
  
|<span data-ttu-id="93835-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="93835-106">Parameter</span></span>|<span data-ttu-id="93835-107">Popis</span><span class="sxs-lookup"><span data-stu-id="93835-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="93835-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="93835-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93835-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93835-109">Remarks</span></span>  
 <span data-ttu-id="93835-110">`<c>` Značky poskytuje způsob, jak určit, že text v popisu musí být označené jako kód.</span><span class="sxs-lookup"><span data-stu-id="93835-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="93835-111">Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="93835-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="93835-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="93835-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93835-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="93835-113">Example</span></span>  
 <span data-ttu-id="93835-114">V tomto příkladu `<c>` značky v souhrnné části, která označuje, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="93835-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="93835-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="93835-115">See Also</span></span>  
 [<span data-ttu-id="93835-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="93835-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
