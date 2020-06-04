---
title: Rozšíření
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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359900"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="fa92d-102">Rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa92d-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="fa92d-103">Označuje, že operátor převodu ( `CType` ) převede třídu nebo strukturu na typ, který může uchovávat všechny možné hodnoty původní třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="fa92d-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="fa92d-104">Převod pomocí klíčového slova rozšiřování</span><span class="sxs-lookup"><span data-stu-id="fa92d-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="fa92d-105">Postup převodu musí být `Public Shared` kromě `Widening` .</span><span class="sxs-lookup"><span data-stu-id="fa92d-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="fa92d-106">Rozšiřující převody jsou vždy úspěšné v době běhu a nikdy neúčtují ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="fa92d-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="fa92d-107">Příklady jsou `Single` `Double` , `Char` do a `String` odvozeného typu na jeho základní typ.</span><span class="sxs-lookup"><span data-stu-id="fa92d-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="fa92d-108">Tento poslední převod se rozšiřuje, protože odvozený typ obsahuje všechny členy základního typu, a proto je instancí základního typu.</span><span class="sxs-lookup"><span data-stu-id="fa92d-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="fa92d-109">Nenáročný kód nemusí být použit `CType` pro rozšiřující převody, a to ani v případě, že `Option Strict` je `On` .</span><span class="sxs-lookup"><span data-stu-id="fa92d-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="fa92d-110">`Widening`Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="fa92d-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="fa92d-111">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="fa92d-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="fa92d-112">Například definice rozšiřujících a zužujících operátorů převodu naleznete v tématu [How to: define a Conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)operator.</span><span class="sxs-lookup"><span data-stu-id="fa92d-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa92d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa92d-113">See also</span></span>

- [<span data-ttu-id="fa92d-114">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="fa92d-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="fa92d-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="fa92d-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="fa92d-116">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="fa92d-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="fa92d-117">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="fa92d-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="fa92d-118">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="fa92d-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="fa92d-119">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="fa92d-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="fa92d-120">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="fa92d-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
