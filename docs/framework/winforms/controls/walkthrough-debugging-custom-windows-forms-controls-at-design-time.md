---
title: 'Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: 824c1e47cf50dc13a3a986e48a49158b15dbb935
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331795"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="b97f5-102">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="b97f5-103">Při vytváření vlastního ovládacího prvku často zjistíte to potřebné k ladění jeho chování během návrhu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="b97f5-104">To platí zejména pokud vytváříte vlastní návrháře pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b97f5-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="b97f5-105">Podrobnosti najdete v tématu [návod: vytváření Windows Forms ovládací prvek, že trvá využívat z doby návrhu funkce sady Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="b97f5-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="b97f5-106">Vlastní ovládací prvky pomocí sady Visual Studio, můžete ladit stejně, jako by ladění jiných tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b97f5-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="b97f5-107">Rozdíl spočívá v tom, že ladíte samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu</span><span class="sxs-lookup"><span data-stu-id="b97f5-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="b97f5-108">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="b97f5-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="b97f5-109">Vytvoření projektu Windows Forms k hostování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b97f5-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="b97f5-110">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b97f5-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="b97f5-111">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b97f5-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="b97f5-112">Přidání vlastního ovládacího prvku na formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="b97f5-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="b97f5-113">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="b97f5-114">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="b97f5-115">Až budete hotovi, budete mít porozumění úloh nezbytných pro ladění chování návrhu vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b97f5-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b97f5-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b97f5-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b97f5-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b97f5-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b97f5-118">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b97f5-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b97f5-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b97f5-119">Creating the Project</span></span>  
 <span data-ttu-id="b97f5-120">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="b97f5-120">The first step is to create the application project.</span></span> <span data-ttu-id="b97f5-121">Tento projekt bude používat k sestavení aplikace, který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b97f5-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b97f5-122">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b97f5-122">To create the project</span></span>  
  
-   <span data-ttu-id="b97f5-123">Vytvořte projekt aplikace Windows s názvem "DebuggingExample" (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="b97f5-123">Create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="b97f5-124">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b97f5-124">Creating a Control Library Project</span></span>  
 <span data-ttu-id="b97f5-125">Dalším krokem je vytvoření projektu knihovny ovládacích prvků a nastavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b97f5-125">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="b97f5-126">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b97f5-126">To create the control library project</span></span>  
  
1.  <span data-ttu-id="b97f5-127">Přidat **Knihovna ovládacích prvků Windows** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="b97f5-127">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="b97f5-128">Přidat nový **UserControl** položky do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="b97f5-128">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="b97f5-129">Podrobnosti najdete v tématu [NIB: postupy: Přidání nové položky projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="b97f5-129">For details, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="b97f5-130">Zadejte základní název "DebugControl" nového zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="b97f5-130">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="b97f5-131">Použití **Průzkumníku řešení**, odstranění výchozího projektu ovládacího prvku tak, že odstraníte soubor kódu základní název s "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="b97f5-131">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="b97f5-132">Podrobnosti najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="b97f5-132">For details, see [NIB:How to: Remove, Delete, and Exclude Items](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="b97f5-133">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="b97f5-133">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="b97f5-134">Kontrolní bod</span><span class="sxs-lookup"><span data-stu-id="b97f5-134">Checkpoint</span></span>  
 <span data-ttu-id="b97f5-135">V tomto okamžiku budete moct zobrazit vaše vlastní ovládací prvky **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="b97f5-135">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="b97f5-136">Chcete-li zkontrolovat průběh</span><span class="sxs-lookup"><span data-stu-id="b97f5-136">To check your progress</span></span>  
  
-   <span data-ttu-id="b97f5-137">Vyhledejte novou kartu **DebugControlLibrary součásti** a kliknutím ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="b97f5-137">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="b97f5-138">Když se otevře, zobrazí se váš ovládací prvek zobrazí jako **DebugControl** s výchozí ikona vedle něj.</span><span class="sxs-lookup"><span data-stu-id="b97f5-138">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="b97f5-139">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b97f5-139">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="b97f5-140">Abychom si předvedli, že kód vlastní ovládací prvek je spuštěný v době návrhu, se přidat vlastnost a nastavte zarážku v kódu, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b97f5-140">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="b97f5-141">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b97f5-141">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="b97f5-142">Otevřít **DebugControl** v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="b97f5-142">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="b97f5-143">Přidejte následující kód do definice třídy:</span><span class="sxs-lookup"><span data-stu-id="b97f5-143">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="b97f5-144">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="b97f5-144">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="b97f5-145">Přidání vlastního ovládacího prvku na formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="b97f5-145">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="b97f5-146">Chcete-li ladit chování návrhu vlastního ovládacího prvku, umístíte instance třídy vlastní ovládací prvek ve formuláři hostitele.</span><span class="sxs-lookup"><span data-stu-id="b97f5-146">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="b97f5-147">Přidání vlastního ovládacího prvku do formuláře hostitele</span><span class="sxs-lookup"><span data-stu-id="b97f5-147">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="b97f5-148">V projektu "DebuggingExample" otevřete Form1 v **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="b97f5-148">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="b97f5-149">V **nástrojů**, otevřete **DebugControlLibrary součásti** kartu a přetáhnout **DebugControl** instance na formulář.</span><span class="sxs-lookup"><span data-stu-id="b97f5-149">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="b97f5-150">Najít `DemoString` vlastní vlastnost v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="b97f5-150">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="b97f5-151">Všimněte si, že stejně jako jakoukoli jinou vlastnosti můžete změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-151">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="b97f5-152">Všimněte si také, že `DemoString` vybrána vlastnost, řetězce popisu vlastnosti se zobrazí v dolní části **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="b97f5-152">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="b97f5-153">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-153">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="b97f5-154">Chcete-li ladit chování vašeho vlastního ovládacího prvku návrhu, bude ladit samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-154">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="b97f5-155">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-155">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="b97f5-156">Klikněte pravým tlačítkem na **DebugControlLibrary** projekt **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b97f5-156">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b97f5-157">V **DebugControlLibrary** seznam vlastností, vyberte **ladění** kartu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-157">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="b97f5-158">V **spustit akci** vyberte **externí program Start**.</span><span class="sxs-lookup"><span data-stu-id="b97f5-158">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="b97f5-159">Bude ladění samostatnou instanci sady Visual Studio, proto klikněte na symbol tří teček (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Procházet pro Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="b97f5-159">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="b97f5-160">Název spustitelného souboru, který je **devenv.exe**, a pokud jste nainstalovali do výchozího umístění, je jeho cesta 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b97f5-160">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="b97f5-161">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="b97f5-161">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="b97f5-162">Klikněte pravým tlačítkem myši **DebugControlLibrary** projektu a vyberte **nastavit jako spouštěný projekt** k povolení této konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="b97f5-162">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="b97f5-163">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-163">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="b97f5-164">Nyní jste připraveni k ladění vlastního ovládacího prvku při jeho spuštění v režimu návrhu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-164">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="b97f5-165">Když spustíte relaci ladění, bude vytvořena nová instance sady Visual Studio a použije k načtení řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="b97f5-165">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="b97f5-166">Když otevřete Form1 v **Návrháře formulářů**, instance vašeho vlastního ovládacího prvku se vytvoří a spustí se systémem.</span><span class="sxs-lookup"><span data-stu-id="b97f5-166">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="b97f5-167">Chcete-li ladit vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-167">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="b97f5-168">Otevřít **DebugControl** zdrojový soubor v **Editor kódu** a umístit zarážky na `Set` přistupující objekt `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b97f5-168">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="b97f5-169">Stisknutím klávesy F5 pro spuštění relace ladění.</span><span class="sxs-lookup"><span data-stu-id="b97f5-169">Press F5 to start the debugging session.</span></span> <span data-ttu-id="b97f5-170">Všimněte si, že je vytvořena nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b97f5-170">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="b97f5-171">Možné rozlišit mezi instancemi dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b97f5-171">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="b97f5-172">Ladění instance obsahuje slovo **systémem** v záhlaví</span><span class="sxs-lookup"><span data-stu-id="b97f5-172">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="b97f5-173">Ladění instance má **Start** tlačítko na jeho **ladění** nástrojů zakázáno</span><span class="sxs-lookup"><span data-stu-id="b97f5-173">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="b97f5-174">Vaše zarážka je nastavena v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="b97f5-174">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="b97f5-175">V nové instanci sady Visual Studio otevřete řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="b97f5-175">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="b97f5-176">Řešení můžete snadno vyhledat tak, že vyberete **posledních projektů** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b97f5-176">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="b97f5-177">Soubor řešení "DebuggingExample.sln", bude uveden jako naposledy použitých souborů.</span><span class="sxs-lookup"><span data-stu-id="b97f5-177">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="b97f5-178">Otevřete Form1 v **Návrháře formulářů** a vyberte **DebugControl** ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b97f5-178">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="b97f5-179">Změňte hodnotu `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b97f5-179">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="b97f5-180">Všimněte si, že když změny potvrdíte, instanci ladění aplikace Visual Studio získá fokus a provádění zastaví na zarážku.</span><span class="sxs-lookup"><span data-stu-id="b97f5-180">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="b97f5-181">Můžete si krokování přistupující objekt vlastnosti stejně jako vaše by jakýkoli jiný kód.</span><span class="sxs-lookup"><span data-stu-id="b97f5-181">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="b97f5-182">Až budete hotovi s vaší relace ladění, můžete ukončit zrušením hostované instance sady Visual Studio nebo kliknutím **Zastavit ladění** tlačítko v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="b97f5-182">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b97f5-183">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b97f5-183">Next Steps</span></span>  
 <span data-ttu-id="b97f5-184">Teď, když vaše vlastní ovládací prvky můžete ladit v době návrhu, existuje mnoho možností pro rozbalení ovládacího prvku interakce s integrovaným vývojovým prostředím sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b97f5-184">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="b97f5-185">Můžete použít <xref:System.ComponentModel.Component.DesignMode%2A> vlastnost <xref:System.ComponentModel.Component> třídy psaní kódu, který se spustí pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b97f5-185">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="b97f5-186">Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="b97f5-186">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="b97f5-187">Několik atributů můžete provést u vlastností ovládacího prvku k manipulaci s vlastní ovládací prvek interakce s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="b97f5-187">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="b97f5-188">Tyto atributy v můžete najít <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b97f5-188">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="b97f5-189">Můžete napsat vlastního návrháře pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b97f5-189">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="b97f5-190">To vám plnou kontrolu nad komfortem při návrhu extensible návrháře infrastruktury zpřístupněný nástrojem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b97f5-190">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="b97f5-191">Podrobnosti najdete v tématu [návod: vytváření Windows Forms ovládací prvek, že trvá využívat z doby návrhu funkce sady Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="b97f5-191">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97f5-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="b97f5-192">See Also</span></span>  
 [<span data-ttu-id="b97f5-193">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-193">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="b97f5-194">Postupy: přístup ke službám během návrhu</span><span class="sxs-lookup"><span data-stu-id="b97f5-194">How to: Access Design-Time Services</span></span>](https://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="b97f5-195">Postupy: přístup k podpoře návrhu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b97f5-195">How to: Access Design-Time Support in Windows Forms</span></span>](https://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
