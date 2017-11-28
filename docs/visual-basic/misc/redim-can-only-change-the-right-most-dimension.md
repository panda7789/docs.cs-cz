---
title: "& č. 39; ReDim & č. 39; lze změnit pouze dimenze nejvíce vpravo"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="b36fb-102">& č. 39; ReDim & č. 39; lze změnit pouze dimenze nejvíce vpravo</span><span class="sxs-lookup"><span data-stu-id="b36fb-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="b36fb-103">A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, které není poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="b36fb-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="b36fb-104">Při použití `Preserve`, můžete změnit velikost pouze poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="b36fb-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="b36fb-105">Pro všechny další dimenze musíte zadat stejnou velikost jako existující pole.</span><span class="sxs-lookup"><span data-stu-id="b36fb-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b36fb-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b36fb-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b36fb-107">Odeberte `Preserve` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b36fb-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36fb-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b36fb-108">See Also</span></span>  
 [<span data-ttu-id="b36fb-109">Pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b36fb-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="b36fb-110">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b36fb-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="b36fb-111">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="b36fb-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="b36fb-112">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="b36fb-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="b36fb-113">Zachovat – odstranit</span><span class="sxs-lookup"><span data-stu-id="b36fb-113">Preserve - delete</span></span>](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
