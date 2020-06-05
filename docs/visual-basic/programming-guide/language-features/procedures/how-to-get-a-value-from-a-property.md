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
ms.openlocfilehash: 2c92cd4a869acbb7c8c52fbf4117112967386498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387891"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="dbbdb-102">Postupy: Získání hodnoty z vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbbdb-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="dbbdb-103">Hodnotu vlastnosti načtete tak, že zahrnete název vlastnosti do výrazu.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="dbbdb-104">`Get`Procedura vlastnosti načte hodnotu, ale explicitně ji nevoláte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="dbbdb-105">Vlastnost použijete stejně, jako byste použili proměnnou.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="dbbdb-106">Visual Basic provede volání procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="dbbdb-107">Načtení hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbbdb-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="dbbdb-108">Použijte název vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="dbbdb-109">Vlastnost můžete použít všude, kde můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="dbbdb-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dbbdb-110">-or-</span></span>  
  
     <span data-ttu-id="dbbdb-111">Použijte název vlastnosti za znaménkem EQUAL ( `=` ) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="dbbdb-112">Následující příklad přečte hodnotu `Now` vlastnosti Visual Basic, implicitně volá její `Get` proceduru.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="dbbdb-113">Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="dbbdb-114">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="dbbdb-115">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="dbbdb-116">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="dbbdb-117">Hodnota vlastnosti se účastní ve výrazu stejně jako proměnná nebo konstanta nebo je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbdb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbbdb-118">See also</span></span>

- [<span data-ttu-id="dbbdb-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="dbbdb-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="dbbdb-120">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbbdb-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="dbbdb-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="dbbdb-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="dbbdb-122">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="dbbdb-122">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="dbbdb-123">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbbdb-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="dbbdb-124">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbbdb-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="dbbdb-125">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="dbbdb-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="dbbdb-126">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbbdb-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="dbbdb-127">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbbdb-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="dbbdb-128">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbbdb-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
