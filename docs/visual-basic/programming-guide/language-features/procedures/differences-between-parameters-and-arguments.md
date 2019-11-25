---
title: Rozdíly mezi parametry a argumenty
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341378"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="a3096-102">Rozdíly mezi parametry a argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3096-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="a3096-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span><span class="sxs-lookup"><span data-stu-id="a3096-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="a3096-104">A procedure that performs repeated or shared tasks uses different information for each call.</span><span class="sxs-lookup"><span data-stu-id="a3096-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="a3096-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span><span class="sxs-lookup"><span data-stu-id="a3096-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="a3096-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span><span class="sxs-lookup"><span data-stu-id="a3096-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="a3096-107">You can think of the parameter as a parking space and the argument as an automobile.</span><span class="sxs-lookup"><span data-stu-id="a3096-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="a3096-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="a3096-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="a3096-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3096-109">Parameters</span></span>  
 <span data-ttu-id="a3096-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span><span class="sxs-lookup"><span data-stu-id="a3096-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="a3096-111">The procedure's declaration defines its parameters.</span><span class="sxs-lookup"><span data-stu-id="a3096-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="a3096-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span><span class="sxs-lookup"><span data-stu-id="a3096-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="a3096-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="a3096-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="a3096-114">You can also indicate that a parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="a3096-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="a3096-115">This means that the calling code does not have to pass a value for it.</span><span class="sxs-lookup"><span data-stu-id="a3096-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="a3096-116">The name of each parameter serves as a *local variable* in the procedure.</span><span class="sxs-lookup"><span data-stu-id="a3096-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="a3096-117">You use the parameter name the same way you use any other variable.</span><span class="sxs-lookup"><span data-stu-id="a3096-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="a3096-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="a3096-118">Arguments</span></span>  
 <span data-ttu-id="a3096-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span><span class="sxs-lookup"><span data-stu-id="a3096-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="a3096-120">The calling code supplies the arguments when it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="a3096-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="a3096-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span><span class="sxs-lookup"><span data-stu-id="a3096-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="a3096-122">Each argument corresponds to the parameter in the same position in the list.</span><span class="sxs-lookup"><span data-stu-id="a3096-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="a3096-123">In contrast to parameter definition, arguments do not have names.</span><span class="sxs-lookup"><span data-stu-id="a3096-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="a3096-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span><span class="sxs-lookup"><span data-stu-id="a3096-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="a3096-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span><span class="sxs-lookup"><span data-stu-id="a3096-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3096-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3096-126">See also</span></span>

- [<span data-ttu-id="a3096-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="a3096-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a3096-128">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="a3096-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a3096-129">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="a3096-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a3096-130">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a3096-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a3096-131">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a3096-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a3096-132">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="a3096-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="a3096-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="a3096-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="a3096-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="a3096-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a3096-135">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="a3096-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="a3096-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="a3096-136">Procedure Overloading</span></span>](./procedure-overloading.md)
