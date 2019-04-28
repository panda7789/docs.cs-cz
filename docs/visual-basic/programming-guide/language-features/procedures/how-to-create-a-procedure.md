---
title: 'Postupy: Vytvořit procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 56099d334a03e85b816cf48983cbbead0784ef5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665803"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="1c9bb-102">Postupy: Vytvořit procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c9bb-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="1c9bb-103">Použijte postup mezi počáteční příkazu deklarace (`Sub` nebo `Function`) a koncové příkazu deklarace (`End Sub` nebo `End Function`).</span><span class="sxs-lookup"><span data-stu-id="1c9bb-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="1c9bb-104">Kód všechny procedury leží mezi těmito příkazy.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="1c9bb-105">Postup nemůže obsahovat jinou proceduru, takže jeho počáteční a koncové příkazy musí být mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="1c9bb-106">Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohy jednou jako postup a následně ji zavolat z různých míst v kódu.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="1c9bb-107">Chcete-li vytvořit proceduru, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="1c9bb-107">To create a procedure that does not return a value</span></span>  
  
1. <span data-ttu-id="1c9bb-108">Mimo všechny procedury, použijte `Sub` příkazu, za nímž následuje `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="1c9bb-109">V `Sub` prohlášení, postupujte `Sub` – klíčové slovo s názvem podle postupu, pak se seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="1c9bb-110">Umístit příkazy kódu podle postupu mezi `Sub` a `End Sub` příkazy.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="1c9bb-111">Chcete-li vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="1c9bb-111">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="1c9bb-112">Mimo všechny procedury, použijte `Function` příkazu, za nímž následuje `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="1c9bb-113">V `Function` příkazu, postupujte `Function` – klíčové slovo s názvem podle postupu, pak se seznam parametrů v závorkách a potom `As` klauzule určující datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3. <span data-ttu-id="1c9bb-114">Umístit příkazy kódu podle postupu mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4. <span data-ttu-id="1c9bb-115">Použití `Return` příkazu vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="1c9bb-116">Připojit nový postup se starou, opakované bloky kódu</span><span class="sxs-lookup"><span data-stu-id="1c9bb-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1. <span data-ttu-id="1c9bb-117">Zkontrolujte, že můžete definovat nové postupu na místě, kde původní kód má přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2. <span data-ttu-id="1c9bb-118">V bloku vaše staré, opakované kódu nahraďte příkazy, které provádějí opakované úlohy s jeden příkaz, který volá `Sub` nebo `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3. <span data-ttu-id="1c9bb-119">Pokud je vaše postup `Function` , která vrací hodnotu, ujistěte se, že volání příkazu provede akci s vrácenou hodnotu, jako je ukládání do proměnné, jinak hodnota se ztratí.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c9bb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c9bb-120">Example</span></span>  
 <span data-ttu-id="1c9bb-121">Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c9bb-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c9bb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c9bb-122">See also</span></span>

- [<span data-ttu-id="1c9bb-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="1c9bb-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1c9bb-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="1c9bb-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="1c9bb-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="1c9bb-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="1c9bb-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1c9bb-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1c9bb-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="1c9bb-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1c9bb-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="1c9bb-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1c9bb-129">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="1c9bb-129">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="1c9bb-130">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="1c9bb-130">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="1c9bb-131">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="1c9bb-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="1c9bb-132">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c9bb-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
