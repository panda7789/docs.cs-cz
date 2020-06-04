---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400160"
---
# <a name="c-visual-basic"></a><span data-ttu-id="8a495-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a495-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="8a495-102">Označuje, že text v rámci popisu je kód.</span><span class="sxs-lookup"><span data-stu-id="8a495-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a495-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a495-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a495-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a495-104">Parameters</span></span>  
  
|<span data-ttu-id="8a495-105">Parametr</span><span class="sxs-lookup"><span data-stu-id="8a495-105">Parameter</span></span>|<span data-ttu-id="8a495-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8a495-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="8a495-107">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="8a495-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a495-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a495-108">Remarks</span></span>  
 <span data-ttu-id="8a495-109">`<c>`Značka poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="8a495-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="8a495-110">Slouží [\<code>](code.md) k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="8a495-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="8a495-111">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="8a495-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a495-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a495-112">Example</span></span>  
 <span data-ttu-id="8a495-113">Tento příklad používá `<c>` značku v části Summary k označení, že `Counter` se jedná o kód.</span><span class="sxs-lookup"><span data-stu-id="8a495-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8a495-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a495-114">See also</span></span>

- [<span data-ttu-id="8a495-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8a495-115">XML Comment Tags</span></span>](index.md)
