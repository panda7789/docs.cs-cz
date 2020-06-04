---
title: V aplikaci '<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6760b931ceb2ad5c2c04169d664da8629badc487
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409410"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="76e64-102">V aplikaci '\<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.</span><span class="sxs-lookup"><span data-stu-id="76e64-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="76e64-103">Aplikace příkazového řádku musí mít `Sub Main` definován.</span><span class="sxs-lookup"><span data-stu-id="76e64-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="76e64-104">`Main`musí být deklarován, jako by `Public Shared` byla definována ve třídě, nebo jako `Public` definice v modulu.</span><span class="sxs-lookup"><span data-stu-id="76e64-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="76e64-105">**ID chyby:** BC30737</span><span class="sxs-lookup"><span data-stu-id="76e64-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76e64-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="76e64-106">To correct this error</span></span>  
  
- <span data-ttu-id="76e64-107">Definujte `Public Sub Main` proceduru pro projekt.</span><span class="sxs-lookup"><span data-stu-id="76e64-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="76e64-108">Deklarujte ho jako `Shared` if a jenom v případě, že ho definujete uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="76e64-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e64-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="76e64-109">See also</span></span>

- [<span data-ttu-id="76e64-110">Struktura programu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76e64-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="76e64-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="76e64-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
