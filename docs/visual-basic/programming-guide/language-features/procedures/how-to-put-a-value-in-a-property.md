---
title: 'Postupy: Vložení hodnoty do vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ad0d0e81f94dd3dead50f21c3bd6ff580c004dd6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346058"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="092ef-102">Postupy: Vložení hodnoty do vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="092ef-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="092ef-103">Hodnotu vlastnosti uložíte tak, že umístíte název vlastnosti na levou stranu příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="092ef-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="092ef-104">Procedura `Set` vlastnosti ukládá hodnotu, ale explicitně ji nevoláte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="092ef-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="092ef-105">Vlastnost použijete stejně, jako byste použili proměnnou.</span><span class="sxs-lookup"><span data-stu-id="092ef-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="092ef-106">Visual Basic provede volání procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="092ef-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="092ef-107">Uložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="092ef-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="092ef-108">Použijte název vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="092ef-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="092ef-109">Následující příklad nastaví hodnotu vlastnosti Visual Basic `TimeOfDay` na Nún, implicitně volá `Set` proceduru.</span><span class="sxs-lookup"><span data-stu-id="092ef-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="092ef-110">Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami.</span><span class="sxs-lookup"><span data-stu-id="092ef-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="092ef-111">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="092ef-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="092ef-112">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="092ef-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="092ef-113">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="092ef-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="092ef-114">Hodnota vygenerovaná na pravé straně příkazu přiřazení je uložena ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="092ef-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092ef-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="092ef-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="092ef-116">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="092ef-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="092ef-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="092ef-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="092ef-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="092ef-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="092ef-119">Rozdíly mezi vlastnostmi a proměnnými v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="092ef-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="092ef-120">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="092ef-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="092ef-121">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="092ef-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="092ef-122">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="092ef-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="092ef-123">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="092ef-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="092ef-124">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="092ef-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
