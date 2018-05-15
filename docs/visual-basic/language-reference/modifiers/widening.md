---
title: Rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="widening-visual-basic"></a><span data-ttu-id="91a12-102">Rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91a12-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="91a12-103">Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu typ, který může obsahovat všechny možné hodnoty z původní třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="91a12-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="91a12-104">Převádění s rozšiřující – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="91a12-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="91a12-105">Musíte zadat procesu převodu `Public Shared` kromě `Widening`.</span><span class="sxs-lookup"><span data-stu-id="91a12-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="91a12-106">Rozšiřující převody proběhnout úspěšně v době běhu a nikdy dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="91a12-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="91a12-107">Příklady `Single` k `Double`, `Char` k `String`a k jeho základní typ odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="91a12-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="91a12-108">Tento poslední převod je rozšíření, protože obsahuje všechny členy základní typ odvozený typ a proto je instance základního typu.</span><span class="sxs-lookup"><span data-stu-id="91a12-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="91a12-109">Není nutné používat kód náročné `CType` pro rozšiřující převody, i když `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="91a12-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="91a12-110">`Widening` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="91a12-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="91a12-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="91a12-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="91a12-112">Například zobrazit definice rozšíření a zúžení operátory převodu [postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="91a12-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a12-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="91a12-113">See Also</span></span>  
 [<span data-ttu-id="91a12-114">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="91a12-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="91a12-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="91a12-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="91a12-116">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="91a12-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="91a12-117">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="91a12-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="91a12-118">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="91a12-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="91a12-119">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="91a12-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="91a12-120">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="91a12-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
