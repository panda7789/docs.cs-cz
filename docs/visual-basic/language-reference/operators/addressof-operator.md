---
title: AddressOf – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 9d8515b6d5b0caf3552ed05a7e0cd4a271efaf54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608343"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="1ff3b-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ff3b-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="1ff3b-103">Vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ff3b-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="1ff3b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1ff3b-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="1ff3b-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-106">Required.</span></span> <span data-ttu-id="1ff3b-107">Určuje postup odkazovat pomocí nově vytvořeného procedury delegáta.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ff3b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ff3b-108">Remarks</span></span>  
 <span data-ttu-id="1ff3b-109">`AddressOf` Operátor vytvoří delegáta funkce, která odkazuje na funkci určené `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="1ff3b-110">Když zadaná procedura je že metodu instance potom delegáta funkce odkazuje na instanci a metodu.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="1ff3b-111">Potom při vyvolání delegáta funkce se nazývá zadanou metodu určené instance.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="1ff3b-112">`AddressOf` Operátor můžete použít jako operand konstruktor delegate, nebo je možné v kontextu, ve kterém můžete určit typ delegáta kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ff3b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ff3b-113">Example</span></span>  
 <span data-ttu-id="1ff3b-114">V tomto příkladu `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="1ff3b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ff3b-115">Example</span></span>  
 <span data-ttu-id="1ff3b-116">V následujícím příkladu `AddressOf` operátor k určení funkce spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="1ff3b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ff3b-117">See also</span></span>

- [<span data-ttu-id="1ff3b-118">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="1ff3b-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="1ff3b-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="1ff3b-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="1ff3b-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="1ff3b-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="1ff3b-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="1ff3b-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
