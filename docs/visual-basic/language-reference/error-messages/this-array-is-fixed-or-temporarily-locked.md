---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c7b5372b6046e25aad87131ba141cb71c580e12c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625946"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="cb3f9-102">Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="cb3f9-103">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="cb3f9-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="cb3f9-104">Pomocí `ReDim` Chcete-li změnit počet elementů pole s pevnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="cb3f9-105">Redimensioning úrovni modulu dynamické pole, ve kterém jeden prvek byl předán jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="cb3f9-106">Pokud je předán element, aby se zabránilo je uzamčen pole zrušení přidělení paměti pro referenční parametr v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="cb3f9-107">Pokus o přiřazení hodnoty k `Variant` proměnnou obsahující pole, ale `Variant` je aktuálně uzamčen.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb3f9-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cb3f9-108">To correct this error</span></span>  
  
1. <span data-ttu-id="cb3f9-109">Ujistěte se, původní pole dynamické spíše než Pevná deklarováním s `ReDim` (Pokud deklaraci pole v rámci procedury), nebo deklarací bez zadání počtu elementů (je-li deklaraci pole na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="cb3f9-110">Určete, jestli je skutečně potřeba předat elementu, protože je viditelné v rámci všechny postupy v modulu.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="cb3f9-111">Zjistit, co je uzamčení `Variant` a napravit.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3f9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb3f9-112">See also</span></span>

- [<span data-ttu-id="cb3f9-113">Pole</span><span class="sxs-lookup"><span data-stu-id="cb3f9-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
