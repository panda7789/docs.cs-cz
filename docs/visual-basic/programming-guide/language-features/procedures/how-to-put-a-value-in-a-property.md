---
title: 'Postupy: Vložení hodnoty do vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 34348d57db0875d9c2c6192ac754b4f83f515ac4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965460"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="e7a66-102">Postupy: Vložení hodnoty do vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7a66-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="e7a66-103">Uložení hodnoty do vlastnosti tak, že vložíte název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e7a66-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="e7a66-104">Vlastnosti `Set` postup uloží hodnotu, ale můžete explicitně ho nevolají podle názvu.</span><span class="sxs-lookup"><span data-stu-id="e7a66-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="e7a66-105">Vlastnost se stejným způsobem, jako by proměnná.</span><span class="sxs-lookup"><span data-stu-id="e7a66-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="e7a66-106">Visual Basic provede volání do procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7a66-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="e7a66-107">K uložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a66-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="e7a66-108">Použijte název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e7a66-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="e7a66-109">Následující příklad nastaví hodnotu jazyka Visual Basic `TimeOfDay` vlastnost noon, implicitně volání jeho `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="e7a66-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  <span data-ttu-id="e7a66-110">Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="e7a66-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e7a66-111">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="e7a66-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="e7a66-112">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="e7a66-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e7a66-113">Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="e7a66-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="e7a66-114">Hodnota generovaná na pravé straně příkazu přiřazení je uložená ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7a66-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a66-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7a66-115">See also</span></span>
- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="e7a66-116">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a66-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e7a66-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="e7a66-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e7a66-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="e7a66-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e7a66-119">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7a66-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="e7a66-120">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a66-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="e7a66-121">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="e7a66-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="e7a66-122">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a66-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="e7a66-123">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7a66-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e7a66-124">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a66-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
