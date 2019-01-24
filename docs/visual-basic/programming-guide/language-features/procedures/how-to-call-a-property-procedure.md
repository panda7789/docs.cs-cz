---
title: 'Postupy: Volání procedury vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 1f8871c2cc5126110fa849d42eed3d8edb3a03f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602569"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="b9f51-102">Postupy: Volání procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9f51-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="b9f51-103">Volání procedury vlastnosti uložení hodnoty do vlastnosti nebo načítání jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9f51-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="b9f51-104">Přístup k vlastnosti stejným způsobem, přístup k proměnné.</span><span class="sxs-lookup"><span data-stu-id="b9f51-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="b9f51-105">Vlastnosti `Set` postup uloží hodnotu a jeho `Get` postup načte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9f51-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="b9f51-106">Však není volána explicitně tyto postupy podle názvu.</span><span class="sxs-lookup"><span data-stu-id="b9f51-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="b9f51-107">Pomocí vlastnosti v příkazu přiřazení nebo výraz, stejně jako by ukládat nebo načítat hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="b9f51-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="b9f51-108">Visual Basic provede volání do procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9f51-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="b9f51-109">Volání procedury Get vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9f51-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="b9f51-110">Použijte název vlastnosti výrazu stejným způsobem použijete název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b9f51-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="b9f51-111">Můžete použít vlastnost kdekoli můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="b9f51-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="b9f51-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b9f51-112">-or-</span></span>  
  
     <span data-ttu-id="b9f51-113">Použijte název vlastnosti po rovnosti (`=`) Přihlaste se příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b9f51-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="b9f51-114">Následující příklad přečte hodnotu <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> vlastnost implicitně volání jeho `Get` postup.</span><span class="sxs-lookup"><span data-stu-id="b9f51-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="b9f51-115">Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="b9f51-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b9f51-116">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="b9f51-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="b9f51-117">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="b9f51-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b9f51-118">Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="b9f51-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="b9f51-119">Hodnota vlastnosti podílí na výraz, stejně jako proměnné by – konstanta nebo je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b9f51-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="b9f51-120">Volání vlastnosti je postup nastavení</span><span class="sxs-lookup"><span data-stu-id="b9f51-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="b9f51-121">Použijte název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b9f51-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="b9f51-122">Následující příklad nastaví hodnotu vlastnosti <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> vlastnost implicitně volání `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="b9f51-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="b9f51-123">Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="b9f51-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b9f51-124">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="b9f51-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="b9f51-125">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="b9f51-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b9f51-126">Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="b9f51-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="b9f51-127">Hodnota generovaná na pravé straně příkazu přiřazení je uložená ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9f51-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f51-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9f51-128">See also</span></span>
- [<span data-ttu-id="b9f51-129">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9f51-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b9f51-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="b9f51-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b9f51-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="b9f51-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="b9f51-132">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9f51-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="b9f51-133">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9f51-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="b9f51-134">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="b9f51-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="b9f51-135">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9f51-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b9f51-136">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9f51-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="b9f51-137">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9f51-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="b9f51-138">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="b9f51-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="b9f51-139">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="b9f51-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
