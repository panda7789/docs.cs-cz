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
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403353"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="d93b5-102">Rozdíly mezi parametry a argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d93b5-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="d93b5-103">Ve většině případů musí mít procedura nějaké informace o okolnostech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="d93b5-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="d93b5-104">Postup, který provádí opakované nebo sdílené úkoly, používá pro každé volání jiné informace.</span><span class="sxs-lookup"><span data-stu-id="d93b5-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="d93b5-105">Tyto informace se skládají z proměnných, konstant a výrazů, které procedury předáte při volání.</span><span class="sxs-lookup"><span data-stu-id="d93b5-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="d93b5-106">Chcete-li sdělit tyto informace proceduře, procedura definuje *parametr*a volající kód předá *argument* tomuto parametru.</span><span class="sxs-lookup"><span data-stu-id="d93b5-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="d93b5-107">Parametr si můžete představit jako místo pro parkování a argument jako automobil.</span><span class="sxs-lookup"><span data-stu-id="d93b5-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="d93b5-108">Stejně jako různé Automobiles mohou být v parkovacím prostoru v různých časech, volající kód může předat jiný argument stejnému parametru pokaždé, když volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="d93b5-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="d93b5-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="d93b5-109">Parameters</span></span>  
 <span data-ttu-id="d93b5-110">*Parametr* představuje hodnotu, kterou procedura očekává, že bude při volání předána.</span><span class="sxs-lookup"><span data-stu-id="d93b5-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="d93b5-111">Deklarace procedury definuje její parametry.</span><span class="sxs-lookup"><span data-stu-id="d93b5-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="d93b5-112">Při definování `Function` `Sub` procedury nebo zadejte *seznam parametrů* v závorkách hned za názvem procedury.</span><span class="sxs-lookup"><span data-stu-id="d93b5-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="d93b5-113">Pro každý parametr určíte název, datový typ a mechanismus předávání ([ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="d93b5-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="d93b5-114">Můžete také indikovat, že parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="d93b5-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="d93b5-115">To znamená, že volající kód nemusí pro něj předat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d93b5-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="d93b5-116">Název každého parametru slouží jako *místní proměnná* v proceduře.</span><span class="sxs-lookup"><span data-stu-id="d93b5-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="d93b5-117">Název parametru použijete stejným způsobem jako jakoukoli jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d93b5-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="d93b5-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="d93b5-118">Arguments</span></span>  
 <span data-ttu-id="d93b5-119">*Argument* představuje hodnotu, která je předána parametru procedury při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="d93b5-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="d93b5-120">Volající kód dodává argumenty při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="d93b5-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="d93b5-121">Při volání `Function` `Sub` procedury nebo můžete do závorek zahrnout *seznam argumentů* hned za názvem procedury.</span><span class="sxs-lookup"><span data-stu-id="d93b5-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="d93b5-122">Každý argument odpovídá parametru ve stejné pozici v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d93b5-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="d93b5-123">Na rozdíl od definice parametru argumenty nemají názvy.</span><span class="sxs-lookup"><span data-stu-id="d93b5-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="d93b5-124">Každý argument je výraz, který může obsahovat nula nebo více proměnných, konstant a literálů.</span><span class="sxs-lookup"><span data-stu-id="d93b5-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="d93b5-125">Datový typ vyhodnoceného výrazu by měl obvykle odpovídat datovému typu definovanému pro příslušný parametr a v každém případě musí být převoditelné na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="d93b5-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93b5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d93b5-126">See also</span></span>

- [<span data-ttu-id="d93b5-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="d93b5-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d93b5-128">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="d93b5-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d93b5-129">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="d93b5-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d93b5-130">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d93b5-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d93b5-131">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="d93b5-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d93b5-132">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="d93b5-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="d93b5-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="d93b5-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d93b5-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="d93b5-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d93b5-135">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="d93b5-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="d93b5-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="d93b5-136">Procedure Overloading</span></span>](./procedure-overloading.md)
