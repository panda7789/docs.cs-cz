---
title: '&#39;Dir&#39; funkce musí být nejdříve volána s &#39;PathName&#39; argument'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585457"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="ff421-102">&#39;Dir&#39; funkce musí být nejdříve volána s &#39;PathName&#39; argument</span><span class="sxs-lookup"><span data-stu-id="ff421-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="ff421-103">Počáteční volání `Dir` funkce nezahrnuje `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="ff421-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="ff421-104">První volání `Dir` musí obsahovat `PathName`, ale následující volání `Dir` nemusí obsahovat parametry pro načtení další položky.</span><span class="sxs-lookup"><span data-stu-id="ff421-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ff421-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ff421-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="ff421-106">Zadejte `PathName` argument ve volání funkce.</span><span class="sxs-lookup"><span data-stu-id="ff421-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff421-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff421-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
