---
title: "& č. 39; Dir & č. 39; funkce musí být nejdříve volána s a & č. 39; Název cesty & č. 39; argument"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="df045-102">& č. 39; Dir & č. 39; funkce musí být nejdříve volána s a & č. 39; Název cesty & č. 39; argument</span><span class="sxs-lookup"><span data-stu-id="df045-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="df045-103">Počáteční volání `Dir` funkce nezahrnuje `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="df045-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="df045-104">První volání `Dir` musí obsahovat `PathName`, ale následující volání `Dir` nemusí obsahovat parametry pro načtení další položky.</span><span class="sxs-lookup"><span data-stu-id="df045-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="df045-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="df045-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="df045-106">Zadejte `PathName` argument ve volání funkce.</span><span class="sxs-lookup"><span data-stu-id="df045-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df045-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="df045-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
