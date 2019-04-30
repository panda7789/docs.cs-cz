---
title: 'Postupy: Předání argumentů proceduře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863438"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="a308d-102">Postupy: Předání argumentů proceduře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a308d-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="a308d-103">Při volání procedury, použijte název procedury se seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="a308d-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="a308d-104">Zadat argument odpovídající každý povinný parametr postupu definuje, a volitelně můžete zadat argumenty, které mají `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="a308d-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="a308d-105">Pokud nezadáte `Optional` parametr ve volání musí obsahovat čárku k označení příslušné místo v seznamu argumentů, pokud zadáváte libovolné další argumenty.</span><span class="sxs-lookup"><span data-stu-id="a308d-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="a308d-106">Pokud chcete předat argument typu dat liší od odpovídajícího parametru, jako například `Byte` k `String`, nastavíte přepínač kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) k `Off`.</span><span class="sxs-lookup"><span data-stu-id="a308d-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="a308d-107">Pokud `Option Strict` je `On`, je nutné použít buď rozšiřující převody nebo klíčová slova explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="a308d-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="a308d-108">Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a308d-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="a308d-109">Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="a308d-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="a308d-110">K předání jeden nebo více argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="a308d-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="a308d-111">V příkazu volání použijte název procedury se závorkami.</span><span class="sxs-lookup"><span data-stu-id="a308d-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="a308d-112">Uvnitř závorek uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="a308d-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="a308d-113">Argument pro každý požadovaný parametr postupu definuje zahrnout a argumenty oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="a308d-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="a308d-114">Ujistěte se, že každý argument není platný výraz, který je vyhodnocen jako typ dat lze převést na typ procesu definuje pro odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="a308d-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="a308d-115">Pokud parametr je definován jako [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md), můžete zahrnout do seznamu argumentů, nebo ji vynechte.</span><span class="sxs-lookup"><span data-stu-id="a308d-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="a308d-116">Pokud ho vynecháte, použije procedura výchozí hodnotu definovanou pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="a308d-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="a308d-117">Pokud vynecháte argument `Optional` parametrů a je jiný parametr v seznamu parametrů po něm, určíte místo vynechaný argument navíc čárkou v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="a308d-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="a308d-118">Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.</span><span class="sxs-lookup"><span data-stu-id="a308d-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="a308d-119">V předchozím příkladu poskytuje požadované první argument, který je řetězec zprávy, který se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="a308d-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="a308d-120">Vynechá argument pro volitelný druhý parametr, který určuje tlačítka, který se má zobrazit v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a308d-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="a308d-121">Protože volání neposkytne hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, zobrazuje pouze **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a308d-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="a308d-122">Označuje druhou čárkou v seznamu argumentů místo vynechaný druhého argumentu a volitelný třetí parametr je předán poslední řetězec `MsgBox`, což je text, který má být zobrazen v záhlaví programu.</span><span class="sxs-lookup"><span data-stu-id="a308d-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a308d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a308d-123">See also</span></span>

- [<span data-ttu-id="a308d-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="a308d-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a308d-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="a308d-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a308d-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a308d-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a308d-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a308d-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a308d-128">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="a308d-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="a308d-129">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="a308d-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a308d-130">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="a308d-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="a308d-131">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="a308d-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="a308d-132">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="a308d-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="a308d-133">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a308d-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
