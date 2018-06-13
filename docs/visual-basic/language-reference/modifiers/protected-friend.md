---
title: Chráněné Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306554"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="4d1a0-102">Chráněné Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d1a0-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="4d1a0-103">`Protected Friend` – Kombinace klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="4d1a0-104">Se uděluje obě [Friend](friend.md) přístup a [chráněné](protected.md) přístup na deklarované elementy, které jsou přístupné z libovolné místo ve stejném sestavení, ze své vlastní třídy a z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="4d1a0-105">Můžete zadat `Protected Friend` pouze u členů tříd; nelze použít `Protected Friend` u členů struktury protože struktury nemůže být zděděno.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="4d1a0-106">V sadě Visual Studio, výběr F1 – Nápověda na `protected friend` poskytuje nápovědu pro buď [chráněné](protected.md) nebo [friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="4d1a0-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="4d1a0-107">Prostředí IDE vybere jeden token pod kurzor spíše než složené aplikace word.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="4d1a0-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="4d1a0-108">Rules</span></span>

- <span data-ttu-id="4d1a0-109">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="4d1a0-109">**Declaration Context.**</span></span> <span data-ttu-id="4d1a0-110">Můžete použít `Protected Friend` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="4d1a0-111">To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.</span><span class="sxs-lookup"><span data-stu-id="4d1a0-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="4d1a0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d1a0-112">See Also</span></span>

[<span data-ttu-id="4d1a0-113">Public</span><span class="sxs-lookup"><span data-stu-id="4d1a0-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="4d1a0-114">Protected</span><span class="sxs-lookup"><span data-stu-id="4d1a0-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="4d1a0-115">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="4d1a0-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="4d1a0-116">Private</span><span class="sxs-lookup"><span data-stu-id="4d1a0-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="4d1a0-117">[Privátní chráněný](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="4d1a0-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="4d1a0-118">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d1a0-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="4d1a0-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d1a0-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="4d1a0-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="4d1a0-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="4d1a0-121">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4d1a0-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
