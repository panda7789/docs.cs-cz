---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f0b80e2be007ff44569365f37a2331f1ecd7a216
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839402"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="c38cb-102">Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c38cb-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="c38cb-103">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="c38cb-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="c38cb-104">Pomocí `ReDim` Chcete-li změnit počet elementů pole s pevnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="c38cb-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="c38cb-105">Redimensioning úrovni modulu dynamické pole, ve kterém jeden prvek byl předán jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="c38cb-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="c38cb-106">Pokud je předán element, aby se zabránilo je uzamčen pole zrušení přidělení paměti pro referenční parametr v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c38cb-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="c38cb-107">Pokus o přiřazení hodnoty k `Variant` proměnnou obsahující pole, ale `Variant` je aktuálně uzamčen.</span><span class="sxs-lookup"><span data-stu-id="c38cb-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c38cb-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c38cb-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c38cb-109">Ujistěte se, původní pole dynamické spíše než Pevná deklarováním s `ReDim` (Pokud deklaraci pole v rámci procedury), nebo deklarací bez zadání počtu elementů (je-li deklaraci pole na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="c38cb-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="c38cb-110">Určete, jestli je skutečně potřeba předat elementu, protože je viditelné v rámci všechny postupy v modulu.</span><span class="sxs-lookup"><span data-stu-id="c38cb-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="c38cb-111">Zjistit, co je uzamčení `Variant` a napravit.</span><span class="sxs-lookup"><span data-stu-id="c38cb-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38cb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c38cb-112">See also</span></span>

- [<span data-ttu-id="c38cb-113">Pole</span><span class="sxs-lookup"><span data-stu-id="c38cb-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
