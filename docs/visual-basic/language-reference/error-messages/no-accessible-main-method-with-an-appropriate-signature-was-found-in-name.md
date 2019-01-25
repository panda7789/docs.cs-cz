---
title: Žádná dostupná &#39;hlavní&#39; v nebyla nalezena metoda s odpovídajícím podpisem &#39; &lt;název&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 3398195ef9d503e47ab569ff85cb2a827c4270f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501487"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="25d3b-102">Žádná dostupná &#39;hlavní&#39; v nebyla nalezena metoda s odpovídajícím podpisem &#39; &lt;název&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="25d3b-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="25d3b-103">Musí mít aplikace příkazového řádku `Sub Main` definované.</span><span class="sxs-lookup"><span data-stu-id="25d3b-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="25d3b-104">`Main` musí být deklarována jako `Public Shared` Pokud je definován ve třídě, nebo jako `Public` Pokud definovaný v modulu.</span><span class="sxs-lookup"><span data-stu-id="25d3b-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="25d3b-105">**ID chyby:** BC30737</span><span class="sxs-lookup"><span data-stu-id="25d3b-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25d3b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="25d3b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="25d3b-107">Definování `Public Sub Main` postup pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="25d3b-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="25d3b-108">Deklarujte ho jako `Shared` pouze v případě definovat uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="25d3b-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d3b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25d3b-109">See also</span></span>
- [<span data-ttu-id="25d3b-110">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25d3b-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="25d3b-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="25d3b-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
