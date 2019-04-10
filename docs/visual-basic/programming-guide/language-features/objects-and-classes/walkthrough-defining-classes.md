---
title: Definování třídy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326213"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="e558c-102">Návod: Definování třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e558c-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="e558c-103">Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="e558c-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="e558c-104">Také ukazuje, jak přidat vlastnosti a metody do nové třídy a ukazuje, jak inicializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="e558c-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="e558c-105">Definování třídy</span><span class="sxs-lookup"><span data-stu-id="e558c-105">To define a class</span></span>
  
1. <span data-ttu-id="e558c-106">Vytvořte projekt kliknutím **nový projekt** na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e558c-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="e558c-107">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e558c-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="e558c-108">Vyberte ze seznamu šablon projektů jazyka Visual Basic k zobrazení nového projektu aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="e558c-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="e558c-109">Přidejte novou třídu do projektu kliknutím **přidat třídu** na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e558c-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="e558c-110">Zobrazí se dialogové okno **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="e558c-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="e558c-111">Vyberte **třídy** šablony.</span><span class="sxs-lookup"><span data-stu-id="e558c-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="e558c-112">Pojmenujte novou třídu `UserNameInfo.vb`a potom klikněte na tlačítko **přidat** zobrazíte kód pro novou třídu.</span><span class="sxs-lookup"><span data-stu-id="e558c-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="e558c-113">Můžete použít Visual Basic **Editor kódu** přidání třídy do svého formuláře po spuštění zadáním `Class` – klíčové slovo, za nímž následuje název nové třídy.</span><span class="sxs-lookup"><span data-stu-id="e558c-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="e558c-114">**Editor kódu** poskytuje odpovídající `End Class` příkaz za vás.</span><span class="sxs-lookup"><span data-stu-id="e558c-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="e558c-115">Definovat privátní pole pro třídu přidáním následujícího kódu mezi `Class` a `End Class` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e558c-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="e558c-116">Deklarace pole jako `Private` znamená, že je možné pouze v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="e558c-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="e558c-117">Můžete zpřístupnit pole z mimo třídu pomocí modifikátorů přístupu, jako `Public` , které poskytují další přístup.</span><span class="sxs-lookup"><span data-stu-id="e558c-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="e558c-118">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e558c-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="e558c-119">Definujte vlastnost třídy přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="e558c-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="e558c-120">Definování metody pro třídu přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="e558c-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="e558c-121">Definování konstruktoru s parametry pro novou třídu přidáním postup s názvem `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="e558c-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="e558c-122">`Sub New` Konstruktor je automaticky volána, když je vytvořen objekt na základě této třídy.</span><span class="sxs-lookup"><span data-stu-id="e558c-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="e558c-123">Tento konstruktor nastaví hodnotu pole, která obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="e558c-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="e558c-124">Chcete-li vytvořit tlačítko pro testovací třídu</span><span class="sxs-lookup"><span data-stu-id="e558c-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="e558c-125">Změna formuláře úvodního formuláře do režimu návrhu kliknutím pravým tlačítkem myši jejího názvu do **Průzkumníka řešení** a pak levým na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e558c-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="e558c-126">Ve výchozím nastavení je formulář spuštění pro projekty aplikací pro Windows s názvem Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="e558c-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="e558c-127">Hlavní formulář se potom zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e558c-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="e558c-128">Přidání tlačítka pro hlavní formulář a dvojím kliknutím ho zobrazte kód `Button1_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e558c-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="e558c-129">Přidejte následující kód do volání procedury testu:</span><span class="sxs-lookup"><span data-stu-id="e558c-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="e558c-130">Ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e558c-130">To run your application</span></span>
  
1. <span data-ttu-id="e558c-131">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e558c-131">Run your application by pressing F5.</span></span> <span data-ttu-id="e558c-132">Klikněte na tlačítko na formulář pro volání procedury testu.</span><span class="sxs-lookup"><span data-stu-id="e558c-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="e558c-133">Zobrazí se zpráva oznamující, že původní `UserName` je "MOORE, Jana", protože procedura volána `Capitalize` metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="e558c-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="e558c-134">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e558c-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="e558c-135">`Button1 Click` Postupu změní hodnotu `UserName` vlastnost a zobrazí zprávu oznamující, že nová hodnota `UserName` je "Worden Joe".</span><span class="sxs-lookup"><span data-stu-id="e558c-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e558c-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e558c-136">See also</span></span>

- [<span data-ttu-id="e558c-137">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e558c-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="e558c-138">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="e558c-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
