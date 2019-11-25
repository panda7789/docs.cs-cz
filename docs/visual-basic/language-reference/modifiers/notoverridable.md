---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351448"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="8c630-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c630-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="8c630-103">Specifies that a property or procedure cannot be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="8c630-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c630-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c630-104">Remarks</span></span>  
 <span data-ttu-id="8c630-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="8c630-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="8c630-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="8c630-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="8c630-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8c630-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="8c630-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span><span class="sxs-lookup"><span data-stu-id="8c630-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="8c630-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="8c630-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="8c630-110">An element that cannot be overridden is sometimes called a *sealed* element.</span><span class="sxs-lookup"><span data-stu-id="8c630-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="8c630-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="8c630-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="8c630-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8c630-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="8c630-113">Combined Modifiers</span><span class="sxs-lookup"><span data-stu-id="8c630-113">Combined Modifiers</span></span>  
 <span data-ttu-id="8c630-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span><span class="sxs-lookup"><span data-stu-id="8c630-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="8c630-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="8c630-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="8c630-116">Použití</span><span class="sxs-lookup"><span data-stu-id="8c630-116">Usage</span></span>  
 <span data-ttu-id="8c630-117">The `NotOverridable` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="8c630-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8c630-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="8c630-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8c630-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="8c630-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8c630-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="8c630-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c630-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c630-121">See also</span></span>

- [<span data-ttu-id="8c630-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8c630-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="8c630-123">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8c630-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="8c630-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8c630-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="8c630-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="8c630-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="8c630-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="8c630-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="8c630-127">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8c630-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8c630-128">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c630-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
