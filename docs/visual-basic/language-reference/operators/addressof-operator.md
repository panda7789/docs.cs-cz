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
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597784"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="2723d-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2723d-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="2723d-103">Vytvoří instanci postup delegáta, který odkazuje na zvláštní postup.</span><span class="sxs-lookup"><span data-stu-id="2723d-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2723d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2723d-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="2723d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2723d-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="2723d-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2723d-106">Required.</span></span> <span data-ttu-id="2723d-107">Určuje postup pro nově vytvořený postup delegát odkazovat.</span><span class="sxs-lookup"><span data-stu-id="2723d-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2723d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2723d-108">Remarks</span></span>  
 <span data-ttu-id="2723d-109">`AddressOf` Operátor vytvoří delegáta funkce, která odkazuje na funkci určeného `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="2723d-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="2723d-110">Když zadanou proceduru je že metodu instance pak delegáta funkce odkazuje na instanci a metoda.</span><span class="sxs-lookup"><span data-stu-id="2723d-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="2723d-111">Potom při vyvolání delegáta funkce se nazývá zadanou metodu určené instance.</span><span class="sxs-lookup"><span data-stu-id="2723d-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="2723d-112">`AddressOf` Operátor lze použít jako operand konstruktor delegáta nebo ji lze použít v kontextu, ve kterém se dá určit typ delegát kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="2723d-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2723d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2723d-113">Example</span></span>  
 <span data-ttu-id="2723d-114">Tento příklad používá `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="2723d-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2723d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="2723d-115">Example</span></span>  
 <span data-ttu-id="2723d-116">Následující příklad používá `AddressOf` operátor a určit funkce spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="2723d-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2723d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2723d-117">See Also</span></span>  
 [<span data-ttu-id="2723d-118">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="2723d-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="2723d-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2723d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="2723d-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="2723d-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2723d-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="2723d-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
