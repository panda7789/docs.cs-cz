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
ms.openlocfilehash: a5e2a8b0bf982ff112d7930e331456fa69485dfc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665914"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="3a91a-102">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="3a91a-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="3a91a-103">Vizuální dědění vám umožní zobrazit ovládací prvky ve formuláři základní a přidání nových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3a91a-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="3a91a-104">V tomto návodu vytvoříte základní formulář a zkompilovat ji do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="3a91a-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="3a91a-105">Bude import této knihovně tříd do jiného projektu a vytvoření nového formuláře, která dědí ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="3a91a-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="3a91a-106">V tomto návodu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="3a91a-106">During this walkthrough, you will learn how to:</span></span>  
  
- <span data-ttu-id="3a91a-107">Vytvořte projekt knihovny tříd obsahující základní formulář.</span><span class="sxs-lookup"><span data-stu-id="3a91a-107">Create a class library project containing a base form.</span></span>  
  
- <span data-ttu-id="3a91a-108">Přidejte tlačítko s vlastnostmi, které odvozené třídy základní formulář můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="3a91a-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
- <span data-ttu-id="3a91a-109">Přidejte tlačítko, které nemůže upravit dědice základní formulář.</span><span class="sxs-lookup"><span data-stu-id="3a91a-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
- <span data-ttu-id="3a91a-110">Vytvořit projekt obsahující formulář, který dědí z `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="3a91a-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="3a91a-111">Nakonec tento návod vám ukáže rozdíl mezi soukromým a chráněným ovládacích prvků na zděděný formulář.</span><span class="sxs-lookup"><span data-stu-id="3a91a-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a91a-112">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="3a91a-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3a91a-113">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3a91a-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3a91a-114">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3a91a-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3a91a-115">Ne všechny ovládací prvky podporují vizuální dědění ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="3a91a-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="3a91a-116">Následující ovládací prvky podle scénáře popsaného v tomto názorném postupu nepodporují:</span><span class="sxs-lookup"><span data-stu-id="3a91a-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
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
>  <span data-ttu-id="3a91a-117">Tyto ovládací prvky ve formuláři zděděné jsou vždy jen pro čtení bez ohledu na to modifikátory použijete (`private`, `protected`, nebo `public`).</span><span class="sxs-lookup"><span data-stu-id="3a91a-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="3a91a-118">Kroky scénáře</span><span class="sxs-lookup"><span data-stu-id="3a91a-118">Scenario Steps</span></span>  
 <span data-ttu-id="3a91a-119">Prvním krokem je vytvoření základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="3a91a-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="3a91a-120">Chcete-li vytvořit projekt knihovny tříd obsahující základního formuláře</span><span class="sxs-lookup"><span data-stu-id="3a91a-120">To create a class library project containing a base form</span></span>  
  
1. <span data-ttu-id="3a91a-121">Z **souboru** nabídce zvolte **nový**a potom **projektu** otevřít **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3a91a-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="3a91a-122">Vytvoření aplikace Windows Forms s názvem `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="3a91a-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3. <span data-ttu-id="3a91a-123">K vytvoření knihovny tříd místo standardní aplikace Windows Forms v **Průzkumníka řešení**, klikněte pravým tlačítkem myši **BaseFormLibrary** uzel projektu a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4. <span data-ttu-id="3a91a-124">Ve vlastnostech projektu změnit **typ výstupu** z **aplikace Windows** k **knihovny tříd**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5. <span data-ttu-id="3a91a-125">Z **souboru** nabídce zvolte **Uložit vše** uložte projekt a soubory do výchozího umístění.</span><span class="sxs-lookup"><span data-stu-id="3a91a-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="3a91a-126">Následující dva postupy přidání tlačítek do základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="3a91a-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="3a91a-127">Abychom si předvedli vizuálního dědění, kterým pojmenujete tlačítka různé úrovně přístupu tak, že nastavíte jejich `Modifiers` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a91a-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="3a91a-128">Chcete-li přidat tlačítko, které můžete upravit dědice základního formuláře</span><span class="sxs-lookup"><span data-stu-id="3a91a-128">To add a button that inheritors of the base form can modify</span></span>  
  
1. <span data-ttu-id="3a91a-129">Otevřít **Form1** v návrháři.</span><span class="sxs-lookup"><span data-stu-id="3a91a-129">Open **Form1** in the designer.</span></span>  
  
2. <span data-ttu-id="3a91a-130">Na **všechny formuláře Windows** karty **nástrojů**, dvakrát klikněte na panel **tlačítko** přidáte tlačítka do formuláře.</span><span class="sxs-lookup"><span data-stu-id="3a91a-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="3a91a-131">Pro nastavení pozice a změňte velikost tlačítka pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="3a91a-131">Use the mouse to position and resize the button.</span></span>  
  
3. <span data-ttu-id="3a91a-132">V okně Vlastnosti nastavte následující vlastnosti tlačítka:</span><span class="sxs-lookup"><span data-stu-id="3a91a-132">In the Properties window, set the following properties of the button:</span></span>  
  
    - <span data-ttu-id="3a91a-133">Nastavte **Text** vlastnost **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    - <span data-ttu-id="3a91a-134">Nastavte **(název)** vlastnost **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    - <span data-ttu-id="3a91a-135">Nastavte **modifikátory** vlastnost **chráněné**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-135">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="3a91a-136">To umožňuje pro formuláře, které dědí **Form1** k úpravě vlastností **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4. <span data-ttu-id="3a91a-137">Dvakrát klikněte **Say Hello** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí.</span><span class="sxs-lookup"><span data-stu-id="3a91a-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5. <span data-ttu-id="3a91a-138">Přidejte následující řádek kódu obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="3a91a-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="3a91a-139">Chcete-li přidat tlačítko, které nemůže upravit dědice základního formuláře</span><span class="sxs-lookup"><span data-stu-id="3a91a-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1. <span data-ttu-id="3a91a-140">Přepnutí do návrhového zobrazení po kliknutí **Form1.vb [Design], Form1.cs [Design] nebo [Design] Form1.jsl** kartu nad editoru kódu nebo stisknutím klávesy F7.</span><span class="sxs-lookup"><span data-stu-id="3a91a-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2. <span data-ttu-id="3a91a-141">Přidejte druhé tlačítko a nastavte jeho vlastnosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3a91a-141">Add a second button and set its properties as follows:</span></span>  
  
    - <span data-ttu-id="3a91a-142">Nastavte **Text** vlastnost **Say Goodbye**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    - <span data-ttu-id="3a91a-143">Nastavte **(název)** vlastnost **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    - <span data-ttu-id="3a91a-144">Nastavte **modifikátory** vlastnost **privátní**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="3a91a-145">To znemožňuje pro formuláře, které dědí **Form1** k úpravě vlastností **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3. <span data-ttu-id="3a91a-146">Dvakrát klikněte **Say Goodbye** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí.</span><span class="sxs-lookup"><span data-stu-id="3a91a-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="3a91a-147">Vložte následující řádek kódu do procedury události:</span><span class="sxs-lookup"><span data-stu-id="3a91a-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4. <span data-ttu-id="3a91a-148">Z **sestavení** nabídce zvolte **sestavení knihovny BaseForm** k vytvoření knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="3a91a-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="3a91a-149">Jakmile knihovny je sestavená, můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="3a91a-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="3a91a-150">Chcete-li vytvořit projekt obsahující formulář, který dědí ze základního formuláře</span><span class="sxs-lookup"><span data-stu-id="3a91a-150">To create a project containing a form that inherits from the base form</span></span>  
  
1. <span data-ttu-id="3a91a-151">Z **souboru** nabídce zvolte **přidat** a potom **nový projekt** otevřít **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3a91a-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="3a91a-152">Vytvoření aplikace Windows Forms s názvem `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="3a91a-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="3a91a-153">Přidat Zděděný formulář</span><span class="sxs-lookup"><span data-stu-id="3a91a-153">To add an inherited form</span></span>  
  
1. <span data-ttu-id="3a91a-154">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projekt, vyberte **přidat**a pak vyberte **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>  
  
2. <span data-ttu-id="3a91a-155">V **přidat novou položku** dialogové okno, vyberte **Windows Forms** kategorie (Pokud máte seznam kategorií) a pak vyberte **zděděné formuláře** šablony.</span><span class="sxs-lookup"><span data-stu-id="3a91a-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3. <span data-ttu-id="3a91a-156">Ponechte výchozí název `Form2` a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4. <span data-ttu-id="3a91a-157">V **výběr dědičnosti** dialogu **Form1** z **BaseFormLibrary** projektu jako formulář dědí a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="3a91a-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="3a91a-158">Tím se vytvoří na formulář v nástrojích **InheritanceTest** projekt, který je odvozen z formuláře v **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5. <span data-ttu-id="3a91a-159">Otevřete Zděděný formulář (**Form2**) v Návrháři poklepáním, pokud ještě není otevřený.</span><span class="sxs-lookup"><span data-stu-id="3a91a-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="3a91a-160">V Návrháři zděděné tlačítka mají symbol (</span><span class="sxs-lookup"><span data-stu-id="3a91a-160">In the designer, the inherited buttons have a symbol (</span></span>![Snímek obrazovky dědičnosti symbol jazyka Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="3a91a-162">) v jejich horním rohu, která se dědí.</span><span class="sxs-lookup"><span data-stu-id="3a91a-162">) in their upper corner, indicating they are inherited.</span></span>  
  
6. <span data-ttu-id="3a91a-163">Vyberte **Say Hello** tlačítko a podívejte se úchyty pro změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="3a91a-163">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="3a91a-164">Protože toto tlačítko je chráněný, dědice můžete přesunout, změnit jeho velikost, změnit titulek a provádět další úpravy.</span><span class="sxs-lookup"><span data-stu-id="3a91a-164">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7. <span data-ttu-id="3a91a-165">Vyberte privátní **Say Goodbye** tlačítko a Všimněte si, že nemá úchyty pro změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="3a91a-165">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="3a91a-166">Kromě toho **vlastnosti** v okně Vlastnosti tohoto tlačítka se šedě k označení, nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="3a91a-166">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8. <span data-ttu-id="3a91a-167">Pokud používáte jazyk Visual C#:</span><span class="sxs-lookup"><span data-stu-id="3a91a-167">If you are using Visual C#:</span></span>  
  
    1. <span data-ttu-id="3a91a-168">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1** v **InheritanceTest** projektu a klikněte na tlačítko **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-168">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="3a91a-169">V okně se zprávou, která se zobrazí, klikněte na tlačítko **OK** potvrďte odstranění.</span><span class="sxs-lookup"><span data-stu-id="3a91a-169">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2. <span data-ttu-id="3a91a-170">Otevřete soubor Program.cs a změňte řádek `Application.Run(new Form1());` k `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="3a91a-170">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="3a91a-171">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-171">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="3a91a-172">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-172">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="3a91a-173">V **InheritanceTest** stránky vlastností, nastavte **spouštěcí objekt** Zděděný formulář (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="3a91a-173">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="3a91a-174">Stisknutím klávesy F5 spusťte aplikaci a sledovat chování Zděděný formulář.</span><span class="sxs-lookup"><span data-stu-id="3a91a-174">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3a91a-175">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3a91a-175">Next Steps</span></span>  
 <span data-ttu-id="3a91a-176">V podstatě stejným způsobem pracuje dědičnost u uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3a91a-176">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="3a91a-177">Otevřete nový projekt knihovny tříd a přidat uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3a91a-177">Open a new class library project and add a user control.</span></span> <span data-ttu-id="3a91a-178">Základní ovládací prvky na něj umístit a kompilaci projektu.</span><span class="sxs-lookup"><span data-stu-id="3a91a-178">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="3a91a-179">Otevřete jinou nový projekt knihovny tříd a přidejte odkaz na knihovnu zkompilované třídy.</span><span class="sxs-lookup"><span data-stu-id="3a91a-179">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="3a91a-180">Také se pokuste přidat zděděný ovládací prvek (prostřednictvím **přidat nové položky** dialogové okno) do projektu a použití **výběr dědičnosti**.</span><span class="sxs-lookup"><span data-stu-id="3a91a-180">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="3a91a-181">Přidat uživatelský ovládací prvek a změnit `Inherits` (`:` v jazyce Visual C#) příkaz.</span><span class="sxs-lookup"><span data-stu-id="3a91a-181">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="3a91a-182">Další informace najdete v tématu [jak: Dědění formulářů Windows](how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3a91a-182">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a91a-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a91a-183">See also</span></span>

- [<span data-ttu-id="3a91a-184">Postupy: Dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="3a91a-184">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="3a91a-185">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a91a-185">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="3a91a-186">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a91a-186">Windows Forms</span></span>](../index.md)
