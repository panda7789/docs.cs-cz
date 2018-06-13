---
title: NotOverridable (Visual Basic)
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
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600750"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="c4b57-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4b57-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="c4b57-103">Určuje, že vlastnost nebo procedury nelze přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="c4b57-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b57-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4b57-104">Remarks</span></span>  
 <span data-ttu-id="c4b57-105">`NotOverridable` Modifikátor brání vlastnosti nebo metody přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="c4b57-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="c4b57-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="c4b57-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="c4b57-107">Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c4b57-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="c4b57-108">Pokud `Overridable` nebo `NotOverridable` modifikátor nezadáte, výchozí nastavení závisí na tom, jestli jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="c4b57-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="c4b57-109">Pokud jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody, výchozí nastavení je `Overridable`, jinak je `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="c4b57-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="c4b57-110">Element, který nebylo možné přepsat se někdy nazývá *zapečetěné* elementu.</span><span class="sxs-lookup"><span data-stu-id="c4b57-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="c4b57-111">Můžete použít `NotOverridable` jenom v příkazu deklarace vlastnosti nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="c4b57-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="c4b57-112">Můžete zadat `NotOverridable` pouze na vlastnosti nebo postup, který přepíše jinou vlastnost nebo postup, který je pouze v kombinaci s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c4b57-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="c4b57-113">Kombinovaná modifikátory</span><span class="sxs-lookup"><span data-stu-id="c4b57-113">Combined Modifiers</span></span>  
 <span data-ttu-id="c4b57-114">Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.</span><span class="sxs-lookup"><span data-stu-id="c4b57-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="c4b57-115">Nelze zadat `NotOverridable` společně s `MustOverride`, `Overridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c4b57-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c4b57-116">Použití</span><span class="sxs-lookup"><span data-stu-id="c4b57-116">Usage</span></span>  
 <span data-ttu-id="c4b57-117">`NotOverridable` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="c4b57-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c4b57-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="c4b57-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c4b57-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="c4b57-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c4b57-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="c4b57-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4b57-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4b57-121">See Also</span></span>  
 [<span data-ttu-id="c4b57-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="c4b57-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="c4b57-123">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="c4b57-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="c4b57-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c4b57-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="c4b57-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="c4b57-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="c4b57-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="c4b57-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="c4b57-127">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c4b57-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="c4b57-128">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4b57-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
