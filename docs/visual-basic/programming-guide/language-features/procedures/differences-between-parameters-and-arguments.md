---
title: "Rozdíly mezi parametry a argumenty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="39619-102">Rozdíly mezi parametry a argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39619-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="39619-103">Ve většině případů musí mít procedury některé informace o v případech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="39619-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="39619-104">Procedury, která provádí opakovaných nebo sdíleného úlohy používá různé informace pro každé volání.</span><span class="sxs-lookup"><span data-stu-id="39619-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="39619-105">Tyto informace se skládá z proměnné, konstanty a výrazy, které se předávají k postupu při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="39619-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="39619-106">Tyto informace k postupu komunikovat, postup definuje *parametr*, a předává volání kód *argument* tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="39619-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="39619-107">Si můžete představit jako prostor parkovací parametr a argument jako automobilu.</span><span class="sxs-lookup"><span data-stu-id="39619-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="39619-108">Stejně jako různých automobilů tedy vůbec v prostoru parkovací v různou dobu, volající kód lze předat jiné argument stejný parametr pokaždé, když to volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="39619-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="39619-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="39619-109">Parameters</span></span>  
 <span data-ttu-id="39619-110">A *parametr* představuje hodnotu, která procedura očekává, že vám při volání ho.</span><span class="sxs-lookup"><span data-stu-id="39619-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="39619-111">Deklarace procedury definuje jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="39619-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="39619-112">Když definujete `Function` nebo `Sub` postupu zadáte *seznam parametrů* v závorkách bezprostředně za název procedury.</span><span class="sxs-lookup"><span data-stu-id="39619-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="39619-113">Pro každý parametr zadejte název, datový typ a mechanismus předávání ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="39619-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="39619-114">Můžete také určit, že je volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="39619-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="39619-115">To znamená, že volající kód nemá předat hodnotu pro ni.</span><span class="sxs-lookup"><span data-stu-id="39619-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="39619-116">Název každého parametru slouží jako *místní proměnné* v postupu.</span><span class="sxs-lookup"><span data-stu-id="39619-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="39619-117">Název parametru použít stejným způsobem jako použijete jakoukoli jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="39619-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="39619-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="39619-118">Arguments</span></span>  
 <span data-ttu-id="39619-119">*Argument* představuje hodnotu, kterou předáte parametr postupu při voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="39619-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="39619-120">Volání kódu poskytuje argumenty, když se volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="39619-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="39619-121">Při volání `Function` nebo `Sub` postupu zahrnete *seznam argumentů* v závorkách bezprostředně za název procedury.</span><span class="sxs-lookup"><span data-stu-id="39619-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="39619-122">Každý argument odpovídá parametru ve stejné pozici v seznamu.</span><span class="sxs-lookup"><span data-stu-id="39619-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="39619-123">Na rozdíl od definici parametru argumenty nemají názvy.</span><span class="sxs-lookup"><span data-stu-id="39619-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="39619-124">Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstanty a literály.</span><span class="sxs-lookup"><span data-stu-id="39619-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="39619-125">Datový typ vyhodnocený výraz by měl odpovídat obvykle datového typu definovaného pro odpovídající parametr a v každém případě musí být převoditelná na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="39619-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39619-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="39619-126">See Also</span></span>  
 [<span data-ttu-id="39619-127">Postupy</span><span class="sxs-lookup"><span data-stu-id="39619-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="39619-128">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="39619-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="39619-129">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="39619-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="39619-130">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="39619-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="39619-131">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="39619-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="39619-132">Postupy: definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="39619-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="39619-133">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="39619-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="39619-134">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="39619-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="39619-135">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="39619-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="39619-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="39619-136">Procedure Overloading</span></span>](./procedure-overloading.md)
