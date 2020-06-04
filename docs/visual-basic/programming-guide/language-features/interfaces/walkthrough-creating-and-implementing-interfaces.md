---
title: Vytvoření a implementace rozhraní
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405064"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="71286-102">Návod: Vytvoření a implementace rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71286-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="71286-103">Rozhraní popisují charakteristiky vlastností, metod a událostí, ale ponechají podrobnosti o implementaci až do struktur nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="71286-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="71286-104">Tento návod ukazuje, jak deklarovat a implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71286-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71286-105">Tento návod neposkytuje informace o tom, jak vytvořit uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71286-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="71286-106">Definování rozhraní</span><span class="sxs-lookup"><span data-stu-id="71286-106">To define an interface</span></span>
  
1. <span data-ttu-id="71286-107">Otevřete nový Visual Basic projekt aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="71286-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="71286-108">Přidejte do projektu nový modul kliknutím na **Přidat modul** v nabídce **projekt** .</span><span class="sxs-lookup"><span data-stu-id="71286-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="71286-109">Pojmenujte nový modul `Module1.vb` a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="71286-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="71286-110">Zobrazí se kód nového modulu.</span><span class="sxs-lookup"><span data-stu-id="71286-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="71286-111">Zadejte rozhraní `TestInterface` , které je pojmenované v rámci `Module1` , zadáním `Interface TestInterface` mezi `Module` `End Module` příkazy a a stisknutím klávesy ENTER.</span><span class="sxs-lookup"><span data-stu-id="71286-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="71286-112">**Editor kódu** odsadí `Interface` klíčové slovo a přidá `End Interface` příkaz pro vytvoření bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="71286-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="71286-113">Určete vlastnost, metodu a událost pro rozhraní umístěním následujícího kódu mezi `Interface` `End Interface` příkazy a:</span><span class="sxs-lookup"><span data-stu-id="71286-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="71286-114">Implementace</span><span class="sxs-lookup"><span data-stu-id="71286-114">Implementation</span></span>

 <span data-ttu-id="71286-115">Můžete si všimnout, že syntaxe použitá pro deklaraci členů rozhraní se liší od syntaxe použité k deklaraci členů třídy.</span><span class="sxs-lookup"><span data-stu-id="71286-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="71286-116">Tento rozdíl odráží skutečnost, že rozhraní nemohou obsahovat implementační kód.</span><span class="sxs-lookup"><span data-stu-id="71286-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="71286-117">Implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="71286-117">To implement the interface</span></span>
  
1. <span data-ttu-id="71286-118">Přidejte třídu s názvem `ImplementationClass` přidáním následujícího příkazu do `Module1` , po `End Interface` příkazu, ale před `End Module` příkazem, a stisknutím klávesy ENTER:</span><span class="sxs-lookup"><span data-stu-id="71286-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="71286-119">Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** `End Class` při stisknutí klávesy ENTER dodá odpovídajícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="71286-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="71286-120">Přidejte následující `Implements` příkaz do `ImplementationClass` , který pojmenuje rozhraní, které třída implementuje:</span><span class="sxs-lookup"><span data-stu-id="71286-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="71286-121">Pokud je uvedeno odděleně od jiných položek v horní části třídy nebo struktury, `Implements` příkaz označuje, že třída nebo struktura implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71286-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="71286-122">Pokud pracujete v integrovaném vývojovém prostředí, **Editor kódu** implementuje členy třídy vyžadované `TestInterface` při stisknutí klávesy ENTER a můžete přeskočit další krok.</span><span class="sxs-lookup"><span data-stu-id="71286-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="71286-123">Pokud nepracujete v integrovaném vývojovém prostředí, je nutné implementovat všechny členy rozhraní `MyInterface` .</span><span class="sxs-lookup"><span data-stu-id="71286-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="71286-124">Přidejte následující kód k `ImplementationClass` implementaci `Event1` , `Method1` a `Prop1` :</span><span class="sxs-lookup"><span data-stu-id="71286-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="71286-125">`Implements`Příkaz zajmenovává rozhraní a člen rozhraní, které je implementováno.</span><span class="sxs-lookup"><span data-stu-id="71286-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="71286-126">Dokončete definici `Prop1` přidáním soukromého pole do třídy, která ukládá hodnotu vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="71286-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="71286-127">Vrátí hodnotu `pval` z přístupového objektu Get vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="71286-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="71286-128">Nastavte hodnotu `pval` v přístupovém objektu sady vlastností.</span><span class="sxs-lookup"><span data-stu-id="71286-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="71286-129">Dokončete definici `Method1` přidáním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="71286-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="71286-130">Testování implementace rozhraní</span><span class="sxs-lookup"><span data-stu-id="71286-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="71286-131">Klikněte pravým tlačítkem myši na spouštěcí formulář v **Průzkumník řešení**a klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="71286-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="71286-132">Editor zobrazuje třídu pro úvodní formulář.</span><span class="sxs-lookup"><span data-stu-id="71286-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="71286-133">Ve výchozím nastavení se volá formulář pro spuštění `Form1` .</span><span class="sxs-lookup"><span data-stu-id="71286-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="71286-134">`testInstance`Do třídy přidejte následující pole `Form1` :</span><span class="sxs-lookup"><span data-stu-id="71286-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="71286-135">Deklarováním `testInstance` jako `WithEvents` `Form1` může třída zpracovávat své události.</span><span class="sxs-lookup"><span data-stu-id="71286-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="71286-136">Přidejte následující obslužnou rutinu události do `Form1` třídy pro zpracování událostí vyvolaných `testInstance` :</span><span class="sxs-lookup"><span data-stu-id="71286-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="71286-137">Přidejte podprogram s názvem `Test` do `Form1` třídy pro otestování třídy implementace:</span><span class="sxs-lookup"><span data-stu-id="71286-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="71286-138">`Test`Procedura vytvoří instanci třídy, která implementuje `MyInterface` , přiřadí tuto instanci k `testInstance` poli, nastaví vlastnost a spustí metodu prostřednictvím rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71286-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="71286-139">Přidejte kód pro volání `Test` procedury z `Form1 Load` procedury spouštěcího formuláře:</span><span class="sxs-lookup"><span data-stu-id="71286-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="71286-140">Spusťte `Test` proceduru stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="71286-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="71286-141">Zobrazí se zpráva "Prop1 byl nastaven na 9".</span><span class="sxs-lookup"><span data-stu-id="71286-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="71286-142">Po kliknutí na tlačítko OK se zobrazí zpráva "parametr X pro – Metoda1 je 5".</span><span class="sxs-lookup"><span data-stu-id="71286-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="71286-143">Klikněte na tlačítko OK a zobrazí se zpráva "obslužná rutina události byla zachycena událost".</span><span class="sxs-lookup"><span data-stu-id="71286-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71286-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="71286-144">See also</span></span>

- [<span data-ttu-id="71286-145">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="71286-145">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="71286-146">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="71286-146">Interfaces</span></span>](index.md)
- [<span data-ttu-id="71286-147">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="71286-147">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="71286-148">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="71286-148">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
