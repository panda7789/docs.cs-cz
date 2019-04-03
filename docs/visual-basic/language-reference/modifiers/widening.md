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
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825310"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="10a5e-102">Rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10a5e-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="10a5e-103">Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který může uchovat všechny možné hodnoty původní třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="10a5e-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="10a5e-104">Převod pomocí rozšiřující – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="10a5e-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="10a5e-105">Proces převodu musíte zadat `Public Shared` kromě `Widening`.</span><span class="sxs-lookup"><span data-stu-id="10a5e-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="10a5e-106">Rozšiřující převody proběhnout úspěšně, v době spuštění a nikdy ztrátě dat se vám účtovat.</span><span class="sxs-lookup"><span data-stu-id="10a5e-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="10a5e-107">Mezi příklady patří `Single` k `Double`, `Char` k `String`a na jeho základní typ odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="10a5e-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="10a5e-108">Tento poslední převod je rozšíření, protože odvozený typ obsahuje všechny členy ze základního typu a tedy instanci základního typu.</span><span class="sxs-lookup"><span data-stu-id="10a5e-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="10a5e-109">Není nutné používat časově náročný kód `CType` pro rozšiřující převody, i když `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="10a5e-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="10a5e-110">`Widening` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="10a5e-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="10a5e-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="10a5e-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="10a5e-112">Příklad naleznete v tématu definice rozšíření a zúžení operátory převodu [jak: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="10a5e-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a5e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10a5e-113">See also</span></span>

- [<span data-ttu-id="10a5e-114">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="10a5e-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="10a5e-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="10a5e-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="10a5e-116">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="10a5e-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="10a5e-117">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="10a5e-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="10a5e-118">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="10a5e-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="10a5e-119">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="10a5e-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="10a5e-120">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="10a5e-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
