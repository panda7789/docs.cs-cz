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
ms.openlocfilehash: f0f7aba25888544dfcc093906850ae7ada621182
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388242"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="25da5-102">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25da5-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="25da5-103">Pokud chcete, aby `Get` `Set` procedury a u vlastnosti měly různé úrovně přístupu, můžete použít přísnější úroveň v `Property` příkazu a více omezující úroveň v `Get` `Set` příkazu or.</span><span class="sxs-lookup"><span data-stu-id="25da5-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="25da5-104">Smíšené úrovně přístupu lze použít pro vlastnost, pokud chcete, aby určité části kódu byly schopny získat hodnotu vlastnosti, a některé další části kódu budou moci změnit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25da5-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="25da5-105">Další informace o úrovních přístupu najdete v tématu [úrovně přístupu v Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="25da5-105">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="25da5-106">Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="25da5-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="25da5-107">Deklarujte vlastnost normálním způsobem a určete méně omezující úroveň přístupu (například `Public` ) v `Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="25da5-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="25da5-108">Deklarujte buď `Get` nebo `Set` proceduru, která určuje více omezující úroveň přístupu (například `Friend` ).</span><span class="sxs-lookup"><span data-stu-id="25da5-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="25da5-109">Nezadávejte úroveň přístupu pro druhý postup vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25da5-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="25da5-110">Předpokládá úroveň přístupu deklarovanou v `Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="25da5-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="25da5-111">Přístup můžete omezit pouze na jeden z procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="25da5-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="25da5-112">V předchozím příkladu `Get` má procedura stejný `Protected` přístup jako vlastnost samotnou, zatímco `Set` procedura má `Private` přístup.</span><span class="sxs-lookup"><span data-stu-id="25da5-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="25da5-113">Třída odvozená z `employee` může číst `salary` hodnotu, ale `employee` může ji nastavit pouze třída.</span><span class="sxs-lookup"><span data-stu-id="25da5-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25da5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="25da5-114">See also</span></span>

- [<span data-ttu-id="25da5-115">Procedury</span><span class="sxs-lookup"><span data-stu-id="25da5-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="25da5-116">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25da5-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="25da5-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="25da5-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="25da5-118">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="25da5-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="25da5-119">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25da5-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="25da5-120">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25da5-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="25da5-121">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25da5-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="25da5-122">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25da5-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="25da5-123">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25da5-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="25da5-124">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25da5-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
