---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351390"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="652e1-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="652e1-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="652e1-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span><span class="sxs-lookup"><span data-stu-id="652e1-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="652e1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="652e1-104">Remarks</span></span>  
 <span data-ttu-id="652e1-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="652e1-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="652e1-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="652e1-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="652e1-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="652e1-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="652e1-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span><span class="sxs-lookup"><span data-stu-id="652e1-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="652e1-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="652e1-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="652e1-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="652e1-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="652e1-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="652e1-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="652e1-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span><span class="sxs-lookup"><span data-stu-id="652e1-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="652e1-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span><span class="sxs-lookup"><span data-stu-id="652e1-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="652e1-114">You can use `Overridable` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="652e1-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="652e1-115">Combined Modifiers</span><span class="sxs-lookup"><span data-stu-id="652e1-115">Combined Modifiers</span></span>  
 <span data-ttu-id="652e1-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span><span class="sxs-lookup"><span data-stu-id="652e1-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="652e1-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="652e1-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="652e1-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="652e1-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="652e1-119">Použití</span><span class="sxs-lookup"><span data-stu-id="652e1-119">Usage</span></span>  
 <span data-ttu-id="652e1-120">The `Overridable` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="652e1-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="652e1-121">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="652e1-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="652e1-122">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="652e1-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="652e1-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="652e1-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="652e1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="652e1-124">See also</span></span>

- [<span data-ttu-id="652e1-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="652e1-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="652e1-126">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="652e1-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="652e1-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="652e1-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="652e1-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="652e1-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="652e1-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="652e1-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="652e1-130">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="652e1-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="652e1-131">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="652e1-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
