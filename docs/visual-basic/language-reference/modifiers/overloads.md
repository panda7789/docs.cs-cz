---
title: Přetížení (Visual Basic)
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
ms.openlocfilehash: b20dbf20c580d08553ae22f6a62ee33a7354db74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624911"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="aaca0-102">Přetížení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaca0-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="aaca0-103">Určuje, že se vlastnost nebo procedura znovu deklaruje jednu nebo více existujících vlastností nebo procedur se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="aaca0-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaca0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaca0-104">Remarks</span></span>  
 <span data-ttu-id="aaca0-105">*Přetížení* je zvyk poskytování více než jednu definici pro danou vlastnost nebo procedura názvu ve stejném oboru.</span><span class="sxs-lookup"><span data-stu-id="aaca0-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="aaca0-106">Změně deklarace se vlastnost nebo procedura s jiným podpisem se někdy označuje jako *skrytí podle podpisu*.</span><span class="sxs-lookup"><span data-stu-id="aaca0-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="aaca0-107">pravidla</span><span class="sxs-lookup"><span data-stu-id="aaca0-107">Rules</span></span>  
  
-   <span data-ttu-id="aaca0-108">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-108">**Declaration Context.**</span></span> <span data-ttu-id="aaca0-109">Můžete použít `Overloads` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="aaca0-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="aaca0-110">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-110">**Combined Modifiers.**</span></span> <span data-ttu-id="aaca0-111">Nelze zadat `Overloads` spolu s [stíny](../../../visual-basic/language-reference/modifiers/shadows.md) ve stejné deklaraci procedury.</span><span class="sxs-lookup"><span data-stu-id="aaca0-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="aaca0-112">**Požadované rozdíly.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-112">**Required Differences.**</span></span> <span data-ttu-id="aaca0-113">*Podpis* v této deklaraci musí být odlišný od podpis každou vlastnost nebo proceduru, která ji přetíží.</span><span class="sxs-lookup"><span data-stu-id="aaca0-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="aaca0-114">Podpis se skládá z názvu vlastnost nebo procedura spolu s následující:</span><span class="sxs-lookup"><span data-stu-id="aaca0-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="aaca0-115">počet parametrů</span><span class="sxs-lookup"><span data-stu-id="aaca0-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="aaca0-116">pořadí parametrů</span><span class="sxs-lookup"><span data-stu-id="aaca0-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="aaca0-117">datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="aaca0-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="aaca0-118">počet parametrů typu (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="aaca0-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="aaca0-119">Návratový typ (pouze pro procedury operátoru převodu)</span><span class="sxs-lookup"><span data-stu-id="aaca0-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="aaca0-120">Všechna přetížení musí mít stejný název, ale každý se musí lišit od všech ostatních počítačů v jedné nebo více předchozích ohledech.</span><span class="sxs-lookup"><span data-stu-id="aaca0-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="aaca0-121">To umožňuje kompilátoru k rozlišení, které verze se má použít, když kód volá vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="aaca0-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="aaca0-122">**Nepovolené rozdíly.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-122">**Disallowed Differences.**</span></span> <span data-ttu-id="aaca0-123">Změna jeden nebo více z následujících akcí není platná pro přetížení se vlastnost nebo procedura, protože nejsou součástí podpisu:</span><span class="sxs-lookup"><span data-stu-id="aaca0-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="aaca0-124">Určuje, jestli vrací hodnotu (postup)</span><span class="sxs-lookup"><span data-stu-id="aaca0-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="aaca0-125">Datový typ vrácené hodnoty (s výjimkou operátoru převodu)</span><span class="sxs-lookup"><span data-stu-id="aaca0-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="aaca0-126">názvy parametrů nebo parametry typu</span><span class="sxs-lookup"><span data-stu-id="aaca0-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="aaca0-127">omezení parametrů typů (pro obecný postup)</span><span class="sxs-lookup"><span data-stu-id="aaca0-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="aaca0-128">klíčová slova modifikátor parametrů (jako například `ByRef` nebo `Optional`)</span><span class="sxs-lookup"><span data-stu-id="aaca0-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="aaca0-129">Vlastnost nebo procedura modifikátor klíčová slova (jako například `Public` nebo `Shared`)</span><span class="sxs-lookup"><span data-stu-id="aaca0-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="aaca0-130">**Volitelný modifikátor.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-130">**Optional Modifier.**</span></span> <span data-ttu-id="aaca0-131">Není nutné používat `Overloads` modifikátor při definování více přetížených vlastností nebo procedur ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="aaca0-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="aaca0-132">Nicméně pokud používáte `Overloads` v jednom z deklarací, je nutné je použít pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="aaca0-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="aaca0-133">**Stínový provoz a přetížení.**</span><span class="sxs-lookup"><span data-stu-id="aaca0-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="aaca0-134">`Overloads` Můžete také použít stínové existujícího člena nebo sadu přetížených členů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="aaca0-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="aaca0-135">Při použití `Overloads` tímto způsobem můžete deklarovat vlastnosti nebo metody se stejným názvem a seznamu parametrů jako člena základní třídy a nezadáte `Shadows` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="aaca0-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="aaca0-136">Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.</span><span class="sxs-lookup"><span data-stu-id="aaca0-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="aaca0-137">`Overloads` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="aaca0-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aaca0-138">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="aaca0-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="aaca0-139">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="aaca0-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="aaca0-140">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="aaca0-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="aaca0-141">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="aaca0-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="aaca0-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaca0-142">See also</span></span>
- [<span data-ttu-id="aaca0-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="aaca0-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="aaca0-144">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="aaca0-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="aaca0-145">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaca0-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="aaca0-146">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="aaca0-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="aaca0-147">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="aaca0-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
