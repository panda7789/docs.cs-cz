---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400121"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="af91a-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af91a-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="af91a-102">Určuje, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="af91a-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af91a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af91a-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="af91a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="af91a-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="af91a-105">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="af91a-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="af91a-106">Kompilátor kontroluje, zda daná výjimka existuje, a překládá se na `member` kanonický název elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="af91a-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="af91a-107">`member`v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="af91a-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="af91a-108">Popis.</span><span class="sxs-lookup"><span data-stu-id="af91a-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af91a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af91a-109">Remarks</span></span>  
 <span data-ttu-id="af91a-110">Použijte `<exception>` značku k určení, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="af91a-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="af91a-111">Tato značka se aplikuje na definici metody.</span><span class="sxs-lookup"><span data-stu-id="af91a-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="af91a-112">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="af91a-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af91a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="af91a-113">Example</span></span>  
 <span data-ttu-id="af91a-114">Tento příklad používá `<exception>` značku k popisu výjimky, kterou `IntDivide` může funkce vyvolat.</span><span class="sxs-lookup"><span data-stu-id="af91a-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="af91a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="af91a-115">See also</span></span>

- [<span data-ttu-id="af91a-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="af91a-116">XML Comment Tags</span></span>](index.md)
