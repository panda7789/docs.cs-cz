---
title: Struktura '<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 7b5bda7b1a2ae37eb509c736deae1652dc5e6ab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374015"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="d40ad-102">Struktura '\<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.</span><span class="sxs-lookup"><span data-stu-id="d40ad-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="d40ad-103">Definice struktury neobsahuje žádné nesdílené proměnné ani nesdílené nesdílené události.</span><span class="sxs-lookup"><span data-stu-id="d40ad-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="d40ad-104">Každá struktura musí mít buď proměnnou, nebo událost, která se vztahuje na jednotlivé konkrétní instance (nesdílené) místo na všechny instance souhrnně ([sdílené](../modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="d40ad-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="d40ad-105">Nesdílené konstanty, vlastnosti a procedury nesplňují tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="d40ad-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="d40ad-106">Kromě toho, pokud nejsou žádné nesdílené proměnné a jenom jedna nesdílená událost, tato událost nemůže být `Custom` událost.</span><span class="sxs-lookup"><span data-stu-id="d40ad-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="d40ad-107">**ID chyby:** BC30941</span><span class="sxs-lookup"><span data-stu-id="d40ad-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d40ad-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d40ad-108">To correct this error</span></span>  
  
- <span data-ttu-id="d40ad-109">Definujte alespoň jednu proměnnou nebo událost, která není `Shared` .</span><span class="sxs-lookup"><span data-stu-id="d40ad-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="d40ad-110">Pokud definujete jenom jednu událost, musí být nevlastní i nesdílená.</span><span class="sxs-lookup"><span data-stu-id="d40ad-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40ad-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d40ad-111">See also</span></span>

- [<span data-ttu-id="d40ad-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="d40ad-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="d40ad-113">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="d40ad-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="d40ad-114">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="d40ad-114">Structure Statement</span></span>](../statements/structure-statement.md)
