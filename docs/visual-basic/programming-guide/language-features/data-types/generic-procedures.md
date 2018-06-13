---
title: Obecné procedury v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649393"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="deb55-102">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="deb55-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="deb55-103">A *obecný postup*, také zavolat *obecná metoda*, je procedura definovaný s alespoň jeden typ parametru.</span><span class="sxs-lookup"><span data-stu-id="deb55-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="deb55-104">To umožňuje přizpůsobit typy dat, které mají požadavky na jeho pokaždé, když se volá proceduru volajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="deb55-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="deb55-105">Postup není obecné jednoduše na základě definovaný v obecné třídy nebo obecná struktura.</span><span class="sxs-lookup"><span data-stu-id="deb55-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="deb55-106">Chcete-li být obecný, musí trvat minimálně jeden parametr typu, kromě všech normální parametrů, může to trvat.</span><span class="sxs-lookup"><span data-stu-id="deb55-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="deb55-107">Obecné třídu nebo strukturu může obsahovat neobecné procedury a neobecná třída, struktura, nebo modul může obsahovat obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="deb55-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="deb55-108">Obecný postup můžete použít jeho parametry typu ve svém seznamu normální parametr, v její návratový typ, pokud má jeden a v jeho postupu kódu.</span><span class="sxs-lookup"><span data-stu-id="deb55-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="deb55-109">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="deb55-109">Type Inference</span></span>  
 <span data-ttu-id="deb55-110">Obecný postup můžete volat bez nutnosti zadávat žádné argumenty typu vůbec.</span><span class="sxs-lookup"><span data-stu-id="deb55-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="deb55-111">Pokud jste ji volat tímto způsobem, kompilátor se pokusí určit příslušné datové typy předat argumenty procedury typu.</span><span class="sxs-lookup"><span data-stu-id="deb55-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="deb55-112">To se označuje jako *odvození typu*.</span><span class="sxs-lookup"><span data-stu-id="deb55-112">This is called *type inference*.</span></span> <span data-ttu-id="deb55-113">Následující kód ukazuje volání v které kompilátor odvodí, že by měl předat typ `String` pro parametr typu `t`.</span><span class="sxs-lookup"><span data-stu-id="deb55-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="deb55-114">Pokud kompilátor nelze odvodit typ argumentů v kontextu volání, nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="deb55-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="deb55-115">Možnou příčinou takové chyby neshodě rozhraní pole rank.</span><span class="sxs-lookup"><span data-stu-id="deb55-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="deb55-116">Předpokládejme například, že definujete normální parametr jako pole parametr typu.</span><span class="sxs-lookup"><span data-stu-id="deb55-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="deb55-117">Když zavoláte obecný postup poskytuje řadu různých pořadí (počet dimenzí), je neshoda způsobí, že odvození typu selhání.</span><span class="sxs-lookup"><span data-stu-id="deb55-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="deb55-118">Následující kód ukazuje volání v který předat do procedury, která očekává jednorozměrné pole dvourozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="deb55-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 <span data-ttu-id="deb55-119">Odvození typu můžete vyvolat jenom vynecháním všechny argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="deb55-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="deb55-120">Pokud zadáte jeden argument typu, je nutné zadat všechny.</span><span class="sxs-lookup"><span data-stu-id="deb55-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="deb55-121">Odvození typu je podporována pouze pro obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="deb55-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="deb55-122">Odvození typu obecné třídy, struktury, rozhraní nebo delegáti nelze vyvolat.</span><span class="sxs-lookup"><span data-stu-id="deb55-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deb55-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="deb55-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="deb55-124">Popis</span><span class="sxs-lookup"><span data-stu-id="deb55-124">Description</span></span>  
 <span data-ttu-id="deb55-125">V následujícím příkladu definuje obecný `Function` postup najít konkrétní prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="deb55-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="deb55-126">Definuje jeden parametr typu a použije ji k vytvoření dva parametry v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="deb55-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="deb55-127">Kód</span><span class="sxs-lookup"><span data-stu-id="deb55-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="deb55-128">Komentáře</span><span class="sxs-lookup"><span data-stu-id="deb55-128">Comments</span></span>  
 <span data-ttu-id="deb55-129">V předchozím příkladu vyžaduje možnost k porovnání `searchValue` proti každý element `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="deb55-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="deb55-130">Pokud chcete zajistit tuto možnost, omezuje parametr typu `T` implementovat <xref:System.IComparable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="deb55-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="deb55-131">Kód používá <xref:System.IComparable%601.CompareTo%2A> metoda místo `=` operátor, protože není zaručeno, že pro zadaný argument typu `T` podporuje `=` operátor.</span><span class="sxs-lookup"><span data-stu-id="deb55-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="deb55-132">Můžete otestovat `findElement` postup následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="deb55-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="deb55-133">Podle předchozích volání `MsgBox` zobrazit "0", "1" a "-1" v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="deb55-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb55-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="deb55-134">See Also</span></span>  
 [<span data-ttu-id="deb55-135">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="deb55-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="deb55-136">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="deb55-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="deb55-137">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="deb55-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="deb55-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="deb55-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="deb55-139">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="deb55-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="deb55-140">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="deb55-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="deb55-141">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="deb55-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
