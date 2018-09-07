---
title: '&lt;výjimka&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 047805ad91d87550da80448fd10883ae58647bd6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081285"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="913df-102">&lt;výjimka&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913df-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="913df-103">Určuje, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="913df-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="913df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="913df-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="913df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="913df-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="913df-106">Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="913df-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="913df-107">Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="913df-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="913df-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="913df-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="913df-109">Popis.</span><span class="sxs-lookup"><span data-stu-id="913df-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="913df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="913df-110">Remarks</span></span>  
 <span data-ttu-id="913df-111">Použití `<exception>` značku k určení, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="913df-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="913df-112">Tato značka se použije k definici metody.</span><span class="sxs-lookup"><span data-stu-id="913df-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="913df-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="913df-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="913df-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="913df-114">Example</span></span>  
 <span data-ttu-id="913df-115">Tento příklad používá `<exception>` značka, které popisují výjimku, která `IntDivide` funkce může vyvolat.</span><span class="sxs-lookup"><span data-stu-id="913df-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="913df-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="913df-116">See Also</span></span>  
 [<span data-ttu-id="913df-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="913df-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
