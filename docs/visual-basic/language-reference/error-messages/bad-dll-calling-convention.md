---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="b25a3-102">Chybná konvence volání knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="b25a3-102">Bad DLL calling convention</span></span>
<span data-ttu-id="b25a3-103">Argumenty předávané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává.</span><span class="sxs-lookup"><span data-stu-id="b25a3-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="b25a3-104">Konvence volání řešit počet, typ a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="b25a3-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="b25a3-105">Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="b25a3-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b25a3-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b25a3-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b25a3-107">Zajistěte, aby že všechny typy argumentů souhlas s těmi, zadaný v deklaraci rutiny, která jsou volání.</span><span class="sxs-lookup"><span data-stu-id="b25a3-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="b25a3-108">Ujistěte se, že předáváte stejný počet argumentů uvedené v deklaraci rutiny, která jsou volání.</span><span class="sxs-lookup"><span data-stu-id="b25a3-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="b25a3-109">Pokud rutina DLL očekává argumentů podle hodnoty, ujistěte se, `ByVal` je zadán pro tyto argumenty v deklaraci pro rutiny.</span><span class="sxs-lookup"><span data-stu-id="b25a3-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25a3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b25a3-110">See Also</span></span>  
 [<span data-ttu-id="b25a3-111">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="b25a3-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="b25a3-112">Call – příkaz</span><span class="sxs-lookup"><span data-stu-id="b25a3-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="b25a3-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="b25a3-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
