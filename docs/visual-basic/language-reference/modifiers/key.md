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
ms.openlocfilehash: 5b060f5fa0042dfb8ffa6876f5e172d3bcda67a3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396217"
---
# <a name="key-visual-basic"></a><span data-ttu-id="78744-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78744-102">Key (Visual Basic)</span></span>
<span data-ttu-id="78744-103">`Key`Klíčové slovo umožňuje zadat chování pro vlastnosti anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="78744-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="78744-104">Pouze vlastnosti, které označíte jako klíčové vlastnosti, se účastní testů rovnosti mezi instancemi anonymního typu nebo výpočtů hodnot kódů hash.</span><span class="sxs-lookup"><span data-stu-id="78744-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="78744-105">Hodnoty vlastností klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="78744-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="78744-106">Vlastnost anonymního typu určujete jako vlastnost klíče umístěním klíčového slova `Key` před jeho deklarací v inicializačním seznamu.</span><span class="sxs-lookup"><span data-stu-id="78744-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="78744-107">V následujícím příkladu `Airline` a `FlightNo` jsou klíčové vlastnosti, ale `Gate` ne.</span><span class="sxs-lookup"><span data-stu-id="78744-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="78744-108">Při vytvoření nového anonymního typu se zdědí přímo z <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="78744-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="78744-109">Kompilátor přepíše tři zděděné členy: <xref:System.Object.Equals%2A> , a <xref:System.Object.GetHashCode%2A> <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="78744-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="78744-110">Kód přepsání, který je vytvořen pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> je založen na vlastnostech klíče.</span><span class="sxs-lookup"><span data-stu-id="78744-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="78744-111">Pokud typ neobsahuje žádné klíčové vlastnosti <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nejsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="78744-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="78744-112">Rovnost</span><span class="sxs-lookup"><span data-stu-id="78744-112">Equality</span></span>  
 <span data-ttu-id="78744-113">Dvě instance anonymního typu jsou stejné, pokud jsou instance stejného typu a jsou-li hodnoty jejich klíčových vlastností stejné.</span><span class="sxs-lookup"><span data-stu-id="78744-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="78744-114">V následujících příkladech `flight2` je rovno `flight1` z předchozího příkladu, protože jsou instancemi stejného anonymního typu a mají shodné hodnoty pro své klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78744-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="78744-115">Není však `flight3` rovno, `flight1` protože má jinou hodnotu pro klíčovou vlastnost `FlightNo` .</span><span class="sxs-lookup"><span data-stu-id="78744-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="78744-116">Instance `flight4` není stejného typu, `flight1` protože určuje různé vlastnosti jako klíčové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78744-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="78744-117">Pokud jsou deklarovány dvě instance s pouze neklíčovým vlastností, které jsou stejné jako název, typ, pořadí a hodnota, tyto dvě instance se neshodují.</span><span class="sxs-lookup"><span data-stu-id="78744-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="78744-118">Instance bez vlastností klíče je stejná jenom pro sebe sama.</span><span class="sxs-lookup"><span data-stu-id="78744-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="78744-119">Další informace o podmínkách, za kterých jsou dvě instance anonymního typu instance stejného anonymního typu, naleznete v tématu [anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="78744-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="78744-120">Výpočet kódu hash</span><span class="sxs-lookup"><span data-stu-id="78744-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="78744-121">Podobně <xref:System.Object.Equals%2A> funkce hash, která je definována v <xref:System.Object.GetHashCode%2A> pro anonymní typ, je založena na klíčových vlastnostech typu.</span><span class="sxs-lookup"><span data-stu-id="78744-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="78744-122">Následující příklady znázorňují interakci mezi vlastnostmi klíče a hodnotami hash kódu.</span><span class="sxs-lookup"><span data-stu-id="78744-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="78744-123">Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče, mají stejnou hodnotu hash kódu, a to i v případě, že vlastnosti bez klíče nemají odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="78744-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="78744-124">Vrátí následující příkaz `True` .</span><span class="sxs-lookup"><span data-stu-id="78744-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="78744-125">Instance anonymního typu, které mají různé hodnoty pro jednu nebo více vlastností klíče, mají jiné hodnoty kódu hash.</span><span class="sxs-lookup"><span data-stu-id="78744-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="78744-126">Vrátí následující příkaz `False` .</span><span class="sxs-lookup"><span data-stu-id="78744-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="78744-127">Instance anonymních typů, které určují různé vlastnosti jako klíčové vlastnosti, nejsou instancemi stejného typu.</span><span class="sxs-lookup"><span data-stu-id="78744-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="78744-128">Mají různé hodnoty hash kódu, a to i v případě, že jsou názvy a hodnoty všech vlastností stejné.</span><span class="sxs-lookup"><span data-stu-id="78744-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="78744-129">Vrátí následující příkaz `False` .</span><span class="sxs-lookup"><span data-stu-id="78744-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="78744-130">Hodnoty jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="78744-130">Read-Only Values</span></span>  
 <span data-ttu-id="78744-131">Hodnoty vlastností klíče nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="78744-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="78744-132">Například v `flight1` předchozích příkladech `Airline` `FlightNo` jsou pole a určena jen pro čtení, ale `Gate` lze je změnit.</span><span class="sxs-lookup"><span data-stu-id="78744-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="78744-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="78744-133">See also</span></span>

- [<span data-ttu-id="78744-134">Definice anonymního typu</span><span class="sxs-lookup"><span data-stu-id="78744-134">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="78744-135">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu</span><span class="sxs-lookup"><span data-stu-id="78744-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="78744-136">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="78744-136">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
