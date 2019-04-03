---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 510b00d2220b9c65b0e2b8fa3ead70925a9f54ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821917"
---
# <a name="example-visual-basic"></a><span data-ttu-id="e0c7d-102">\<Příklad > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0c7d-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="e0c7d-103">Příklad určuje pro člena.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0c7d-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0c7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0c7d-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e0c7d-106">Popis ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0c7d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0c7d-107">Remarks</span></span>  
 <span data-ttu-id="e0c7d-108">`<example>` Značky vám umožní určit příklad použití metody nebo jiný člen knihovny.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="e0c7d-109">To obvykle zahrnuje použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) značky.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="e0c7d-110">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0c7d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0c7d-111">Example</span></span>  
 <span data-ttu-id="e0c7d-112">V tomto příkladu `<example>` značka, které zahrnují příkladu pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="e0c7d-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e0c7d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0c7d-113">See also</span></span>

- [<span data-ttu-id="e0c7d-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e0c7d-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
