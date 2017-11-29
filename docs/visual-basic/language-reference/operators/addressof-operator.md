---
title: "AddressOf – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="ab372-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab372-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="ab372-103">Vytvoří instanci postup delegáta, který odkazuje na zvláštní postup.</span><span class="sxs-lookup"><span data-stu-id="ab372-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab372-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab372-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="ab372-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ab372-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="ab372-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ab372-106">Required.</span></span> <span data-ttu-id="ab372-107">Určuje postup pro nově vytvořený postup delegát odkazovat.</span><span class="sxs-lookup"><span data-stu-id="ab372-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab372-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab372-108">Remarks</span></span>  
 <span data-ttu-id="ab372-109">`AddressOf` Operátor vytvoří delegáta funkce, která odkazuje na funkci určeného `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="ab372-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="ab372-110">Když zadanou proceduru je že metodu instance pak delegáta funkce odkazuje na instanci a metoda.</span><span class="sxs-lookup"><span data-stu-id="ab372-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="ab372-111">Potom při vyvolání delegáta funkce se nazývá zadanou metodu určené instance.</span><span class="sxs-lookup"><span data-stu-id="ab372-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="ab372-112">`AddressOf` Operátor lze použít jako operand konstruktor delegáta nebo ji lze použít v kontextu, ve kterém se dá určit typ delegát kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="ab372-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab372-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab372-113">Example</span></span>  
 <span data-ttu-id="ab372-114">Tento příklad používá `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="ab372-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ab372-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab372-115">Example</span></span>  
 <span data-ttu-id="ab372-116">Následující příklad používá `AddressOf` operátor a určit funkce spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="ab372-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ab372-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab372-117">See Also</span></span>  
 [<span data-ttu-id="ab372-118">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="ab372-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="ab372-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="ab372-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="ab372-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="ab372-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="ab372-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="ab372-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
