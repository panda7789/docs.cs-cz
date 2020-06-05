---
title: Proměnné
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410384"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="f1a94-102">Proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1a94-102">Variables in Visual Basic</span></span>
<span data-ttu-id="f1a94-103">Při provádění výpočtů s Visual Basic často potřebujete ukládat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f1a94-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="f1a94-104">Můžete například chtít vypočítat několik hodnot, porovnat je a provádět na nich různé operace v závislosti na výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="f1a94-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="f1a94-105">Hodnoty je třeba zachovat, pokud je chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="f1a94-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f1a94-106">Využití</span><span class="sxs-lookup"><span data-stu-id="f1a94-106">Usage</span></span>  
 <span data-ttu-id="f1a94-107">Visual Basic, stejně jako většina programovacích jazyků, používá proměnné pro ukládání hodnot.</span><span class="sxs-lookup"><span data-stu-id="f1a94-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="f1a94-108">*Proměnná* má název (slovo, které použijete k odkazování na hodnotu, kterou proměnná obsahuje).</span><span class="sxs-lookup"><span data-stu-id="f1a94-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="f1a94-109">Proměnná má také datový typ (který určuje druh dat, která proměnná může uložit).</span><span class="sxs-lookup"><span data-stu-id="f1a94-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="f1a94-110">Proměnná může představovat pole, pokud má uložit indexovanou sadu úzce souvisejících datových položek.</span><span class="sxs-lookup"><span data-stu-id="f1a94-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="f1a94-111">Odvození místního typu umožňuje deklarovat proměnné bez explicitního oznámení datového typu.</span><span class="sxs-lookup"><span data-stu-id="f1a94-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="f1a94-112">Místo toho kompilátor odvodí typ proměnné z typu inicializačního výrazu.</span><span class="sxs-lookup"><span data-stu-id="f1a94-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="f1a94-113">Další informace naleznete v tématu [odvození místního typu](local-type-inference.md) a [příkaz k odvození možnosti](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f1a94-113">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="f1a94-114">Přiřazení hodnot</span><span class="sxs-lookup"><span data-stu-id="f1a94-114">Assigning Values</span></span>  
 <span data-ttu-id="f1a94-115">Příkazy přiřazení slouží k provádění výpočtů a přiřazení výsledku proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f1a94-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="f1a94-116">Symbol rovná se ( `=` ) v tomto příkladu je operátor přiřazení, nikoli operátor rovnosti.</span><span class="sxs-lookup"><span data-stu-id="f1a94-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="f1a94-117">Hodnota je přiřazena proměnné `applesSold` .</span><span class="sxs-lookup"><span data-stu-id="f1a94-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="f1a94-118">Další informace najdete v tématu [Postup: přesun dat do proměnné a z ní](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="f1a94-118">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="f1a94-119">Proměnné a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f1a94-119">Variables and Properties</span></span>  
 <span data-ttu-id="f1a94-120">Podobně jako proměnná *vlastnost* představuje hodnotu, ke které máte přístup.</span><span class="sxs-lookup"><span data-stu-id="f1a94-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="f1a94-121">Je však složitější než proměnná.</span><span class="sxs-lookup"><span data-stu-id="f1a94-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="f1a94-122">Vlastnost používá bloky kódu, které řídí, jak nastavit a načíst jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f1a94-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="f1a94-123">Další informace naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="f1a94-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a94-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1a94-124">See also</span></span>

- [<span data-ttu-id="f1a94-125">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="f1a94-125">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="f1a94-126">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="f1a94-126">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="f1a94-127">Řešení potíží s proměnnými</span><span class="sxs-lookup"><span data-stu-id="f1a94-127">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="f1a94-128">Postupy: Přesun dat do proměnné a z proměnné</span><span class="sxs-lookup"><span data-stu-id="f1a94-128">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="f1a94-129">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1a94-129">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="f1a94-130">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f1a94-130">Local Type Inference</span></span>](local-type-inference.md)
