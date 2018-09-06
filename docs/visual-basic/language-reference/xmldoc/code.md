---
title: '&lt;kód&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: e66aebe35dd8f6443fefe3b07842b37270159e6e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858636"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="f5e1c-102">&lt;kód&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5e1c-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="f5e1c-103">Označuje, že text je více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5e1c-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5e1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5e1c-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="f5e1c-106">Text k označení jako kódu.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e1c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5e1c-107">Remarks</span></span>  
 <span data-ttu-id="f5e1c-108">Použití `<code>` značky k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="f5e1c-109">Použití [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) k označení, že text v popisu musí být označené jako kód.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="f5e1c-110">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e1c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5e1c-111">Example</span></span>  
 <span data-ttu-id="f5e1c-112">V tomto příkladu \<kód > značka, které zahrnují ukázkový kód pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="f5e1c-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5e1c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5e1c-113">See Also</span></span>  
 [<span data-ttu-id="f5e1c-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="f5e1c-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
