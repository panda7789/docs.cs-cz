---
title: Přepsání
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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392025"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="2b35d-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b35d-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="2b35d-103">Určuje, že vlastnost nebo procedura Přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2b35d-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="2b35d-104">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2b35d-104">Rules</span></span>

- <span data-ttu-id="2b35d-105">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="2b35d-105">**Declaration Context.**</span></span> <span data-ttu-id="2b35d-106">Můžete použít `Overrides` pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="2b35d-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="2b35d-107">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="2b35d-107">**Combined Modifiers.**</span></span> <span data-ttu-id="2b35d-108">Nelze zadat `Overrides` společně s `Shadows` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="2b35d-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="2b35d-109">Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="2b35d-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="2b35d-110">**Vyhovující signatury.**</span><span class="sxs-lookup"><span data-stu-id="2b35d-110">**Matching Signatures.**</span></span> <span data-ttu-id="2b35d-111">Signatura této deklarace musí přesně odpovídat *podpisu* vlastnosti nebo procedury, kterou Přepisuje.</span><span class="sxs-lookup"><span data-stu-id="2b35d-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="2b35d-112">To znamená, že seznamy parametrů musí mít stejný počet parametrů ve stejném pořadí se stejnými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="2b35d-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="2b35d-113">Kromě signatury musí překrytá deklarace také přesně odpovídat následujícímu:</span><span class="sxs-lookup"><span data-stu-id="2b35d-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="2b35d-114">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="2b35d-114">The access level</span></span>

  - <span data-ttu-id="2b35d-115">Návratový typ, pokud existuje</span><span class="sxs-lookup"><span data-stu-id="2b35d-115">The return type, if any</span></span>

- <span data-ttu-id="2b35d-116">**Obecné podpisy**</span><span class="sxs-lookup"><span data-stu-id="2b35d-116">**Generic Signatures.**</span></span> <span data-ttu-id="2b35d-117">Pro obecný postup signatura obsahuje počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="2b35d-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="2b35d-118">Proto musí přepsání deklarace odpovídat verzi základní třídy i v tomto ohledu.</span><span class="sxs-lookup"><span data-stu-id="2b35d-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="2b35d-119">**Další shoda.**</span><span class="sxs-lookup"><span data-stu-id="2b35d-119">**Additional Matching.**</span></span> <span data-ttu-id="2b35d-120">Kromě shody signatury verze základní třídy musí tato deklarace také odpovídat těmto kritériím v následujících ohledech:</span><span class="sxs-lookup"><span data-stu-id="2b35d-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="2b35d-121">Modifikátor úrovně přístupu (například [Public](public.md))</span><span class="sxs-lookup"><span data-stu-id="2b35d-121">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="2b35d-122">Předání mechanismu každého parametru ([ByVal](byval.md) nebo [ByRef](byref.md))</span><span class="sxs-lookup"><span data-stu-id="2b35d-122">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="2b35d-123">Seznamy omezení pro každý parametr typu Obecné procedury</span><span class="sxs-lookup"><span data-stu-id="2b35d-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="2b35d-124">**Nastínování a přepisování.**</span><span class="sxs-lookup"><span data-stu-id="2b35d-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="2b35d-125">Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="2b35d-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="2b35d-126">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="2b35d-126">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="2b35d-127">Použijete `Overrides` -li, kompilátor implicitně přidá, `Overloads` aby vaše rozhraní API knihovny pracovalo s jazykem C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="2b35d-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="2b35d-128">`Overrides`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="2b35d-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="2b35d-129">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="2b35d-129">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="2b35d-130">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2b35d-130">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="2b35d-131">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="2b35d-131">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="2b35d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b35d-132">See also</span></span>

- [<span data-ttu-id="2b35d-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="2b35d-133">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="2b35d-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="2b35d-134">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="2b35d-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="2b35d-135">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="2b35d-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2b35d-136">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="2b35d-137">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b35d-137">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="2b35d-138">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b35d-138">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="2b35d-139">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="2b35d-139">Type List</span></span>](../statements/type-list.md)
