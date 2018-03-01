---
title: "Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic)."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="62f6f-102">Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="62f6f-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="62f6f-103">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="62f6f-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="62f6f-104">Pomocí `ReDim` Chcete-li změnit počet elementů pole pevné velikosti.</span><span class="sxs-lookup"><span data-stu-id="62f6f-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="62f6f-105">Redimensioning úroveň modulu dynamická pole, ve kterém jeden element. byl předán jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="62f6f-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="62f6f-106">Pokud není předán element pole je pevně nastavené zabránit rušení přidělení paměti pro parametr odkaz v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="62f6f-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="62f6f-107">Probíhá pokus o přiřazení hodnoty k `Variant` Proměnná obsahující pole, ale `Variant` je aktuálně uzamčena.</span><span class="sxs-lookup"><span data-stu-id="62f6f-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62f6f-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="62f6f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="62f6f-109">Zkontrolujte pole původní dynamické místo opravených deklarace její `ReDim` (Pokud pole deklarované v rámci postupu), nebo deklarováním bez určující počet elementů (je-li toto pole je deklarovaná na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="62f6f-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="62f6f-110">Určete, jestli je skutečně potřeba předat elementu, protože je viditelné v rámci všechny postupy v modulu.</span><span class="sxs-lookup"><span data-stu-id="62f6f-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="62f6f-111">Zjistit, co je uzamčení `Variant` a napravit.</span><span class="sxs-lookup"><span data-stu-id="62f6f-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f6f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="62f6f-112">See Also</span></span>  
 [<span data-ttu-id="62f6f-113">Pole</span><span class="sxs-lookup"><span data-stu-id="62f6f-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
