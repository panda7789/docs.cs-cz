---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).'
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
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651489"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="ccab1-102">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ccab1-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="ccab1-103">Pokud má procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nelze definovat přetížené verze trvá jednorozměrné pole pro parametr pole.</span><span class="sxs-lookup"><span data-stu-id="ccab1-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="ccab1-104">Další informace najdete v tématu "Implicitní přetížení pro ParamArray parametr" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ccab1-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="ccab1-105">Chcete-li přetížení procedury, která přebírá proměnné počet parametrů</span><span class="sxs-lookup"><span data-stu-id="ccab1-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="ccab1-106">Zjistí, že postup a volání výhody logiku kód z přetížený verze více než `ParamArray` parametr.</span><span class="sxs-lookup"><span data-stu-id="ccab1-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="ccab1-107">Najdete v části "Přetížení a ParamArrays" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ccab1-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="ccab1-108">Určete, které počtu zadaných hodnot postupu by měl přijmout v proměnné části Seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="ccab1-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="ccab1-109">To může zahrnovat i v případě žádná hodnota, a v případě jedné jednorozměrné pole může obsahovat.</span><span class="sxs-lookup"><span data-stu-id="ccab1-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="ccab1-110">Pro každý přijatelné počet zadaných hodnot zápisu `Sub` nebo `Function` deklarace příkaz, který definuje odpovídající seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="ccab1-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="ccab1-111">Nepoužívejte buď `Optional` nebo `ParamArray` – klíčové slovo v této verzi přetížená.</span><span class="sxs-lookup"><span data-stu-id="ccab1-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="ccab1-112">V každé deklaraci předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ccab1-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="ccab1-113">Následující každá deklarace psát kód postup, který by měl spustit, když kód volání poskytuje hodnoty pro seznam parametrů tohoto prohlášení.</span><span class="sxs-lookup"><span data-stu-id="ccab1-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="ccab1-114">Terminate – každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ccab1-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccab1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccab1-115">Example</span></span>  
 <span data-ttu-id="ccab1-116">Následující příklad ukazuje postup definovaný s [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr a potom ekvivalentní sadu přetížené procedury.</span><span class="sxs-lookup"><span data-stu-id="ccab1-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="ccab1-117">Tento postup se seznam parametrů, která přebírá jednorozměrné pole pro parametr pole nelze přetížení.</span><span class="sxs-lookup"><span data-stu-id="ccab1-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="ccab1-118">Můžete však použít signatur implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="ccab1-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="ccab1-119">Následující deklarace znázornění.</span><span class="sxs-lookup"><span data-stu-id="ccab1-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="ccab1-120">Kód v přetížené verze nemá k ověření, zda jeden nebo více hodnot pro zadaný kód volání `ParamArray` parametr, nebo pokud ano, kolik.</span><span class="sxs-lookup"><span data-stu-id="ccab1-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="ccab1-121">Visual Basic předá ovládacího prvku na verzi odpovídající volání seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="ccab1-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccab1-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ccab1-122">Compiling the Code</span></span>  
 <span data-ttu-id="ccab1-123">Protože procedura se `ParamArray` parametr je ekvivalentní sadu přetížené verze, tento postup nelze přetížení se seznamem parametr odpovídající některé z těchto implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="ccab1-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="ccab1-124">Další informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ccab1-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ccab1-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ccab1-125">.NET Framework Security</span></span>  
 <span data-ttu-id="ccab1-126">Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccab1-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="ccab1-127">Pokud přijmete pole parametrů, doporučujeme otestovat délka pole Kód volání do ní předán a proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ccab1-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccab1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccab1-128">See Also</span></span>  
 [<span data-ttu-id="ccab1-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="ccab1-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ccab1-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="ccab1-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ccab1-131">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="ccab1-131">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="ccab1-132">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="ccab1-132">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="ccab1-133">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="ccab1-133">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="ccab1-134">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="ccab1-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="ccab1-135">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="ccab1-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="ccab1-136">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="ccab1-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="ccab1-137">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="ccab1-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="ccab1-138">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="ccab1-138">Overload Resolution</span></span>](./overload-resolution.md)
