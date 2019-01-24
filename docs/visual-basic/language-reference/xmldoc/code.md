---
title: '&lt;kód&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566304"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="e4a8b-102">&lt;kód&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4a8b-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="e4a8b-103">Označuje, že text je více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a8b-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4a8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4a8b-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e4a8b-106">Text k označení jako kódu.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4a8b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4a8b-107">Remarks</span></span>  
 <span data-ttu-id="e4a8b-108">Použití `<code>` značky k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="e4a8b-109">Použití [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) k označení, že text v popisu musí být označené jako kód.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="e4a8b-110">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4a8b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a8b-111">Example</span></span>  
 <span data-ttu-id="e4a8b-112">V tomto příkladu \<kód > značka, které zahrnují ukázkový kód pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e4a8b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4a8b-113">See also</span></span>
- [<span data-ttu-id="e4a8b-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e4a8b-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
