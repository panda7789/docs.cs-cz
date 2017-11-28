---
title: "Návod: Demonstrace vizuálního dědění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 711f823e418a1bbea1479b9d6a8d70d4fa506365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="f47a0-102">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="f47a0-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="f47a0-103">Dědičnost vizuálních prvků umožňuje zobrazíte ovládacích prvků na formuláři základní a přidejte nové ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f47a0-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="f47a0-104">V tomto návodu vytvoříte základní formulář a kompilována knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="f47a0-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="f47a0-105">Bude tato knihovna tříd importovat do jiného projektu a vytvořte nový formulář, který dědí ze základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="f47a0-106">Během tohoto návodu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="f47a0-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="f47a0-107">Vytvoření projektu knihovny tříd obsahující základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="f47a0-108">Přidáte lze upravit tlačítko s vlastnostmi, které odvozené třídy základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="f47a0-109">Přidání tlačítka, které nelze změnit pomocí dědice základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="f47a0-110">Vytvoření projektu obsahující formulář, který dědí z `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="f47a0-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="f47a0-111">Nakonec tento návod popisuje rozdíl mezi privátním a chráněné ovládacích prvků na zděděné formuláře.</span><span class="sxs-lookup"><span data-stu-id="f47a0-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f47a0-112">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f47a0-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f47a0-113">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f47a0-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f47a0-114">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f47a0-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f47a0-115">Ne všechny ovládací prvky podporují vizuálního dědění ze základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="f47a0-116">Ovládací prvky nepodporují podle scénáře popsaného v tomto průvodci:</span><span class="sxs-lookup"><span data-stu-id="f47a0-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
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
>  <span data-ttu-id="f47a0-117">Tyto ovládací prvky ve formuláři zděděné jsou vždy jen pro čtení bez ohledu na to modifikátory použijete (`private`, `protected`, nebo `public`).</span><span class="sxs-lookup"><span data-stu-id="f47a0-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="f47a0-118">Kroky scénáře</span><span class="sxs-lookup"><span data-stu-id="f47a0-118">Scenario Steps</span></span>  
 <span data-ttu-id="f47a0-119">Prvním krokem je vytvoření základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="f47a0-120">Vytvoření projektu knihovny tříd obsahující základní formulář</span><span class="sxs-lookup"><span data-stu-id="f47a0-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="f47a0-121">Z **soubor** nabídce zvolte **nový**a potom **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f47a0-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f47a0-122">Vytvoření aplikace Windows Forms s názvem `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f47a0-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="f47a0-123">K vytvoření knihovny tříd místo u standardní aplikace Windows Forms v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **BaseFormLibrary** uzel projektu a potom vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="f47a0-124">Ve vlastnostech projektu, změňte **výstupní typ** z **aplikace Windows** k **knihovny tříd**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="f47a0-125">Z **soubor** nabídce zvolte **Uložit vše** uložte projekt a soubory do výchozího umístění.</span><span class="sxs-lookup"><span data-stu-id="f47a0-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="f47a0-126">Následující dva postupy přidání tlačítka do základní formulář.</span><span class="sxs-lookup"><span data-stu-id="f47a0-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="f47a0-127">K předvedení dědičnost vizuálních prvků, kterým pojmenujete tlačítka různé úrovně přístupu nastavením jejich `Modifiers` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f47a0-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="f47a0-128">Chcete-li přidat tlačítko, které můžete upravit dědice základní formulář</span><span class="sxs-lookup"><span data-stu-id="f47a0-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="f47a0-129">Otevřete **Form1** v návrháři.</span><span class="sxs-lookup"><span data-stu-id="f47a0-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="f47a0-130">Na **všechny formuláře Windows** kartě **sada nástrojů**, dvakrát klikněte na **tlačítko** přidání tlačítka do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f47a0-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="f47a0-131">Umístění a změna velikosti tlačítko pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="f47a0-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="f47a0-132">V okně vlastností nastavte následující vlastnosti tlačítka:</span><span class="sxs-lookup"><span data-stu-id="f47a0-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="f47a0-133">Nastavte **Text** vlastnost **Hello indikované**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="f47a0-134">Nastavte **(název)** vlastnost **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="f47a0-135">Nastavte**modifikátory** vlastnost **chráněné**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="f47a0-136">Díky tomu může pro formuláře, které dědí od **Form1** k úpravě vlastností **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="f47a0-137">Dvakrát klikněte na **Hello indikované** tlačítko pro přidání obslužné rutiny události pro **klikněte na tlačítko** událostí.</span><span class="sxs-lookup"><span data-stu-id="f47a0-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="f47a0-138">Přidejte následující kód do obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="f47a0-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="f47a0-139">Chcete-li přidat tlačítko, které nelze změnit pomocí dědice základní formulář</span><span class="sxs-lookup"><span data-stu-id="f47a0-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="f47a0-140">Přepnout na zobrazení návrhu kliknutím **Form1.vb [Design], Form1.cs [Design] nebo [návrhu] Form1.jsl** kartě nad editoru kódu nebo stisknutím klávesy F7.</span><span class="sxs-lookup"><span data-stu-id="f47a0-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="f47a0-141">Druhý tlačítko Přidat a nastavit jeho vlastnosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f47a0-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="f47a0-142">Nastavte **Text** vlastnost **dát sbohem všem indikované**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="f47a0-143">Nastavte **(název)** vlastnost **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="f47a0-144">Nastavte **modifikátory** vlastnost **privátní**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="f47a0-145">To znemožňuje pro formuláře, které dědí od **Form1** k úpravě vlastností **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="f47a0-146">Dvakrát klikněte **indikované dát sbohem všem** tlačítko pro přidání obslužné rutiny události pro **klikněte na** událostí.</span><span class="sxs-lookup"><span data-stu-id="f47a0-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="f47a0-147">Vložte následující řádek kódu v proceduře události:</span><span class="sxs-lookup"><span data-stu-id="f47a0-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="f47a0-148">Z **sestavení** nabídce zvolte **sestavení knihovny BaseForm** k vytvoření knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="f47a0-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="f47a0-149">Po knihovny, můžete vytvořit nový projekt, který dědí z formuláře, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f47a0-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="f47a0-150">Chcete-li vytvořit projekt obsahující formulář, který dědí ze základního formuláře</span><span class="sxs-lookup"><span data-stu-id="f47a0-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="f47a0-151">Z **soubor** nabídce zvolte **přidat** a potom **nový projekt** otevřete **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f47a0-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f47a0-152">Vytvoření aplikace Windows Forms s názvem `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="f47a0-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="f47a0-153">Chcete-li přidat zděděné formuláře</span><span class="sxs-lookup"><span data-stu-id="f47a0-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="f47a0-154">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projekt, vyberte **přidat**a potom vyberte**novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="f47a0-155">V **přidat novou položku** dialogové okno, vyberte **Windows Forms** kategorie (Pokud máte seznam kategorií) a potom vyberte **zděděná formuláře** šablony.</span><span class="sxs-lookup"><span data-stu-id="f47a0-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="f47a0-156">Ponechte výchozí název `Form2` a pak klikněte na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="f47a0-157">V **výběr dědičnosti** dialogové okno, vyberte **Form1** z **BaseFormLibrary** projektu jako formulář dědí a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="f47a0-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="f47a0-158">Tím se vytvoří do formuláře **InheritanceTest** projekt, který je odvozen z formuláře v **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="f47a0-159">Otevřít formulář zděděné (**Form2**) v Návrháři dvojitým kliknutím na soubor, pokud ještě není otevřené.</span><span class="sxs-lookup"><span data-stu-id="f47a0-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="f47a0-160">V Návrháři zděděné tlačítka mají symbol (![VisualBasicInheritanceSymbol – snímek obrazovky](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) v jejich horního rohu, která určuje, že zděděná.</span><span class="sxs-lookup"><span data-stu-id="f47a0-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="f47a0-161">Vyberte **Hello indikované** tlačítko a sledovat změny velikosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="f47a0-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="f47a0-162">Protože toto tlačítko je chráněn, dědice můžete přesunout ho, jeho velikost, změnit jeho popisek a provádět další úpravy.</span><span class="sxs-lookup"><span data-stu-id="f47a0-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="f47a0-163">Vyberte privátní **dát sbohem všem indikované** tlačítko a Všimněte si, nemá změny velikosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="f47a0-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="f47a0-164">Kromě toho **vlastnosti** okně Vlastnosti toto tlačítko se šedý k označení je nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="f47a0-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="f47a0-165">Pokud používáte [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f47a0-165">If you are using [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="f47a0-166">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1** v **InheritanceTest** projektu a potom zvolte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="f47a0-167">V dialogovém okně se zobrazí, klikněte na **OK** potvrďte odstranění.</span><span class="sxs-lookup"><span data-stu-id="f47a0-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="f47a0-168">Otevřete soubor Program.cs a změňte řádek `Application.Run(new Form1());` k `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="f47a0-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="f47a0-169">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="f47a0-170">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **InheritanceTest** projektu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="f47a0-171">V **InheritanceTest** nastavení stránek vlastností **spouštěcí objekt** být zděděné formuláře (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="f47a0-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="f47a0-172">Stisknutím klávesy F5 spusťte aplikaci a pozorovat chování zděděné formuláře.</span><span class="sxs-lookup"><span data-stu-id="f47a0-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f47a0-173">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f47a0-173">Next Steps</span></span>  
 <span data-ttu-id="f47a0-174">Dědičnost pro uživatelské ovládací prvky funguje stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f47a0-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="f47a0-175">Otevřete nový projekt knihovny tříd a přidat uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f47a0-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="f47a0-176">Umístěte základních ovládacích prvků na něm a kompilaci projektu.</span><span class="sxs-lookup"><span data-stu-id="f47a0-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="f47a0-177">Otevřete jiné nového projektu knihovny tříd a přidejte odkaz na knihovnu zkompilované třídy.</span><span class="sxs-lookup"><span data-stu-id="f47a0-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="f47a0-178">Navíc zkuste přidat ovládací prvek zděděné (prostřednictvím **přidat nové položky** dialogové okno) do projektu a pomocí **výběr dědičnosti**.</span><span class="sxs-lookup"><span data-stu-id="f47a0-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="f47a0-179">Přidat uživatelský ovládací prvek a změňte `Inherits` (`:` v [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) příkaz.</span><span class="sxs-lookup"><span data-stu-id="f47a0-179">Add a user control, and change the `Inherits` (`:` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) statement.</span></span> <span data-ttu-id="f47a0-180">Další informace najdete v tématu [postupy: dědění Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f47a0-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47a0-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="f47a0-181">See Also</span></span>  
 [<span data-ttu-id="f47a0-182">Postupy: dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="f47a0-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="f47a0-183">Vizuální dědění Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f47a0-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="f47a0-184">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f47a0-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
