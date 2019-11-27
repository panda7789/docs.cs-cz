---
title: Obecné procedury
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
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350086"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="e2c43-102">Obecné procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2c43-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="e2c43-103">*Obecný postup*, označovaný také jako *Obecná metoda*, je procedura definovaná s alespoň jedním parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="e2c43-104">To umožňuje volajícímu kódu přizpůsobit datové typy na požadavky pokaždé, když volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="e2c43-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="e2c43-105">Procedura není obecná pouhým definováním v obecné třídě nebo obecné struktuře.</span><span class="sxs-lookup"><span data-stu-id="e2c43-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="e2c43-106">Aby bylo možné obecné, procedura musí kromě všech normálních parametrů, které může trvat, obsahovat alespoň jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="e2c43-107">Obecná třída nebo struktura může obsahovat neobecné postupy a neobecnou třídu, strukturu nebo modul může obsahovat obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="e2c43-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="e2c43-108">Obecný postup může použít jeho parametry typu v seznamu normálních parametrů, v jeho návratovém typu, pokud má jednu, a v kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="e2c43-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="e2c43-109">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="e2c43-109">Type Inference</span></span>  
 <span data-ttu-id="e2c43-110">Můžete zavolat obecný postup bez nutnosti zadávat žádné argumenty typu vůbec.</span><span class="sxs-lookup"><span data-stu-id="e2c43-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="e2c43-111">Pokud je zavoláte tímto způsobem, kompilátor se pokusí určit vhodné datové typy, které mají být předávány do argumentů typu procedury.</span><span class="sxs-lookup"><span data-stu-id="e2c43-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="e2c43-112">Tato metoda se nazývá *odvození typu*.</span><span class="sxs-lookup"><span data-stu-id="e2c43-112">This is called *type inference*.</span></span> <span data-ttu-id="e2c43-113">Následující kód ukazuje volání, ve kterém kompilátor odvodí, že by měl předat typ `String` parametru typu `t`.</span><span class="sxs-lookup"><span data-stu-id="e2c43-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="e2c43-114">Pokud kompilátor nemůže odvodit argumenty typu z kontextu volání, ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="e2c43-115">Jednou z možných příčin této chyby je neshoda pořadí polí.</span><span class="sxs-lookup"><span data-stu-id="e2c43-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="e2c43-116">Předpokládejme například, že definujete normální parametr jako pole parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="e2c43-117">Pokud voláte obecný postup poskytnutí pole odlišného pořadí (počet dimenzí), neshoda způsobuje neúspěch typu odvození typu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="e2c43-118">Následující kód ukazuje volání, ve kterém je dvojrozměrné pole předáno proceduře, který očekává jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="e2c43-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="e2c43-119">Odvození typu lze vyvolat pouze vynecháním všech argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="e2c43-120">Pokud zadáte jeden argument typu, je nutné je zadat.</span><span class="sxs-lookup"><span data-stu-id="e2c43-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="e2c43-121">Odvození typu je podporováno pouze pro obecné procedury.</span><span class="sxs-lookup"><span data-stu-id="e2c43-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="e2c43-122">Nemůžete vyvolat odvození typu u obecných tříd, struktur, rozhraní a delegátů.</span><span class="sxs-lookup"><span data-stu-id="e2c43-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c43-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2c43-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e2c43-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e2c43-124">Description</span></span>  
 <span data-ttu-id="e2c43-125">Následující příklad definuje obecný `Function` postup pro nalezení konkrétního prvku v poli.</span><span class="sxs-lookup"><span data-stu-id="e2c43-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="e2c43-126">Definuje jeden parametr typu a používá ho k sestavení dvou parametrů v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="e2c43-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e2c43-127">Kód</span><span class="sxs-lookup"><span data-stu-id="e2c43-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="e2c43-128">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e2c43-128">Comments</span></span>  
 <span data-ttu-id="e2c43-129">Předchozí příklad vyžaduje možnost porovnat `searchValue` s každým prvkem `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="e2c43-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="e2c43-130">Chcete-li zaručit tuto schopnost, omezuje parametr typu `T` k implementaci rozhraní <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="e2c43-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="e2c43-131">Kód používá metodu <xref:System.IComparable%601.CompareTo%2A> namísto operátoru `=`, protože není nijak zaručeno, že argumentu typu, který je zadán pro `T`, podporuje operátor `=`.</span><span class="sxs-lookup"><span data-stu-id="e2c43-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="e2c43-132">`findElement`ovou proceduru můžete otestovat pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="e2c43-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="e2c43-133">Předchozí volání pro `MsgBox` zobrazují "0", "1" a "-1" v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e2c43-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c43-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2c43-134">See also</span></span>

- [<span data-ttu-id="e2c43-135">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2c43-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e2c43-136">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy</span><span class="sxs-lookup"><span data-stu-id="e2c43-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="e2c43-137">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="e2c43-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="e2c43-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="e2c43-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e2c43-139">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="e2c43-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e2c43-140">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="e2c43-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="e2c43-141">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="e2c43-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
