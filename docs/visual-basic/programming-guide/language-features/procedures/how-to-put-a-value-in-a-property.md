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
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650368"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="58bb4-102">Postupy: Vložení hodnoty do vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58bb4-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="58bb4-103">Hodnota uložená v vlastnost umístěním název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="58bb4-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="58bb4-104">Vlastnosti `Set` postup ukládá hodnotu, ale můžete explicitně ho nevolají podle názvu.</span><span class="sxs-lookup"><span data-stu-id="58bb4-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="58bb4-105">Stejně, jako by použijete proměnnou, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58bb4-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="58bb4-106">Visual Basic umožňuje volání procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58bb4-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="58bb4-107">K uložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58bb4-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="58bb4-108">Na levé straně příkazu přiřazení pomocí názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58bb4-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="58bb4-109">Následující příklad nastaví hodnotu Visual Basicu `TimeOfDay` vlastnost poledne, implicitně volání jeho `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="58bb4-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="58bb4-110">Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="58bb4-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="58bb4-111">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="58bb4-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="58bb4-112">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="58bb4-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="58bb4-113">Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.</span><span class="sxs-lookup"><span data-stu-id="58bb4-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="58bb4-114">Hodnota generovaná na pravé straně přiřazení příkazu je uložené v určité vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58bb4-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bb4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="58bb4-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="58bb4-116">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58bb4-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="58bb4-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="58bb4-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="58bb4-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="58bb4-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="58bb4-119">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58bb4-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="58bb4-120">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58bb4-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="58bb4-121">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="58bb4-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="58bb4-122">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58bb4-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="58bb4-123">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58bb4-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="58bb4-124">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58bb4-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
