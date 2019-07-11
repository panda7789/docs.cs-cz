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
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760373"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="452d9-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="452d9-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="452d9-103">Vytvoří instanci delegáta, který odkazuje na konkrétní postup.</span><span class="sxs-lookup"><span data-stu-id="452d9-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="452d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="452d9-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="452d9-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="452d9-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="452d9-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="452d9-106">Required.</span></span> <span data-ttu-id="452d9-107">Určuje postup, který se odkazuje nově vytvořený delegát.</span><span class="sxs-lookup"><span data-stu-id="452d9-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="452d9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="452d9-108">Remarks</span></span>  
 <span data-ttu-id="452d9-109">`AddressOf` Operátor vytvoří delegát, který odkazuje na sub nebo function určené `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="452d9-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="452d9-110">Když zadaná procedura je že pak delegát metody instance odkazuje na instanci a metody.</span><span class="sxs-lookup"><span data-stu-id="452d9-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="452d9-111">Potom když je vyvolán delegát se nazývá zadanou metodu zadanou instanci.</span><span class="sxs-lookup"><span data-stu-id="452d9-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="452d9-112">`AddressOf` Operátor můžete použít jako operand konstruktor delegate, nebo je možné v kontextu, ve kterém můžete určit typ delegáta kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="452d9-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="452d9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="452d9-113">Example</span></span>  
 <span data-ttu-id="452d9-114">V tomto příkladu `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="452d9-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="452d9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="452d9-115">Example</span></span>  
 <span data-ttu-id="452d9-116">V následujícím příkladu `AddressOf` operátor k určení funkce spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="452d9-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="452d9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="452d9-117">See also</span></span>

- [<span data-ttu-id="452d9-118">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="452d9-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="452d9-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="452d9-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="452d9-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="452d9-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="452d9-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="452d9-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
