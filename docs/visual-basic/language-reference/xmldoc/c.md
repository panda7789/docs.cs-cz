---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523937"
---
# <a name="c-visual-basic"></a><span data-ttu-id="c3b14-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b14-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="c3b14-103">Označuje, že text v rámci popisu je kód.</span><span class="sxs-lookup"><span data-stu-id="c3b14-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3b14-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3b14-105">Parameters</span></span>  
  
|<span data-ttu-id="c3b14-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="c3b14-106">Parameter</span></span>|<span data-ttu-id="c3b14-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c3b14-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="c3b14-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="c3b14-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3b14-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3b14-109">Remarks</span></span>  
 <span data-ttu-id="c3b14-110">Značka `<c>` poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="c3b14-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="c3b14-111">Pomocí [\<code >](../../../visual-basic/language-reference/xmldoc/code.md) označit více řádků jako kód.</span><span class="sxs-lookup"><span data-stu-id="c3b14-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="c3b14-112">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c3b14-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b14-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3b14-113">Example</span></span>  
 <span data-ttu-id="c3b14-114">Tento příklad používá značku `<c>` v části Summary k označení toho, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="c3b14-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c3b14-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3b14-115">See also</span></span>

- [<span data-ttu-id="c3b14-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c3b14-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
