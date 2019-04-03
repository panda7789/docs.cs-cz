---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842301"
---
# <a name="key-visual-basic"></a><span data-ttu-id="5a840-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a840-102">Key (Visual Basic)</span></span>
<span data-ttu-id="5a840-103">`Key` – Klíčové slovo umožňuje zadat chování vlastností anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="5a840-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="5a840-104">Pouze vlastnosti, kterou určíte jako vlastnosti klíče účasti v testech rovnost mezi anonymního typu instance nebo výpočet hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="5a840-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="5a840-105">Nelze změnit hodnoty vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="5a840-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="5a840-106">Vlastnost anonymního typu určíte jako klíčová vlastnost tak, že klíčové slovo `Key` před deklarací ve inicializačního seznamu.</span><span class="sxs-lookup"><span data-stu-id="5a840-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="5a840-107">V následujícím příkladu `Airline` a `FlightNo` jsou klíčové vlastnosti, ale `Gate` není.</span><span class="sxs-lookup"><span data-stu-id="5a840-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="5a840-108">Když se vytvoří nové anonymní typ, dědí přímo z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5a840-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="5a840-109">Kompilátor nahradí tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a840-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="5a840-110">Přepsání kód, který je vytvořen pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> vychází z klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a840-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="5a840-111">Pokud nejsou žádné klíčové vlastnosti v typu, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nejsou přepsána.</span><span class="sxs-lookup"><span data-stu-id="5a840-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="5a840-112">Rovnost</span><span class="sxs-lookup"><span data-stu-id="5a840-112">Equality</span></span>  
 <span data-ttu-id="5a840-113">Když jsou instance stejného typu, a pokud jsou hodnoty jejich klíče vlastnosti stejné dvě instance anonymního typu jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="5a840-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="5a840-114">V následujících příkladech `flight2` rovná `flight1` z předchozího příkladu vzhledem k tomu, že jsou instance anonymní stejného typu a mají odpovídající hodnoty pro jejich vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="5a840-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="5a840-115">Ale `flight3` není roven `flight1` vzhledem k tomu, že má jinou hodnotu pro klíčovou vlastnost `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="5a840-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="5a840-116">Instance `flight4` není stejného typu jako `flight1` vzhledem k tomu, že se určit různé vlastnosti jako vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="5a840-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="5a840-117">Pokud není deklarovaný dvě instance s pouze neklíčovým vlastnostmi, identické název, typ, pořadí a hodnoty, nejsou dvě instance stejné.</span><span class="sxs-lookup"><span data-stu-id="5a840-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="5a840-118">Instance bez klíčové vlastnosti rovná pouze na sebe sama.</span><span class="sxs-lookup"><span data-stu-id="5a840-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="5a840-119">Další informace o podmínkách, za kterých jsou dvě instance anonymního typu instance stejného typu anonymní najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="5a840-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="5a840-120">Výpočet hodnoty hash kód</span><span class="sxs-lookup"><span data-stu-id="5a840-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="5a840-121">Stejně jako <xref:System.Object.Equals%2A>, funkci hash, která je definována v <xref:System.Object.GetHashCode%2A> anonymního typu je založena na klíčové vlastnosti typu.</span><span class="sxs-lookup"><span data-stu-id="5a840-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="5a840-122">Následující příklady ukazují interakce mezi klíčové vlastnosti a hodnotu hash hodnoty kódu.</span><span class="sxs-lookup"><span data-stu-id="5a840-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="5a840-123">Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče mají stejnou hodnotu hash kód, i v případě, že vlastnosti neklíčovým nemají odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a840-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="5a840-124">Následující příkaz vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="5a840-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="5a840-125">Instance anonymního typu, které mají různé hodnoty pro jeden nebo více klíčové vlastnosti mají odlišné kódu hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="5a840-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="5a840-126">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="5a840-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="5a840-127">Instance anonymních typů, které určují různé vlastnosti jako vlastnosti klíče nejsou instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5a840-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="5a840-128">Hodnoty hash různých mají i v případě, že názvy a hodnoty všech vlastností jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="5a840-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="5a840-129">Následující příkaz vrátí `False`.</span><span class="sxs-lookup"><span data-stu-id="5a840-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="5a840-130">Hodnoty jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5a840-130">Read-Only Values</span></span>  
 <span data-ttu-id="5a840-131">Nelze změnit hodnoty vlastnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="5a840-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="5a840-132">Například v `flight1` v předchozích příkladech `Airline` a `FlightNo` pole jsou jen pro čtení, ale `Gate` lze změnit.</span><span class="sxs-lookup"><span data-stu-id="5a840-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="5a840-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a840-133">See also</span></span>

- [<span data-ttu-id="5a840-134">Definice anonymního typu</span><span class="sxs-lookup"><span data-stu-id="5a840-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="5a840-135">Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností</span><span class="sxs-lookup"><span data-stu-id="5a840-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="5a840-136">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="5a840-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
