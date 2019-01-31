---
title: Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282583"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="c7046-102">Funkce 'Dir' musí být nejdříve volána s argumentem 'PathName'.</span><span class="sxs-lookup"><span data-stu-id="c7046-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="c7046-103">Počáteční volání `Dir` funkce nezahrnuje `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="c7046-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="c7046-104">První volání `Dir` musí obsahovat `PathName`, ale následné volání `Dir` není potřeba zahrnovat parametry se mají načíst další položky.</span><span class="sxs-lookup"><span data-stu-id="c7046-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7046-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c7046-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c7046-106">Zadat `PathName` argument ve volání funkce.</span><span class="sxs-lookup"><span data-stu-id="c7046-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7046-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7046-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
