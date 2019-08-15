---
title: 'Návod: Demonstrace vizuálního dědění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040323"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="012f7-102">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="012f7-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="012f7-103">Dědičnost vizuálů umožňuje zobrazit ovládací prvky na základním formuláři a přidat nové ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="012f7-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="012f7-104">V tomto návodu vytvoříte základní formulář a zkompilujete ho do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="012f7-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="012f7-105">Tuto knihovnu tříd naimportujete do jiného projektu a vytvoříte nový formulář, který bude dědit ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="012f7-106">V tomto návodu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="012f7-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="012f7-107">Vytvořte projekt knihovny tříd obsahující základní formulář.</span><span class="sxs-lookup"><span data-stu-id="012f7-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="012f7-108">Přidejte tlačítko s vlastnostmi, které mohou změnit odvozené třídy základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="012f7-109">Přidejte tlačítko, které nemůže být změněno děděním základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="012f7-110">Vytvořte projekt obsahující formulář, ze `BaseForm`kterého se dědí.</span><span class="sxs-lookup"><span data-stu-id="012f7-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="012f7-111">Nakonec tento návod ukáže rozdíl mezi soukromými a chráněnými ovládacími prvky ve zděděném formuláři.</span><span class="sxs-lookup"><span data-stu-id="012f7-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="012f7-112">Ne všechny ovládací prvky podporují vizuální dědění ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="012f7-113">Následující ovládací prvky nepodporují Scénář popsaný v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="012f7-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
>  <xref:System.Windows.Forms.WebBrowser>
>
>  <xref:System.Windows.Forms.ToolStrip>
>
>  <xref:System.Windows.Forms.ToolStripPanel>
>
>  <xref:System.Windows.Forms.TableLayoutPanel>
>
>  <xref:System.Windows.Forms.FlowLayoutPanel>
>
>  <xref:System.Windows.Forms.DataGridView>
>
>  <span data-ttu-id="012f7-114">Tyto ovládací prvky ve zděděném formuláři jsou vždycky jen pro čtení, bez ohledu na modifikátory, které`private`používáte `protected`(, `public`nebo).</span><span class="sxs-lookup"><span data-stu-id="012f7-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="012f7-115">Vytvořit projekt knihovny tříd obsahující základní formulář</span><span class="sxs-lookup"><span data-stu-id="012f7-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="012f7-116">V aplikaci Visual Studio v nabídce **soubor** vyberte možnost **Nový** > **projekt** , čímž otevřete dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="012f7-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="012f7-117">Vytvořte aplikaci model Windows Forms s názvem `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="012f7-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="012f7-118">Chcete-li vytvořit knihovnu tříd namísto standardní model Windows Forms aplikace, v **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **BaseFormLibrary** a poté vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="012f7-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="012f7-119">Ve vlastnostech projektu změňte **Typ výstupu** z **aplikace systému Windows** na **Knihovna tříd**.</span><span class="sxs-lookup"><span data-stu-id="012f7-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="012f7-120">V nabídce **soubor** klikněte na příkaz **Uložit vše** a uložte projekt a soubory do výchozího umístění.</span><span class="sxs-lookup"><span data-stu-id="012f7-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

 <span data-ttu-id="012f7-121">Následující dva postupy přidávají tlačítka do základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="012f7-122">K demonstraci vizuální dědičnosti získáte tlačítka různé úrovně přístupu nastavením jejich `Modifiers` vlastností.</span><span class="sxs-lookup"><span data-stu-id="012f7-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="012f7-123">Přidat tlačítko, které dědí dědění základního formuláře, se může změnit.</span><span class="sxs-lookup"><span data-stu-id="012f7-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="012f7-124">Otevřete **Form1** v návrháři.</span><span class="sxs-lookup"><span data-stu-id="012f7-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="012f7-125">Na kartě **všechny model Windows Forms** panelu **nástrojů**klikněte dvakrát na tlačítko a přidejte tak tlačítko do formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="012f7-126">Pomocí myši umístěte a změňte velikost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="012f7-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="012f7-127">V okno Vlastnosti nastavte následující vlastnosti tlačítka:</span><span class="sxs-lookup"><span data-stu-id="012f7-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="012f7-128">Nastavte vlastnost **text** na text **říká**se Hello.</span><span class="sxs-lookup"><span data-stu-id="012f7-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="012f7-129">Nastavte vlastnost **(Name)** na **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="012f7-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="012f7-130">Nastavte vlastnost **modifikátory** na hodnotu **Protected**.</span><span class="sxs-lookup"><span data-stu-id="012f7-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="012f7-131">Díky tomu je možné, že formuláře, které dědí z **Form1** , upravou vlastnosti **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="012f7-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="012f7-132">Dvojím kliknutím na tlačítko **vyslovení Hello** přidejte obslužnou rutinu události pro událost **Click** .</span><span class="sxs-lookup"><span data-stu-id="012f7-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="012f7-133">Do obslužné rutiny události přidejte následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="012f7-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="012f7-134">Přidejte tlačítko, které nemůže být změněno děděním základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="012f7-135">Přepněte do zobrazení návrhu kliknutím na kartu **Form1. vb [Design], Form1.cs [Design] nebo Form1. jsl [Design]** nad Editor kódu nebo stisknutím klávesy F7.</span><span class="sxs-lookup"><span data-stu-id="012f7-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="012f7-136">Přidejte druhé tlačítko a nastavte jeho vlastnosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="012f7-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="012f7-137">Nastavte vlastnost **text** na **nepravdu**.</span><span class="sxs-lookup"><span data-stu-id="012f7-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="012f7-138">Nastavte vlastnost **(Name)** na **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="012f7-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="012f7-139">Nastavte vlastnost **modifikátory** na **Private**.</span><span class="sxs-lookup"><span data-stu-id="012f7-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="012f7-140">To znemožňuje, aby formuláře, které dědí z **Form1** , upravily vlastnosti **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="012f7-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="012f7-141">Dvojím kliknutím na tlačítko **vyslovit** nemožnost přidejte obslužnou rutinu události pro událost **Click** .</span><span class="sxs-lookup"><span data-stu-id="012f7-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="012f7-142">Do procedury události vložte následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="012f7-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="012f7-143">V nabídce **sestavení** vyberte možnost **sestavit BaseForm Library** a sestavte knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="012f7-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="012f7-144">Po sestavení knihovny můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="012f7-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="012f7-145">Vytvoří projekt obsahující formulář, který dědí z základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="012f7-146">V nabídce **soubor** zvolte možnost **Přidat** a **Nový projekt** . otevře se dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="012f7-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="012f7-147">Vytvořte aplikaci model Windows Forms s názvem `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="012f7-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="012f7-148">Přidat zděděný formulář</span><span class="sxs-lookup"><span data-stu-id="012f7-148">Add an inherited form</span></span>

1. <span data-ttu-id="012f7-149">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **InheritanceTest** , vyberte možnost **Přidat**a poté vyberte možnost **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="012f7-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="012f7-150">V dialogovém okně **Přidat novou položku** vyberte kategorii **model Windows Forms** (Pokud máte seznam kategorií) a pak vyberte zděděnou šablonu **formuláře** .</span><span class="sxs-lookup"><span data-stu-id="012f7-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="012f7-151">Ponechte výchozí název `Form2` a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="012f7-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="012f7-152">V dialogovém okně **Výběr dědičnosti** vyberte v projektu **BaseFormLibrary** položku **Form1** jako formulář, ze kterého chcete dědit, a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="012f7-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="012f7-153">Tím se vytvoří formulář v projektu **InheritanceTest** , který je odvozený z formuláře v **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="012f7-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="012f7-154">Otevřete zděděný formulář (**Form2**) v Návrháři tak, že na něj dvakrát kliknete, pokud ještě není otevřený.</span><span class="sxs-lookup"><span data-stu-id="012f7-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

     <span data-ttu-id="012f7-155">V Návrháři mají zděděná tlačítka symbol (</span><span class="sxs-lookup"><span data-stu-id="012f7-155">In the designer, the inherited buttons have a symbol (</span></span>![Snímek obrazovky Visual Basic symbolu dědičnosti](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="012f7-157">) v horním rohu, což označuje, že jsou zděděné.</span><span class="sxs-lookup"><span data-stu-id="012f7-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="012f7-158">Vyberte tlačítko **vyslovit Hello** a sledujte úchyty pro změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="012f7-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="012f7-159">Vzhledem k tomu, že je toto tlačítko chráněno, mohou dědit jej přesunout, změnit jeho popisek a provést další úpravy.</span><span class="sxs-lookup"><span data-stu-id="012f7-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="012f7-160">Vyberte tlačítko pro nemožnost nevlastníení a Všimněte si, že nemá úchyty pro změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="012f7-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="012f7-161">Kromě toho v okně **vlastnosti** jsou vlastnosti tohoto tlačítka zobrazeny šedě, aby označovaly, že nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="012f7-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="012f7-162">Pokud používáte vizuál C#:</span><span class="sxs-lookup"><span data-stu-id="012f7-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="012f7-163">V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Form1** v projektu **InheritanceTest** a pak zvolte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="012f7-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="012f7-164">V zobrazeném okně se zprávou potvrďte odstranění kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="012f7-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="012f7-165">Otevřete soubor program.cs a změňte řádek `Application.Run(new Form1());` na. `Application.Run(new Form2());`</span><span class="sxs-lookup"><span data-stu-id="012f7-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="012f7-166">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **InheritanceTest** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="012f7-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="012f7-167">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **InheritanceTest** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="012f7-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="012f7-168">Na stránkách vlastností **InheritanceTest** nastavte **spouštěcí objekt** na zděděný formulář (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="012f7-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="012f7-169">Stisknutím klávesy **F5** spusťte aplikaci a sledujte chování zděděné formuláře.</span><span class="sxs-lookup"><span data-stu-id="012f7-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="012f7-170">Další kroky</span><span class="sxs-lookup"><span data-stu-id="012f7-170">Next steps</span></span>

<span data-ttu-id="012f7-171">Dědičnost uživatelských ovládacích prvků pracuje podobně jako u sebe.</span><span class="sxs-lookup"><span data-stu-id="012f7-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="012f7-172">Otevřete nový projekt knihovny tříd a přidejte uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="012f7-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="012f7-173">Umístěte ovládací prvky prvku na ni a zkompilujte projekt.</span><span class="sxs-lookup"><span data-stu-id="012f7-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="012f7-174">Otevřete jiný nový projekt knihovny tříd a přidejte odkaz na zkompilované knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="012f7-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="012f7-175">Také se pokuste přidat Zděděný ovládací prvek (pomocí dialogového okna **Přidat nové položky** ) do projektu a použít **Výběr dědičnosti**.</span><span class="sxs-lookup"><span data-stu-id="012f7-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="012f7-176">Přidejte uživatelský ovládací prvek a změňte `Inherits` příkaz (`:` v jazyce Visual C#).</span><span class="sxs-lookup"><span data-stu-id="012f7-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="012f7-177">Další informace najdete v tématu [jak: Zdědit model Windows Forms](how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="012f7-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="012f7-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="012f7-178">See also</span></span>

- [<span data-ttu-id="012f7-179">Postupy: Zdědit model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="012f7-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="012f7-180">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="012f7-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="012f7-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="012f7-181">Windows Forms</span></span>](../index.md)
