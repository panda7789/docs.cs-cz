---
title: Definování tříd
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
ms.openlocfilehash: bd3f6e5cff41551240d9904ab93af8758eb104d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346078"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="ec83a-102">Návod: Definování tříd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec83a-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="ec83a-103">Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="ec83a-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="ec83a-104">Také ukazuje, jak přidat vlastnosti a metody do nové třídy a ukazuje, jak inicializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="ec83a-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="ec83a-105">Definování třídy</span><span class="sxs-lookup"><span data-stu-id="ec83a-105">To define a class</span></span>
  
1. <span data-ttu-id="ec83a-106">Vytvořte projekt kliknutím na **Nový projekt** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="ec83a-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="ec83a-107">Zobrazí se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="ec83a-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ec83a-108">Vyberte možnost aplikace systému Windows ze seznamu Visual Basic šablony projektu, chcete-li zobrazit nový projekt.</span><span class="sxs-lookup"><span data-stu-id="ec83a-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="ec83a-109">Kliknutím na **Přidat třídu** v nabídce **projekt** přidejte do projektu novou třídu.</span><span class="sxs-lookup"><span data-stu-id="ec83a-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="ec83a-110">Zobrazí se dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="ec83a-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="ec83a-111">Vyberte šablonu **třídy** .</span><span class="sxs-lookup"><span data-stu-id="ec83a-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="ec83a-112">Pojmenujte novou třídu `UserNameInfo.vb`a potom kliknutím na tlačítko **Přidat** zobrazte kód pro novou třídu.</span><span class="sxs-lookup"><span data-stu-id="ec83a-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="ec83a-113">Pomocí **editoru kódu** Visual Basic můžete přidat třídu do formuláře po spuštění zadáním klíčového slova `Class` následovaného názvem nové třídy.</span><span class="sxs-lookup"><span data-stu-id="ec83a-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="ec83a-114">**Editor kódu** poskytuje odpovídající příkaz `End Class` za vás.</span><span class="sxs-lookup"><span data-stu-id="ec83a-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="ec83a-115">Definujte soukromé pole pro třídu přidáním následujícího kódu mezi příkazy `Class` a `End Class`:</span><span class="sxs-lookup"><span data-stu-id="ec83a-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="ec83a-116">Deklarace pole jako `Private` znamená, že může být použita pouze v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="ec83a-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="ec83a-117">Pole, která jsou k dispozici vně třídy, můžete zpřístupnit pomocí modifikátorů přístupu, jako je `Public`, které poskytují další přístup.</span><span class="sxs-lookup"><span data-stu-id="ec83a-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="ec83a-118">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ec83a-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="ec83a-119">Definujte vlastnost pro třídu přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ec83a-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="ec83a-120">Definujte metodu pro třídu přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ec83a-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="ec83a-121">Definujte parametrizovaný konstruktor pro novou třídu přidáním procedury s názvem `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="ec83a-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="ec83a-122">Konstruktor `Sub New` se nazývá automaticky při vytvoření objektu založeného na této třídě.</span><span class="sxs-lookup"><span data-stu-id="ec83a-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="ec83a-123">Tento konstruktor nastaví hodnotu pole, které obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="ec83a-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="ec83a-124">Chcete-li vytvořit tlačítko pro otestování třídy</span><span class="sxs-lookup"><span data-stu-id="ec83a-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="ec83a-125">Změňte spouštěcí formulář na režim návrhu kliknutím pravým tlačítkem myši na jeho název v **Průzkumník řešení** a následným kliknutím na položku **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ec83a-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="ec83a-126">Ve výchozím nastavení je úvodní formulář pro projekty aplikací pro Windows pojmenovaný Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="ec83a-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="ec83a-127">Pak se zobrazí hlavní formulář.</span><span class="sxs-lookup"><span data-stu-id="ec83a-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="ec83a-128">Přidejte do hlavního formuláře tlačítko a dvojím kliknutím na něj zobrazte kód pro obslužnou rutinu události `Button1_Click`.</span><span class="sxs-lookup"><span data-stu-id="ec83a-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="ec83a-129">Přidejte následující kód pro volání testovací procedury:</span><span class="sxs-lookup"><span data-stu-id="ec83a-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="ec83a-130">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ec83a-130">To run your application</span></span>
  
1. <span data-ttu-id="ec83a-131">Spusťte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="ec83a-131">Run your application by pressing F5.</span></span> <span data-ttu-id="ec83a-132">Klikněte na tlačítko ve formuláři pro volání testovací procedury.</span><span class="sxs-lookup"><span data-stu-id="ec83a-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="ec83a-133">Zobrazí se zpráva s oznámením, že původní `UserName` jsou "MOORE, BOBBY", protože procedura volala metodu `Capitalize` objektu.</span><span class="sxs-lookup"><span data-stu-id="ec83a-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="ec83a-134">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ec83a-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="ec83a-135">Procedura `Button1 Click` změní hodnotu vlastnosti `UserName` a zobrazí zprávu s oznámením, že nová hodnota `UserName` je "Worden, Jana".</span><span class="sxs-lookup"><span data-stu-id="ec83a-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec83a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec83a-136">See also</span></span>

- [<span data-ttu-id="ec83a-137">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec83a-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="ec83a-138">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="ec83a-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
