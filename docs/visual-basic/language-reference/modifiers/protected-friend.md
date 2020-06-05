---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404833"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="297c5-102">Chráněný přítel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="297c5-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="297c5-103">`Protected Friend`Kombinace klíčového slova je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="297c5-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="297c5-104">Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="297c5-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="297c5-105">Můžete zadat `Protected Friend` pouze členy tříd. nemůžete použít `Protected Friend` pro členy struktury, protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="297c5-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="297c5-106">V aplikaci Visual Studio vyberte nápovědu F1, která `protected friend` poskytuje nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="297c5-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="297c5-107">Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.</span><span class="sxs-lookup"><span data-stu-id="297c5-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="297c5-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="297c5-108">Rules</span></span>

<span data-ttu-id="297c5-109">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="297c5-109">**Declaration Context.**</span></span> <span data-ttu-id="297c5-110">Můžete použít `Protected Friend` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="297c5-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="297c5-111">To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="297c5-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="297c5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="297c5-112">See also</span></span>

- [<span data-ttu-id="297c5-113">Republik</span><span class="sxs-lookup"><span data-stu-id="297c5-113">Public</span></span>](public.md)
- [<span data-ttu-id="297c5-114">Proti</span><span class="sxs-lookup"><span data-stu-id="297c5-114">Protected</span></span>](protected.md)
- [<span data-ttu-id="297c5-115">Friend</span><span class="sxs-lookup"><span data-stu-id="297c5-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="297c5-116">Hlášen</span><span class="sxs-lookup"><span data-stu-id="297c5-116">Private</span></span>](private.md)
- [<span data-ttu-id="297c5-117">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="297c5-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="297c5-118">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="297c5-118">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="297c5-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="297c5-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="297c5-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="297c5-120">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="297c5-121">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="297c5-121">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
