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
ms.openlocfilehash: 9a88a979a6b46f897e5f04f4481d4a23e245b165
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569460"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="e900c-102">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e900c-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="e900c-103">A *obecný postup*, označované také jako *obecnou metodu*, postup definované s alespoň jedním parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="e900c-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="e900c-104">To umožňuje volajícímu kódu pro datové typy na své požadavky na přizpůsobení pokaždé, když volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="e900c-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="e900c-105">Postup není obecná jednoduše tím, že je definována uvnitř obecnou třídu nebo o obecnou strukturu.</span><span class="sxs-lookup"><span data-stu-id="e900c-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="e900c-106">Je obecný, musí trvat aspoň jeden parametr typu, kromě jakékoliv běžné parametry, které může trvat.</span><span class="sxs-lookup"><span data-stu-id="e900c-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="e900c-107">Obecná třída nebo struktura může obsahovat neobecné postupy a neobecná třída, struktura, nebo modul může obsahovat obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="e900c-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="e900c-108">Obecný postup můžete použít jeho parametry typu jejího seznamu parametrů normální, v jejím návratovém typu, pokud má kód z nich a v její postup.</span><span class="sxs-lookup"><span data-stu-id="e900c-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="e900c-109">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="e900c-109">Type Inference</span></span>  
 <span data-ttu-id="e900c-110">Obecný postup lze volat bez poskytnutí vůbec žádné argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="e900c-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="e900c-111">Při volání tímto způsobem, kompilátor se pokusí určit příslušné datové typy k předávání argumentů podle postupu.</span><span class="sxs-lookup"><span data-stu-id="e900c-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="e900c-112">Tento postup se nazývá *odvození typu*.</span><span class="sxs-lookup"><span data-stu-id="e900c-112">This is called *type inference*.</span></span> <span data-ttu-id="e900c-113">Následující kód ukazuje volání ve kterém kompilátor odvodí, že by měla předat typ `String` na parametr typu `t`.</span><span class="sxs-lookup"><span data-stu-id="e900c-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="e900c-114">Pokud kompilátor nemůže odvodit argumenty typu z kontextu volání, hlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="e900c-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="e900c-115">Jednou z možných příčin takové chyby je řadit nesoulad pole.</span><span class="sxs-lookup"><span data-stu-id="e900c-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="e900c-116">Předpokládejme například, že definovat normální parametr jako pole parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e900c-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="e900c-117">Při volání obecný postup poskytuje celou řadu jiné hodnosti (počet rozměrů), neshoda způsobí, že odvození typu selhání.</span><span class="sxs-lookup"><span data-stu-id="e900c-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="e900c-118">Následující kód ukazuje volání v které dvourozměrné pole se předává procedury, která očekává, že jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="e900c-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="e900c-119">Odvození typu proměnné lze vyvolat pouze vynecháním všechny argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="e900c-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="e900c-120">Pokud zadáte jeden argument typu, je třeba zadat všechny.</span><span class="sxs-lookup"><span data-stu-id="e900c-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="e900c-121">Odvození typu je podporován pouze pro obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="e900c-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="e900c-122">Nejde vyvolat odvození typu na obecné třídy, struktury, rozhraní nebo delegátů.</span><span class="sxs-lookup"><span data-stu-id="e900c-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e900c-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e900c-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e900c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e900c-124">Description</span></span>  
 <span data-ttu-id="e900c-125">Následující příklad definuje obecný `Function` procedury k nalezení konkrétní element v poli.</span><span class="sxs-lookup"><span data-stu-id="e900c-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="e900c-126">Definuje jeden parametr typu a použije je k vytvoření dva parametry v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="e900c-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e900c-127">Kód</span><span class="sxs-lookup"><span data-stu-id="e900c-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="e900c-128">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e900c-128">Comments</span></span>  
 <span data-ttu-id="e900c-129">V předchozím příkladu vyžaduje schopnost porovnávat `searchValue` proti každý prvek `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="e900c-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="e900c-130">Pokud chcete zajistit tuto možnost, omezuje parametr typu `T` k implementaci <xref:System.IComparable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e900c-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="e900c-131">Tento kód použije <xref:System.IComparable%601.CompareTo%2A> metoda místo `=` operátoru, protože není k dispozici žádná záruka, že argument typu zadaný pro `T` podporuje `=` operátor.</span><span class="sxs-lookup"><span data-stu-id="e900c-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="e900c-132">Můžete testovat `findElement` procedury s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="e900c-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="e900c-133">Předchozí volání `MsgBox` zobrazení "0", "1" a "-1" v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e900c-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e900c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e900c-134">See Also</span></span>  
 [<span data-ttu-id="e900c-135">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e900c-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="e900c-136">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="e900c-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="e900c-137">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="e900c-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="e900c-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="e900c-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="e900c-139">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="e900c-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e900c-140">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="e900c-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="e900c-141">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="e900c-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
