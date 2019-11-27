---
title: 'Postupy: Získání hodnoty z vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339827"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="5a077-102">Postupy: Získání hodnoty z vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a077-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="5a077-103">Hodnotu vlastnosti načtete tak, že zahrnete název vlastnosti do výrazu.</span><span class="sxs-lookup"><span data-stu-id="5a077-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="5a077-104">Procedura `Get` vlastnosti načte hodnotu, ale explicitně ji nevoláte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="5a077-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="5a077-105">Vlastnost použijete stejně, jako byste použili proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5a077-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="5a077-106">Visual Basic provede volání procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="5a077-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="5a077-107">Načtení hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a077-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="5a077-108">Použijte název vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné.</span><span class="sxs-lookup"><span data-stu-id="5a077-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="5a077-109">Vlastnost můžete použít všude, kde můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="5a077-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="5a077-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5a077-110">-or-</span></span>  
  
     <span data-ttu-id="5a077-111">Použijte název vlastnosti za znaménkem rovnosti (`=`) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5a077-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="5a077-112">Následující příklad přečte hodnotu vlastnosti Visual Basic `Now`, implicitně volá `Get` proceduru.</span><span class="sxs-lookup"><span data-stu-id="5a077-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="5a077-113">Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami.</span><span class="sxs-lookup"><span data-stu-id="5a077-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5a077-114">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="5a077-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="5a077-115">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="5a077-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5a077-116">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="5a077-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="5a077-117">Hodnota vlastnosti se účastní ve výrazu stejně jako proměnná nebo konstanta nebo je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5a077-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a077-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a077-118">See also</span></span>

- [<span data-ttu-id="5a077-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="5a077-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5a077-120">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a077-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="5a077-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5a077-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5a077-122">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="5a077-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="5a077-123">Rozdíly mezi vlastnostmi a proměnnými v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a077-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="5a077-124">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a077-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="5a077-125">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="5a077-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="5a077-126">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a077-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="5a077-127">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a077-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="5a077-128">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a077-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
