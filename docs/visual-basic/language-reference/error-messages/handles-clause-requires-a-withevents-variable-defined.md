---
title: Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 291240bade84bcdd3d64dac24c8c91da5ff72d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816771"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="5ae0c-102">Klauzule Handles vyžaduje proměnnou WithEvents definovanou v nadřazeném typu nebo v některém z jeho základních typů.</span><span class="sxs-lookup"><span data-stu-id="5ae0c-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="5ae0c-103">Jste nezadali `WithEvents` proměnné ve vaší `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5ae0c-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="5ae0c-104">`Handles` Klíčového slova na konci deklaraci procedury způsobí, že okno zpracovávají události vyvolané proměnná deklarovaná pomocí objektu `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5ae0c-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>  
  
 <span data-ttu-id="5ae0c-105">**ID chyby:** BC30506</span><span class="sxs-lookup"><span data-stu-id="5ae0c-105">**Error ID:** BC30506</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ae0c-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5ae0c-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5ae0c-107">Zadejte nezbytné `WithEvents` proměnné.</span><span class="sxs-lookup"><span data-stu-id="5ae0c-107">Supply the necessary `WithEvents` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae0c-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ae0c-108">See also</span></span>

- [<span data-ttu-id="5ae0c-109">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="5ae0c-109">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
