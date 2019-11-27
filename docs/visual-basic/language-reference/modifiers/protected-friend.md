---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351312"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="0ea8c-102">Chráněný přítel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ea8c-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="0ea8c-103">Kombinací klíčového slova `Protected Friend` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="0ea8c-104">Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="0ea8c-105">Můžete zadat `Protected Friend` pouze pro členy třídy; `Protected Friend` nelze použít u členů struktury, protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="0ea8c-106">V aplikaci Visual Studio vyberte nápovědu F1 v `protected friend` poskytne nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="0ea8c-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="0ea8c-107">Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="0ea8c-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="0ea8c-108">Rules</span></span>

<span data-ttu-id="0ea8c-109">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="0ea8c-109">**Declaration Context.**</span></span> <span data-ttu-id="0ea8c-110">`Protected Friend` lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="0ea8c-111">To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="0ea8c-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ea8c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ea8c-112">See also</span></span>

- [<span data-ttu-id="0ea8c-113">Public</span><span class="sxs-lookup"><span data-stu-id="0ea8c-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="0ea8c-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0ea8c-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="0ea8c-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0ea8c-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="0ea8c-116">Private</span><span class="sxs-lookup"><span data-stu-id="0ea8c-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="0ea8c-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0ea8c-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="0ea8c-118">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ea8c-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0ea8c-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="0ea8c-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0ea8c-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="0ea8c-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0ea8c-121">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="0ea8c-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
