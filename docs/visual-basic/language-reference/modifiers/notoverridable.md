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
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920650"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="135b5-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="135b5-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="135b5-103">Určuje, že vlastnost nebo procedura nedá přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="135b5-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135b5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="135b5-104">Remarks</span></span>  
 <span data-ttu-id="135b5-105">`NotOverridable` Modifikátor zabraňuje vlastnosti nebo metody přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="135b5-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="135b5-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="135b5-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="135b5-107">Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="135b5-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="135b5-108">Pokud `Overridable` nebo `NotOverridable` modifikátor není zadán, výchozí nastavení závisí na tom, zda vlastnosti nebo metody přepíše vlastnost základní třídy nebo metody.</span><span class="sxs-lookup"><span data-stu-id="135b5-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="135b5-109">Pokud vlastnost nebo metoda přepíše vlastnost základní třídy nebo metody, ve výchozím nastavení je `Overridable`; v opačném případě je `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="135b5-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="135b5-110">Někdy se označuje jako element, který nelze přepsat *zapečetěné* elementu.</span><span class="sxs-lookup"><span data-stu-id="135b5-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="135b5-111">Můžete použít `NotOverridable` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="135b5-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="135b5-112">Můžete zadat `NotOverridable` pouze na vlastnost nebo procedura, která přepíše jiné vlastnost nebo procedura, tedy pouze v kombinaci s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="135b5-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="135b5-113">Kombinované modifikátory</span><span class="sxs-lookup"><span data-stu-id="135b5-113">Combined Modifiers</span></span>  
 <span data-ttu-id="135b5-114">Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.</span><span class="sxs-lookup"><span data-stu-id="135b5-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="135b5-115">Nelze zadat `NotOverridable` spolu s `MustOverride`, `Overridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="135b5-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="135b5-116">Použití</span><span class="sxs-lookup"><span data-stu-id="135b5-116">Usage</span></span>  
 <span data-ttu-id="135b5-117">`NotOverridable` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="135b5-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="135b5-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="135b5-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="135b5-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="135b5-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="135b5-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="135b5-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="135b5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="135b5-121">See also</span></span>

- [<span data-ttu-id="135b5-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="135b5-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="135b5-123">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="135b5-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="135b5-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="135b5-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="135b5-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="135b5-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="135b5-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="135b5-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="135b5-127">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="135b5-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="135b5-128">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="135b5-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
