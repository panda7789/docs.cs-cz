---
title: Metoda '<methodname>' má několik definic s identickými podpisy.
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 3b397711cc2fb1fd0c1dfd76899b162ab5fc1542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397230"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="4c0b0-102">Metoda '\<methodname>' má několik definic s identickými podpisy.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="4c0b0-103">`Function` `Sub` Deklarace procedury nebo používá stejný název procedury a seznam argumentů jako předchozí deklarace.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="4c0b0-104">Jednou z možných příčin je pokus o přetížení původní procedury.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="4c0b0-105">Přetížené procedury musí mít různé seznamy argumentů.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="4c0b0-106">**ID chyby:** BC30269</span><span class="sxs-lookup"><span data-stu-id="4c0b0-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c0b0-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4c0b0-107">To correct this error</span></span>  
  
- <span data-ttu-id="4c0b0-108">Změňte název procedury nebo seznam argumentů nebo odeberte duplicitní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0b0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c0b0-109">See also</span></span>

- [<span data-ttu-id="4c0b0-110">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="4c0b0-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="4c0b0-111">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="4c0b0-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
