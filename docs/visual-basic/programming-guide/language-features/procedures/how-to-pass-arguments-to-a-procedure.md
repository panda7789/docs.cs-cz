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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333903"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="38506-102">Postupy: Předání argumentů proceduře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38506-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="38506-103">Při volání procedury, použijte název procedury se seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="38506-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="38506-104">Zadat argument odpovídající každý povinný parametr postupu definuje, a volitelně můžete zadat argumenty, které mají `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="38506-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="38506-105">Pokud nezadáte `Optional` parametr ve volání musí obsahovat čárku k označení příslušné místo v seznamu argumentů, pokud zadáváte libovolné další argumenty.</span><span class="sxs-lookup"><span data-stu-id="38506-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="38506-106">Pokud chcete předat argument typu dat liší od odpovídajícího parametru, jako například `Byte` k `String`, nastavíte přepínač kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) k `Off`.</span><span class="sxs-lookup"><span data-stu-id="38506-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="38506-107">Pokud `Option Strict` je `On`, je nutné použít buď rozšiřující převody nebo klíčová slova explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="38506-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="38506-108">Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="38506-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="38506-109">Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="38506-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="38506-110">K předání jeden nebo více argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="38506-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="38506-111">V příkazu volání použijte název procedury se závorkami.</span><span class="sxs-lookup"><span data-stu-id="38506-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="38506-112">Uvnitř závorek uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="38506-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="38506-113">Argument pro každý požadovaný parametr postupu definuje zahrnout a argumenty oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="38506-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="38506-114">Ujistěte se, že každý argument není platný výraz, který je vyhodnocen jako typ dat lze převést na typ procesu definuje pro odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="38506-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="38506-115">Pokud parametr je definován jako [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md), můžete zahrnout do seznamu argumentů, nebo ji vynechte.</span><span class="sxs-lookup"><span data-stu-id="38506-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="38506-116">Pokud ho vynecháte, použije procedura výchozí hodnotu definovanou pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="38506-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="38506-117">Pokud vynecháte argument `Optional` parametrů a je jiný parametr v seznamu parametrů po něm, určíte místo vynechaný argument navíc čárkou v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="38506-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="38506-118">Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.</span><span class="sxs-lookup"><span data-stu-id="38506-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="38506-119">V předchozím příkladu poskytuje požadované první argument, který je řetězec zprávy, který se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="38506-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="38506-120">Vynechá argument pro volitelný druhý parametr, který určuje tlačítka, který se má zobrazit v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="38506-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="38506-121">Protože volání neposkytne hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, zobrazuje pouze **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="38506-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="38506-122">Označuje druhou čárkou v seznamu argumentů místo vynechaný druhého argumentu a volitelný třetí parametr je předán poslední řetězec `MsgBox`, což je text, který má být zobrazen v záhlaví programu.</span><span class="sxs-lookup"><span data-stu-id="38506-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38506-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38506-123">See also</span></span>

- [<span data-ttu-id="38506-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="38506-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="38506-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="38506-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="38506-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="38506-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="38506-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="38506-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="38506-128">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="38506-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="38506-129">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="38506-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="38506-130">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="38506-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="38506-131">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="38506-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="38506-132">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="38506-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="38506-133">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38506-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
