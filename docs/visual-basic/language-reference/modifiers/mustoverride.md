---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396191"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="b47b0-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b47b0-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="b47b0-103">Určuje, že vlastnost nebo procedura není v této třídě implementována a musí být přepsána v odvozené třídě předtím, než je možné ji použít.</span><span class="sxs-lookup"><span data-stu-id="b47b0-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b47b0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b47b0-104">Remarks</span></span>  
 <span data-ttu-id="b47b0-105">Můžete použít `MustOverride` pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="b47b0-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="b47b0-106">Vlastnost nebo procedura, která určuje, `MustOverride` musí být členem třídy a třída musí být označena jako [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="b47b0-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b47b0-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="b47b0-107">Rules</span></span>  
  
- <span data-ttu-id="b47b0-108">**Neúplná deklarace**</span><span class="sxs-lookup"><span data-stu-id="b47b0-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="b47b0-109">Pokud zadáte `MustOverride` , nezadáte žádné další řádky kódu pro vlastnost nebo proceduru, nikoli `End Function` `End Property` příkaz, nebo `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="b47b0-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="b47b0-110">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="b47b0-110">**Combined Modifiers.**</span></span> <span data-ttu-id="b47b0-111">Nelze zadat `MustOverride` společně s `NotOverridable` , `Overridable` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="b47b0-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="b47b0-112">**Nastínování a přepisování.**</span><span class="sxs-lookup"><span data-stu-id="b47b0-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="b47b0-113">Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="b47b0-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="b47b0-114">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="b47b0-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="b47b0-115">**Alternativní výrazy.**</span><span class="sxs-lookup"><span data-stu-id="b47b0-115">**Alternate Terms.**</span></span> <span data-ttu-id="b47b0-116">Element, který nelze použít s výjimkou v přepsání, se někdy označuje jako *čistě virtuální* prvek.</span><span class="sxs-lookup"><span data-stu-id="b47b0-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="b47b0-117">`MustOverride`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="b47b0-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b47b0-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="b47b0-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="b47b0-119">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="b47b0-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="b47b0-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="b47b0-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b47b0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b47b0-121">See also</span></span>

- [<span data-ttu-id="b47b0-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b47b0-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="b47b0-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="b47b0-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="b47b0-124">Přepsání</span><span class="sxs-lookup"><span data-stu-id="b47b0-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="b47b0-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="b47b0-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="b47b0-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b47b0-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="b47b0-127">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b47b0-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
