---
title: Přetížení
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392103"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="d5d6a-102">Přetížení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="d5d6a-103">Určuje, že vlastnost nebo procedura znovu deklaruje jednu nebo více existujících vlastností nebo procedur se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5d6a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5d6a-104">Remarks</span></span>

<span data-ttu-id="d5d6a-105">*Přetížení* je postup poskytnutí více než jedné definice pro danou vlastnost nebo název procedury ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="d5d6a-106">Redeklarace vlastnosti nebo procedury s jiným podpisem se někdy označuje jako *skrývání pomocí signatury*.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="d5d6a-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="d5d6a-107">Rules</span></span>

- <span data-ttu-id="d5d6a-108">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-108">**Declaration Context.**</span></span> <span data-ttu-id="d5d6a-109">Můžete použít `Overloads` pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="d5d6a-110">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-110">**Combined Modifiers.**</span></span> <span data-ttu-id="d5d6a-111">Nemůžete zadat `Overloads` společně se [stíny](shadows.md) v rámci stejné deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-111">You cannot specify `Overloads` together with [Shadows](shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="d5d6a-112">**Požadované rozdíly**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-112">**Required Differences.**</span></span> <span data-ttu-id="d5d6a-113">*Signatura* v této deklaraci musí být odlišná od signatury každé vlastnosti nebo procedury, kterou přetěžuje.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="d5d6a-114">Signatura zahrnuje název vlastnosti nebo procedury spolu s následujícími vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="d5d6a-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="d5d6a-115">počet parametrů</span><span class="sxs-lookup"><span data-stu-id="d5d6a-115">the number of parameters</span></span>

  - <span data-ttu-id="d5d6a-116">pořadí parametrů</span><span class="sxs-lookup"><span data-stu-id="d5d6a-116">the order of the parameters</span></span>

  - <span data-ttu-id="d5d6a-117">datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="d5d6a-117">the data types of the parameters</span></span>

  - <span data-ttu-id="d5d6a-118">počet parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="d5d6a-119">návratový typ (pouze pro proceduru operátora převodu)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="d5d6a-120">Všechna přetížení musí mít stejný název, ale každá se musí lišit od všech ostatních v jednom nebo více předchozích ohledech.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="d5d6a-121">To umožňuje kompilátoru odlišit, která verze se má použít, když kód volá vlastnost nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="d5d6a-122">**Nepovolené rozdíly.**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-122">**Disallowed Differences.**</span></span> <span data-ttu-id="d5d6a-123">Změna jednoho nebo více následujících možností není platná pro přetížení vlastnosti nebo procedury, protože nejsou součástí signatury:</span><span class="sxs-lookup"><span data-stu-id="d5d6a-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="d5d6a-124">bez ohledu na to, jestli vrátí hodnotu (pro proceduru)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="d5d6a-125">datový typ návratové hodnoty (s výjimkou operátoru převodu)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="d5d6a-126">názvy parametrů nebo parametrů typu</span><span class="sxs-lookup"><span data-stu-id="d5d6a-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="d5d6a-127">omezení parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="d5d6a-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="d5d6a-128">Klíčová slova modifikátoru parametru (například `ByRef` nebo `Optional` )</span><span class="sxs-lookup"><span data-stu-id="d5d6a-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="d5d6a-129">Klíčová slova modifikátoru vlastnosti nebo procedury (například `Public` nebo `Shared` )</span><span class="sxs-lookup"><span data-stu-id="d5d6a-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="d5d6a-130">**Volitelný modifikátor**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-130">**Optional Modifier.**</span></span> <span data-ttu-id="d5d6a-131">Nemusíte používat `Overloads` Modifikátor při definování více přetížených vlastností nebo procedur ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="d5d6a-132">Pokud však použijete `Overloads` v jedné z deklarací, je nutné ji použít ve všech těchto deklaracích.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="d5d6a-133">**Nastínování a přetížení.**</span><span class="sxs-lookup"><span data-stu-id="d5d6a-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="d5d6a-134">`Overloads`lze také použít pro stín existujícího člena nebo sadu přetížených členů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="d5d6a-135">Při použití `Overloads` tímto způsobem deklarujete vlastnost nebo metodu se stejným názvem a stejným seznamem parametrů jako člen základní třídy a nezadáte `Shadows` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="d5d6a-136">Použijete `Overrides` -li, kompilátor implicitně přidá, `Overloads` aby vaše rozhraní API knihovny pracovalo s jazykem C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="d5d6a-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="d5d6a-137">`Overloads`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="d5d6a-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="d5d6a-138">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5d6a-138">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="d5d6a-139">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5d6a-139">Operator Statement</span></span>](../statements/operator-statement.md)

- [<span data-ttu-id="d5d6a-140">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5d6a-140">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="d5d6a-141">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5d6a-141">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="d5d6a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5d6a-142">See also</span></span>

- [<span data-ttu-id="d5d6a-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="d5d6a-143">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="d5d6a-144">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="d5d6a-144">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d5d6a-145">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5d6a-145">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d5d6a-146">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="d5d6a-146">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="d5d6a-147">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="d5d6a-147">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
