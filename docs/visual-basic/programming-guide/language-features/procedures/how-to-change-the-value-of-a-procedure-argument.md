---
title: 'Postupy: Změna hodnoty argumentu procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: deac87ca4690990a4d00f63d0ea9b843c3f9a9c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344479"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="5e568-102">Postupy: Změna hodnoty argumentu procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e568-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="5e568-103">Když zavoláte proceduru, každý argument, který zadáte, odpovídá jednomu z parametrů definovaných v proceduře.</span><span class="sxs-lookup"><span data-stu-id="5e568-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="5e568-104">V některých případech kód procedury může změnit hodnotu podkladové hodnoty argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e568-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="5e568-105">V jiných případech může procedura změnit pouze svou místní kopii argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e568-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="5e568-106">Když zavoláte proceduru, Visual Basic vytvoří místní kopii každého argumentu, který je předaný metodě [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="5e568-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="5e568-107">Pro každý argument předaný [parametr ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)Visual Basic poskytne kód procedury přímý odkaz na programovací element podkladové argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e568-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="5e568-108">Pokud podkladový prvek v kódu volání je upravitelný prvek a argument je předán `ByRef`, kód procedury může použít přímý odkaz pro změnu hodnoty prvku v kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="5e568-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="5e568-109">Změna základní hodnoty</span><span class="sxs-lookup"><span data-stu-id="5e568-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="5e568-110">Změna základní hodnoty argumentu procedury v kódu volání</span><span class="sxs-lookup"><span data-stu-id="5e568-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="5e568-111">V deklaraci procedury zadejte typ [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pro parametr odpovídající argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e568-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="5e568-112">V kódu volajícího předejte jako argument upravitelný programový prvek.</span><span class="sxs-lookup"><span data-stu-id="5e568-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="5e568-113">V kódu volajícího nemusíte v seznamu argumentů uzavřít argument do závorek.</span><span class="sxs-lookup"><span data-stu-id="5e568-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="5e568-114">V kódu procedury použijte název parametru pro přiřazení hodnoty k základnímu prvku v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e568-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="5e568-115">Ukázku najdete v níže uvedeném příkladu.</span><span class="sxs-lookup"><span data-stu-id="5e568-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="5e568-116">Změna místních kopií</span><span class="sxs-lookup"><span data-stu-id="5e568-116">Changing Local Copies</span></span>  
 <span data-ttu-id="5e568-117">Pokud podkladový prvek v kódu volání je neupravitelný prvek, nebo pokud je argument předán `ByVal`, procedura nemůže změnit jeho hodnotu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e568-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="5e568-118">Procedura však může změnit svou místní kopii takového argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e568-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="5e568-119">Chcete-li změnit kopii argumentu procedury v kódu procedury</span><span class="sxs-lookup"><span data-stu-id="5e568-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="5e568-120">V deklaraci procedury zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pro parametr odpovídající argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e568-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="5e568-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5e568-121">-or-</span></span>  
  
     <span data-ttu-id="5e568-122">V kódu volajícího uveďte argument do závorek v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="5e568-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="5e568-123">To vynutí Visual Basic předat argument podle hodnoty, a to i v případě, že odpovídající parametr určuje `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="5e568-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="5e568-124">V kódu procedury použijte název parametru k přiřazení hodnoty místní kopii argumentu.</span><span class="sxs-lookup"><span data-stu-id="5e568-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="5e568-125">Podkladová hodnota v kódu volajícího není změněna.</span><span class="sxs-lookup"><span data-stu-id="5e568-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e568-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e568-126">Example</span></span>  
 <span data-ttu-id="5e568-127">Následující příklad ukazuje dva postupy, které přebírají proměnnou pole a pracují s jejími prvky.</span><span class="sxs-lookup"><span data-stu-id="5e568-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="5e568-128">Postup `increase` jednoduše přidá jeden do každého prvku.</span><span class="sxs-lookup"><span data-stu-id="5e568-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="5e568-129">`replace` procedura přiřadí parametr novému poli `a()` a poté přidá jeden do každého prvku.</span><span class="sxs-lookup"><span data-stu-id="5e568-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="5e568-130">První `MsgBox` volání zobrazí "po zvýšení (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="5e568-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="5e568-131">Protože `n` pole je odkazový typ, `replace` mohou změnit jeho členy, i když je mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="5e568-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="5e568-132">Druhý `MsgBox` volání zobrazí "po nahrazení (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="5e568-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="5e568-133">Vzhledem k tomu, že `n` je předán `ByRef`, `replace` může změnit proměnnou `n` ve volání kódu a přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="5e568-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="5e568-134">Vzhledem k tomu, že `n` je odkazový typ, `replace` mohou také měnit jeho členy.</span><span class="sxs-lookup"><span data-stu-id="5e568-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="5e568-135">Můžete zabránit postupu v úpravě proměnné samotné v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="5e568-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="5e568-136">Viz [Postupy: Ochrana argumentu procedury proti změnám hodnot](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="5e568-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="5e568-137">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5e568-137">Compile the code</span></span>  
 <span data-ttu-id="5e568-138">Pokud předáte proměnnou odkazem, je nutné použít klíčové slovo `ByRef` k určení tohoto mechanismu.</span><span class="sxs-lookup"><span data-stu-id="5e568-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="5e568-139">Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5e568-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="5e568-140">Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) s každým deklarovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="5e568-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="5e568-141">To usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="5e568-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5e568-142">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e568-142">.NET Framework Security</span></span>  
 <span data-ttu-id="5e568-143">V případě, že je možné změnit hodnotu podkladového typu argumentu v volajícím kódu, je vždy potenciálním rizikem.</span><span class="sxs-lookup"><span data-stu-id="5e568-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="5e568-144">Ujistěte se, že jste očekávali, že tato hodnota se má změnit, a je připravená ji před použitím ověřit.</span><span class="sxs-lookup"><span data-stu-id="5e568-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e568-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e568-145">See also</span></span>

- [<span data-ttu-id="5e568-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e568-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5e568-147">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5e568-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5e568-148">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="5e568-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="5e568-149">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="5e568-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="5e568-150">Rozdíly mezi upravitelnými a neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="5e568-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="5e568-151">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="5e568-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="5e568-152">Postupy: Ochrana argumentu procedury před změnami hodnoty</span><span class="sxs-lookup"><span data-stu-id="5e568-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="5e568-153">Postupy: Vynucení předání argumentu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="5e568-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="5e568-154">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="5e568-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="5e568-155">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="5e568-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
