---
title: Rozdíly mezi parametry a argumenty (Visual Basic)
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
ms.openlocfilehash: ec7c92975bc056fd740033b602b15cd1611c44d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694032"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="00a90-102">Rozdíly mezi parametry a argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00a90-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="00a90-103">Ve většině případů procedury musí mít některé informace o okolnostech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="00a90-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="00a90-104">Postup, který provádí úlohy opakovaných nebo sdílené používá různé informace pro každé volání.</span><span class="sxs-lookup"><span data-stu-id="00a90-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="00a90-105">Tyto informace se skládá z proměnné, konstanty a výrazy, které předáváte k postupu při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="00a90-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="00a90-106">Sdělovat tyto informace k postupu podle postupu definuje *parametr*, a předá volající kód *argument* tomuto parametru.</span><span class="sxs-lookup"><span data-stu-id="00a90-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="00a90-107">Si můžete představit jako parkovací místo parametru a argument jako automobilu.</span><span class="sxs-lookup"><span data-stu-id="00a90-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="00a90-108">Stejně jako různých automobilů můžete park v prostoru parkovací v různých časech, volající kód lze předat jako argument jiné stejný parametr pokaždé, když se volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="00a90-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="00a90-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="00a90-109">Parameters</span></span>  
 <span data-ttu-id="00a90-110">A *parametr* představuje hodnotu, která procedura očekává, že budete při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="00a90-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="00a90-111">Podle postupu prohlášení definuje jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="00a90-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="00a90-112">Při definování `Function` nebo `Sub` postupu zadáte *seznam parametrů* v závorkách bezprostředně za název procedury.</span><span class="sxs-lookup"><span data-stu-id="00a90-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="00a90-113">Pro každý parametr, můžete zadat název, datový typ a mechanismus pro předávání ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="00a90-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="00a90-114">Můžete také určit, že parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="00a90-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="00a90-115">To znamená, že volající kód nemá předat hodnotu pro něj.</span><span class="sxs-lookup"><span data-stu-id="00a90-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="00a90-116">Název každého parametru slouží jako *lokální proměnná* v postupu.</span><span class="sxs-lookup"><span data-stu-id="00a90-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="00a90-117">Název parametru použít stejným způsobem můžete použít jakoukoli jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="00a90-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="00a90-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="00a90-118">Arguments</span></span>  
 <span data-ttu-id="00a90-119">*Argument* představuje hodnotu, kterou můžete předat parametr procedury při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="00a90-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="00a90-120">Volající kód poskytuje argumenty při volání postup.</span><span class="sxs-lookup"><span data-stu-id="00a90-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="00a90-121">Při volání `Function` nebo `Sub` postupu zahrnete *seznam argumentů* v závorkách bezprostředně za název procedury.</span><span class="sxs-lookup"><span data-stu-id="00a90-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="00a90-122">Každý argument odpovídající parametru na stejné pozici v seznamu.</span><span class="sxs-lookup"><span data-stu-id="00a90-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="00a90-123">Na rozdíl od definice parametru argumenty nemají názvy.</span><span class="sxs-lookup"><span data-stu-id="00a90-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="00a90-124">Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstant a literály.</span><span class="sxs-lookup"><span data-stu-id="00a90-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="00a90-125">Datový typ vyhodnocený výraz by měl odpovídat obvykle datového typu definovaného u odpovídajícího parametru a v každém případě musí být převoditelný na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="00a90-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a90-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00a90-126">See also</span></span>
- [<span data-ttu-id="00a90-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="00a90-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="00a90-128">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="00a90-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="00a90-129">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="00a90-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="00a90-130">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="00a90-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="00a90-131">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="00a90-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="00a90-132">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="00a90-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="00a90-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="00a90-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="00a90-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="00a90-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="00a90-135">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="00a90-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="00a90-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="00a90-136">Procedure Overloading</span></span>](./procedure-overloading.md)
