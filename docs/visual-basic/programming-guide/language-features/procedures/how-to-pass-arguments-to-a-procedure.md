---
title: 'Postupy: Předání argumentů proceduře'
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
ms.openlocfilehash: 0267eed7c145988d61de715fd661bd4906d8d57d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344848"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="cb4e1-102">Postupy: Předání argumentů proceduře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb4e1-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cb4e1-103">Při volání procedury se v závorkách použije název procedury se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="cb4e1-104">Zadejte argument odpovídající každému požadovanému parametru, který procedura definuje, a volitelně můžete zadat argumenty `Optional`m parametrům.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="cb4e1-105">Pokud nezadáte parametr `Optional` ve volání, je nutné zahrnout čárku k označení místa v seznamu argumentů, pokud zadáváte další argumenty.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="cb4e1-106">Pokud máte v úmyslu předat argument datového typu, který se liší od odpovídajícího parametru, například `Byte` pro `String`, můžete nastavit přepínač pro kontrolu typu ([Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) na `Off`.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="cb4e1-107">Pokud je `Option Strict` `On`, musíte použít buď rozšiřující převody, nebo explicitní klíčová slova pro převod.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="cb4e1-108">Další informace najdete v tématu [rozšiřování a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkcí pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cb4e1-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="cb4e1-109">Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="cb4e1-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="cb4e1-110">Předání jednoho nebo více argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="cb4e1-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="cb4e1-111">V příkazu call použijte název procedury s závorkami.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="cb4e1-112">Uvnitř závorek vložte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="cb4e1-113">Zahrňte argument pro každý povinný parametr, který procedura definuje, a oddělte argumenty čárkami.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="cb4e1-114">Ujistěte se, že každý argument je platný výraz, který je vyhodnocen jako datový typ převoditelný na typ, který definuje procedura pro odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="cb4e1-115">Pokud je parametr definovaný jako [volitelný](../../../../visual-basic/language-reference/modifiers/optional.md), můžete ho buď zahrnout do seznamu argumentů, nebo ho vynechat.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="cb4e1-116">Pokud ji vynecháte, procedura použije výchozí hodnotu definovanou pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="cb4e1-117">Vynecháte-li argument pro parametr `Optional` a za ním v seznamu parametrů je uveden jiný parametr, můžete místo vynechaného argumentu označit čárkou v seznamu argumentů znak nadbytečné čárky.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="cb4e1-118">Následující příklad volá funkci Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="cb4e1-119">Předchozí příklad dodá požadovaný první argument, což je řetězec zprávy, který má být zobrazen.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="cb4e1-120">Vynechá argument pro nepovinný druhý parametr, který určuje tlačítka, která se mají zobrazit v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="cb4e1-121">Protože volání neposkytuje hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, která zobrazuje pouze tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="cb4e1-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="cb4e1-122">Druhá čárka v seznamu argumentů označuje místo vynechaného druhého argumentu a poslední řetězec je předán volitelnému třetímu parametru `MsgBox`, což je text, který se má zobrazit v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="cb4e1-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4e1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb4e1-123">See also</span></span>

- [<span data-ttu-id="cb4e1-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="cb4e1-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cb4e1-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="cb4e1-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="cb4e1-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cb4e1-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cb4e1-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="cb4e1-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cb4e1-128">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="cb4e1-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="cb4e1-129">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="cb4e1-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="cb4e1-130">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="cb4e1-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="cb4e1-131">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="cb4e1-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="cb4e1-132">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="cb4e1-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="cb4e1-133">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb4e1-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
