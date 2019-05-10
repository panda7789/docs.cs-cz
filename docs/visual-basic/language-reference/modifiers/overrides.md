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
ms.openlocfilehash: 7fff91d993743574d13030aa3d5cc1e462e76838
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751024"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="6606b-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6606b-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="6606b-103">Určuje, že se vlastnost nebo procedura přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6606b-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="6606b-104">pravidla</span><span class="sxs-lookup"><span data-stu-id="6606b-104">Rules</span></span>

- <span data-ttu-id="6606b-105">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="6606b-105">**Declaration Context.**</span></span> <span data-ttu-id="6606b-106">Můžete použít `Overrides` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="6606b-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="6606b-107">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="6606b-107">**Combined Modifiers.**</span></span> <span data-ttu-id="6606b-108">Nelze zadat `Overrides` spolu s `Shadows` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6606b-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="6606b-109">Vzhledem k tomu, že element přepsání přepsatelné, nelze kombinovat `Overridable` s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6606b-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="6606b-110">**Odpovídající podpisy.**</span><span class="sxs-lookup"><span data-stu-id="6606b-110">**Matching Signatures.**</span></span> <span data-ttu-id="6606b-111">Signatura této deklarace musí přesně odpovídat *podpis* vlastnost nebo proceduru, která přepíše.</span><span class="sxs-lookup"><span data-stu-id="6606b-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="6606b-112">To znamená, že v seznamu parametrů musí mít stejný počet parametrů, ve stejném pořadí, se stejnými typy dat.</span><span class="sxs-lookup"><span data-stu-id="6606b-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="6606b-113">Kromě podpis přepsání deklarace musí také přesně odpovídat následující:</span><span class="sxs-lookup"><span data-stu-id="6606b-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="6606b-114">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="6606b-114">The access level</span></span>

  - <span data-ttu-id="6606b-115">Návratový typ, pokud existuje</span><span class="sxs-lookup"><span data-stu-id="6606b-115">The return type, if any</span></span>

- <span data-ttu-id="6606b-116">**Generických signatur.**</span><span class="sxs-lookup"><span data-stu-id="6606b-116">**Generic Signatures.**</span></span> <span data-ttu-id="6606b-117">Obecný postup je popsán podpis obsahuje počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="6606b-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="6606b-118">Proto přepsání deklarace musí odpovídat verzi základní třídy v tomto ohledu také.</span><span class="sxs-lookup"><span data-stu-id="6606b-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="6606b-119">**Další shodu.**</span><span class="sxs-lookup"><span data-stu-id="6606b-119">**Additional Matching.**</span></span> <span data-ttu-id="6606b-120">Kromě vzorů podpis verze základní třídy, tato deklarace se taky musí shodovat se v těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="6606b-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="6606b-121">Modifikátor úroveň přístupu (například [veřejné](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="6606b-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="6606b-122">Předání mechanismus každého parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="6606b-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="6606b-123">Omezení jsou uvedeny na jednotlivé parametry typu obecné procedury</span><span class="sxs-lookup"><span data-stu-id="6606b-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="6606b-124">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="6606b-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="6606b-125">Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="6606b-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="6606b-126">Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="6606b-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="6606b-127">Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="6606b-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="6606b-128">`Overrides` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="6606b-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="6606b-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="6606b-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="6606b-130">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="6606b-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="6606b-131">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="6606b-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="6606b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6606b-132">See also</span></span>

- [<span data-ttu-id="6606b-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="6606b-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="6606b-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="6606b-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="6606b-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="6606b-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="6606b-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6606b-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6606b-137">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6606b-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="6606b-138">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6606b-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="6606b-139">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="6606b-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
