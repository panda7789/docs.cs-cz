---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 54a8a65db6e1f532cd21e36eeb5b98670efd4289
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506391"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="c8f2b-102">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8f2b-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="c8f2b-103">Pokud má procedura [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nelze definovat přetížené verze, přičemž jednorozměrné pole pro pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="c8f2b-104">Další informace najdete v tématu "Implicitní přetížení pro parametrem ParamArray" [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c8f2b-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="c8f2b-105">Přetížení procedury, která přijímá proměnný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="c8f2b-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="c8f2b-106">Ověření, že postup a výhody logiku kódu z volání přetížené verze víc než `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="c8f2b-107">Viz "Přetížení a ParamArrays" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c8f2b-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="c8f2b-108">Určení, která čísla zadané hodnoty by měla přijímat podle postupu v části proměnných ze seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="c8f2b-109">To může zahrnovat i v případě žádnou hodnotu a může obsahovat velikost písmen jednoho jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="c8f2b-110">Pro každý přijatelné počet zadaných hodnot, zápisu `Sub` nebo `Function` příkazu deklarace, která definuje odpovídající seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="c8f2b-111">Nepoužívejte buď `Optional` nebo `ParamArray` – klíčové slovo v této verzi přetížená.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="c8f2b-112">V deklaraci, předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="c8f2b-113">Po deklaraci psát kód postup, který by se měl spustit, když volající kód poskytuje hodnoty pro tato deklarace seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="c8f2b-114">Ukončit každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8f2b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8f2b-115">Example</span></span>  
 <span data-ttu-id="c8f2b-116">Následující příklad ukazuje definované pomocí procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr a ekvivalentní sadu přetížené procedury.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="c8f2b-117">Tento postup se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="c8f2b-118">Můžete však použít podpisy implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="c8f2b-119">Následující deklarace ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="c8f2b-120">Není potřeba otestovat, zda volající kód zadali jednu nebo více hodnot pro kód v přetížené verze `ParamArray` parametr, nebo pokud ano, kolik.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="c8f2b-121">Visual Basic předá řízení verzi, která odpovídá seznamu argumentů volání.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8f2b-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c8f2b-122">Compiling the Code</span></span>  
 <span data-ttu-id="c8f2b-123">Protože procedura se `ParamArray` parametr je ekvivalentní k sadě přetížené verze, nejde přetížit tento postup se seznamem parametrů odpovídá některé z těchto implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="c8f2b-124">Další informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c8f2b-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c8f2b-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c8f2b-125">.NET Framework Security</span></span>  
 <span data-ttu-id="c8f2b-126">Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="c8f2b-127">Pokud souhlasíte s polem parametrů, by měl test pro délku pole do něho předaný volající kód a proveďte příslušné kroky, pokud je příliš velký pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c8f2b-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f2b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8f2b-128">See also</span></span>
- [<span data-ttu-id="c8f2b-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="c8f2b-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c8f2b-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="c8f2b-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c8f2b-131">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="c8f2b-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="c8f2b-132">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="c8f2b-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="c8f2b-133">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="c8f2b-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="c8f2b-134">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="c8f2b-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="c8f2b-135">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="c8f2b-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="c8f2b-136">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="c8f2b-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="c8f2b-137">Postupy: Přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="c8f2b-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="c8f2b-138">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="c8f2b-138">Overload Resolution</span></span>](./overload-resolution.md)
