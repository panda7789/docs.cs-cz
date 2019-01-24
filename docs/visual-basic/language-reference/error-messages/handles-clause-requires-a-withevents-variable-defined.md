---
title: Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 9e018f4babd3ec6b212673494c6ae30f13c49737
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608846"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="359a4-102">Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="359a4-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="359a4-103">Jste nezadali `WithEvents` proměnné ve vaší `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="359a4-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="359a4-104">`Handles` Klíčového slova na konci deklaraci procedury způsobí, že okno zpracovávají události vyvolané proměnná deklarovaná pomocí objektu `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="359a4-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>  
  
 <span data-ttu-id="359a4-105">**ID chyby:** BC30506</span><span class="sxs-lookup"><span data-stu-id="359a4-105">**Error ID:** BC30506</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="359a4-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="359a4-106">To correct this error</span></span>  
  
-   <span data-ttu-id="359a4-107">Zadejte nezbytné `WithEvents` proměnné.</span><span class="sxs-lookup"><span data-stu-id="359a4-107">Supply the necessary `WithEvents` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359a4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="359a4-108">See also</span></span>
- [<span data-ttu-id="359a4-109">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="359a4-109">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
