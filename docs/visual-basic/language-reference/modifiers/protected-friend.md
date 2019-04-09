---
title: Chráněné Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151772"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="b26ce-102">Chráněné Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b26ce-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="b26ce-103">`Protected Friend` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="b26ce-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="b26ce-104">To uděluje obě [Friend](friend.md) přístup a [chráněné](protected.md) přístup na deklarované elementy, takže jsou přístupné odkudkoli ve stejném sestavení, ze své vlastní třídy a z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="b26ce-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="b26ce-105">Můžete zadat `Protected Friend` pouze pro členy třídy; nelze použít `Protected Friend` na členy struktury protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="b26ce-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="b26ce-106">V sadě Visual Studio, že vyberete nápovědy klávesy F1 na `protected friend` poskytuje nápovědu pro buď [chráněné](protected.md) nebo [friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="b26ce-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="b26ce-107">Rozhraní IDE zvolí jeden token pod kurzor spíše než složené slovo.</span><span class="sxs-lookup"><span data-stu-id="b26ce-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="b26ce-108">pravidla</span><span class="sxs-lookup"><span data-stu-id="b26ce-108">Rules</span></span>

- **<span data-ttu-id="b26ce-109">Místní deklarace.</span><span class="sxs-lookup"><span data-stu-id="b26ce-109">Declaration Context.</span></span>** <span data-ttu-id="b26ce-110">Můžete použít `Protected Friend` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="b26ce-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="b26ce-111">To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="b26ce-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 

## <a name="see-also"></a><span data-ttu-id="b26ce-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b26ce-112">See also</span></span>

- [<span data-ttu-id="b26ce-113">Public</span><span class="sxs-lookup"><span data-stu-id="b26ce-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="b26ce-114">Chráněno</span><span class="sxs-lookup"><span data-stu-id="b26ce-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="b26ce-115">Friend</span><span class="sxs-lookup"><span data-stu-id="b26ce-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="b26ce-116">Soukromé</span><span class="sxs-lookup"><span data-stu-id="b26ce-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="b26ce-117">Privátní, chráněné</span><span class="sxs-lookup"><span data-stu-id="b26ce-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="b26ce-118">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b26ce-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b26ce-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="b26ce-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="b26ce-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="b26ce-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b26ce-121">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="b26ce-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
