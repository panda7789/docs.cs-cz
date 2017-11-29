---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2f7bdba4b01bd307e0c52802509669f772b5eb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="ed5ef-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed5ef-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="ed5ef-103">Určuje, že vlastnost nebo postup není implementována v této třídě a musí být přepsána nastaveními v odvozené třídě před použitím.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed5ef-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed5ef-104">Remarks</span></span>  
 <span data-ttu-id="ed5ef-105">Můžete použít `MustOverride` jenom v příkazu deklarace vlastnosti nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="ed5ef-106">Vlastnost nebo procedury, která určuje `MustOverride` musí být členem třídy, a musí být označen třída [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="ed5ef-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ed5ef-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="ed5ef-107">Rules</span></span>  
  
-   <span data-ttu-id="ed5ef-108">**Nedokončené deklarace.**</span><span class="sxs-lookup"><span data-stu-id="ed5ef-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="ed5ef-109">Pokud zadáte `MustOverride`, nezadáte není žádné další řádky kódu pro vlastnost nebo postupu, i na `End Function`, `End Property`, nebo `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="ed5ef-110">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="ed5ef-110">**Combined Modifiers.**</span></span> <span data-ttu-id="ed5ef-111">Nelze zadat `MustOverride` společně s `NotOverridable`, `Overridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="ed5ef-112">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="ed5ef-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="ed5ef-113">Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="ed5ef-114">Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="ed5ef-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="ed5ef-115">**Alternativní podmínky.**</span><span class="sxs-lookup"><span data-stu-id="ed5ef-115">**Alternate Terms.**</span></span> <span data-ttu-id="ed5ef-116">Element, který nelze použít s výjimkou v přepsání se někdy nazývá *čistý virtuální* elementu.</span><span class="sxs-lookup"><span data-stu-id="ed5ef-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="ed5ef-117">`MustOverride` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="ed5ef-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ed5ef-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="ed5ef-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ed5ef-119">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="ed5ef-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ed5ef-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="ed5ef-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed5ef-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed5ef-121">See Also</span></span>  
 [<span data-ttu-id="ed5ef-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ed5ef-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="ed5ef-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="ed5ef-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="ed5ef-124">Přepsání</span><span class="sxs-lookup"><span data-stu-id="ed5ef-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="ed5ef-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="ed5ef-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="ed5ef-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ed5ef-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="ed5ef-127">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed5ef-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
