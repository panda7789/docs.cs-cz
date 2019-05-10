---
title: V aplikaci '<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591983"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="972fa-102">Nebyla nalezena žádná metoda přístupné 'Main' s odpovídajícím podpisem v "\<název >"</span><span class="sxs-lookup"><span data-stu-id="972fa-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="972fa-103">Musí mít aplikace příkazového řádku `Sub Main` definované.</span><span class="sxs-lookup"><span data-stu-id="972fa-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="972fa-104">`Main` musí být deklarována jako `Public Shared` Pokud je definován ve třídě, nebo jako `Public` Pokud definovaný v modulu.</span><span class="sxs-lookup"><span data-stu-id="972fa-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="972fa-105">**ID chyby:** BC30737</span><span class="sxs-lookup"><span data-stu-id="972fa-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="972fa-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="972fa-106">To correct this error</span></span>  
  
- <span data-ttu-id="972fa-107">Definování `Public Sub Main` postup pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="972fa-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="972fa-108">Deklarujte ho jako `Shared` pouze v případě definovat uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="972fa-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972fa-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="972fa-109">See also</span></span>

- [<span data-ttu-id="972fa-110">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="972fa-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="972fa-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="972fa-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
