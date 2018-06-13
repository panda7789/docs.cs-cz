---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602516"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="7ed87-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ed87-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="7ed87-103">Určuje, že vlastnost nebo postup přepisuje stejně jako s názvem vlastnosti nebo postup zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="7ed87-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ed87-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ed87-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7ed87-105">Pravidla</span><span class="sxs-lookup"><span data-stu-id="7ed87-105">Rules</span></span>  
  
-   <span data-ttu-id="7ed87-106">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-106">**Declaration Context.**</span></span> <span data-ttu-id="7ed87-107">Můžete použít `Overrides` jenom v příkazu deklarace vlastnosti nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="7ed87-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="7ed87-108">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-108">**Combined Modifiers.**</span></span> <span data-ttu-id="7ed87-109">Nelze zadat `Overrides` společně s `Shadows` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7ed87-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="7ed87-110">Element přepsání je implicitně přepisovatelné, a proto nelze kombinovat `Overridable` s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="7ed87-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="7ed87-111">**Odpovídající podpisy.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-111">**Matching Signatures.**</span></span> <span data-ttu-id="7ed87-112">Podpis tohoto prohlášení, musí přesně shodovat *podpis* vlastnost nebo postup, který přepíše.</span><span class="sxs-lookup"><span data-stu-id="7ed87-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="7ed87-113">To znamená, seznamy parametr musí mít stejný počet parametrů, ve stejném pořadí, se stejnými typy data.</span><span class="sxs-lookup"><span data-stu-id="7ed87-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="7ed87-114">Kromě podpis přepsání deklaraci musí také přesně shodovat následující:</span><span class="sxs-lookup"><span data-stu-id="7ed87-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="7ed87-115">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="7ed87-115">The access level</span></span>  
  
    -   <span data-ttu-id="7ed87-116">Návratový typ, pokud existuje</span><span class="sxs-lookup"><span data-stu-id="7ed87-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="7ed87-117">**Obecné podpisy.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-117">**Generic Signatures.**</span></span> <span data-ttu-id="7ed87-118">Obecný postup zahrnuje podpis počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="7ed87-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="7ed87-119">Přepsání deklaraci proto musí shodovat s verzí základní třídy v tomto ohledu také.</span><span class="sxs-lookup"><span data-stu-id="7ed87-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="7ed87-120">**Další odpovídající.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-120">**Additional Matching.**</span></span> <span data-ttu-id="7ed87-121">Kromě párování podpis verze základní třídy, toto prohlášení se taky musí shodovat se v těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="7ed87-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="7ed87-122">Úroveň přístupu – modifikátor (například [veřejné](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="7ed87-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="7ed87-123">Předávání mechanismus každý parametr ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="7ed87-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="7ed87-124">Omezení jsou uvedeny na každý parametr typu obecné procedury</span><span class="sxs-lookup"><span data-stu-id="7ed87-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="7ed87-125">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="7ed87-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="7ed87-126">Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="7ed87-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="7ed87-127">Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="7ed87-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="7ed87-128">Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="7ed87-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="7ed87-129">`Overrides` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="7ed87-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7ed87-130">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="7ed87-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="7ed87-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="7ed87-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="7ed87-132">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="7ed87-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ed87-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ed87-133">See Also</span></span>  
 [<span data-ttu-id="7ed87-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="7ed87-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="7ed87-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="7ed87-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="7ed87-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="7ed87-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="7ed87-137">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7ed87-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="7ed87-138">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ed87-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="7ed87-139">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ed87-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="7ed87-140">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="7ed87-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
