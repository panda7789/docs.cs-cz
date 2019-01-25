---
title: Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako &#39;vlastní&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: d8c654c212a459d40c6cf20cd62c3e0fcda8511b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603778"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="ee287-102">Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako &#39;vlastní&#39;</span><span class="sxs-lookup"><span data-stu-id="ee287-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="ee287-103">Definice struktury neobsahuje žádné nesdílených proměnných nebo nesdílené nevlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="ee287-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="ee287-104">Každý struktura musí mít proměnná nebo událost, která se vztahuje na každý konkrétní instanci místo (nesdílené) do všech instancí souhrnně ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="ee287-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="ee287-105">Tento požadavek nesplňují nesdílené konstanty, vlastnosti a postupy.</span><span class="sxs-lookup"><span data-stu-id="ee287-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="ee287-106">Kromě toho, pokud neexistují žádné nesdílených proměnných a jenom jedna událost nesdílené, tuto událost nemůže být `Custom` událostí.</span><span class="sxs-lookup"><span data-stu-id="ee287-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="ee287-107">**ID chyby:** BC30941</span><span class="sxs-lookup"><span data-stu-id="ee287-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ee287-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ee287-108">To correct this error</span></span>  
  
-   <span data-ttu-id="ee287-109">Definujte alespoň jednu proměnnou nebo událostí, které nejsou `Shared`.</span><span class="sxs-lookup"><span data-stu-id="ee287-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="ee287-110">Pokud definujete jen jednu událost, musí být nevlastní, jakož i nesdílené.</span><span class="sxs-lookup"><span data-stu-id="ee287-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee287-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee287-111">See also</span></span>
- [<span data-ttu-id="ee287-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="ee287-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ee287-113">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="ee287-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ee287-114">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="ee287-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
