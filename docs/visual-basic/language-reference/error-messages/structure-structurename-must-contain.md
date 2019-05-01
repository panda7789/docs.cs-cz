---
title: Struktura '<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055105"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="162c7-102">Struktura '\<%{structurename/ >' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako 'Custom'</span><span class="sxs-lookup"><span data-stu-id="162c7-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="162c7-103">Definice struktury neobsahuje žádné nesdílených proměnných nebo nesdílené nevlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="162c7-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="162c7-104">Každý struktura musí mít proměnná nebo událost, která se vztahuje na každý konkrétní instanci místo (nesdílené) do všech instancí souhrnně ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="162c7-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="162c7-105">Tento požadavek nesplňují nesdílené konstanty, vlastnosti a postupy.</span><span class="sxs-lookup"><span data-stu-id="162c7-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="162c7-106">Kromě toho, pokud neexistují žádné nesdílených proměnných a jenom jedna událost nesdílené, tuto událost nemůže být `Custom` událostí.</span><span class="sxs-lookup"><span data-stu-id="162c7-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="162c7-107">**ID chyby:** BC30941</span><span class="sxs-lookup"><span data-stu-id="162c7-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="162c7-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="162c7-108">To correct this error</span></span>  
  
- <span data-ttu-id="162c7-109">Definujte alespoň jednu proměnnou nebo událostí, které nejsou `Shared`.</span><span class="sxs-lookup"><span data-stu-id="162c7-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="162c7-110">Pokud definujete jen jednu událost, musí být nevlastní, jakož i nesdílené.</span><span class="sxs-lookup"><span data-stu-id="162c7-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162c7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="162c7-111">See also</span></span>

- [<span data-ttu-id="162c7-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="162c7-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="162c7-113">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="162c7-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="162c7-114">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="162c7-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
