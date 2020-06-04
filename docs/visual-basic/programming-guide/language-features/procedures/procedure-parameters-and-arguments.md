---
title: Parametry a argumenty procedury
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
ms.openlocfilehash: 178206ca2ee103bbdb5a4ac03bca0df903c8c5d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406713"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="b879c-102">Parametry a argumenty procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b879c-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="b879c-103">Ve většině případů procedura potřebuje nějaké informace o okolnostech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="b879c-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="b879c-104">Postup, který provádí opakované nebo sdílené úkoly, používá pro každé volání jiné informace.</span><span class="sxs-lookup"><span data-stu-id="b879c-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="b879c-105">Tyto informace se skládají z proměnných, konstant a výrazů, které procedury předáte při volání.</span><span class="sxs-lookup"><span data-stu-id="b879c-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="b879c-106">*Parametr* představuje hodnotu, kterou procedura očekává při volání metody.</span><span class="sxs-lookup"><span data-stu-id="b879c-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="b879c-107">Deklarace procedury definuje její parametry.</span><span class="sxs-lookup"><span data-stu-id="b879c-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="b879c-108">Můžete definovat proceduru bez parametrů, jeden parametr nebo více než jeden.</span><span class="sxs-lookup"><span data-stu-id="b879c-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="b879c-109">Část definice procedury, která určuje parametry, se nazývá *seznam parametrů*.</span><span class="sxs-lookup"><span data-stu-id="b879c-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="b879c-110">*Argument* představuje hodnotu, kterou zadáte parametru procedury při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="b879c-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="b879c-111">Volající kód dodává argumenty při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="b879c-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="b879c-112">Část volání procedury, která určuje argumenty, se nazývá *seznam argumentů*.</span><span class="sxs-lookup"><span data-stu-id="b879c-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="b879c-113">Následující ilustrace znázorňuje kód, který volá proceduru `safeSquareRoot` ze dvou různých míst.</span><span class="sxs-lookup"><span data-stu-id="b879c-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="b879c-114">První volání předává hodnotu proměnné `x` (4,0) parametru `number` a návratová hodnota v `root` (2,0) je přiřazena proměnné `y` .</span><span class="sxs-lookup"><span data-stu-id="b879c-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="b879c-115">Druhé volání předá hodnotu literálu 9,0 `number` a přiřadí návratovou hodnotu (3,0) proměnné `z` .</span><span class="sxs-lookup"><span data-stu-id="b879c-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagram, který ukazuje předání argumentu parametru](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="b879c-117">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b879c-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="b879c-118">Datový typ parametru</span><span class="sxs-lookup"><span data-stu-id="b879c-118">Parameter Data Type</span></span>  
 <span data-ttu-id="b879c-119">Můžete definovat datový typ pro parametr pomocí `As` klauzule v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="b879c-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="b879c-120">Například následující funkce přijímá řetězec a celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b879c-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="b879c-121">Pokud je přepínač pro kontrolu typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) `Off,` `As` klauzule Optional, s výjimkou toho, že pokud některý parametr používá, musí je použít všechny parametry.</span><span class="sxs-lookup"><span data-stu-id="b879c-121">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="b879c-122">Pokud je kontrola typu `On` , `As` je vyžadována klauzule pro všechny parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="b879c-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="b879c-123">Pokud volající kód očekává zadání argumentu s datovým typem, který se liší od odpovídajícího parametru, například `Byte` s `String` parametrem, musí provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b879c-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="b879c-124">Poskytněte pouze argumenty s datovými typy, které se rozšíří na datový typ parametru;</span><span class="sxs-lookup"><span data-stu-id="b879c-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="b879c-125">Nastavte `Option Strict Off` na povolení implicitních zužujících převodů; nebo</span><span class="sxs-lookup"><span data-stu-id="b879c-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="b879c-126">K explicitnímu převodu datového typu použijte klíčové slovo Conversion.</span><span class="sxs-lookup"><span data-stu-id="b879c-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="b879c-127">Parametry typu</span><span class="sxs-lookup"><span data-stu-id="b879c-127">Type Parameters</span></span>  
 <span data-ttu-id="b879c-128">*Obecný postup* také definuje jeden nebo více *parametrů typu* kromě jeho běžných parametrů.</span><span class="sxs-lookup"><span data-stu-id="b879c-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="b879c-129">Obecný postup umožňuje volajícímu kódu předat různým datovým typům při každém volání procedury, takže může přizpůsobit datové typy na požadavky každého jednotlivého volání.</span><span class="sxs-lookup"><span data-stu-id="b879c-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="b879c-130">Viz [Obecné procedury v Visual Basic](../data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b879c-130">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b879c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b879c-131">See also</span></span>

- [<span data-ttu-id="b879c-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="b879c-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b879c-133">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="b879c-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b879c-134">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="b879c-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b879c-135">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b879c-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b879c-136">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="b879c-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b879c-137">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="b879c-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="b879c-138">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="b879c-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="b879c-139">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="b879c-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b879c-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="b879c-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="b879c-141">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b879c-141">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
