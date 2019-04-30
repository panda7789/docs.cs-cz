---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938590"
---
# <a name="c-visual-basic"></a><span data-ttu-id="81d19-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81d19-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="81d19-103">Označuje, že je text v rámci popis kódu.</span><span class="sxs-lookup"><span data-stu-id="81d19-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81d19-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81d19-105">Parameters</span></span>  
  
|<span data-ttu-id="81d19-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="81d19-106">Parameter</span></span>|<span data-ttu-id="81d19-107">Popis</span><span class="sxs-lookup"><span data-stu-id="81d19-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="81d19-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="81d19-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d19-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81d19-109">Remarks</span></span>  
 <span data-ttu-id="81d19-110">`<c>` Značky poskytuje způsob, jak určit, že text v popisu musí být označené jako kód.</span><span class="sxs-lookup"><span data-stu-id="81d19-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="81d19-111">Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="81d19-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="81d19-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="81d19-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d19-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="81d19-113">Example</span></span>  
 <span data-ttu-id="81d19-114">V tomto příkladu `<c>` značky v souhrnné části, která označuje, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="81d19-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="81d19-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81d19-115">See also</span></span>

- [<span data-ttu-id="81d19-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="81d19-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
