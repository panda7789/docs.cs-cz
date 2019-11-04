---
title: 'Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 64f637b232cf21701185e7b87d86f63fdece5127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459523"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="78503-102">Návod: vytvoření ovládacího prvku, který bude využívat funkce pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="78503-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="78503-103">Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="78503-104">Tento článek ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="78503-105">Implementujete `MarqueeControl` typ a přidruženou třídu návrháře nazvanou `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="78503-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="78503-106">Typ `MarqueeControl` implementuje zobrazení podobné textu v kino s animovanými indikátory a blikajícím textem.</span><span class="sxs-lookup"><span data-stu-id="78503-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="78503-107">Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="78503-108">Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci pomocí animovaných světel a blikání textu v mnoha kombinacích.</span><span class="sxs-lookup"><span data-stu-id="78503-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="78503-109">Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="78503-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="78503-110">Až budete s tímto návodem hotový, váš vlastní ovládací prvek bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="78503-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="78503-112">Úplný výpis kódu naleznete v tématu [How to: Create a model Windows Forms Control, který využívá funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="78503-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78503-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78503-113">Prerequisites</span></span>

<span data-ttu-id="78503-114">Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78503-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="78503-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="78503-115">Create the project</span></span>

<span data-ttu-id="78503-116">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="78503-116">The first step is to create the application project.</span></span> <span data-ttu-id="78503-117">Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="78503-118">V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte jej **MarqueeControlTest**.</span><span class="sxs-lookup"><span data-stu-id="78503-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="78503-119">Vytvořit projekt knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="78503-119">Create the control library project</span></span>

1. <span data-ttu-id="78503-120">Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="78503-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="78503-121">Pojmenujte projekt **MarqueeControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="78503-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="78503-122">Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce.</span><span class="sxs-lookup"><span data-stu-id="78503-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="78503-123">Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-124">Dejte novému zdrojovému souboru základní název **MarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="78503-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="78503-125">Pomocí **Průzkumník řešení**vytvořte novou složku v projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="78503-126">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="78503-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="78503-127">Pojmenujte ho **MarqueeControlRootDesigner**.</span><span class="sxs-lookup"><span data-stu-id="78503-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="78503-128">Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="78503-129">Odkaz na projekt vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="78503-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="78503-130">K otestování vlastního ovládacího prvku použijete `MarqueeControlTest` projekt.</span><span class="sxs-lookup"><span data-stu-id="78503-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="78503-131">Testovací projekt se při přidání odkazu na projekt do sestavení `MarqueeControlLibrary` stane vědět o vlastním ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="78503-132">V projektu `MarqueeControlTest` přidejte odkaz na projekt do sestavení `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="78503-133">Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.</span><span class="sxs-lookup"><span data-stu-id="78503-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="78503-134">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="78503-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="78503-135">Vlastní ovládací prvek bude odvozen z třídy <xref:System.Windows.Forms.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="78503-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="78503-136">To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.</span><span class="sxs-lookup"><span data-stu-id="78503-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="78503-137">Vlastní ovládací prvek bude mít přidružený vlastní Návrhář.</span><span class="sxs-lookup"><span data-stu-id="78503-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="78503-138">To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="78503-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="78503-139">K přidružení ovládacího prvku ke svému návrháři použijte třídu <xref:System.ComponentModel.DesignerAttribute>.</span><span class="sxs-lookup"><span data-stu-id="78503-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="78503-140">Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat rozhraní <xref:System.ComponentModel.Design.IRootDesigner>.</span><span class="sxs-lookup"><span data-stu-id="78503-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="78503-141">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="78503-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="78503-142">Otevřete zdrojový soubor `MarqueeControl` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-143">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="78503-144">Přidejte <xref:System.ComponentModel.DesignerAttribute> do deklarace třídy `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="78503-145">Tím přiřadíte vlastní ovládací prvek ke svému návrháři.</span><span class="sxs-lookup"><span data-stu-id="78503-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="78503-146">Otevřete zdrojový soubor `MarqueeControlRootDesigner` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-147">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="78503-148">Změňte deklaraci `MarqueeControlRootDesigner`, aby dědila z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="78503-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="78503-149">Použijte <xref:System.ComponentModel.ToolboxItemFilterAttribute> k určení interakce návrháře pomocí **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="78503-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="78503-150">Definice pro třídu `MarqueeControlRootDesigner` byla uzavřená v oboru názvů s názvem MarqueeControlLibrary. Design.</span><span class="sxs-lookup"><span data-stu-id="78503-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="78503-151">Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.</span><span class="sxs-lookup"><span data-stu-id="78503-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="78503-152">Definujte konstruktor pro třídu `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="78503-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="78503-153">Do těla konstruktoru vložte příkaz <xref:System.Diagnostics.Trace.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="78503-154">To bude užitečné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="78503-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="78503-155">Vytvoření instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="78503-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="78503-156">Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlTest`.</span><span class="sxs-lookup"><span data-stu-id="78503-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="78503-157">Dejte novému zdrojovému souboru základní název **DemoMarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="78503-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="78503-158">Otevřete `DemoMarqueeControl` soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="78503-159">V horní části souboru importujte `MarqueeControlLibrary` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="78503-160">Změňte deklaraci `DemoMarqueeControl`, aby dědila z `MarqueeControl` třídy.</span><span class="sxs-lookup"><span data-stu-id="78503-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="78503-161">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="78503-161">Build the project.</span></span>

5. <span data-ttu-id="78503-162">Otevřete Form1 v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="78503-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="78503-163">V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji.</span><span class="sxs-lookup"><span data-stu-id="78503-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="78503-164">Přetáhněte `DemoMarqueeControl` ze **sady nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="78503-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="78503-165">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="78503-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="78503-166">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="78503-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="78503-167">Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty.</span><span class="sxs-lookup"><span data-stu-id="78503-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="78503-168">Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="78503-169">Další informace naleznete v tématu [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="78503-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="78503-170">Klikněte pravým tlačítkem na projekt `MarqueeControlLibrary` a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="78503-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="78503-171">V dialogovém okně **stránky vlastností MarqueeControlLibrary** vyberte stránku **ladění** .</span><span class="sxs-lookup"><span data-stu-id="78503-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="78503-172">V části **spouštěcí akce** vyberte **spustit externí program**.</span><span class="sxs-lookup"><span data-stu-id="78503-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="78503-173">Budete ladit samostatnou instanci aplikace Visual Studio, proto klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) a vyhledejte integrované vývojové prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78503-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="78503-174">Název spustitelného souboru je devenv. exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*.</span><span class="sxs-lookup"><span data-stu-id="78503-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="78503-175">Kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="78503-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="78503-176">Klikněte pravým tlačítkem na projekt MarqueeControlLibrary a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.</span><span class="sxs-lookup"><span data-stu-id="78503-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="78503-177">Kontrolní bod</span><span class="sxs-lookup"><span data-stu-id="78503-177">Checkpoint</span></span>

<span data-ttu-id="78503-178">Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="78503-179">Jakmile zjistíte, že je prostředí ladění správně nastavené, otestujete přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.</span><span class="sxs-lookup"><span data-stu-id="78503-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="78503-180">Otestování ladicího prostředí a přidružení návrháře</span><span class="sxs-lookup"><span data-stu-id="78503-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="78503-181">Otevřete zdrojový soubor MarqueeControlRootDesigner v **editoru kódu** a umístěte zarážku na příkaz <xref:System.Diagnostics.Trace.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="78503-182">Stisknutím klávesy **F5** spusťte relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="78503-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="78503-183">Vytvoří se nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78503-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="78503-184">V nové instanci aplikace Visual Studio otevřete řešení MarqueeControlTest.</span><span class="sxs-lookup"><span data-stu-id="78503-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="78503-185">Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="78503-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="78503-186">Soubor řešení MarqueeControlTest. sln bude uveden jako naposledy použitý soubor.</span><span class="sxs-lookup"><span data-stu-id="78503-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="78503-187">Otevřete `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="78503-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="78503-188">Instance ladění aplikace Visual Studio získá fokus a provádění se zastaví na zarážce.</span><span class="sxs-lookup"><span data-stu-id="78503-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="78503-189">Stisknutím klávesy **F5** pokračujte v relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="78503-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="78503-190">V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="78503-191">Zbývající část tohoto článku se zaměřuje na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="78503-192">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="78503-192">Implement the Custom Control</span></span>

<span data-ttu-id="78503-193">`MarqueeControl` je <xref:System.Windows.Forms.UserControl> s malým množstvím přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="78503-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="78503-194">Zpřístupňuje dvě metody: `Start`, který spustí animaci běžící na hranice a `Stop`, která zastaví animaci.</span><span class="sxs-lookup"><span data-stu-id="78503-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="78503-195">Vzhledem k tomu, že `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují rozhraní `IMarqueeWidget`, `Start` a `Stop` vyčíslení každého podřízeného ovládacího prvku a volání `StartMarquee` a `StopMarquee` metody v uvedeném pořadí v každém podřízeném ovládacím prvku, který implementuje `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="78503-196">Vzhled ovládacích prvků `MarqueeBorder` a `MarqueeText` je závislý na rozložení, takže `MarqueeControl` přepisuje metodu <xref:System.Windows.Forms.Control.OnLayout%2A> a volá <xref:System.Windows.Forms.Control.PerformLayout%2A> na podřízených ovládacích prvcích tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="78503-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="78503-197">Toto je rozsah přizpůsobení `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="78503-198">Běhové funkce jsou implementovány ovládacími prvky `MarqueeBorder` a `MarqueeText` a funkce v době návrhu jsou implementovány třídami `MarqueeBorderDesigner` a `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="78503-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="78503-199">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="78503-199">To implement your custom control</span></span>

1. <span data-ttu-id="78503-200">Otevřete zdrojový soubor `MarqueeControl` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-201">Implementujte metody `Start` a `Stop`.</span><span class="sxs-lookup"><span data-stu-id="78503-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="78503-202">Přepsat metodu <xref:System.Windows.Forms.Control.OnLayout%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="78503-203">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="78503-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="78503-204">`MarqueeControl` bude hostovat dva druhy podřízených ovládacích prvků: ovládací prvek `MarqueeBorder` a ovládací prvek `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="78503-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="78503-205">`MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů.</span><span class="sxs-lookup"><span data-stu-id="78503-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="78503-206">Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat.</span><span class="sxs-lookup"><span data-stu-id="78503-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="78503-207">Rychlost, s jakou jsou indikátory blesku ovládány vlastností nazvanou `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="78503-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="78503-208">Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="78503-209">Dvě metody nazvané `StartMarquee` a `StopMarquee`určují, kdy se animace spouští a zastavuje.</span><span class="sxs-lookup"><span data-stu-id="78503-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="78503-210">`MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec.</span><span class="sxs-lookup"><span data-stu-id="78503-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="78503-211">Podobně jako u ovládacího prvku `MarqueeBorder` je rychlost, s jakou je text blikající, ovládána vlastností `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="78503-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="78503-212">Ovládací prvek `MarqueeText` má také společné metody `StartMarquee` a `StopMarquee` s ovládacím prvkem `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="78503-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="78503-213">V době návrhu `MarqueeControlRootDesigner` umožňuje přidat tyto dva typy ovládacích prvků do `MarqueeControl` v jakékoli kombinaci.</span><span class="sxs-lookup"><span data-stu-id="78503-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="78503-214">Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="78503-215">To umožňuje `MarqueeControl` objevit podřízené ovládací prvky související s rámečkem a dát jim speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="78503-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="78503-216">K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objektů z oboru názvů <xref:System.ComponentModel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78503-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="78503-217">Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale v případě, že existuje mnoho objektů `IMarqueeWidget`, nemusí být jedno vlákno uživatelského rozhraní schopné s animací zůstat.</span><span class="sxs-lookup"><span data-stu-id="78503-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="78503-218">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="78503-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="78503-219">Přidejte do projektu `MarqueeControlLibrary` novou položku třídy.</span><span class="sxs-lookup"><span data-stu-id="78503-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-220">Dejte novému zdrojovému souboru základní název "IMarqueeWidget".</span><span class="sxs-lookup"><span data-stu-id="78503-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="78503-221">Otevřete zdrojový soubor `IMarqueeWidget` v **editoru kódu** a změňte deklaraci z `class` na `interface`:</span><span class="sxs-lookup"><span data-stu-id="78503-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="78503-222">Přidejte následující kód do rozhraní `IMarqueeWidget` pro vystavení dvou metod a vlastnost, která zpracovává animaci běžícího výběru:</span><span class="sxs-lookup"><span data-stu-id="78503-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="78503-223">Přidejte novou položku **vlastního ovládacího prvku** do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-224">Dejte novému zdrojovému souboru základní název "MarqueeText".</span><span class="sxs-lookup"><span data-stu-id="78503-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="78503-225">Přetáhněte komponentu <xref:System.ComponentModel.BackgroundWorker> z **panelu nástrojů** do ovládacího prvku `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="78503-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="78503-226">Tato součást umožní, aby se ovládací prvek `MarqueeText` sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="78503-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="78503-227">V okně **vlastnosti** nastavte vlastnost <xref:System.ComponentModel.BackgroundWorker> `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="78503-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="78503-228">Tato nastavení umožňují, aby součást <xref:System.ComponentModel.BackgroundWorker> pravidelně vyvolala událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="78503-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="78503-229">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="78503-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="78503-230">Otevřete zdrojový soubor `MarqueeText` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-231">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="78503-232">Změňte deklaraci `MarqueeText`, aby dědila z <xref:System.Windows.Forms.Label> a implementovala rozhraní `IMarqueeWidget`:</span><span class="sxs-lookup"><span data-stu-id="78503-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="78503-233">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="78503-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="78503-234">Pole `isLit` určuje, zda se má text vykreslit barvou určenou vlastností `LightColor`.</span><span class="sxs-lookup"><span data-stu-id="78503-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="78503-235">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="78503-236">Metody `StartMarquee` a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody komponenty <xref:System.ComponentModel.BackgroundWorker> ke spuštění a zastavení animace.</span><span class="sxs-lookup"><span data-stu-id="78503-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="78503-237">Atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na vlastnost `UpdatePeriod`, takže se zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".</span><span class="sxs-lookup"><span data-stu-id="78503-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="78503-238">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-238">Implement the property accessors.</span></span> <span data-ttu-id="78503-239">Pro klienty vystavíte dvě vlastnosti: `LightColor` a `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="78503-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="78503-240">Na tyto vlastnosti se aplikují atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti nazvané "výběr".</span><span class="sxs-lookup"><span data-stu-id="78503-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="78503-241">Implementujte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker> komponenty.</span><span class="sxs-lookup"><span data-stu-id="78503-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="78503-242">Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.DoWork> v režimu spánku po dobu v milisekundách určené `UpdatePeriod` poté vyvolá událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="78503-243">Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> přepíná text mezi jeho světlým a tmavým stavem, aby bylo možné podobu blikání.</span><span class="sxs-lookup"><span data-stu-id="78503-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="78503-244">Přepište metodu <xref:System.Windows.Forms.Control.OnPaint%2A> pro povolení animace.</span><span class="sxs-lookup"><span data-stu-id="78503-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="78503-245">Stisknutím klávesy **F6** Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="78503-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="78503-246">Vytvoření podřízeného ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="78503-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="78503-247">`MarqueeBorder` ovládací prvek je poněkud složitější než ovládací prvek `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="78503-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="78503-248">Má více vlastností a další informace o animaci v metodě <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="78503-249">V zásadě je poměrně podobný ovládacímu prvku `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="78503-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="78503-250">Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může mít podřízené ovládací prvky, musí mít informace o <xref:System.Windows.Forms.Control.Layout>ch událostech.</span><span class="sxs-lookup"><span data-stu-id="78503-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="78503-251">Vytvoření ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="78503-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="78503-252">Přidejte novou položku **vlastního ovládacího prvku** do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-253">Dejte novému zdrojovému souboru základní název "MarqueeBorder".</span><span class="sxs-lookup"><span data-stu-id="78503-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="78503-254">Přetáhněte komponentu <xref:System.ComponentModel.BackgroundWorker> z **panelu nástrojů** do ovládacího prvku `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="78503-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="78503-255">Tato součást umožní, aby se ovládací prvek `MarqueeBorder` sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="78503-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="78503-256">V okně **vlastnosti** nastavte vlastnost <xref:System.ComponentModel.BackgroundWorker> `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="78503-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="78503-257">Tato nastavení umožňují, aby součást <xref:System.ComponentModel.BackgroundWorker> pravidelně vyvolala událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="78503-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="78503-258">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="78503-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="78503-259">V okně **vlastnosti** vyberte tlačítko **události** .</span><span class="sxs-lookup"><span data-stu-id="78503-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="78503-260">Připojte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.</span><span class="sxs-lookup"><span data-stu-id="78503-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="78503-261">Otevřete zdrojový soubor `MarqueeBorder` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-262">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="78503-263">Změňte deklaraci `MarqueeBorder`, aby dědila z <xref:System.Windows.Forms.Panel> a implementovala rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="78503-264">Deklarujete dva výčty pro správu stavu `MarqueeBorder` ovládacího prvku: `MarqueeSpinDirection`, který určuje směr, ve kterém se světla otáčí kolem ohraničení a `MarqueeLightShape`, která určuje tvar světel (čtvercové nebo kruhové).</span><span class="sxs-lookup"><span data-stu-id="78503-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="78503-265">Tyto deklarace umístěte před deklaraci třídy `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="78503-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="78503-266">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="78503-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="78503-267">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="78503-268">Metody `StartMarquee` a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody komponenty <xref:System.ComponentModel.BackgroundWorker> ke spuštění a zastavení animace.</span><span class="sxs-lookup"><span data-stu-id="78503-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="78503-269">Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může obsahovat podřízené ovládací prvky, metoda `StartMarquee` vytvoří výčet všech podřízených ovládacích prvků a volání `StartMarquee` na těch, které implementují `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="78503-270">Metoda `StopMarquee` má podobnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="78503-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="78503-271">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-271">Implement the property accessors.</span></span> <span data-ttu-id="78503-272">Ovládací prvek `MarqueeBorder` má několik vlastností pro řízení jeho vzhledu.</span><span class="sxs-lookup"><span data-stu-id="78503-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="78503-273">Implementujte obslužné rutiny pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker> komponenty.</span><span class="sxs-lookup"><span data-stu-id="78503-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="78503-274">Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.DoWork> v režimu spánku po dobu v milisekundách určené `UpdatePeriod` poté vyvolá událost <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="78503-275">Obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zvýší pozici "základního" světla, ze kterého je určován stav světla nebo tmavého světla, a zavolá metodu <xref:System.Windows.Forms.Control.Refresh%2A>, která způsobí, že ovládací prvek překreslí sám sebe.</span><span class="sxs-lookup"><span data-stu-id="78503-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="78503-276">Implementujte pomocné metody `IsLit` a `DrawLight`.</span><span class="sxs-lookup"><span data-stu-id="78503-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="78503-277">Metoda `IsLit` Určuje barvu světla na dané pozici.</span><span class="sxs-lookup"><span data-stu-id="78503-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="78503-278">Indikátory, které jsou "osvětlené", jsou vykresleny barevnou vlastností `LightColor` a ty, které jsou "tmavé" jsou vykresleny v barvě dané vlastností `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="78503-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="78503-279">Metoda `DrawLight` kreslí světlo pomocí příslušné barvy, tvaru a pozice.</span><span class="sxs-lookup"><span data-stu-id="78503-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="78503-280">Přepište metody <xref:System.Windows.Forms.Control.OnLayout%2A> a <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="78503-281">Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> kreslí světla podél okrajů ovládacího prvku `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="78503-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="78503-282">Vzhledem k tomu, že metoda <xref:System.Windows.Forms.Control.OnPaint%2A> závisí na rozměrech ovládacího prvku `MarqueeBorder`, je nutné jej zavolat při každé změně rozložení.</span><span class="sxs-lookup"><span data-stu-id="78503-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="78503-283">Chcete-li to dosáhnout, přepište <xref:System.Windows.Forms.Control.OnLayout%2A> a zavolejte <xref:System.Windows.Forms.Control.Refresh%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="78503-284">Vytvoření vlastního návrháře pro stínové a filtrové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="78503-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="78503-285">Třída `MarqueeControlRootDesigner` poskytuje implementaci pro kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="78503-286">Kromě tohoto návrháře, který pracuje na `MarqueeControl`, budete potřebovat vlastního návrháře, který je konkrétně přidružen k ovládacímu prvku `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="78503-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="78503-287">Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="78503-288">Konkrétně `MarqueeBorderDesigner` bude "Stínová" a bude filtrovat určité vlastnosti ovládacího prvku `MarqueeBorder` a změnit jejich interakci s návrhovým prostředím.</span><span class="sxs-lookup"><span data-stu-id="78503-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="78503-289">Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning".</span><span class="sxs-lookup"><span data-stu-id="78503-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="78503-290">Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.</span><span class="sxs-lookup"><span data-stu-id="78503-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="78503-291">V tomto příkladu budou vlastnosti <xref:System.Windows.Forms.Control.Visible%2A> a <xref:System.Windows.Forms.Control.Enabled%2A> vystínované `MarqueeBorderDesigner`, což brání uživateli v tom, aby během návrhu byl ovládací prvek `MarqueeBorder` neviditelný nebo zakázaný.</span><span class="sxs-lookup"><span data-stu-id="78503-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="78503-292">Návrháři mohou také přidávat a odebírat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="78503-293">V tomto příkladu bude vlastnost <xref:System.Windows.Forms.Control.Padding%2A> odebrána v době návrhu, protože ovládací prvek `MarqueeBorder` programově nastaví odsazení na základě velikosti světel určených vlastností `LightSize`.</span><span class="sxs-lookup"><span data-stu-id="78503-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="78503-294">Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:</span><span class="sxs-lookup"><span data-stu-id="78503-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="78503-295">Při změně veřejného rozhraní komponenty pomocí těchto metod použijte tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="78503-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="78503-296">Přidat nebo odebrat položky pouze z `PreFilter`ch metod</span><span class="sxs-lookup"><span data-stu-id="78503-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="78503-297">Upravit existující položky jenom v `PostFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="78503-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="78503-298">Vždy volejte základní implementaci nejprve v metodách `PreFilter`</span><span class="sxs-lookup"><span data-stu-id="78503-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="78503-299">Vždy volat základní implementaci jako poslední v metodách `PostFilter`</span><span class="sxs-lookup"><span data-stu-id="78503-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="78503-300">Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.</span><span class="sxs-lookup"><span data-stu-id="78503-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="78503-301">Třída <xref:System.ComponentModel.Design.ComponentDesigner> poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.</span><span class="sxs-lookup"><span data-stu-id="78503-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="78503-302">Vytvoření vlastního návrháře pro vlastnosti stínu a filtru</span><span class="sxs-lookup"><span data-stu-id="78503-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="78503-303">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="78503-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="78503-304">Dejte zdrojovému souboru základní název **MarqueeBorderDesigner**.</span><span class="sxs-lookup"><span data-stu-id="78503-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="78503-305">Otevřete zdrojový soubor MarqueeBorderDesigner v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-306">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="78503-307">Změňte deklaraci `MarqueeBorderDesigner`, aby dědila z <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span><span class="sxs-lookup"><span data-stu-id="78503-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="78503-308">Vzhledem k tomu, že ovládací prvek `MarqueeBorder` může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner>, což zpracovává interakci nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="78503-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="78503-309">Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="78503-310">Implementujte vlastnosti <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="78503-311">Tyto implementace nastínují vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="78503-312">Zpracovat změny součásti</span><span class="sxs-lookup"><span data-stu-id="78503-312">Handle Component Changes</span></span>

<span data-ttu-id="78503-313">Třída `MarqueeControlRootDesigner` poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance.</span><span class="sxs-lookup"><span data-stu-id="78503-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="78503-314">Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="78503-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="78503-315">Váš kód bude implementovat dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="78503-316">Když uživatelé navrhují své `MarqueeControl` instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="78503-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="78503-317">Prostředí pro dobu návrhu nabízí pohodlný službu, <xref:System.ComponentModel.Design.IComponentChangeService>pro sledování změn stavu komponent.</span><span class="sxs-lookup"><span data-stu-id="78503-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="78503-318">Odkaz na tuto službu získáte dotazem na prostředí pomocí metody <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="78503-319">Pokud je dotaz úspěšný, může váš návrhář připojit obslužnou rutinu pro událost <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="78503-320">V případě `MarqueeControlRootDesigner` třídy zavoláte metodu <xref:System.Windows.Forms.Control.Refresh%2A> na každý objekt `IMarqueeWidget` obsažený v `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="78503-321">Tím dojde k tomu, že objekt `IMarqueeWidget` pro překreslení sebe sama o sobě vhodně, když se změní vlastnosti, jako je jeho nadřazený <xref:System.Windows.Forms.Control.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="78503-322">Zpracování změn součástí</span><span class="sxs-lookup"><span data-stu-id="78503-322">To handle component changes</span></span>

1. <span data-ttu-id="78503-323">Otevřete zdrojový soubor `MarqueeControlRootDesigner` v **editoru kódu** a přepište metodu <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="78503-324">Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz na <xref:System.ComponentModel.Design.IComponentChangeService>.</span><span class="sxs-lookup"><span data-stu-id="78503-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="78503-325">Implementujte obslužnou rutinu události <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="78503-326">Otestujte typ odesílající komponenty, a pokud se jedná o `IMarqueeWidget`, zavolejte metodu <xref:System.Windows.Forms.Control.Refresh%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="78503-327">Přidání příkazů návrháře do vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="78503-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="78503-328">Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="78503-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="78503-329">Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="78503-330">Další informace najdete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="78503-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="78503-331">Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**.</span><span class="sxs-lookup"><span data-stu-id="78503-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="78503-332">Tyto příkazy vám umožní zobrazit v době návrhu chování `MarqueeControl` v době běhu.</span><span class="sxs-lookup"><span data-stu-id="78503-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="78503-333">Tyto operace budou přidány do `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="78503-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="78503-334">Při vyvolání příkazu **Spustit test** bude obslužná rutina události příkazu volat metodu `StartMarquee` v `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="78503-335">Při vyvolání příkazu **zastavit test** obslužná rutina události vyvolá metodu `StopMarquee` v `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="78503-336">Implementace metod `StartMarquee` a `StopMarquee` volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.</span><span class="sxs-lookup"><span data-stu-id="78503-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="78503-337">Přidání příkazů návrháře do vlastních návrhářů</span><span class="sxs-lookup"><span data-stu-id="78503-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="78503-338">Ve třídě `MarqueeControlRootDesigner` přidejte obslužné rutiny událostí s názvem `OnVerbRunTest` a `OnVerbStopTest`.</span><span class="sxs-lookup"><span data-stu-id="78503-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="78503-339">Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře.</span><span class="sxs-lookup"><span data-stu-id="78503-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="78503-340">`MarqueeControlRootDesigner` dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> z jeho základní třídy.</span><span class="sxs-lookup"><span data-stu-id="78503-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="78503-341">Vytvoříte dva nové objekty <xref:System.ComponentModel.Design.DesignerVerb> a přidáte je do této kolekce v metodě <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="78503-342">Vytvoření vlastního Editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="78503-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="78503-343">Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="78503-344">To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="78503-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="78503-345">Ovládací prvek `MarqueeBorder` zpřístupňuje v okno Vlastnosti několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="78503-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="78503-346">Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty.</span><span class="sxs-lookup"><span data-stu-id="78503-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="78503-347">Pro ilustraci použití Editoru typů uživatelského rozhraní bude mít vlastnost `MarqueeLightShape` přidruženou třídu <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="78503-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="78503-348">Vytvoření vlastního editoru typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="78503-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="78503-349">Otevřete zdrojový soubor `MarqueeBorder` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="78503-350">V definici třídy `MarqueeBorder` Deklarujte třídu nazvanou `LightShapeEditor`, která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="78503-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="78503-351">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance nazvanou `editorService`.</span><span class="sxs-lookup"><span data-stu-id="78503-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="78503-352">Přepsat metodu <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="78503-353">Tato implementace vrací <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, která oznamuje vývojovému prostředí, jak zobrazit `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="78503-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="78503-354">Přepsat metodu <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="78503-355">Tato implementace se dotazuje návrhového prostředí pro objekt <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>.</span><span class="sxs-lookup"><span data-stu-id="78503-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="78503-356">V případě úspěchu vytvoří `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="78503-357">Metoda <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> je vyvolána pro spuštění `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="78503-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="78503-358">Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="78503-359">Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="78503-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="78503-360">Vlastnost `MarqueeLightShape` podporuje dva typy lehkých tvarů: `Square` a `Circle`.</span><span class="sxs-lookup"><span data-stu-id="78503-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="78503-361">Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="78503-362">Tento vlastní ovládací prvek bude použit vaším <xref:System.Drawing.Design.UITypeEditor> k interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="78503-363">Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="78503-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="78503-364">Přidejte novou <xref:System.Windows.Forms.UserControl>ovou položku do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="78503-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-365">Dejte novému zdrojovému souboru základní název **LightShapeSelectionControl**.</span><span class="sxs-lookup"><span data-stu-id="78503-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="78503-366">Přetáhněte dva ovládací prvky <xref:System.Windows.Forms.Panel> z **panelu nástrojů** na `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="78503-367">Pojmenujte je `squarePanel` a `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="78503-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="78503-368">Uspořádejte je vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="78503-368">Arrange them side by side.</span></span> <span data-ttu-id="78503-369">Nastavte vlastnost <xref:System.Windows.Forms.Control.Size%2A> obou ovládacích prvků <xref:System.Windows.Forms.Panel> na **(60, 60)** .</span><span class="sxs-lookup"><span data-stu-id="78503-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="78503-370">Nastavte vlastnost <xref:System.Windows.Forms.Control.Location%2A> ovládacího prvku `squarePanel` na **(8, 10)** .</span><span class="sxs-lookup"><span data-stu-id="78503-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="78503-371">Nastavte vlastnost <xref:System.Windows.Forms.Control.Location%2A> ovládacího prvku `circlePanel` na **(80, 10)** .</span><span class="sxs-lookup"><span data-stu-id="78503-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="78503-372">Nakonec nastavte vlastnost <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` na **(150, 80)** .</span><span class="sxs-lookup"><span data-stu-id="78503-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="78503-373">Otevřete zdrojový soubor `LightShapeSelectionControl` v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="78503-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="78503-374">V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="78503-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="78503-375">Implementujte <xref:System.Windows.Forms.Control.Click> obslužných rutin událostí pro ovládací prvky `squarePanel` a `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="78503-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="78503-376">Tyto metody vyvolávají <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> pro ukončení relace úprav vlastního <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="78503-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="78503-377">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance nazvanou `editorService`.</span><span class="sxs-lookup"><span data-stu-id="78503-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="78503-378">Deklarujte `MarqueeLightShape` proměnnou instance nazvanou `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="78503-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="78503-379">V konstruktoru `LightShapeSelectionControl` připojte obslužné rutiny události <xref:System.Windows.Forms.Control.Click> k <xref:System.Windows.Forms.Control.Click> událostem `squarePanel` a `circlePanel`ch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="78503-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="78503-380">Také definujte přetížení konstruktoru, které přiřadí hodnotu `MarqueeLightShape` z návrhového prostředí do pole `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="78503-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="78503-381">V metodě <xref:System.ComponentModel.Component.Dispose%2A> odpojte obslužné rutiny události <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="78503-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="78503-382">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="78503-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="78503-383">Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici metody <xref:System.ComponentModel.Component.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="78503-384">Implementujte vlastnost `LightShape`.</span><span class="sxs-lookup"><span data-stu-id="78503-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="78503-385">Přepsat metodu <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="78503-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="78503-386">Tato implementace Vykreslí vyplněný čtverec a kruh.</span><span class="sxs-lookup"><span data-stu-id="78503-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="78503-387">Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.</span><span class="sxs-lookup"><span data-stu-id="78503-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="78503-388">Testování vlastního ovládacího prvku v Návrháři</span><span class="sxs-lookup"><span data-stu-id="78503-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="78503-389">V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt.</span><span class="sxs-lookup"><span data-stu-id="78503-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="78503-390">Otestujte implementaci vytvořením ovládacího prvku, který dědí z třídy `MarqueeControl` a použijete jej na formuláři.</span><span class="sxs-lookup"><span data-stu-id="78503-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="78503-391">Vytvoření vlastní implementace MarqueeControl</span><span class="sxs-lookup"><span data-stu-id="78503-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="78503-392">Otevřete `DemoMarqueeControl` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="78503-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="78503-393">Tím se vytvoří instance typu `DemoMarqueeControl` a zobrazí se v instanci `MarqueeControlRootDesigner` typu.</span><span class="sxs-lookup"><span data-stu-id="78503-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="78503-394">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se ovládací prvky `MarqueeBorder` a `MarqueeText` dostupné pro výběr.</span><span class="sxs-lookup"><span data-stu-id="78503-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="78503-395">Přetáhněte instanci ovládacího prvku `MarqueeBorder` na návrhovou plochu `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="78503-396">Ukotvit tento ovládací prvek `MarqueeBorder` do nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78503-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="78503-397">Přetáhněte instanci ovládacího prvku `MarqueeText` na návrhovou plochu `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="78503-398">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="78503-398">Build the solution.</span></span>

6. <span data-ttu-id="78503-399">Klikněte pravým tlačítkem myši na `DemoMarqueeControl` a z místní nabídky vyberte možnost **Spustit test** . tím se spustí animace.</span><span class="sxs-lookup"><span data-stu-id="78503-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="78503-400">Kliknutím na **zastavit test** zastavte animaci.</span><span class="sxs-lookup"><span data-stu-id="78503-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="78503-401">Otevřete **Form1** v zobrazení Návrh.</span><span class="sxs-lookup"><span data-stu-id="78503-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="78503-402">Do formuláře umístěte dva ovládací prvky <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="78503-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="78503-403">Pojmenujte je `startButton` a `stopButton`a změňte hodnoty vlastností <xref:System.Windows.Forms.Control.Text%2A> na **Start** a **stop**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="78503-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="78503-404">Implementujte obslužné rutiny událostí <xref:System.Windows.Forms.Control.Click> pro ovládací prvky <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="78503-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="78503-405">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="78503-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="78503-406">Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .</span><span class="sxs-lookup"><span data-stu-id="78503-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="78503-407">V obslužných rutinách události <xref:System.Windows.Forms.Control.Click> volejte na `DemoMarqueeControl`metody `Start` a `Stop`.</span><span class="sxs-lookup"><span data-stu-id="78503-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. <span data-ttu-id="78503-408">Nastavte projekt `MarqueeControlTest` jako spouštěný projekt a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="78503-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="78503-409">Zobrazí se formulář zobrazující `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="78503-410">Kliknutím na tlačítko **Start** spustíte animaci.</span><span class="sxs-lookup"><span data-stu-id="78503-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="78503-411">Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.</span><span class="sxs-lookup"><span data-stu-id="78503-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78503-412">Další kroky</span><span class="sxs-lookup"><span data-stu-id="78503-412">Next steps</span></span>

<span data-ttu-id="78503-413">`MarqueeControlLibrary` ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů.</span><span class="sxs-lookup"><span data-stu-id="78503-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="78503-414">Tuto ukázku můžete udělat několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="78503-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="78503-415">Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="78503-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="78503-416">Chcete-li vytvořit vnořený efekt, přidejte další ovládací prvky `MarqueBorder` a ukotvěte je Dock v rámci jejich nadřazených instancí.</span><span class="sxs-lookup"><span data-stu-id="78503-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="78503-417">Experimentujte s různými nastaveními `UpdatePeriod` a vlastností souvisejícími s osvětlením.</span><span class="sxs-lookup"><span data-stu-id="78503-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="78503-418">Vytvořte vlastní implementace `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="78503-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="78503-419">Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.</span><span class="sxs-lookup"><span data-stu-id="78503-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="78503-420">Dále upravte prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="78503-420">Further customize the design-time experience.</span></span> <span data-ttu-id="78503-421">Můžete vyzkoušet více vlastností stínové kopie než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>a můžete přidat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="78503-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="78503-422">Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="78503-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="78503-423">License `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="78503-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="78503-424">Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy.</span><span class="sxs-lookup"><span data-stu-id="78503-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="78503-425">Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="78503-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78503-426">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78503-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
