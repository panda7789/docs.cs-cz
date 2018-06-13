---
title: Definice tříd (Visual Basic)
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
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650638"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="59fb4-102">Návod: Definování tříd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59fb4-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="59fb4-103">Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="59fb4-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="59fb4-104">Také ukazuje, jak přidat vlastnosti a metody pro novou třídu a ukazuje, jak k chybě při inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="59fb4-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="59fb4-105">Chcete-li definovat třídu</span><span class="sxs-lookup"><span data-stu-id="59fb4-105">To define a class</span></span>
  
1.  <span data-ttu-id="59fb4-106">Vytvoření projektu kliknutím **nový projekt** na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="59fb4-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="59fb4-107">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="59fb4-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="59fb4-108">Aplikace systému Windows vyberte ze seznamu šablon projektu jazyka Visual Basic pro zobrazení nového projektu.</span><span class="sxs-lookup"><span data-stu-id="59fb4-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="59fb4-109">Přidejte novou třídu do projektu kliknutím **přidat třídu** na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="59fb4-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="59fb4-110">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="59fb4-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="59fb4-111">Vyberte **třída** šablony.</span><span class="sxs-lookup"><span data-stu-id="59fb4-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="59fb4-112">Pojmenujte novou třídu `UserNameInfo.vb`a potom klikněte na **přidat** k zobrazení kódu nové třídy.</span><span class="sxs-lookup"><span data-stu-id="59fb4-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="59fb4-113">Můžete použít Visual Basicu **Editor kódu** přidat třídu do svého formuláře spuštění zadáním `Class` – klíčové slovo a název nové třídy.</span><span class="sxs-lookup"><span data-stu-id="59fb4-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="59fb4-114">**Editor kódu** poskytuje odpovídající `End Class` příkaz za vás.</span><span class="sxs-lookup"><span data-stu-id="59fb4-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="59fb4-115">Definování soukromé pole pro třídu přidáním následujícího kódu mezi `Class` a `End Class` příkazy:</span><span class="sxs-lookup"><span data-stu-id="59fb4-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="59fb4-116">Deklarace pole jako `Private` znamená ho lze použít pouze v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="59fb4-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="59fb4-117">Můžete zpřístupnit pole z mimo třídu pomocí modifikátory přístupu, jako `Public` , poskytovat další přístup.</span><span class="sxs-lookup"><span data-stu-id="59fb4-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="59fb4-118">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="59fb4-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="59fb4-119">Definujte vlastnosti pro třídu přidáním následující kód:</span><span class="sxs-lookup"><span data-stu-id="59fb4-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  <span data-ttu-id="59fb4-120">Definujte metody pro třídu přidáním následující kód:</span><span class="sxs-lookup"><span data-stu-id="59fb4-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="59fb4-121">Definice parametrizované konstruktoru pro novou třídu přidáním proceduru s názvem `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="59fb4-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="59fb4-122">`Sub New` Konstruktor je automaticky volána, když je vytvořen objekt na základě této třídy.</span><span class="sxs-lookup"><span data-stu-id="59fb4-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="59fb4-123">Tento konstruktor nastaví hodnotu pole, která obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="59fb4-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="59fb4-124">Chcete-li vytvořit tlačítko můžete otestovat třídy</span><span class="sxs-lookup"><span data-stu-id="59fb4-124">To create a button to test the class</span></span>
  
1.  <span data-ttu-id="59fb4-125">Změnit formulář spuštění do režimu návrhu kliknutím pravým tlačítkem na jeho název v **Průzkumníku řešení** a pak levým na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="59fb4-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="59fb4-126">Ve výchozím nastavení je spouštěcí formulář pro projekty Windows aplikací s názvem Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="59fb4-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="59fb4-127">Hlavní formulář se potom zobrazí.</span><span class="sxs-lookup"><span data-stu-id="59fb4-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="59fb4-128">Přidání tlačítka do hlavní formulář a poklikejte na něj zobrazíte kód pro `Button1_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="59fb4-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="59fb4-129">Přidejte následující kód k volání procedury testu:</span><span class="sxs-lookup"><span data-stu-id="59fb4-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="59fb4-130">Spusťte aplikaci</span><span class="sxs-lookup"><span data-stu-id="59fb4-130">To run your application</span></span>
  
1.  <span data-ttu-id="59fb4-131">Spusťte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="59fb4-131">Run your application by pressing F5.</span></span> <span data-ttu-id="59fb4-132">Klikněte na tlačítko ve formuláři voláním procedury testu.</span><span class="sxs-lookup"><span data-stu-id="59fb4-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="59fb4-133">Zobrazí zprávu, že původní `UserName` je "STOKLASY, Jana", protože procedura volána `Capitalize` metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="59fb4-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="59fb4-134">Klikněte na tlačítko **OK** se zavřít okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="59fb4-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="59fb4-135">`Button1 Click` Postup změní hodnotu `UserName` vlastnost a zobrazí zprávu, že nová hodnota `UserName` je "Worden, Jan".</span><span class="sxs-lookup"><span data-stu-id="59fb4-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fb4-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="59fb4-136">See also</span></span>

[<span data-ttu-id="59fb4-137">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59fb4-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
[<span data-ttu-id="59fb4-138">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="59fb4-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)