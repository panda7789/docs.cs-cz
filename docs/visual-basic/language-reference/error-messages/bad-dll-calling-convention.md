---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409878"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="be6cd-102">Chybná konvence volání knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="be6cd-102">Bad DLL calling convention</span></span>
<span data-ttu-id="be6cd-103">Argumenty předané dynamické knihovně (DLL) se musí přesně shodovat s hodnotami, které rutina očekávala.</span><span class="sxs-lookup"><span data-stu-id="be6cd-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="be6cd-104">Konvence volání se zabývat číslem, typem a pořadím argumentů.</span><span class="sxs-lookup"><span data-stu-id="be6cd-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="be6cd-105">Váš program může volat rutinu v knihovně DLL, která je předána nesprávnému typu nebo počtu argumentů.</span><span class="sxs-lookup"><span data-stu-id="be6cd-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be6cd-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="be6cd-106">To correct this error</span></span>  
  
1. <span data-ttu-id="be6cd-107">Zajistěte, aby všechny typy argumentů souhlasily s hodnotami uvedenými v deklaraci rutiny, kterou voláte.</span><span class="sxs-lookup"><span data-stu-id="be6cd-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="be6cd-108">Ujistěte se, že jste předali stejný počet argumentů, které jsou uvedeny v deklaraci rutiny, které voláte.</span><span class="sxs-lookup"><span data-stu-id="be6cd-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="be6cd-109">Pokud rutina DLL očekává argumenty podle hodnoty, ujistěte se, že `ByVal` je zadána pro tyto argumenty v deklaraci rutiny.</span><span class="sxs-lookup"><span data-stu-id="be6cd-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6cd-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="be6cd-110">See also</span></span>

- [<span data-ttu-id="be6cd-111">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="be6cd-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="be6cd-112">Call – příkaz</span><span class="sxs-lookup"><span data-stu-id="be6cd-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="be6cd-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="be6cd-113">Declare Statement</span></span>](../statements/declare-statement.md)
