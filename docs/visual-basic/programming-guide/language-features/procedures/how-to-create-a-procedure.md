---
title: "Postupy: Vytvoření procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a44918b7a1426d215cee0ff2981f5763432a48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="32b0c-102">Postupy: Vytvoření procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32b0c-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="32b0c-103">Uzavřete procedury mezi počáteční příkaz deklarace (`Sub` nebo `Function`) a příkazu koncová deklarace (`End Sub` nebo `End Function`).</span><span class="sxs-lookup"><span data-stu-id="32b0c-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="32b0c-104">Všechny postup kód je mezi těmito příkazy.</span><span class="sxs-lookup"><span data-stu-id="32b0c-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="32b0c-105">Procedury nemůže obsahovat jinou proceduru, jeho počáteční a koncovou příkazy musí být mimo jiné procedury.</span><span class="sxs-lookup"><span data-stu-id="32b0c-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="32b0c-106">Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohy jednou jako proceduru a poté ji volat z různých místech v kódu.</span><span class="sxs-lookup"><span data-stu-id="32b0c-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="32b0c-107">K vytvoření procedury, která nevrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="32b0c-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="32b0c-108">Mimo jiné postup použijte `Sub` prohlášení, za nímž následuje `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="32b0c-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="32b0c-109">V `Sub` prohlášení, postupujte podle `Sub` – klíčové slovo s názvem postup, pak se seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="32b0c-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="32b0c-110">Umístit postup kód příkazy mezi `Sub` a `End Sub` příkazy.</span><span class="sxs-lookup"><span data-stu-id="32b0c-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="32b0c-111">K vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="32b0c-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="32b0c-112">Mimo jiné postup použijte `Function` prohlášení, za nímž následuje `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="32b0c-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="32b0c-113">V `Function` prohlášení, postupujte podle `Function` – klíčové slovo s názvem postup, pak se seznam parametrů v závorkách a potom `As` klauzule určující datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32b0c-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="32b0c-114">Umístit postup kód příkazy mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="32b0c-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="32b0c-115">Použití `Return` příkaz k vrácení hodnoty volání kódu.</span><span class="sxs-lookup"><span data-stu-id="32b0c-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="32b0c-116">Připojit nový postup s původním, opakovaných bloky kódu</span><span class="sxs-lookup"><span data-stu-id="32b0c-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="32b0c-117">Zajistěte, aby že definovat nový postup na místě, kde původní kód k němu má přístup.</span><span class="sxs-lookup"><span data-stu-id="32b0c-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="32b0c-118">V bloku vaše staré, opakovaných kódu nahraďte příkazy, které provádějí opakované úlohy s jediný příkaz, který volá `Sub` nebo `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="32b0c-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="32b0c-119">Pokud je vaše postupu `Function` , vrátí hodnotu, ujistěte se, že volání údajů provádí akce s vrácené hodnoty, jako je například ukládání do proměnné, jinak hodnota budou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="32b0c-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b0c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="32b0c-120">Example</span></span>  
 <span data-ttu-id="32b0c-121">Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32b0c-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="32b0c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="32b0c-122">See Also</span></span>  
 [<span data-ttu-id="32b0c-123">Postupy</span><span class="sxs-lookup"><span data-stu-id="32b0c-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="32b0c-124">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="32b0c-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="32b0c-125">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="32b0c-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="32b0c-126">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="32b0c-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="32b0c-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="32b0c-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="32b0c-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="32b0c-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="32b0c-129">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="32b0c-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="32b0c-130">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="32b0c-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="32b0c-131">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="32b0c-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="32b0c-132">Objektově orientované programování</span><span class="sxs-lookup"><span data-stu-id="32b0c-132">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
