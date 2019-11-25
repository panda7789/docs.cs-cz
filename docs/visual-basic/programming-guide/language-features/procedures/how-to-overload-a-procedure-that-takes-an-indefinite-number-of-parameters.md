---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.'
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
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345840"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="43ad9-102">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="43ad9-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="43ad9-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span><span class="sxs-lookup"><span data-stu-id="43ad9-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="43ad9-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="43ad9-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="43ad9-105">To overload a procedure that takes a variable number of parameters</span><span class="sxs-lookup"><span data-stu-id="43ad9-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="43ad9-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span><span class="sxs-lookup"><span data-stu-id="43ad9-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="43ad9-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="43ad9-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="43ad9-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span><span class="sxs-lookup"><span data-stu-id="43ad9-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="43ad9-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span><span class="sxs-lookup"><span data-stu-id="43ad9-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="43ad9-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span><span class="sxs-lookup"><span data-stu-id="43ad9-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="43ad9-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span><span class="sxs-lookup"><span data-stu-id="43ad9-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="43ad9-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="43ad9-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="43ad9-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span><span class="sxs-lookup"><span data-stu-id="43ad9-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="43ad9-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="43ad9-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43ad9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="43ad9-115">Example</span></span>  
 <span data-ttu-id="43ad9-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span><span class="sxs-lookup"><span data-stu-id="43ad9-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="43ad9-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span><span class="sxs-lookup"><span data-stu-id="43ad9-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="43ad9-118">However, you can use the signatures of the other implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="43ad9-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="43ad9-119">The following declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="43ad9-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="43ad9-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span><span class="sxs-lookup"><span data-stu-id="43ad9-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="43ad9-121">Visual Basic passes control to the version matching the calling argument list.</span><span class="sxs-lookup"><span data-stu-id="43ad9-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43ad9-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="43ad9-122">Compiling the Code</span></span>  
 <span data-ttu-id="43ad9-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span><span class="sxs-lookup"><span data-stu-id="43ad9-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="43ad9-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="43ad9-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="43ad9-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43ad9-125">.NET Framework Security</span></span>  
 <span data-ttu-id="43ad9-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span><span class="sxs-lookup"><span data-stu-id="43ad9-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="43ad9-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span><span class="sxs-lookup"><span data-stu-id="43ad9-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ad9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43ad9-128">See also</span></span>

- [<span data-ttu-id="43ad9-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="43ad9-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="43ad9-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="43ad9-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="43ad9-131">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="43ad9-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="43ad9-132">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="43ad9-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="43ad9-133">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="43ad9-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="43ad9-134">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="43ad9-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="43ad9-135">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="43ad9-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="43ad9-136">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="43ad9-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="43ad9-137">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="43ad9-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="43ad9-138">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="43ad9-138">Overload Resolution</span></span>](./overload-resolution.md)
