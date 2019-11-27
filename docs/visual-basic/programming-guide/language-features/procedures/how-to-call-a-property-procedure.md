---
title: 'Postupy: Volání procedury vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340558"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="06ccd-102">Postupy: Volání procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ccd-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="06ccd-103">Proceduru vlastnosti zavoláte uložením hodnoty do vlastnosti nebo načtením její hodnoty.</span><span class="sxs-lookup"><span data-stu-id="06ccd-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="06ccd-104">K vlastnosti přistupujete stejným způsobem jako při přístupu k proměnné.</span><span class="sxs-lookup"><span data-stu-id="06ccd-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="06ccd-105">Procedura `Set` vlastnosti ukládá hodnotu a její `Get` procedura načítá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="06ccd-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="06ccd-106">Nevolejte ale explicitně tyto procedury podle názvu.</span><span class="sxs-lookup"><span data-stu-id="06ccd-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="06ccd-107">Vlastnost použijete v příkazu přiřazení nebo výrazu stejně, jako byste ukládali nebo načetli hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="06ccd-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="06ccd-108">Visual Basic provede volání procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="06ccd-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="06ccd-109">Volání procedury Get vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="06ccd-110">Použijte název vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné.</span><span class="sxs-lookup"><span data-stu-id="06ccd-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="06ccd-111">Vlastnost můžete použít všude, kde můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="06ccd-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="06ccd-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="06ccd-112">-or-</span></span>  
  
     <span data-ttu-id="06ccd-113">Použijte název vlastnosti za znaménkem rovnosti (`=`) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="06ccd-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="06ccd-114">Následující příklad přečte hodnotu vlastnosti <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> implicitně volá její `Get` proceduru.</span><span class="sxs-lookup"><span data-stu-id="06ccd-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="06ccd-115">Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami.</span><span class="sxs-lookup"><span data-stu-id="06ccd-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="06ccd-116">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="06ccd-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="06ccd-117">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="06ccd-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="06ccd-118">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="06ccd-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="06ccd-119">Hodnota vlastnosti se účastní ve výrazu stejně jako proměnná nebo konstanta nebo je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="06ccd-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="06ccd-120">Volání procedury set vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="06ccd-121">Použijte název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="06ccd-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="06ccd-122">Následující příklad nastaví hodnotu vlastnosti <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> implicitně volá proceduru `Set`.</span><span class="sxs-lookup"><span data-stu-id="06ccd-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="06ccd-123">Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami.</span><span class="sxs-lookup"><span data-stu-id="06ccd-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="06ccd-124">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="06ccd-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="06ccd-125">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="06ccd-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="06ccd-126">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="06ccd-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="06ccd-127">Hodnota vygenerovaná na pravé straně příkazu přiřazení je uložena ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="06ccd-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ccd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06ccd-128">See also</span></span>

- [<span data-ttu-id="06ccd-129">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="06ccd-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="06ccd-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="06ccd-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="06ccd-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="06ccd-132">Rozdíly mezi vlastnostmi a proměnnými v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06ccd-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="06ccd-133">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="06ccd-134">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="06ccd-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="06ccd-135">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06ccd-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="06ccd-136">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="06ccd-137">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06ccd-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="06ccd-138">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="06ccd-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="06ccd-139">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="06ccd-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
