---
title: Klíč
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351509"
---
# <a name="key-visual-basic"></a><span data-ttu-id="081b6-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="081b6-102">Key (Visual Basic)</span></span>
<span data-ttu-id="081b6-103">Klíčové slovo `Key` umožňuje zadat chování pro vlastnosti anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="081b6-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="081b6-104">Pouze vlastnosti, které označíte jako klíčové vlastnosti, se účastní testů rovnosti mezi instancemi anonymního typu nebo výpočtů hodnot kódů hash.</span><span class="sxs-lookup"><span data-stu-id="081b6-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="081b6-105">Hodnoty vlastností klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="081b6-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="081b6-106">Vlastnost anonymního typu určíte tak, že umístíte klíčové slovo `Key` před jeho deklaraci v inicializačním seznamu.</span><span class="sxs-lookup"><span data-stu-id="081b6-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="081b6-107">V následujícím příkladu jsou `Airline` a `FlightNo` klíčové vlastnosti, ale `Gate` není.</span><span class="sxs-lookup"><span data-stu-id="081b6-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="081b6-108">Při vytvoření nového anonymního typu se zdědí přímo z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="081b6-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="081b6-109">Kompilátor přepíše tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>a <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="081b6-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="081b6-110">Kód přepsání, který je vytvořen pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> je založen na vlastnostech klíče.</span><span class="sxs-lookup"><span data-stu-id="081b6-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="081b6-111">Pokud typ neobsahuje žádné klíčové vlastnosti, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="081b6-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="081b6-112">Rovnost</span><span class="sxs-lookup"><span data-stu-id="081b6-112">Equality</span></span>  
 <span data-ttu-id="081b6-113">Dvě instance anonymního typu jsou stejné, pokud jsou instance stejného typu a jsou-li hodnoty jejich klíčových vlastností stejné.</span><span class="sxs-lookup"><span data-stu-id="081b6-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="081b6-114">V následujících příkladech je `flight2` rovno `flight1` z předchozího příkladu, protože jsou instancemi stejného anonymního typu a mají odpovídající hodnoty pro své klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="081b6-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="081b6-115">`flight3` se ale nerovná `flight1`, protože má jinou hodnotu pro klíčovou vlastnost `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="081b6-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="081b6-116">Instance `flight4` není stejného typu jako `flight1`, protože určují různé vlastnosti jako klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="081b6-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="081b6-117">Pokud jsou deklarovány dvě instance s pouze neklíčovým vlastností, které jsou stejné jako název, typ, pořadí a hodnota, tyto dvě instance se neshodují.</span><span class="sxs-lookup"><span data-stu-id="081b6-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="081b6-118">Instance bez vlastností klíče je stejná jenom pro sebe sama.</span><span class="sxs-lookup"><span data-stu-id="081b6-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="081b6-119">Další informace o podmínkách, za kterých jsou dvě instance anonymního typu instance stejného anonymního typu, naleznete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="081b6-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="081b6-120">Výpočet kódu hash</span><span class="sxs-lookup"><span data-stu-id="081b6-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="081b6-121">Podobně jako <xref:System.Object.Equals%2A>, funkce hash, která je definována v <xref:System.Object.GetHashCode%2A> anonymního typu, je založena na klíčových vlastnostech typu.</span><span class="sxs-lookup"><span data-stu-id="081b6-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="081b6-122">Následující příklady znázorňují interakci mezi vlastnostmi klíče a hodnotami hash kódu.</span><span class="sxs-lookup"><span data-stu-id="081b6-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="081b6-123">Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče, mají stejnou hodnotu hash kódu, a to i v případě, že vlastnosti bez klíče nemají odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="081b6-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="081b6-124">Následující příkaz vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="081b6-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="081b6-125">Instance anonymního typu, které mají různé hodnoty pro jednu nebo více vlastností klíče, mají jiné hodnoty kódu hash.</span><span class="sxs-lookup"><span data-stu-id="081b6-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="081b6-126">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="081b6-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="081b6-127">Instance anonymních typů, které určují různé vlastnosti jako klíčové vlastnosti, nejsou instancemi stejného typu.</span><span class="sxs-lookup"><span data-stu-id="081b6-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="081b6-128">Mají různé hodnoty hash kódu, a to i v případě, že jsou názvy a hodnoty všech vlastností stejné.</span><span class="sxs-lookup"><span data-stu-id="081b6-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="081b6-129">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="081b6-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="081b6-130">Hodnoty jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="081b6-130">Read-Only Values</span></span>  
 <span data-ttu-id="081b6-131">Hodnoty vlastností klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="081b6-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="081b6-132">Například v `flight1` v předchozích příkladech jsou pole `Airline` a `FlightNo` pouze pro čtení, ale `Gate` lze změnit.</span><span class="sxs-lookup"><span data-stu-id="081b6-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="081b6-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="081b6-133">See also</span></span>

- [<span data-ttu-id="081b6-134">Definice anonymního typu</span><span class="sxs-lookup"><span data-stu-id="081b6-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="081b6-135">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu</span><span class="sxs-lookup"><span data-stu-id="081b6-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="081b6-136">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="081b6-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
