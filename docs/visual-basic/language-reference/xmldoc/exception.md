---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 4e2f441863d6a8677593a257cdb2cc841634d47c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820240"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="e1a73-102">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1a73-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="e1a73-103">Určuje, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="e1a73-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1a73-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1a73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1a73-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="e1a73-106">Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="e1a73-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="e1a73-107">Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e1a73-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="e1a73-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="e1a73-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e1a73-109">Popis.</span><span class="sxs-lookup"><span data-stu-id="e1a73-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1a73-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1a73-110">Remarks</span></span>  
 <span data-ttu-id="e1a73-111">Použití `<exception>` značku k určení, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="e1a73-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="e1a73-112">Tato značka se použije k definici metody.</span><span class="sxs-lookup"><span data-stu-id="e1a73-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="e1a73-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e1a73-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1a73-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1a73-114">Example</span></span>  
 <span data-ttu-id="e1a73-115">Tento příklad používá `<exception>` značka, které popisují výjimku, která `IntDivide` funkce může vyvolat.</span><span class="sxs-lookup"><span data-stu-id="e1a73-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e1a73-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1a73-116">See also</span></span>

- [<span data-ttu-id="e1a73-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e1a73-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
