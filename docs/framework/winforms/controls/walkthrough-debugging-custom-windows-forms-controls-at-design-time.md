---
title: Ladit vlastní ovládací prvky v době návrhu
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740195"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="fb145-102">Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="fb145-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="fb145-103">Při vytváření vlastního ovládacího prvku často zjistíte, že je nutné ladit jeho chování při návrhu.</span><span class="sxs-lookup"><span data-stu-id="fb145-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="fb145-104">To platí hlavně v případě, že vytváříte vlastního návrháře vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb145-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="fb145-105">Podrobnosti najdete v tématu [Návod: vytváření model Windows Forms ovládacího prvku, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="fb145-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="fb145-106">Pomocí sady Visual Studio můžete ladit vlastní ovládací prvky stejně, jako byste provedete ladění jakékoli jiné .NET Framework třídy.</span><span class="sxs-lookup"><span data-stu-id="fb145-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="fb145-107">Rozdíl je, že budete ladit samostatnou instanci aplikace Visual Studio, která spouští kód vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb145-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="fb145-108">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fb145-108">Create the project</span></span>

<span data-ttu-id="fb145-109">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb145-109">The first step is to create the application project.</span></span> <span data-ttu-id="fb145-110">Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb145-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="fb145-111">V aplikaci Visual Studio vytvořte projekt aplikace pro systém Windows a pojmenujte jej **DebuggingExample**.</span><span class="sxs-lookup"><span data-stu-id="fb145-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="fb145-112">Vytvořit projekt knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fb145-112">Create the control library project</span></span>

1. <span data-ttu-id="fb145-113">Přidejte do řešení projekt **knihovny ovládacích prvků systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="fb145-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="fb145-114">Přidejte novou položku **UserControl** do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="fb145-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="fb145-115">Pojmenujte ho **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="fb145-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="fb145-116">V **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním souboru s kódem se základním názvem UserControl1.</span><span class="sxs-lookup"><span data-stu-id="fb145-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="fb145-117">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="fb145-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="fb145-118">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="fb145-118">Checkpoint</span></span>

<span data-ttu-id="fb145-119">V tomto okamžiku budete moci zobrazit vlastní ovládací prvek v sadě **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="fb145-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="fb145-120">Pokud chcete zjistit svůj průběh, najděte novou kartu s názvem **součásti DebugControlLibrary** a kliknutím ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="fb145-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="fb145-121">Po otevření se ovládací prvek zobrazí jako **DebugControl** s výchozí ikonou vedle něj.</span><span class="sxs-lookup"><span data-stu-id="fb145-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="fb145-122">Přidání vlastnosti do vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fb145-122">Add a property to your custom control</span></span>

<span data-ttu-id="fb145-123">Chcete-li předvést, že váš kód vlastního ovládacího prvku je spuštěn v době návrhu, přidejte vlastnost a nastavte zarážku v kódu, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb145-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="fb145-124">Otevřete **DebugControl** v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="fb145-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="fb145-125">Do definice třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="fb145-125">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="fb145-126">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="fb145-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="fb145-127">Přidat vlastní ovládací prvek do formuláře hostitele</span><span class="sxs-lookup"><span data-stu-id="fb145-127">Add your custom control to the host form</span></span>

<span data-ttu-id="fb145-128">Chcete-li ladit chování vlastního ovládacího prvku v době návrhu, umístěte instanci třídy vlastního ovládacího prvku do formuláře hostitele.</span><span class="sxs-lookup"><span data-stu-id="fb145-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="fb145-129">V projektu "DebuggingExample" otevřete Form1 v **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="fb145-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="fb145-130">V **sadě nástrojů**otevřete kartu **součásti DebugControlLibrary** a přetáhněte instanci **DebugControl** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="fb145-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="fb145-131">V okně **vlastnosti** vyhledejte vlastní vlastnost `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="fb145-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="fb145-132">Všimněte si, že můžete změnit její hodnotu stejně jako jakoukoli jinou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb145-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="fb145-133">Všimněte si také, že pokud je vybrána vlastnost `DemoString`, zobrazí se v dolní části okna **vlastností** řetězec popisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fb145-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="fb145-134">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="fb145-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="fb145-135">Chcete-li ladit chování vlastního ovládacího prvku v době návrhu, budete ladit samostatnou instanci aplikace Visual Studio, ve které je spuštěn kód vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb145-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="fb145-136">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt **DebugControlLibrary** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb145-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="fb145-137">V seznamu vlastností **DebugControlLibrary** vyberte kartu **ladění** .</span><span class="sxs-lookup"><span data-stu-id="fb145-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="fb145-138">V části **spouštěcí akce** vyberte **spustit externí program**.</span><span class="sxs-lookup"><span data-stu-id="fb145-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="fb145-139">Budete ladit samostatnou instanci aplikace Visual Studio, proto klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) a vyhledejte integrované vývojové prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb145-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="fb145-140">Název spustitelného souboru je **devenv. exe**a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="fb145-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="fb145-141">Kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fb145-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="fb145-142">Klikněte pravým tlačítkem na projekt **DebugControlLibrary** a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.</span><span class="sxs-lookup"><span data-stu-id="fb145-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="fb145-143">Ladění vlastního ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="fb145-143">Debug your custom control at design time</span></span>

<span data-ttu-id="fb145-144">Nyní jste připraveni ladit vlastní ovládací prvek při spuštění v režimu návrhu.</span><span class="sxs-lookup"><span data-stu-id="fb145-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="fb145-145">Když spustíte relaci ladění, vytvoří se nová instance aplikace Visual Studio, kterou použijete k načtení řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="fb145-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="fb145-146">Když otevřete Form1 v **Návrháři formulářů**, vytvoří se instance vlastního ovládacího prvku a spustí se.</span><span class="sxs-lookup"><span data-stu-id="fb145-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="fb145-147">Otevřete zdrojový soubor **DebugControl** v **editoru kódu** a umístěte zarážku na přistupující objekt `Set` vlastnosti `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="fb145-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="fb145-148">Stisknutím klávesy **F5** spusťte relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="fb145-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="fb145-149">Vytvoří se nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb145-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="fb145-150">Mezi instancemi můžete rozlišovat dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="fb145-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="fb145-151">Instance ladění má slovo **běžící** v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="fb145-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="fb145-152">Instance ladění má tlačítko **Spustit** na panelu nástrojů **ladění** zakázáno.</span><span class="sxs-lookup"><span data-stu-id="fb145-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="fb145-153">Zarážka je nastavena v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="fb145-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="fb145-154">V nové instanci aplikace Visual Studio otevřete řešení "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="fb145-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="fb145-155">Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="fb145-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="fb145-156">Soubor řešení "DebuggingExample. sln" bude uveden jako naposledy použitý soubor.</span><span class="sxs-lookup"><span data-stu-id="fb145-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="fb145-157">Otevřete Form1 v **Návrháři formulářů** a vyberte ovládací prvek **DebugControl** .</span><span class="sxs-lookup"><span data-stu-id="fb145-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="fb145-158">Změňte hodnotu vlastnosti `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="fb145-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="fb145-159">Když změníte změnu, instance ladění sady Visual Studio získá fokus a spuštění se zastaví na zarážce.</span><span class="sxs-lookup"><span data-stu-id="fb145-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="fb145-160">Přístup k jednotlivým krokům můžete procházet prostřednictvím přistupujícího objektu vlastnosti stejně jako jakýkoli jiný kód.</span><span class="sxs-lookup"><span data-stu-id="fb145-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="fb145-161">Chcete-li zastavit ladění, ukončete hostovanou instanci sady Visual Studio nebo vyberte tlačítko **Zastavit ladění** v instanci ladění.</span><span class="sxs-lookup"><span data-stu-id="fb145-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb145-162">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fb145-162">Next steps</span></span>

<span data-ttu-id="fb145-163">Nyní, když můžete ladit vlastní ovládací prvky v době návrhu, existuje mnoho možností pro rozšíření interakce ovládacího prvku pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb145-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="fb145-164">Můžete použít vlastnost <xref:System.ComponentModel.Component.DesignMode%2A> třídy <xref:System.ComponentModel.Component> k zápisu kódu, který bude proveden pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fb145-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="fb145-165">Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb145-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="fb145-166">Existuje několik atributů, které lze použít pro vlastnosti ovládacího prvku pro manipulaci s interakcí vlastního ovládacího prvku s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="fb145-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="fb145-167">Tyto atributy můžete najít v oboru názvů <xref:System.ComponentModel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb145-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="fb145-168">Můžete napsat vlastní Návrhář pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fb145-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="fb145-169">Díky tomu máte plnou kontrolu nad prostředím pro návrh pomocí rozšiřitelné infrastruktury návrháře zveřejněné v rámci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb145-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="fb145-170">Podrobnosti najdete v tématu [Návod: vytváření model Windows Forms ovládacího prvku, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="fb145-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb145-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb145-171">See also</span></span>

- [<span data-ttu-id="fb145-172">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="fb145-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
