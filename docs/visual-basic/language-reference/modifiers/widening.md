---
title: "Rozšíření (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a><span data-ttu-id="5a145-102">Rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a145-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="5a145-103">Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu typ, který může obsahovat všechny možné hodnoty z původní třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5a145-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="5a145-104">Převádění s rozšiřující – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="5a145-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="5a145-105">Musíte zadat procesu převodu `Public Shared` kromě `Widening`.</span><span class="sxs-lookup"><span data-stu-id="5a145-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="5a145-106">Rozšiřující převody proběhnout úspěšně v době běhu a nikdy dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="5a145-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="5a145-107">Příklady `Single` k `Double`, `Char` k `String`a k jeho základní typ odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="5a145-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="5a145-108">Tento poslední převod je rozšíření, protože obsahuje všechny členy základní typ odvozený typ a proto je instance základního typu.</span><span class="sxs-lookup"><span data-stu-id="5a145-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="5a145-109">Není nutné používat kód náročné `CType` pro rozšiřující převody, i když `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="5a145-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="5a145-110">`Widening` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="5a145-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="5a145-111">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a145-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="5a145-112">Například zobrazit definice rozšíření a zúžení operátory převodu [postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5a145-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a145-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a145-113">See Also</span></span>  
 [<span data-ttu-id="5a145-114">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a145-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="5a145-115">Zužující</span><span class="sxs-lookup"><span data-stu-id="5a145-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="5a145-116">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="5a145-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="5a145-117">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="5a145-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="5a145-118">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="5a145-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="5a145-119">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a145-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="5a145-120">Postupy: definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="5a145-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
