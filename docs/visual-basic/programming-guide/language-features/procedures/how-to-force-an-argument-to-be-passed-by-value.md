---
title: 'Postupy: Vynucení předání argumentu podle hodnoty'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 8261d126f988bdcf05b4a2af3106b38717e46bc8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344520"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="93de0-102">Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93de0-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="93de0-103">The procedure declaration determines the passing mechanism.</span><span class="sxs-lookup"><span data-stu-id="93de0-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="93de0-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span><span class="sxs-lookup"><span data-stu-id="93de0-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="93de0-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="93de0-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="93de0-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span><span class="sxs-lookup"><span data-stu-id="93de0-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="93de0-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span><span class="sxs-lookup"><span data-stu-id="93de0-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="93de0-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span><span class="sxs-lookup"><span data-stu-id="93de0-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="93de0-109">To force an argument to be passed by value</span><span class="sxs-lookup"><span data-stu-id="93de0-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="93de0-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span><span class="sxs-lookup"><span data-stu-id="93de0-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="93de0-111">Visual Basic already expects to pass the argument by value.</span><span class="sxs-lookup"><span data-stu-id="93de0-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="93de0-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span><span class="sxs-lookup"><span data-stu-id="93de0-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93de0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="93de0-113">Example</span></span>  
 <span data-ttu-id="93de0-114">The following example overrides a `ByRef` parameter declaration.</span><span class="sxs-lookup"><span data-stu-id="93de0-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="93de0-115">In the call that forces `ByVal`, note the two levels of parentheses.</span><span class="sxs-lookup"><span data-stu-id="93de0-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="93de0-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span><span class="sxs-lookup"><span data-stu-id="93de0-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="93de0-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span><span class="sxs-lookup"><span data-stu-id="93de0-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93de0-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="93de0-118">Compiling the Code</span></span>  
 <span data-ttu-id="93de0-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span><span class="sxs-lookup"><span data-stu-id="93de0-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="93de0-120">The default in Visual Basic is to pass arguments by value.</span><span class="sxs-lookup"><span data-stu-id="93de0-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="93de0-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span><span class="sxs-lookup"><span data-stu-id="93de0-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="93de0-122">This makes your code easier to read.</span><span class="sxs-lookup"><span data-stu-id="93de0-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="93de0-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="93de0-123">Robust Programming</span></span>  
 <span data-ttu-id="93de0-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="93de0-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="93de0-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span><span class="sxs-lookup"><span data-stu-id="93de0-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="93de0-126">This might produce unexpected results in the calling code.</span><span class="sxs-lookup"><span data-stu-id="93de0-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="93de0-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="93de0-127">.NET Framework Security</span></span>  
 <span data-ttu-id="93de0-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="93de0-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="93de0-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span><span class="sxs-lookup"><span data-stu-id="93de0-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93de0-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93de0-130">See also</span></span>

- [<span data-ttu-id="93de0-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="93de0-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="93de0-132">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="93de0-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="93de0-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="93de0-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="93de0-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="93de0-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="93de0-135">Rozdíly mezi upravitelnými a neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="93de0-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="93de0-136">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="93de0-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="93de0-137">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="93de0-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="93de0-138">Postupy: Ochrana argumentu procedury před změnami hodnoty</span><span class="sxs-lookup"><span data-stu-id="93de0-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="93de0-139">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="93de0-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="93de0-140">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="93de0-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
