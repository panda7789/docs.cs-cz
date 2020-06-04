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
ms.openlocfilehash: 646c6ce307131f3edba194af19920eade9c1753c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389111"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="8e479-102">Návod: Definování tříd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e479-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="8e479-103">Tento návod ukazuje, jak definovat třídy, které pak můžete použít k vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="8e479-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="8e479-104">Také ukazuje, jak přidat vlastnosti a metody do nové třídy a ukazuje, jak inicializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="8e479-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="8e479-105">Definování třídy</span><span class="sxs-lookup"><span data-stu-id="8e479-105">To define a class</span></span>
  
1. <span data-ttu-id="8e479-106">Vytvořte projekt kliknutím na **Nový projekt** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="8e479-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="8e479-107">Zobrazí se dialogové okno **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="8e479-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="8e479-108">Vyberte možnost aplikace systému Windows ze seznamu Visual Basic šablony projektu, chcete-li zobrazit nový projekt.</span><span class="sxs-lookup"><span data-stu-id="8e479-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="8e479-109">Kliknutím na **Přidat třídu** v nabídce **projekt** přidejte do projektu novou třídu.</span><span class="sxs-lookup"><span data-stu-id="8e479-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="8e479-110">Zobrazí se dialogové okno **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="8e479-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="8e479-111">Vyberte šablonu **třídy** .</span><span class="sxs-lookup"><span data-stu-id="8e479-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="8e479-112">Pojmenujte novou třídu `UserNameInfo.vb` a potom kliknutím na tlačítko **Přidat** zobrazte kód pro novou třídu.</span><span class="sxs-lookup"><span data-stu-id="8e479-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="8e479-113">Pomocí **editoru kódu** Visual Basic můžete přidat třídu do formuláře po spuštění zadáním `Class` klíčového slova následovaného názvem nové třídy.</span><span class="sxs-lookup"><span data-stu-id="8e479-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="8e479-114">**Editor kódu** poskytuje odpovídající `End Class` příkaz pro vás.</span><span class="sxs-lookup"><span data-stu-id="8e479-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="8e479-115">Definujte soukromé pole pro třídu přidáním následujícího kódu mezi `Class` `End Class` příkazy a:</span><span class="sxs-lookup"><span data-stu-id="8e479-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="8e479-116">Deklarace pole jako `Private` znamená, že se dá použít jenom uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="8e479-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="8e479-117">Pole, která jsou k dispozici vně třídy, můžete zpřístupnit pomocí modifikátorů přístupu, jako je například `Public` , které poskytují více přístupu.</span><span class="sxs-lookup"><span data-stu-id="8e479-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="8e479-118">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8e479-118">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="8e479-119">Definujte vlastnost pro třídu přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e479-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="8e479-120">Definujte metodu pro třídu přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8e479-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="8e479-121">Definujte parametrizovaný konstruktor pro novou třídu přidáním procedury s názvem `Sub New` :</span><span class="sxs-lookup"><span data-stu-id="8e479-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="8e479-122">`Sub New`Konstruktor se nazývá automaticky, pokud je objekt založen na této třídě vytvořen.</span><span class="sxs-lookup"><span data-stu-id="8e479-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="8e479-123">Tento konstruktor nastaví hodnotu pole, které obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="8e479-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="8e479-124">Chcete-li vytvořit tlačítko pro otestování třídy</span><span class="sxs-lookup"><span data-stu-id="8e479-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="8e479-125">Změňte spouštěcí formulář na režim návrhu kliknutím pravým tlačítkem myši na jeho název v **Průzkumník řešení** a následným kliknutím na položku **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="8e479-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="8e479-126">Ve výchozím nastavení je úvodní formulář pro projekty aplikací pro Windows pojmenovaný Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="8e479-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="8e479-127">Pak se zobrazí hlavní formulář.</span><span class="sxs-lookup"><span data-stu-id="8e479-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="8e479-128">Přidejte do hlavního formuláře tlačítko a dvojím kliknutím na něj zobrazte kód pro `Button1_Click` obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="8e479-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="8e479-129">Přidejte následující kód pro volání testovací procedury:</span><span class="sxs-lookup"><span data-stu-id="8e479-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="8e479-130">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="8e479-130">To run your application</span></span>
  
1. <span data-ttu-id="8e479-131">Spusťte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="8e479-131">Run your application by pressing F5.</span></span> <span data-ttu-id="8e479-132">Klikněte na tlačítko ve formuláři pro volání testovací procedury.</span><span class="sxs-lookup"><span data-stu-id="8e479-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="8e479-133">Zobrazí se zpráva s oznámením, že originál `UserName` je "Moore, Bobby", protože procedura se nazývá `Capitalize` metoda objektu.</span><span class="sxs-lookup"><span data-stu-id="8e479-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="8e479-134">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="8e479-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="8e479-135">`Button1 Click`Procedura změní hodnotu `UserName` vlastnosti a zobrazí zprávu s oznámením, že nová hodnota `UserName` je "Worden, Jana".</span><span class="sxs-lookup"><span data-stu-id="8e479-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e479-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e479-136">See also</span></span>

- [<span data-ttu-id="8e479-137">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e479-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="8e479-138">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="8e479-138">Objects and Classes</span></span>](index.md)
