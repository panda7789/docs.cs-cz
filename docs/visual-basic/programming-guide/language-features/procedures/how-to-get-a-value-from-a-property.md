---
title: 'Postupy: Získání hodnoty z vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863633"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="a2e87-102">Postupy: Získání hodnoty z vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e87-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="a2e87-103">Načtení hodnoty vlastnosti včetně názvu vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="a2e87-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="a2e87-104">Vlastnosti `Get` postup načte hodnotu, ale můžete explicitně ho nevolají podle názvu.</span><span class="sxs-lookup"><span data-stu-id="a2e87-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="a2e87-105">Vlastnost se stejným způsobem, jako by proměnná.</span><span class="sxs-lookup"><span data-stu-id="a2e87-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="a2e87-106">Visual Basic provede volání do procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a2e87-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="a2e87-107">K načtení hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2e87-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="a2e87-108">Použijte název vlastnosti výrazu stejným způsobem použijete název proměnné.</span><span class="sxs-lookup"><span data-stu-id="a2e87-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="a2e87-109">Můžete použít vlastnost kdekoli můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="a2e87-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="a2e87-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a2e87-110">-or-</span></span>  
  
     <span data-ttu-id="a2e87-111">Použijte název vlastnosti po rovnosti (`=`) Přihlaste se příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a2e87-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="a2e87-112">Následující příklad přečte hodnotu jazyka Visual Basic `Now` vlastnost implicitně volání jeho `Get` postup.</span><span class="sxs-lookup"><span data-stu-id="a2e87-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="a2e87-113">Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="a2e87-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a2e87-114">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="a2e87-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="a2e87-115">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="a2e87-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a2e87-116">Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="a2e87-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="a2e87-117">Hodnota vlastnosti podílí na výraz, stejně jako proměnné by – konstanta nebo je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a2e87-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e87-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2e87-118">See also</span></span>

- [<span data-ttu-id="a2e87-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="a2e87-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a2e87-120">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2e87-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a2e87-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="a2e87-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a2e87-122">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="a2e87-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="a2e87-123">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2e87-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="a2e87-124">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2e87-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="a2e87-125">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="a2e87-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="a2e87-126">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2e87-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="a2e87-127">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2e87-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a2e87-128">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a2e87-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
