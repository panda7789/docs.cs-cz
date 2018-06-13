---
title: Žádné dostupné &#39;hlavní&#39; nebyla nalezena metoda s odpovídajícím podpisem v &#39; &lt;název&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593217"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="fd7be-102">Žádné dostupné &#39;hlavní&#39; nebyla nalezena metoda s odpovídajícím podpisem v &#39; &lt;název&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="fd7be-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="fd7be-103">Aplikace příkazového řádku musí mít `Sub Main` definované.</span><span class="sxs-lookup"><span data-stu-id="fd7be-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="fd7be-104">`Main` musí být deklarována jako `Public Shared` Pokud je definována v třídě nebo jako `Public` Pokud definovaná v modulu.</span><span class="sxs-lookup"><span data-stu-id="fd7be-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="fd7be-105">**ID chyby:** BC30737</span><span class="sxs-lookup"><span data-stu-id="fd7be-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd7be-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fd7be-106">To correct this error</span></span>  
  
-   <span data-ttu-id="fd7be-107">Definování `Public Sub Main` postup pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="fd7be-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="fd7be-108">Deklarujte ji jako `Shared` jenom v případě můžete definovat uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="fd7be-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd7be-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd7be-109">See Also</span></span>  
 [<span data-ttu-id="fd7be-110">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd7be-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="fd7be-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="fd7be-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
