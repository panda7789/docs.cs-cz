---
title: 'Postupy: Předání procedur jiným postupům'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345251"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="b1d47-102">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1d47-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="b1d47-103">Tento příklad ukazuje, jak použít delegáty k předání procedury jinému postupu.</span><span class="sxs-lookup"><span data-stu-id="b1d47-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="b1d47-104">Delegát je typ, který můžete použít jako jakýkoli jiný typ v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b1d47-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="b1d47-105">Operátor `AddressOf` vrací objekt delegáta při použití na název procedury.</span><span class="sxs-lookup"><span data-stu-id="b1d47-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="b1d47-106">Tento příklad má proceduru s parametrem delegáta, který může odkazovat na jiný postup získaný pomocí operátoru `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="b1d47-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="b1d47-107">Vytvořit delegáta a postupy pro porovnání</span><span class="sxs-lookup"><span data-stu-id="b1d47-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="b1d47-108">Vytvořte delegáta s názvem `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="b1d47-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="b1d47-109">Vytvořte proceduru s názvem `AddNumbers` s parametry a návratovou hodnotou, která odpovídá hodnotám `MathOperator`, aby se podpisy shodovaly.</span><span class="sxs-lookup"><span data-stu-id="b1d47-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="b1d47-110">Vytvořte proceduru s názvem `SubtractNumbers` s podpisem, který odpovídá `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="b1d47-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="b1d47-111">Vytvořte proceduru s názvem `DelegateTest`, která přebírá delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b1d47-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="b1d47-112">Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich signatury odpovídají signatuře `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="b1d47-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="b1d47-113">Vytvořte proceduru s názvem `Test`, která volá `DelegateTest` jednou s delegátem pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b1d47-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="b1d47-114">Při volání `Test` se nejprve zobrazí výsledek `AddNumbers` působícího na `5` a `3`, což je 8.</span><span class="sxs-lookup"><span data-stu-id="b1d47-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="b1d47-115">Pak se zobrazí výsledek `SubtractNumbers` jednající `9` a `3`, což je 6.</span><span class="sxs-lookup"><span data-stu-id="b1d47-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d47-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1d47-116">See also</span></span>

- [<span data-ttu-id="b1d47-117">Delegáti</span><span class="sxs-lookup"><span data-stu-id="b1d47-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="b1d47-118">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="b1d47-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="b1d47-119">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="b1d47-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="b1d47-120">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="b1d47-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
