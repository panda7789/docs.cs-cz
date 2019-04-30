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
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920562"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="2f98a-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f98a-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="2f98a-103">Určuje, že se vlastnost nebo procedura přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2f98a-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f98a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f98a-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2f98a-105">pravidla</span><span class="sxs-lookup"><span data-stu-id="2f98a-105">Rules</span></span>  
  
-   <span data-ttu-id="2f98a-106">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-106">**Declaration Context.**</span></span> <span data-ttu-id="2f98a-107">Můžete použít `Overrides` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="2f98a-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="2f98a-108">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-108">**Combined Modifiers.**</span></span> <span data-ttu-id="2f98a-109">Nelze zadat `Overrides` spolu s `Shadows` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="2f98a-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="2f98a-110">Vzhledem k tomu, že element přepsání přepsatelné, nelze kombinovat `Overridable` s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="2f98a-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="2f98a-111">**Odpovídající podpisy.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-111">**Matching Signatures.**</span></span> <span data-ttu-id="2f98a-112">Signatura této deklarace musí přesně odpovídat *podpis* vlastnost nebo proceduru, která přepíše.</span><span class="sxs-lookup"><span data-stu-id="2f98a-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="2f98a-113">To znamená, že v seznamu parametrů musí mít stejný počet parametrů, ve stejném pořadí, se stejnými typy dat.</span><span class="sxs-lookup"><span data-stu-id="2f98a-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="2f98a-114">Kromě podpis přepsání deklarace musí také přesně odpovídat následující:</span><span class="sxs-lookup"><span data-stu-id="2f98a-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="2f98a-115">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="2f98a-115">The access level</span></span>  
  
    -   <span data-ttu-id="2f98a-116">Návratový typ, pokud existuje</span><span class="sxs-lookup"><span data-stu-id="2f98a-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="2f98a-117">**Generických signatur.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-117">**Generic Signatures.**</span></span> <span data-ttu-id="2f98a-118">Obecný postup je popsán podpis obsahuje počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="2f98a-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="2f98a-119">Proto přepsání deklarace musí odpovídat verzi základní třídy v tomto ohledu také.</span><span class="sxs-lookup"><span data-stu-id="2f98a-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="2f98a-120">**Další shodu.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-120">**Additional Matching.**</span></span> <span data-ttu-id="2f98a-121">Kromě vzorů podpis verze základní třídy, tato deklarace se taky musí shodovat se v těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="2f98a-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="2f98a-122">Modifikátor úroveň přístupu (například [veřejné](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="2f98a-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="2f98a-123">Předání mechanismus každého parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="2f98a-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="2f98a-124">Omezení jsou uvedeny na jednotlivé parametry typu obecné procedury</span><span class="sxs-lookup"><span data-stu-id="2f98a-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="2f98a-125">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="2f98a-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="2f98a-126">Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="2f98a-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="2f98a-127">Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="2f98a-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="2f98a-128">Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="2f98a-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="2f98a-129">`Overrides` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="2f98a-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2f98a-130">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2f98a-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2f98a-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="2f98a-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2f98a-132">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="2f98a-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f98a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f98a-133">See also</span></span>

- [<span data-ttu-id="2f98a-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="2f98a-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="2f98a-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="2f98a-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="2f98a-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="2f98a-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="2f98a-137">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2f98a-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="2f98a-138">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f98a-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="2f98a-139">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f98a-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="2f98a-140">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="2f98a-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
