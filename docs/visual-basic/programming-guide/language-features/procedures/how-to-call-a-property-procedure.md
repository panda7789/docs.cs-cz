---
title: "Postupy: Volání procedury vlastnosti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="b7436-102">Postupy: Volání procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7436-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="b7436-103">Volání procedury vlastnosti ukládání hodnotu ve vlastnosti nebo načtení jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b7436-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="b7436-104">Přístup k vlastnosti stejným způsobem jako přístup k proměnné.</span><span class="sxs-lookup"><span data-stu-id="b7436-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="b7436-105">Vlastnosti `Set` postup ukládá hodnotu a jeho `Get` postup načte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7436-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="b7436-106">Ale Nevolejte explicitně tyto postupy podle názvu.</span><span class="sxs-lookup"><span data-stu-id="b7436-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="b7436-107">Pomocí vlastnosti v příkazu přiřazení nebo výraz, stejně, jako by ukládat a načítat hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="b7436-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="b7436-108">Díky volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b7436-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="b7436-109">K volání procedury Get vlastnost</span><span class="sxs-lookup"><span data-stu-id="b7436-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="b7436-110">Pomocí názvu vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b7436-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="b7436-111">Můžete použít vlastnost kdekoli můžete proměnné nebo konstantní.</span><span class="sxs-lookup"><span data-stu-id="b7436-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="b7436-112">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b7436-112">-or-</span></span>  
  
     <span data-ttu-id="b7436-113">Použít následující rovná název vlastnosti (`=`) přihlásit příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b7436-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="b7436-114">Následující příklad načte hodnotu <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> vlastnost implicitně volání jeho `Get` postupu.</span><span class="sxs-lookup"><span data-stu-id="b7436-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="b7436-115">Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="b7436-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b7436-116">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="b7436-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="b7436-117">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="b7436-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b7436-118">Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.</span><span class="sxs-lookup"><span data-stu-id="b7436-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="b7436-119">Hodnota vlastnosti, na které se účastní výraz stejně jako proměnné Konstanta by nebo je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b7436-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="b7436-120">Volání vlastnosti sadu postup</span><span class="sxs-lookup"><span data-stu-id="b7436-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="b7436-121">Na levé straně příkazu přiřazení pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b7436-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="b7436-122">Nastaví hodnotu v následujícím příkladu <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> vlastnost implicitně volání `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="b7436-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="b7436-123">Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="b7436-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b7436-124">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="b7436-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="b7436-125">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="b7436-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b7436-126">Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.</span><span class="sxs-lookup"><span data-stu-id="b7436-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="b7436-127">Hodnota generovaná na pravé straně přiřazení příkazu je uložené v určité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b7436-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7436-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7436-128">See Also</span></span>  
 [<span data-ttu-id="b7436-129">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="b7436-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="b7436-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="b7436-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b7436-131">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7436-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="b7436-132">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7436-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="b7436-133">Postupy: vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7436-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="b7436-134">Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="b7436-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="b7436-135">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7436-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="b7436-136">Postupy: vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7436-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="b7436-137">Postupy: získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7436-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="b7436-138">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7436-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="b7436-139">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7436-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
