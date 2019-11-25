---
title: Vytvoření a implementace rozhraní
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 47176d2e7a512d8e8c27a90ac04d2a2a2af274b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345044"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="e759e-102">Návod: Vytvoření a implementace rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e759e-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="e759e-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span><span class="sxs-lookup"><span data-stu-id="e759e-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="e759e-104">This walkthrough demonstrates how to declare and implement an interface.</span><span class="sxs-lookup"><span data-stu-id="e759e-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e759e-105">This walkthrough doesn't provide information about how to create a user interface.</span><span class="sxs-lookup"><span data-stu-id="e759e-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="e759e-106">To define an interface</span><span class="sxs-lookup"><span data-stu-id="e759e-106">To define an interface</span></span>
  
1. <span data-ttu-id="e759e-107">Open a new Visual Basic Windows Application project.</span><span class="sxs-lookup"><span data-stu-id="e759e-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="e759e-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span><span class="sxs-lookup"><span data-stu-id="e759e-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="e759e-109">Name the new module `Module1.vb` and click **Add**.</span><span class="sxs-lookup"><span data-stu-id="e759e-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="e759e-110">The code for the new module is displayed.</span><span class="sxs-lookup"><span data-stu-id="e759e-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="e759e-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span><span class="sxs-lookup"><span data-stu-id="e759e-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="e759e-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span><span class="sxs-lookup"><span data-stu-id="e759e-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="e759e-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span><span class="sxs-lookup"><span data-stu-id="e759e-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="e759e-114">Implementace</span><span class="sxs-lookup"><span data-stu-id="e759e-114">Implementation</span></span>

 <span data-ttu-id="e759e-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span><span class="sxs-lookup"><span data-stu-id="e759e-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="e759e-116">This difference reflects the fact that interfaces cannot contain implementation code.</span><span class="sxs-lookup"><span data-stu-id="e759e-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="e759e-117">To implement the interface</span><span class="sxs-lookup"><span data-stu-id="e759e-117">To implement the interface</span></span>
  
1. <span data-ttu-id="e759e-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span><span class="sxs-lookup"><span data-stu-id="e759e-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="e759e-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span><span class="sxs-lookup"><span data-stu-id="e759e-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="e759e-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span><span class="sxs-lookup"><span data-stu-id="e759e-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="e759e-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span><span class="sxs-lookup"><span data-stu-id="e759e-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="e759e-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span><span class="sxs-lookup"><span data-stu-id="e759e-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="e759e-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="e759e-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="e759e-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="e759e-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="e759e-125">The `Implements` statement names the interface and interface member being implemented.</span><span class="sxs-lookup"><span data-stu-id="e759e-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="e759e-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span><span class="sxs-lookup"><span data-stu-id="e759e-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="e759e-127">Return the value of the `pval` from the property get accessor.</span><span class="sxs-lookup"><span data-stu-id="e759e-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="e759e-128">Set the value of `pval` in the property set accessor.</span><span class="sxs-lookup"><span data-stu-id="e759e-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="e759e-129">Complete the definition of `Method1` by adding the following code.</span><span class="sxs-lookup"><span data-stu-id="e759e-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="e759e-130">To test the implementation of the interface</span><span class="sxs-lookup"><span data-stu-id="e759e-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="e759e-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span><span class="sxs-lookup"><span data-stu-id="e759e-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="e759e-132">The editor displays the class for your startup form.</span><span class="sxs-lookup"><span data-stu-id="e759e-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="e759e-133">By default, the startup form is called `Form1`.</span><span class="sxs-lookup"><span data-stu-id="e759e-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="e759e-134">Add the following `testInstance` field to the `Form1` class:</span><span class="sxs-lookup"><span data-stu-id="e759e-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="e759e-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span><span class="sxs-lookup"><span data-stu-id="e759e-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="e759e-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="e759e-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="e759e-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span><span class="sxs-lookup"><span data-stu-id="e759e-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="e759e-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span><span class="sxs-lookup"><span data-stu-id="e759e-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="e759e-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span><span class="sxs-lookup"><span data-stu-id="e759e-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="e759e-140">Run the `Test` procedure by pressing F5.</span><span class="sxs-lookup"><span data-stu-id="e759e-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="e759e-141">The message "Prop1 was set to 9" is displayed.</span><span class="sxs-lookup"><span data-stu-id="e759e-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="e759e-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span><span class="sxs-lookup"><span data-stu-id="e759e-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="e759e-143">Click OK, and the message "The event handler caught the event" is displayed.</span><span class="sxs-lookup"><span data-stu-id="e759e-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e759e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e759e-144">See also</span></span>

- [<span data-ttu-id="e759e-145">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="e759e-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="e759e-146">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e759e-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="e759e-147">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="e759e-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="e759e-148">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="e759e-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
