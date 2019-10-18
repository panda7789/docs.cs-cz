---
title: Chráněný přítel (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524771"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="c7949-102">Chráněný přítel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7949-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="c7949-103">Kombinací klíčového slova `Protected Friend` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="c7949-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="c7949-104">Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="c7949-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="c7949-105">Můžete zadat `Protected Friend` pouze pro členy třídy; `Protected Friend` nelze použít u členů struktury, protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="c7949-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="c7949-106">V aplikaci Visual Studio vyberte nápovědu F1 v `protected friend` poskytne nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="c7949-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="c7949-107">Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.</span><span class="sxs-lookup"><span data-stu-id="c7949-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="c7949-108">Pravidly</span><span class="sxs-lookup"><span data-stu-id="c7949-108">Rules</span></span>

<span data-ttu-id="c7949-109">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="c7949-109">**Declaration Context.**</span></span> <span data-ttu-id="c7949-110">@No__t_0 lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="c7949-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="c7949-111">To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="c7949-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7949-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7949-112">See also</span></span>

- [<span data-ttu-id="c7949-113">Public</span><span class="sxs-lookup"><span data-stu-id="c7949-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="c7949-114">Protected</span><span class="sxs-lookup"><span data-stu-id="c7949-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="c7949-115">Friend</span><span class="sxs-lookup"><span data-stu-id="c7949-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="c7949-116">Private</span><span class="sxs-lookup"><span data-stu-id="c7949-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="c7949-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c7949-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="c7949-118">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7949-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c7949-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="c7949-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c7949-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="c7949-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c7949-121">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="c7949-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
