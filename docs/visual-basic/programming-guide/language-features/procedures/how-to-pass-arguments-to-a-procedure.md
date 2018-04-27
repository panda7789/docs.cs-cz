---
title: 'Postupy: Předání argumentů proceduře (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e8f8e438dc749e7f5f0d33aeaa26dfbcf4c29f3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="4e726-102">Postupy: Předání argumentů proceduře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e726-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="4e726-103">Při volání procedury, postupujte podle název procedury s seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4e726-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="4e726-104">Zadejte argument odpovídající všechny požadované parametry postupu definuje a volitelně můžete zadat argumenty, které mají `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="4e726-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="4e726-105">Pokud nezadáte `Optional` parametr ve volání, musí obsahovat čárkami k označení jeho místo v seznamu argumentů, pokud jsou zadávání žádné další argumenty.</span><span class="sxs-lookup"><span data-stu-id="4e726-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="4e726-106">Pokud máte v úmyslu předat argument typu dat, jako z jeho odpovídající parametr `Byte` k `String`, můžete nastavit přepínač kontrola typu ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) k `Off`.</span><span class="sxs-lookup"><span data-stu-id="4e726-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="4e726-107">Pokud `Option Strict` je `On`, je nutné použít buď rozšiřující převody nebo klíčových slov explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="4e726-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="4e726-108">Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4e726-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="4e726-109">Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4e726-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="4e726-110">Předání jeden nebo více argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="4e726-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="4e726-111">V příkazu volání postupujte podle název procedury v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4e726-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="4e726-112">V závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="4e726-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="4e726-113">Argument pro každý požadovaný parametr postupu definuje zahrnout a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="4e726-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="4e726-114">Zajistěte, aby že každý argument je platný výraz, který se vyhodnotí jako typ dat lze převést na typ postupu definuje pro odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="4e726-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="4e726-115">Pokud parametr je definován jako [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md), můžete zahrnout do seznamu argumentů nebo ji vynechat.</span><span class="sxs-lookup"><span data-stu-id="4e726-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="4e726-116">Pokud ji vynecháte, postup používá výchozí hodnotu definovanou pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="4e726-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="4e726-117">Pokud vynecháte argument `Optional` parametr a jiný parametr, který je po ho v seznamu parametrů, můžete označit místní vynechání argumentu navíc čárkou v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="4e726-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="4e726-118">V následujícím příkladu volání jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.</span><span class="sxs-lookup"><span data-stu-id="4e726-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     <span data-ttu-id="4e726-119">V předchozím příkladu poskytuje požadované první argument, který je zpráva řetězec, který se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="4e726-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="4e726-120">Se vynechá argument volitelný druhý parametr, který určuje tlačítka, který se má zobrazit v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="4e726-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="4e726-121">Protože volání neposkytuje hodnotu, `MsgBox` používá výchozí hodnotu `MsgBoxStyle.OKOnly`, který zobrazuje pouze **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4e726-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="4e726-122">Druhý čárkou v seznamu argumentů označí místo vynechaných druhý argument a je předán poslední řetězec volitelný třetí parametr `MsgBox`, což je text, který se zobrazí v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4e726-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e726-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e726-123">See also</span></span>

 [<span data-ttu-id="4e726-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="4e726-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="4e726-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="4e726-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="4e726-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4e726-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="4e726-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="4e726-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="4e726-128">Postupy: Definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="4e726-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="4e726-129">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="4e726-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4e726-130">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="4e726-130">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="4e726-131">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="4e726-131">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="4e726-132">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4e726-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="4e726-133">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e726-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
