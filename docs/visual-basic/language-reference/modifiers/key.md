---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="9f2ad-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f2ad-102">Key (Visual Basic)</span></span>
<span data-ttu-id="9f2ad-103">`Key` – Klíčové slovo můžete určit chování pro vlastnosti anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="9f2ad-104">Pouze vlastnosti, které označíte jako vlastnosti klíče účastnit testy rovnosti mezi anonymní typ instance nebo výpočtu hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="9f2ad-105">Hodnoty vlastnosti klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="9f2ad-106">Vlastnost anonymní typ určíte jako vlastnosti klíče, tím, že umístíte klíčové slovo `Key` před jeho deklaraci v seznamu inicializace.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="9f2ad-107">V následujícím příkladu `Airline` a `FlightNo` jsou klíčové vlastnosti, ale `Gate` není.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="9f2ad-108">Když je vytvořen nový anonymní typ, dědí přímo z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="9f2ad-109">Kompilátor přepsání tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="9f2ad-110">Kód přepsání, která je vytvořena pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> je založena na klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="9f2ad-111">Pokud nejsou žádné klíčové vlastnosti v typu, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nepřepíše.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="9f2ad-112">Rovnost</span><span class="sxs-lookup"><span data-stu-id="9f2ad-112">Equality</span></span>  
 <span data-ttu-id="9f2ad-113">Dvě instance anonymního typu jsou stejné, pokud jsou instance stejného typu a hodnoty jejich klíčové vlastnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="9f2ad-114">V následujících příkladech `flight2` rovná `flight1` z předchozího příkladu protože jsou instance anonymní stejného typu a mají odpovídající hodnoty pro jejich vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="9f2ad-115">Ale `flight3` se nerovná `flight1` protože má jinou hodnotu pro klíčovou vlastnost `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="9f2ad-116">Instance `flight4` není stejného typu jako `flight1` vzhledem k tomu, že určit různé vlastnosti jako vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="9f2ad-117">Pokud jsou dvě instance deklarovat s pouze neklíčovými vlastnostmi, stejná název, typ, pořadí a hodnoty, nejsou dvě instance stejné.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="9f2ad-118">Instance bez vlastnosti klíče je rovna pouze na sebe sama.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="9f2ad-119">Další informace o podmínkách, pod kterým jsou dvě instance anonymní typ instance stejného typu anonymní najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9f2ad-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="9f2ad-120">Výpočet hodnoty hash kódu</span><span class="sxs-lookup"><span data-stu-id="9f2ad-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="9f2ad-121">Jako <xref:System.Object.Equals%2A>, funkce algoritmu hash, která je definována v <xref:System.Object.GetHashCode%2A> pro anonymní typ je založena na klíčové vlastnosti typu.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="9f2ad-122">Následující příklady ukazují interakce mezi klíčové vlastnosti a hodnotu hash hodnoty kódu.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="9f2ad-123">Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče mají stejnou hodnotu hash kód, i když neklíčovými vlastnostmi nemají odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="9f2ad-124">Následující příkaz vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="9f2ad-125">Anonymní typ instancí, které mají různé hodnoty pro jeden nebo více klíčové vlastnosti mít hodnoty různých hash.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="9f2ad-126">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="9f2ad-127">Instance anonymní typy, které určit různé vlastnosti jako vlastnosti klíče nejsou instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="9f2ad-128">Hodnoty hash různých mají i v případě, že názvy a hodnoty všech vlastností jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="9f2ad-129">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="9f2ad-130">Jen pro čtení hodnoty</span><span class="sxs-lookup"><span data-stu-id="9f2ad-130">Read-Only Values</span></span>  
 <span data-ttu-id="9f2ad-131">Hodnoty vlastnosti klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="9f2ad-132">Například v `flight1` v předchozích příkladech `Airline` a `FlightNo` pole jsou jen pro čtení, ale `Gate` lze změnit.</span><span class="sxs-lookup"><span data-stu-id="9f2ad-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2ad-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f2ad-133">See Also</span></span>  
 [<span data-ttu-id="9f2ad-134">Definice autonomního typu</span><span class="sxs-lookup"><span data-stu-id="9f2ad-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="9f2ad-135">Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností</span><span class="sxs-lookup"><span data-stu-id="9f2ad-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="9f2ad-136">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9f2ad-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
