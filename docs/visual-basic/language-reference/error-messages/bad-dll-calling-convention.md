---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583835"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="51aee-102">Chybná konvence volání knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="51aee-102">Bad DLL calling convention</span></span>
<span data-ttu-id="51aee-103">Argumenty předávané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává.</span><span class="sxs-lookup"><span data-stu-id="51aee-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="51aee-104">Konvence volání řešit počet, typ a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="51aee-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="51aee-105">Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="51aee-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51aee-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="51aee-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="51aee-107">Zajistěte, aby že všechny typy argumentů souhlas s těmi, zadaný v deklaraci rutiny, která jsou volání.</span><span class="sxs-lookup"><span data-stu-id="51aee-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="51aee-108">Ujistěte se, že předáváte stejný počet argumentů uvedené v deklaraci rutiny, která jsou volání.</span><span class="sxs-lookup"><span data-stu-id="51aee-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="51aee-109">Pokud rutina DLL očekává argumentů podle hodnoty, ujistěte se, `ByVal` je zadán pro tyto argumenty v deklaraci pro rutiny.</span><span class="sxs-lookup"><span data-stu-id="51aee-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51aee-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="51aee-110">See Also</span></span>  
 [<span data-ttu-id="51aee-111">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="51aee-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="51aee-112">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="51aee-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="51aee-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="51aee-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
