---
title: "Vytvoření a implementace rozhraní (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="57e08-102">Návod: Vytvoření a implementace rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e08-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="57e08-103">Rozhraní popisují charakteristiky vlastností, metod a událostí, ale nechte podrobnosti implementace až struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="57e08-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="57e08-104">Tento návod ukazuje, jak deklarace a implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57e08-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57e08-105">Tento návod neposkytuje informace o tom, jak vytvořit uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57e08-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="57e08-106">Chcete-li definovat rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e08-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="57e08-107">Otevřete nový [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="57e08-107">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="57e08-108">Přidejte nový modul do projektu kliknutím **přidat modul** na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="57e08-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="57e08-109">Název nového modulu `Module1.vb` a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="57e08-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="57e08-110">Kód pro nový modul se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="57e08-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="57e08-111">Definování rozhraní s názvem `TestInterface` v rámci `Module1` zadáním `Interface TestInterface` mezi `Module` a `End Module` příkazy a stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="57e08-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="57e08-112">**Editor kódu** odsazení `Interface` – klíčové slovo a přidá `End Interface` příkaz k vytvoření bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="57e08-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="57e08-113">Definuje vlastnosti, metodu a událostí pro rozhraní následující kód mezi umístěním `Interface` a `End Interface` příkazy:</span><span class="sxs-lookup"><span data-stu-id="57e08-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a><span data-ttu-id="57e08-114">Implementace</span><span class="sxs-lookup"><span data-stu-id="57e08-114">Implementation</span></span>  
 <span data-ttu-id="57e08-115">Můžete si všimnout, že syntaxe používá k deklaraci členové rozhraní se liší od syntaxe používá k deklaraci členy třídy.</span><span class="sxs-lookup"><span data-stu-id="57e08-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="57e08-116">Tento rozdíl odráží fakt, že rozhraní nemůže obsahovat implementaci kódu.</span><span class="sxs-lookup"><span data-stu-id="57e08-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="57e08-117">Implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e08-117">To implement the interface</span></span>  
  
1.  <span data-ttu-id="57e08-118">Přidejte třídu s názvem `ImplementationClass` přidáním následující příkaz a `Module1`, po `End Interface` příkaz ale předtím, než `End Module` příkaz a stiskněte ENTER:</span><span class="sxs-lookup"><span data-stu-id="57e08-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     <span data-ttu-id="57e08-119">Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** poskytuje odpovídající `End Class` příkaz po stisknutí klávesy ENTER.</span><span class="sxs-lookup"><span data-stu-id="57e08-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="57e08-120">Přidejte následující `Implements` příkaz, který má `ImplementationClass`, které názvy rozhraní třída implementuje:</span><span class="sxs-lookup"><span data-stu-id="57e08-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     <span data-ttu-id="57e08-121">Když uvedené odděleně od jiných položek v horní části třídu nebo strukturu, `Implements` příkaz označuje, že třídu nebo strukturu implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57e08-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="57e08-122">Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** implementuje členy třídy vyžadovanou `TestInterface` při stisknutí klávesy ENTER, a můžete přejít na další krok.</span><span class="sxs-lookup"><span data-stu-id="57e08-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="57e08-123">Pokud nepracujete v integrovaném vývojovém prostředí, je nutné implementovat všechny členy rozhraní `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="57e08-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="57e08-124">Přidejte následující kód, který `ImplementationClass` implementovat `Event1`, `Method1`, a `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="57e08-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     <span data-ttu-id="57e08-125">`Implements` Příkaz názvy rozhraní a člena rozhraní se implementuje.</span><span class="sxs-lookup"><span data-stu-id="57e08-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="57e08-126">Dokončit definici `Prop1` přidáním soukromé pole na třídu, která uložená hodnota vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57e08-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     <span data-ttu-id="57e08-127">Vrátí hodnotu `pval` z vlastnosti načtení přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="57e08-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     <span data-ttu-id="57e08-128">Nastavte hodnotu `pval` ve vlastnosti nastavení přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="57e08-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  <span data-ttu-id="57e08-129">Dokončit definici `Method1` přidáním následující kód.</span><span class="sxs-lookup"><span data-stu-id="57e08-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="57e08-130">Pro testování implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e08-130">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="57e08-131">Klikněte pravým tlačítkem na spouštěcí formulář pro projekt v **Průzkumníku řešení**a klikněte na tlačítko **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="57e08-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="57e08-132">Editor zobrazí třídu pro formulář spuštění.</span><span class="sxs-lookup"><span data-stu-id="57e08-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="57e08-133">Ve výchozím nastavení, je volána spouštěcí formulář `Form1`.</span><span class="sxs-lookup"><span data-stu-id="57e08-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="57e08-134">Přidejte následující `testInstance` pole na `Form1` třídy:</span><span class="sxs-lookup"><span data-stu-id="57e08-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     <span data-ttu-id="57e08-135">Deklarováním `testInstance` jako `WithEvents`, `Form1` třída může zpracovávat události.</span><span class="sxs-lookup"><span data-stu-id="57e08-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="57e08-136">Přidejte následující obslužné rutiny události pro `Form1` třídy pro zpracování události vyvolané službou `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="57e08-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  <span data-ttu-id="57e08-137">Přidat podprogramu s názvem `Test` k `Form1` třída k testování třída implementace:</span><span class="sxs-lookup"><span data-stu-id="57e08-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     <span data-ttu-id="57e08-138">`Test` Postup vytvoří instanci třídy, který implementuje `MyInterface`, přiřadí tuto instanci k `testInstance` pole, nastaví vlastnost a spustí metodu přes rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57e08-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="57e08-139">Přidejte kód volání `Test` procedury `Form1 Load` postup spuštění formuláře:</span><span class="sxs-lookup"><span data-stu-id="57e08-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  <span data-ttu-id="57e08-140">Spustit `Test` postup stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="57e08-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="57e08-141">Zobrazí se zpráva "vlastnost1 byla nastavena na 9".</span><span class="sxs-lookup"><span data-stu-id="57e08-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="57e08-142">Zobrazí se po kliknutí na tlačítko OK, zpráva "parametr X pro Method1 je 5".</span><span class="sxs-lookup"><span data-stu-id="57e08-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="57e08-143">Klikněte na tlačítko OK a zobrazí se zpráva "obslužné rutiny události zachycena událost".</span><span class="sxs-lookup"><span data-stu-id="57e08-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e08-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="57e08-144">See Also</span></span>  
 [<span data-ttu-id="57e08-145">Implements – příkaz</span><span class="sxs-lookup"><span data-stu-id="57e08-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="57e08-146">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e08-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="57e08-147">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="57e08-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="57e08-148">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="57e08-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
