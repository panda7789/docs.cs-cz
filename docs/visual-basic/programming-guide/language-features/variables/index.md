---
title: Proměnné v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7a47ad7e4ade9f15159c27ac672aeb937a05493
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="744ba-102">Proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="744ba-102">Variables in Visual Basic</span></span>
<span data-ttu-id="744ba-103">Často je nutné uložit hodnoty při provádění výpočtů s [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="744ba-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="744ba-104">Můžete například chtít výpočet několik hodnot, porovnat a provádět různé operace na nich, v závislosti na výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="744ba-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="744ba-105">Budete muset zachovat hodnoty, pokud chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="744ba-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="744ba-106">Použití</span><span class="sxs-lookup"><span data-stu-id="744ba-106">Usage</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="744ba-107">, stejně jako většinu programovacích jazyků, používá pro ukládání hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="744ba-107">, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="744ba-108">A *proměnné* má název (word, který používáte k odkazování na hodnotu, která obsahuje proměnnou).</span><span class="sxs-lookup"><span data-stu-id="744ba-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="744ba-109">Proměnné také má datový typ (který určuje typ dat, které můžete ukládat proměnné).</span><span class="sxs-lookup"><span data-stu-id="744ba-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="744ba-110">Pokud má k uložení indexované sadu úzce související datových položek, může představovat proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="744ba-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="744ba-111">Odvození místního typu umožňuje deklarujte proměnné bez explicitně s informacemi o tom datovým typem.</span><span class="sxs-lookup"><span data-stu-id="744ba-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="744ba-112">Místo toho kompilátor odvodí typ proměnné z typu inicializace výrazu.</span><span class="sxs-lookup"><span data-stu-id="744ba-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="744ba-113">Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="744ba-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="744ba-114">Přidělování hodnot</span><span class="sxs-lookup"><span data-stu-id="744ba-114">Assigning Values</span></span>  
 <span data-ttu-id="744ba-115">Příkazy přiřazení slouží k provádění výpočtů a přiřadit výsledek proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="744ba-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="744ba-116">Znaménkem rovnosti (`=`) v tomto příkladu je operátor přiřazení, není operátor rovnosti.</span><span class="sxs-lookup"><span data-stu-id="744ba-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="744ba-117">Hodnota je právě přiřazován proměnnou `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="744ba-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="744ba-118">Další informace najdete v tématu [postupy: Přesun dat do a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="744ba-118">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="744ba-119">Proměnné a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="744ba-119">Variables and Properties</span></span>  
 <span data-ttu-id="744ba-120">Jako proměnnou, *vlastnost* představuje hodnotu, která se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="744ba-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="744ba-121">Je však mnohem složitější než proměnné.</span><span class="sxs-lookup"><span data-stu-id="744ba-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="744ba-122">Vlastnost používá bloky kódu, které řídí nastavení a načtení jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="744ba-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="744ba-123">Další informace najdete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="744ba-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744ba-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="744ba-124">See Also</span></span>  
 [<span data-ttu-id="744ba-125">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="744ba-125">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="744ba-126">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="744ba-126">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="744ba-127">Řešení potíží s proměnnými</span><span class="sxs-lookup"><span data-stu-id="744ba-127">Troubleshooting Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [<span data-ttu-id="744ba-128">Postupy: Přesun dat do a z proměnné</span><span class="sxs-lookup"><span data-stu-id="744ba-128">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="744ba-129">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="744ba-129">Differences Between Properties and Variables in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [<span data-ttu-id="744ba-130">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="744ba-130">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
