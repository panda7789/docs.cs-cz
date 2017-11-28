---
title: "Předávání argumentů podle pozice a názvu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="bd876-102">Předávání argumentů podle pozice a názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd876-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="bd876-103">Při volání `Sub` nebo `Function` postupu můžete předat argumenty *umístěním* – v pořadí, ve kterém se zobrazí v postupu pro definici – nebo můžete je předat *podle názvu*, bez ohledem na pozici.</span><span class="sxs-lookup"><span data-stu-id="bd876-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="bd876-104">Při předání argumentu podle názvu, zadáte argument je deklarovaný název následovaný dvojtečkou a symbolem rovná (`:=`), za nímž následují hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="bd876-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="bd876-105">Můžete zadat pojmenované argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bd876-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="bd876-106">Například následující `Sub` procedura používá tři argumenty:</span><span class="sxs-lookup"><span data-stu-id="bd876-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="bd876-107">Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo pomocí kombinaci těchto dvou možností.</span><span class="sxs-lookup"><span data-stu-id="bd876-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="bd876-108">Předávání argumentů podle pozice</span><span class="sxs-lookup"><span data-stu-id="bd876-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="bd876-109">Postup můžete volat `studentInfo` s argumenty předaná pozice a oddělená čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bd876-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="bd876-110">Pokud vynecháte za volitelným argumentem v seznamu poziční argument, musí obsahovat příslušné místo oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="bd876-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="bd876-111">Následující příklad volání `studentInfo` bez `age` argument:</span><span class="sxs-lookup"><span data-stu-id="bd876-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="bd876-112">Předávání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="bd876-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="bd876-113">Alternativně můžete volat `studentInfo` s argumentů předaných podle názvu, také oddělená čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bd876-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="bd876-114">Kombinování argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="bd876-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="bd876-115">Argumentů podle pozice a podle názvu ve volání jedinou proceduru, můžete zadat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bd876-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="bd876-116">V předchozím příkladu, je potřeba k umístění na místo vynechání žádné další čárkami `age` argument, protože `birth` je předán podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bd876-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="bd876-117">Když zadáte argumenty podle směs pozice a názvu, poziční argumenty musí všechny nejdřív se musí uvést.</span><span class="sxs-lookup"><span data-stu-id="bd876-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="bd876-118">Jakmile zadáte argument podle názvu, musí všechny zbývající argumenty být podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bd876-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="bd876-119">Poskytnutí volitelné argumenty podle názvu</span><span class="sxs-lookup"><span data-stu-id="bd876-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="bd876-120">Předávání argumentů podle názvu je obzvláště užitečná při volání procedury, která má více než jeden nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="bd876-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="bd876-121">Pokud zadáte argumenty podle názvu, nemáte použít po sobě jdoucích čárkami k označení chybí poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="bd876-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="bd876-122">Předávání argumentů podle názvu taky usnadní ke sledování které argumenty jsou předávání a ty, které jsou vynechá.</span><span class="sxs-lookup"><span data-stu-id="bd876-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="bd876-123">Omezení pro zadávání argumenty podle názvu</span><span class="sxs-lookup"><span data-stu-id="bd876-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="bd876-124">Nelze předat argumenty podle názvu, abyste nemuseli zadávat povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="bd876-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="bd876-125">Pouze volitelné argumenty, můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="bd876-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="bd876-126">Pole parametrů nelze předat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bd876-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="bd876-127">Je to proto, že při volání postupu zadáte nekonečný počet textový soubor s oddělovači argumenty pro parametr pole a kompilátor nelze přidružit více než jeden argument s jedním názvem.</span><span class="sxs-lookup"><span data-stu-id="bd876-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd876-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd876-128">See Also</span></span>  
 [<span data-ttu-id="bd876-129">Postupy</span><span class="sxs-lookup"><span data-stu-id="bd876-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="bd876-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="bd876-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="bd876-131">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="bd876-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="bd876-132">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="bd876-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="bd876-133">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="bd876-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="bd876-134">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="bd876-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="bd876-135">Volitelné</span><span class="sxs-lookup"><span data-stu-id="bd876-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="bd876-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="bd876-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
