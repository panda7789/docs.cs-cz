---
title: 'Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 67cc9e85d249365a7b4b7636c99766087314622d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596854"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="533d0-102">Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="533d0-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="533d0-103">Anonymní typy umožňují žádný mechanismus pro datové typy vlastností přímo zadáním.</span><span class="sxs-lookup"><span data-stu-id="533d0-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="533d0-104">Typy všech vlastností jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="533d0-104">Types of all properties are inferred.</span></span> <span data-ttu-id="533d0-105">V následujícím příkladu, typy `Name` a `Price` jsou odvozeny z hodnoty, které se používají k inicializaci je přímo.</span><span class="sxs-lookup"><span data-stu-id="533d0-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 <span data-ttu-id="533d0-106">Anonymní typy lze odvodit také názvy vlastností a typy z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="533d0-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="533d0-107">Následující části obsahují seznam okolností, kde je možné odvození a příklady situací, kdy není.</span><span class="sxs-lookup"><span data-stu-id="533d0-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="533d0-108">Úspěšné odvození</span><span class="sxs-lookup"><span data-stu-id="533d0-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="533d0-109">Anonymní typy lze odvodit názvy vlastností a typy z následujících zdrojů:</span><span class="sxs-lookup"><span data-stu-id="533d0-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="533d0-110">Z názvů proměnných.</span><span class="sxs-lookup"><span data-stu-id="533d0-110">From variable names.</span></span> <span data-ttu-id="533d0-111">Anonymní typ `anonProduct` bude mít dvě vlastnosti `productName` a `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="533d0-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="533d0-112">Jejich datové typy, budou původní proměnných `String` a `Double`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="533d0-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   <span data-ttu-id="533d0-113">Vlastnost nebo pole názvů jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="533d0-113">From property or field names of other objects.</span></span> <span data-ttu-id="533d0-114">Představte si třeba `car` objekt `CarClass` typ, který zahrnuje `Name` a `ID` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="533d0-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="533d0-115">Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovány s hodnotami z `car` objektu, můžete napsat následující:</span><span class="sxs-lookup"><span data-stu-id="533d0-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     <span data-ttu-id="533d0-116">Předchozí deklarace je ekvivalentní delší řádek kódu, který definuje anonymního typu `car2`.</span><span class="sxs-lookup"><span data-stu-id="533d0-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   <span data-ttu-id="533d0-117">Z názvů členů XML.</span><span class="sxs-lookup"><span data-stu-id="533d0-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     <span data-ttu-id="533d0-118">Výsledný typ pro `anon` by mít jednu vlastnost `Book`, typu <xref:System.Collections.IEnumerable>(XElement z).</span><span class="sxs-lookup"><span data-stu-id="533d0-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="533d0-119">Z funkce, která nemá žádné parametry, jako například `SomeFunction` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="533d0-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="533d0-120">Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost s názvem znak `First`.</span><span class="sxs-lookup"><span data-stu-id="533d0-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="533d0-121">Tento kód zobrazí písmeno "E", písmeno, kterou vrátí funkce <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="533d0-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a><span data-ttu-id="533d0-122">Odvození selhání</span><span class="sxs-lookup"><span data-stu-id="533d0-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="533d0-123">Název odvození se nezdaří v mnoha případech platí, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="533d0-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="533d0-124">Odvození je odvozena z volání metody, konstruktor nebo parametrizovanou vlastnost, která vyžaduje argumenty.</span><span class="sxs-lookup"><span data-stu-id="533d0-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="533d0-125">Předchozí deklarace této třídy `anon1` selže, pokud `someFunction` má jeden nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="533d0-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="533d0-126">Přiřazení na nový název vlastnosti byl problém vyřešen.</span><span class="sxs-lookup"><span data-stu-id="533d0-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="533d0-127">Odvození je odvozena z složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="533d0-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="533d0-128">Chybu lze vyřešit tak, že přiřadíte výsledek výrazu název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="533d0-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   <span data-ttu-id="533d0-129">Odvození pro více vlastností vytvoří dva nebo více vlastností, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="533d0-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="533d0-130">Odkazující zpět na deklarace v předchozích příkladech, vás není možné vypsat obě `product.Name` a `car1.Name` jako vlastnosti anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="533d0-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="533d0-131">Důvodem je, že by být odvozené identifikátor pro každou z těchto `Name`.</span><span class="sxs-lookup"><span data-stu-id="533d0-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="533d0-132">Tento problém lze vyřešit přiřazení hodnoty k vlastnosti odlišné názvy.</span><span class="sxs-lookup"><span data-stu-id="533d0-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     <span data-ttu-id="533d0-133">Všimněte si, že změny v případě, že (změny se mezi velkými a malými písmeny) Nedovolte, aby byly dva názvy distinct.</span><span class="sxs-lookup"><span data-stu-id="533d0-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="533d0-134">Počáteční typ a hodnotu jednu vlastnost závisí na jiné vlastnosti, která zatím nebyl určen.</span><span class="sxs-lookup"><span data-stu-id="533d0-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="533d0-135">Například `.IDName = .LastName` není platný v deklaraci anonymního typu není-li `.LastName` již byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="533d0-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="533d0-136">V tomto příkladu můžete opravit problém přehozením pořadí, ve kterém jsou deklarovány vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="533d0-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   <span data-ttu-id="533d0-137">Název vlastnosti anonymního typu je stejný jako název člena <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="533d0-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="533d0-138">Například následující deklaraci selže, protože `Equals` je metoda <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="533d0-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="533d0-139">Problém můžete vyřešit tak, že změníte název vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="533d0-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="533d0-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="533d0-140">See also</span></span>
- [<span data-ttu-id="533d0-141">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="533d0-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="533d0-142">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="533d0-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="533d0-143">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="533d0-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="533d0-144">Key</span><span class="sxs-lookup"><span data-stu-id="533d0-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
