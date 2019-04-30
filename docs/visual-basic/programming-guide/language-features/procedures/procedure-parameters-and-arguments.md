---
title: Parametry a argumenty procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791906"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="351bd-102">Parametry a argumenty procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="351bd-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="351bd-103">Ve většině případů postup potřebuje určité informace o okolnostech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="351bd-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="351bd-104">Postup, který provádí úlohy opakovaných nebo sdílené používá různé informace pro každé volání.</span><span class="sxs-lookup"><span data-stu-id="351bd-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="351bd-105">Tyto informace se skládá z proměnné, konstanty a výrazy, které předáváte k postupu při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="351bd-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="351bd-106">A *parametr* představuje hodnotu, která procedura očekává, že můžete zadat při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="351bd-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="351bd-107">Podle postupu prohlášení definuje jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="351bd-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="351bd-108">Můžete definovat postup s žádné parametry, jeden parametr nebo více než jeden.</span><span class="sxs-lookup"><span data-stu-id="351bd-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="351bd-109">Je volána část definice procedury, která určuje parametry *seznam parametrů*.</span><span class="sxs-lookup"><span data-stu-id="351bd-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="351bd-110">*Argument* představuje hodnotu zadáte parametr procedury při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="351bd-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="351bd-111">Volající kód poskytuje argumenty při volání postup.</span><span class="sxs-lookup"><span data-stu-id="351bd-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="351bd-112">Část volání procedury, která určuje argumenty se nazývá *seznam argumentů*.</span><span class="sxs-lookup"><span data-stu-id="351bd-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="351bd-113">Následující obrázek znázorňuje kódu volající proces `safeSquareRoot` ze dvou různých míst.</span><span class="sxs-lookup"><span data-stu-id="351bd-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="351bd-114">První volání předá hodnotu proměnné `x` (4.0) k parametru `number`a návratová hodnota v `root` (2.0) je přiřazená k proměnné `y`.</span><span class="sxs-lookup"><span data-stu-id="351bd-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="351bd-115">Druhé volání předá hodnotu literálu 9.0 na `number`a přiřadí proměnné návratovou hodnotu (3.0) `z`.</span><span class="sxs-lookup"><span data-stu-id="351bd-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagram zobrazující průběh předání argumentu pro parametr](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="351bd-117">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="351bd-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="351bd-118">Datový typ parametru</span><span class="sxs-lookup"><span data-stu-id="351bd-118">Parameter Data Type</span></span>  
 <span data-ttu-id="351bd-119">Definovat datový typ pro parametr pomocí `As` klauzule v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="351bd-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="351bd-120">Například následující funkce přijímá řetězec a celé číslo.</span><span class="sxs-lookup"><span data-stu-id="351bd-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="351bd-121">Pokud kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off,` `As` klauzule je volitelné, s tím rozdílem, že pokud ho používáte jakékoli jeden parametr, musíte použít všechny parametry, ho.</span><span class="sxs-lookup"><span data-stu-id="351bd-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="351bd-122">Pokud je kontrola typu `On`, `As` klauzule se vyžaduje pro všechny parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="351bd-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="351bd-123">Pokud volající kód očekává, že chcete zadat argument s datovým typem, který se liší od odpovídajícího parametru, například `Byte` k `String` parametr, musíte udělat jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="351bd-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="351bd-124">Zadejte pouze argumenty s datovými typy, které rozšířit na datový typ parametru;</span><span class="sxs-lookup"><span data-stu-id="351bd-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="351bd-125">Nastavte `Option Strict Off` povolit implicitní zužující převody; nebo</span><span class="sxs-lookup"><span data-stu-id="351bd-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="351bd-126">Použijte klíčové slovo převodu k explicitnímu převodu datového typu.</span><span class="sxs-lookup"><span data-stu-id="351bd-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="351bd-127">Parametry typu</span><span class="sxs-lookup"><span data-stu-id="351bd-127">Type Parameters</span></span>  
 <span data-ttu-id="351bd-128">A *obecný postup* také definuje jeden nebo více *parametry typu* kromě své normální parametry.</span><span class="sxs-lookup"><span data-stu-id="351bd-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="351bd-129">Obecný postup umožňuje volajícímu kódu k předání různých typů dat pokaždé, když volá proceduru, takže ho můžete přizpůsobit datové typy s požadavky každého jednotlivého volání.</span><span class="sxs-lookup"><span data-stu-id="351bd-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="351bd-130">Zobrazit [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="351bd-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351bd-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="351bd-131">See also</span></span>

- [<span data-ttu-id="351bd-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="351bd-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="351bd-133">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="351bd-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="351bd-134">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="351bd-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="351bd-135">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="351bd-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="351bd-136">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="351bd-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="351bd-137">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="351bd-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="351bd-138">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="351bd-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="351bd-139">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="351bd-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="351bd-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="351bd-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="351bd-141">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="351bd-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
