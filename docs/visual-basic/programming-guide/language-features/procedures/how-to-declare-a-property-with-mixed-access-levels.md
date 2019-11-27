---
title: 'Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349687"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="a7c7d-102">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7c7d-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="a7c7d-103">Pokud chcete, aby `Get` a `Set` postupy u vlastnosti měly různé úrovně přístupu, můžete použít přísnější úroveň v příkazu `Property` a více omezující úroveň v příkazu `Get` nebo `Set`.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="a7c7d-104">Smíšené úrovně přístupu lze použít pro vlastnost, pokud chcete, aby určité části kódu byly schopny získat hodnotu vlastnosti, a některé další části kódu budou moci změnit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="a7c7d-105">Další informace o úrovních přístupu najdete v tématu [úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a7c7d-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="a7c7d-106">Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="a7c7d-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="a7c7d-107">Deklarujte vlastnost normálním způsobem a v příkazu `Property` určete úroveň přístupu s méně omezujícími možnostmi (například `Public`).</span><span class="sxs-lookup"><span data-stu-id="a7c7d-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="a7c7d-108">Deklarujte buď `Get`, nebo `Set` proceduru, která určuje více omezující úroveň přístupu (například `Friend`).</span><span class="sxs-lookup"><span data-stu-id="a7c7d-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="a7c7d-109">Nezadávejte úroveň přístupu pro druhý postup vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="a7c7d-110">Předpokládá úroveň přístupu deklarovanou v příkazu `Property`.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="a7c7d-111">Přístup můžete omezit pouze na jeden z procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="a7c7d-112">V předchozím příkladu má procedura `Get` stejný `Protected` přístup jako vlastnost, zatímco `Set` procedura má `Private` přístup.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="a7c7d-113">Třída odvozená z `employee` může číst hodnotu `salary`, ale může ji nastavit pouze třída `employee`.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c7d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-114">See also</span></span>

- [<span data-ttu-id="a7c7d-115">Procedury</span><span class="sxs-lookup"><span data-stu-id="a7c7d-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a7c7d-116">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7c7d-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a7c7d-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="a7c7d-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a7c7d-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="a7c7d-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="a7c7d-119">Rozdíly mezi vlastnostmi a proměnnými v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7c7d-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="a7c7d-120">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7c7d-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="a7c7d-121">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7c7d-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="a7c7d-122">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7c7d-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a7c7d-123">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7c7d-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="a7c7d-124">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7c7d-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
