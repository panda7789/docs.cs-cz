---
title: 'Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 5bd4e0a760bcedf8f5e96c2cebe3a71b9050a420
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582283"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="a0375-102">Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0375-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="a0375-103">Anonymní typy neposkytují žádný mechanismus pro přímé určení datových typů vlastností.</span><span class="sxs-lookup"><span data-stu-id="a0375-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="a0375-104">Typy všech vlastností jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="a0375-104">Types of all properties are inferred.</span></span> <span data-ttu-id="a0375-105">V následujícím příkladu jsou typy `Name` a `Price` odvozeny přímo z hodnot, které jsou použity k jejich inicializaci.</span><span class="sxs-lookup"><span data-stu-id="a0375-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="a0375-106">Anonymní typy mohou také odvodit názvy vlastností a typy z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="a0375-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="a0375-107">Níže uvedené části obsahují seznam případů, ve kterých je odvozeno odvozování, a příklady situací, kdy není možné.</span><span class="sxs-lookup"><span data-stu-id="a0375-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="a0375-108">Úspěšné odvození</span><span class="sxs-lookup"><span data-stu-id="a0375-108">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="a0375-109">Anonymní typy mohou odvodit názvy vlastností a typy z následujících zdrojů:</span><span class="sxs-lookup"><span data-stu-id="a0375-109">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="a0375-110">Z názvů proměnných.</span><span class="sxs-lookup"><span data-stu-id="a0375-110">From variable names.</span></span> <span data-ttu-id="a0375-111">@No__t_0 anonymního typu budou mít dvě vlastnosti, `productName` a `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="a0375-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="a0375-112">Jejich datové typy budou ty z původních proměnných, `String` a `Double`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a0375-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="a0375-113">Z vlastností nebo názvů polí jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="a0375-113">From property or field names of other objects.</span></span> <span data-ttu-id="a0375-114">Zvažte například `car` objekt `CarClass` typu, který obsahuje vlastnosti `Name` a `ID`.</span><span class="sxs-lookup"><span data-stu-id="a0375-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="a0375-115">Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovány s hodnotami z objektu `car`, můžete zapsat následující:</span><span class="sxs-lookup"><span data-stu-id="a0375-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="a0375-116">Předchozí deklarace je ekvivalentní s delším řádkem kódu, který definuje anonymní typ `car2`.</span><span class="sxs-lookup"><span data-stu-id="a0375-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="a0375-117">Z názvů členů XML.</span><span class="sxs-lookup"><span data-stu-id="a0375-117">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="a0375-118">Výsledný typ pro `anon` by měl mít jednu vlastnost `Book` typu <xref:System.Collections.IEnumerable> (Of XElement).</span><span class="sxs-lookup"><span data-stu-id="a0375-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="a0375-119">Z funkce, která nemá žádné parametry, například `SomeFunction` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0375-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="a0375-120">Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost, znak nazvaný `First`.</span><span class="sxs-lookup"><span data-stu-id="a0375-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="a0375-121">Tento kód zobrazí písmeno "E", které je vráceno funkcí <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0375-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="a0375-122">Selhání odvození</span><span class="sxs-lookup"><span data-stu-id="a0375-122">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="a0375-123">Odvození názvu selže v mnoha případech, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="a0375-123">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="a0375-124">Odvození je odvozeno od vyvolání metody, konstruktoru nebo parametrizované vlastnosti, která vyžaduje argumenty.</span><span class="sxs-lookup"><span data-stu-id="a0375-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="a0375-125">Předchozí deklarace `anon1` se nezdařila, pokud `someFunction` jeden nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="a0375-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="a0375-126">Přiřazení k novému názvu vlastnosti tento problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="a0375-126">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="a0375-127">Odvození je odvozeno od složitého výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0375-127">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="a0375-128">Chybu lze vyřešit přiřazením výsledku výrazu k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0375-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="a0375-129">Odvození pro více vlastností vytváří dvě nebo více vlastností, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="a0375-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="a0375-130">Odkazy zpět na deklarace v předchozích příkladech nemůžete uvést `product.Name` a `car1.Name` jako vlastnosti stejného anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="a0375-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="a0375-131">Důvodem je, že odvozený identifikátor každého z nich by byl `Name`.</span><span class="sxs-lookup"><span data-stu-id="a0375-131">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="a0375-132">Problém lze vyřešit přiřazením hodnot k jedinečným názvům vlastností.</span><span class="sxs-lookup"><span data-stu-id="a0375-132">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="a0375-133">Všimněte si, že změny v případě (změny mezi velkými a malými písmeny) nedělají dva názvy odlišně.</span><span class="sxs-lookup"><span data-stu-id="a0375-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="a0375-134">Počáteční typ a hodnota jedné vlastnosti závisí na jiné vlastnosti, která ještě není navázána.</span><span class="sxs-lookup"><span data-stu-id="a0375-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="a0375-135">Například `.IDName = .LastName` není platný v deklaraci anonymního typu, pokud není `.LastName` již inicializována.</span><span class="sxs-lookup"><span data-stu-id="a0375-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="a0375-136">V tomto příkladu lze problém vyřešit zrušením pořadí, ve kterém jsou vlastnosti deklarovány.</span><span class="sxs-lookup"><span data-stu-id="a0375-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="a0375-137">Název vlastnosti anonymního typu je stejný jako název členu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a0375-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="a0375-138">Například následující deklarace se nezdařila, protože `Equals` je metoda <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a0375-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="a0375-139">Problém můžete vyřešit tak, že změníte název vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a0375-139">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="a0375-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0375-140">See also</span></span>

- [<span data-ttu-id="a0375-141">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a0375-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="a0375-142">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="a0375-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="a0375-143">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a0375-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="a0375-144">Key</span><span class="sxs-lookup"><span data-stu-id="a0375-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
