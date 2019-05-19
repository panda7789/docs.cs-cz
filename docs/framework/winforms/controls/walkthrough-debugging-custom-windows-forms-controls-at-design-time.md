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
ms.openlocfilehash: 39adcbd6d915f8b086df7e425efbe08ae8680a45
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882466"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="76cb0-102">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="76cb0-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="76cb0-103">Při vytváření vlastního ovládacího prvku často zjistíte to potřebné k ladění jeho chování během návrhu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="76cb0-104">To platí zejména pokud vytváříte vlastní návrháře pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="76cb0-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="76cb0-105">Podrobnosti najdete v tématu [názorný postup: Vytváření Windows Forms ovládací prvek, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="76cb0-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="76cb0-106">Vlastní ovládací prvky pomocí sady Visual Studio, můžete ladit stejně, jako by ladění jiných tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76cb0-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="76cb0-107">Rozdíl spočívá v tom, že ladíte samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu</span><span class="sxs-lookup"><span data-stu-id="76cb0-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>

<span data-ttu-id="76cb0-108">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="76cb0-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="76cb0-109">Vytvoření projektu Windows Forms k hostování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="76cb0-109">Creating a Windows Forms project to host your custom control</span></span>

- <span data-ttu-id="76cb0-110">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="76cb0-110">Creating a control library project</span></span>

- <span data-ttu-id="76cb0-111">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="76cb0-111">Adding a property to your custom control</span></span>

- <span data-ttu-id="76cb0-112">Přidání vlastního ovládacího prvku na formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="76cb0-112">Adding your custom control to the host form</span></span>

- <span data-ttu-id="76cb0-113">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="76cb0-113">Setting up the project for design-time debugging</span></span>

- <span data-ttu-id="76cb0-114">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="76cb0-114">Debugging your custom control at design time</span></span>

<span data-ttu-id="76cb0-115">Až budete hotovi, budete mít porozumění úloh nezbytných pro ladění chování návrhu vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76cb0-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="76cb0-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="76cb0-116">Create the project</span></span>

<span data-ttu-id="76cb0-117">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="76cb0-117">The first step is to create the application project.</span></span> <span data-ttu-id="76cb0-118">Tento projekt bude používat k sestavení aplikace, který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76cb0-118">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="76cb0-119">V sadě Visual Studio vytvořte projekt aplikace Windows s názvem "DebuggingExample" (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaciWindowsForms**).</span><span class="sxs-lookup"><span data-stu-id="76cb0-119">In Visual Studio, create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="76cb0-120">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="76cb0-120">Create the control library project</span></span>

1. <span data-ttu-id="76cb0-121">Přidat **Knihovna ovládacích prvků Windows** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="76cb0-121">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="76cb0-122">Přidat nový **UserControl** položky do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="76cb0-122">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="76cb0-123">Podrobnosti najdete v tématu [jak: Přidání nových položek projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="76cb0-123">For details, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="76cb0-124">Zadejte základní název "DebugControl" nového zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="76cb0-124">Give the new source file a base name of "DebugControl".</span></span>

3. <span data-ttu-id="76cb0-125">Použití **Průzkumníku řešení**, odstranění výchozího projektu ovládacího prvku tak, že odstraníte soubor kódu základní název s "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="76cb0-125">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="76cb0-126">Podrobnosti najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="76cb0-126">For details, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

4. <span data-ttu-id="76cb0-127">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="76cb0-127">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="76cb0-128">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="76cb0-128">Checkpoint</span></span>

<span data-ttu-id="76cb0-129">V tomto okamžiku budete moct zobrazit vaše vlastní ovládací prvky **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="76cb0-129">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="76cb0-130">Pokud chcete zkontrolovat průběh, vyhledejte novou kartu **DebugControlLibrary součásti** a kliknutím ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="76cb0-130">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="76cb0-131">Když se otevře, zobrazí se váš ovládací prvek zobrazí jako **DebugControl** s výchozí ikona vedle něj.</span><span class="sxs-lookup"><span data-stu-id="76cb0-131">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="76cb0-132">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="76cb0-132">Add a property to your custom control</span></span>

<span data-ttu-id="76cb0-133">Abychom si předvedli, že kód vlastní ovládací prvek je spuštěný v době návrhu, se přidat vlastnost a nastavte zarážku v kódu, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76cb0-133">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="76cb0-134">Otevřít **DebugControl** v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="76cb0-134">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="76cb0-135">Přidejte následující kód do definice třídy:</span><span class="sxs-lookup"><span data-stu-id="76cb0-135">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="76cb0-136">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="76cb0-136">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="76cb0-137">Přidání vlastního ovládacího prvku formulář hostitele</span><span class="sxs-lookup"><span data-stu-id="76cb0-137">Add your custom control to the host form</span></span>

<span data-ttu-id="76cb0-138">Chcete-li ladit chování návrhu vlastního ovládacího prvku, umístíte instance třídy vlastní ovládací prvek ve formuláři hostitele.</span><span class="sxs-lookup"><span data-stu-id="76cb0-138">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="76cb0-139">V projektu "DebuggingExample" otevřete Form1 v **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="76cb0-139">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="76cb0-140">V **nástrojů**, otevřete **DebugControlLibrary součásti** kartu a přetáhnout **DebugControl** instance na formulář.</span><span class="sxs-lookup"><span data-stu-id="76cb0-140">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="76cb0-141">Najít `DemoString` vlastní vlastnost v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="76cb0-141">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="76cb0-142">Všimněte si, že stejně jako jakoukoli jinou vlastnosti můžete změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-142">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="76cb0-143">Všimněte si také, že `DemoString` vybrána vlastnost, řetězce popisu vlastnosti se zobrazí v dolní části **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="76cb0-143">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="76cb0-144">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="76cb0-144">Set up the project for design-time debugging</span></span>

<span data-ttu-id="76cb0-145">Chcete-li ladit chování vašeho vlastního ovládacího prvku návrhu, bude ladit samostatnou instanci sady Visual Studio, na kterém běží vaše vlastní ovládací prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-145">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="76cb0-146">Klikněte pravým tlačítkem na **DebugControlLibrary** projekt **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="76cb0-146">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="76cb0-147">V **DebugControlLibrary** seznam vlastností, vyberte **ladění** kartu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-147">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="76cb0-148">V **spustit akci** vyberte **externí program Start**.</span><span class="sxs-lookup"><span data-stu-id="76cb0-148">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="76cb0-149">Bude ladění samostatnou instanci sady Visual Studio, proto klikněte na symbol tří teček (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) tlačítko Procházet pro Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="76cb0-149">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="76cb0-150">Název spustitelného souboru, který je **devenv.exe**, a pokud jste nainstalovali do výchozího umístění, je jeho cesta 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76cb0-150">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

3. <span data-ttu-id="76cb0-151">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="76cb0-151">Click **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="76cb0-152">Klikněte pravým tlačítkem myši **DebugControlLibrary** projektu a vyberte **nastavit jako spouštěný projekt** k povolení této konfiguraci ladění.</span><span class="sxs-lookup"><span data-stu-id="76cb0-152">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="76cb0-153">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="76cb0-153">Debug your custom control at design time</span></span>

<span data-ttu-id="76cb0-154">Nyní jste připraveni k ladění vlastního ovládacího prvku při jeho spuštění v režimu návrhu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-154">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="76cb0-155">Když spustíte relaci ladění, bude vytvořena nová instance sady Visual Studio a použije k načtení řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="76cb0-155">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="76cb0-156">Když otevřete Form1 v **Návrháře formulářů**, instance vašeho vlastního ovládacího prvku se vytvoří a spustí se systémem.</span><span class="sxs-lookup"><span data-stu-id="76cb0-156">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="76cb0-157">Otevřít **DebugControl** zdrojový soubor v **Editor kódu** a umístit zarážky na `Set` přistupující objekt `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76cb0-157">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="76cb0-158">Stisknutím klávesy F5 pro spuštění relace ladění.</span><span class="sxs-lookup"><span data-stu-id="76cb0-158">Press F5 to start the debugging session.</span></span> <span data-ttu-id="76cb0-159">Všimněte si, že je vytvořena nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76cb0-159">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="76cb0-160">Možné rozlišit mezi instancemi dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="76cb0-160">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="76cb0-161">Ladění instance obsahuje slovo **systémem** v záhlaví</span><span class="sxs-lookup"><span data-stu-id="76cb0-161">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="76cb0-162">Ladění instance má **Start** tlačítko na jeho **ladění** nástrojů zakázáno</span><span class="sxs-lookup"><span data-stu-id="76cb0-162">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

     <span data-ttu-id="76cb0-163">Vaše zarážka je nastavena v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="76cb0-163">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="76cb0-164">V nové instanci sady Visual Studio otevřete řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="76cb0-164">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="76cb0-165">Řešení můžete snadno vyhledat tak, že vyberete **posledních projektů** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="76cb0-165">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="76cb0-166">Soubor řešení "DebuggingExample.sln", bude uveden jako naposledy použitých souborů.</span><span class="sxs-lookup"><span data-stu-id="76cb0-166">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="76cb0-167">Otevřete Form1 v **Návrháře formulářů** a vyberte **DebugControl** ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76cb0-167">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="76cb0-168">Změňte hodnotu `DemoString` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76cb0-168">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="76cb0-169">Všimněte si, že když změny potvrdíte, instanci ladění aplikace Visual Studio získá fokus a provádění zastaví na zarážku.</span><span class="sxs-lookup"><span data-stu-id="76cb0-169">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="76cb0-170">Můžete si krokování přistupující objekt vlastnosti stejně jako vaše by jakýkoli jiný kód.</span><span class="sxs-lookup"><span data-stu-id="76cb0-170">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="76cb0-171">Až budete hotovi s vaší relace ladění, můžete ukončit zrušením hostované instance sady Visual Studio nebo kliknutím **Zastavit ladění** tlačítko v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="76cb0-171">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="76cb0-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="76cb0-172">Next steps</span></span>

<span data-ttu-id="76cb0-173">Teď, když vaše vlastní ovládací prvky můžete ladit v době návrhu, existuje mnoho možností pro rozbalení ovládacího prvku interakce s integrovaným vývojovým prostředím sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76cb0-173">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="76cb0-174">Můžete použít <xref:System.ComponentModel.Component.DesignMode%2A> vlastnost <xref:System.ComponentModel.Component> třídy psaní kódu, který se spustí pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="76cb0-174">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="76cb0-175">Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="76cb0-175">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="76cb0-176">Několik atributů můžete provést u vlastností ovládacího prvku k manipulaci s vlastní ovládací prvek interakce s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="76cb0-176">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="76cb0-177">Tyto atributy v můžete najít <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76cb0-177">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="76cb0-178">Můžete napsat vlastního návrháře pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="76cb0-178">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="76cb0-179">To vám plnou kontrolu nad komfortem při návrhu extensible návrháře infrastruktury zpřístupněný nástrojem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76cb0-179">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="76cb0-180">Podrobnosti najdete v tématu [názorný postup: Vytváření Windows Forms ovládací prvek, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="76cb0-180">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76cb0-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76cb0-181">See also</span></span>

- [<span data-ttu-id="76cb0-182">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio Design-Time</span><span class="sxs-lookup"><span data-stu-id="76cb0-182">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
- <span data-ttu-id="76cb0-183">[Postupy: Přístup ke službám během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="76cb0-183">[How to: Access Design-Time Services](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span></span>
- <span data-ttu-id="76cb0-184">[Postupy: Podpora návrhu přístupu ve Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="76cb0-184">[How to: Access Design-Time Support in Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span></span>
