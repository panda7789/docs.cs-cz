---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306622"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="9bf1f-102">Chybná konvence volání knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="9bf1f-102">Bad DLL calling convention</span></span>
<span data-ttu-id="9bf1f-103">Argumenty předané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="9bf1f-104">Konvence volání využívání počet, typ a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="9bf1f-105">Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bf1f-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9bf1f-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9bf1f-107">Ujistěte se, že všechny typy argumentů souhlasí s argumenty zadaného v deklaraci rutiny, která se označuje jako volání.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="9bf1f-108">Ujistěte se, že předáváte stejný počet argumentů, které jsou uvedené v deklaraci rutiny, která se označuje jako volání.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="9bf1f-109">Pokud rutina DLL očekává, že argumentů podle hodnoty, ujistěte se, že `ByVal` je určená pro tyto argumenty v deklaraci pro rutiny.</span><span class="sxs-lookup"><span data-stu-id="9bf1f-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf1f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bf1f-110">See also</span></span>

- [<span data-ttu-id="9bf1f-111">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="9bf1f-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9bf1f-112">Call – příkaz</span><span class="sxs-lookup"><span data-stu-id="9bf1f-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)
- [<span data-ttu-id="9bf1f-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="9bf1f-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
