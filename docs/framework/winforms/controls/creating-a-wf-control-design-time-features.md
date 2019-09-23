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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 53824336e1ae47870e6acffe20340f145caf9b4d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182589"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="99d39-102">Návod: Vytvoření ovládacího prvku, který bude využívat funkce pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="99d39-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="99d39-103">Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="99d39-104">Tento článek ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="99d39-105">Implementujete `MarqueeControl` typ a přidruženou třídu návrháře s názvem `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="99d39-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="99d39-106">`MarqueeControl` Typ implementuje zobrazení podobné textu v kino s animovanými indikátory a blikající text.</span><span class="sxs-lookup"><span data-stu-id="99d39-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="99d39-107">Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="99d39-108">Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci s animovanými indikátory a blikající text v mnoha kombinacích.</span><span class="sxs-lookup"><span data-stu-id="99d39-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="99d39-109">Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="99d39-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="99d39-110">Až budete s tímto návodem hotový, váš vlastní ovládací prvek bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="99d39-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="99d39-112">Úplný výpis kódu naleznete v tématu [How to: Vytvořte model Windows Forms ovládací prvek, který bude využívat funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99d39-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99d39-113">Prerequisites</span></span>

<span data-ttu-id="99d39-114">Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99d39-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="99d39-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="99d39-115">Create the project</span></span>

<span data-ttu-id="99d39-116">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="99d39-116">The first step is to create the application project.</span></span> <span data-ttu-id="99d39-117">Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="99d39-118">V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte jej **MarqueeControlTest**.</span><span class="sxs-lookup"><span data-stu-id="99d39-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="99d39-119">Vytvořit projekt knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="99d39-119">Create the control library project</span></span>

1. <span data-ttu-id="99d39-120">Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="99d39-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="99d39-121">Pojmenujte projekt **MarqueeControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="99d39-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="99d39-122">Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce.</span><span class="sxs-lookup"><span data-stu-id="99d39-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="99d39-123"><xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlLibrary` do projektu novou položku.</span><span class="sxs-lookup"><span data-stu-id="99d39-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-124">Dejte novému zdrojovému souboru základní název **MarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="99d39-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="99d39-125">Pomocí **Průzkumník řešení**vytvořte v `MarqueeControlLibrary` projektu novou složku.</span><span class="sxs-lookup"><span data-stu-id="99d39-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="99d39-126">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="99d39-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="99d39-127">Pojmenujte ho **MarqueeControlRootDesigner**.</span><span class="sxs-lookup"><span data-stu-id="99d39-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="99d39-128">Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="99d39-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="99d39-129">Odkaz na projekt vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="99d39-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="99d39-130">K otestování vlastního ovládacího prvku použijete projekt.`MarqueeControlTest`</span><span class="sxs-lookup"><span data-stu-id="99d39-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="99d39-131">Testovací projekt se při přidání odkazu na projekt do `MarqueeControlLibrary` sestavení změní na vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="99d39-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="99d39-132">V projektu přidejte odkaz na projekt do `MarqueeControlLibrary` sestavení. `MarqueeControlTest`</span><span class="sxs-lookup"><span data-stu-id="99d39-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="99d39-133">Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.</span><span class="sxs-lookup"><span data-stu-id="99d39-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="99d39-134">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="99d39-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="99d39-135">Vlastní ovládací prvek bude odvozen z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="99d39-136">To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.</span><span class="sxs-lookup"><span data-stu-id="99d39-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="99d39-137">Vlastní ovládací prvek bude mít přidružený vlastní Návrhář.</span><span class="sxs-lookup"><span data-stu-id="99d39-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="99d39-138">To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="99d39-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="99d39-139">K přidružení ovládacího prvku ke svému návrháři použijte <xref:System.ComponentModel.DesignerAttribute> třídu.</span><span class="sxs-lookup"><span data-stu-id="99d39-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="99d39-140">Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99d39-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="99d39-141">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="99d39-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="99d39-142">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-143">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="99d39-144"><xref:System.ComponentModel.DesignerAttribute> Přidejte`MarqueeControl` do deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="99d39-145">Tím přiřadíte vlastní ovládací prvek ke svému návrháři.</span><span class="sxs-lookup"><span data-stu-id="99d39-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="99d39-146">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="99d39-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-147">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="99d39-148">Změňte deklaraci `MarqueeControlRootDesigner` na dědění <xref:System.Windows.Forms.Design.DocumentDesigner> z třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="99d39-149">Použijte pro určení interakce návrháře pomocí **sady nástrojů.** <xref:System.ComponentModel.ToolboxItemFilterAttribute></span><span class="sxs-lookup"><span data-stu-id="99d39-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="99d39-150">Definice pro `MarqueeControlRootDesigner` třídu byla uzavřená v oboru názvů s názvem MarqueeControlLibrary. Design.</span><span class="sxs-lookup"><span data-stu-id="99d39-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="99d39-151">Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.</span><span class="sxs-lookup"><span data-stu-id="99d39-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="99d39-152">Definujte konstruktor pro `MarqueeControlRootDesigner` třídu.</span><span class="sxs-lookup"><span data-stu-id="99d39-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="99d39-153"><xref:System.Diagnostics.Trace.WriteLine%2A> Vloží příkaz do těla konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="99d39-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="99d39-154">To bude užitečné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="99d39-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="99d39-155">Vytvoření instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="99d39-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="99d39-156"><xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlTest` do projektu novou položku.</span><span class="sxs-lookup"><span data-stu-id="99d39-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="99d39-157">Dejte novému zdrojovému souboru základní název **DemoMarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="99d39-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="99d39-158">Otevřete soubor v **editoru kódu.** `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-159">V horní části souboru importujte `MarqueeControlLibrary` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="99d39-160">Změňte deklaraci `DemoMarqueeControl` na dědění `MarqueeControl` z třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="99d39-161">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="99d39-161">Build the project.</span></span>

5. <span data-ttu-id="99d39-162">Otevřete Form1 v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="99d39-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="99d39-163">V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji.</span><span class="sxs-lookup"><span data-stu-id="99d39-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="99d39-164">Přetáhněte z panelu nástrojů do formuláře. `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="99d39-165">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="99d39-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="99d39-166">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="99d39-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="99d39-167">Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty.</span><span class="sxs-lookup"><span data-stu-id="99d39-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="99d39-168">Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="99d39-169">Další informace najdete v tématu [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="99d39-170">Klikněte pravým tlačítkem `MarqueeControlLibrary` na projekt a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="99d39-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="99d39-171">V dialogovém okně **stránky vlastností MarqueeControlLibrary** vyberte stránku **ladění** .</span><span class="sxs-lookup"><span data-stu-id="99d39-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="99d39-172">V části **spouštěcí akce** vyberte **spustit externí program**.</span><span class="sxs-lookup"><span data-stu-id="99d39-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="99d39-173">Budete ladit samostatnou instanci sady Visual Studio, takže kliknutím na tlačítko se třemi![tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) můžete procházet prostředí IDE sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99d39-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="99d39-174">Název spustitelného souboru je devenv. exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE\devenv.exe*.</span><span class="sxs-lookup"><span data-stu-id="99d39-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="99d39-175">Kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="99d39-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="99d39-176">Klikněte pravým tlačítkem na projekt MarqueeControlLibrary a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.</span><span class="sxs-lookup"><span data-stu-id="99d39-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="99d39-177">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="99d39-177">Checkpoint</span></span>

<span data-ttu-id="99d39-178">Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="99d39-179">Jakmile zjistíte, že je prostředí ladění správně nastavené, otestujete přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.</span><span class="sxs-lookup"><span data-stu-id="99d39-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="99d39-180">Otestování ladicího prostředí a přidružení návrháře</span><span class="sxs-lookup"><span data-stu-id="99d39-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="99d39-181">Otevřete zdrojový soubor MarqueeControlRootDesigner v **editoru kódu** a umístěte zarážku na <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="99d39-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="99d39-182">Stisknutím klávesy **F5** spusťte relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="99d39-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="99d39-183">Vytvoří se nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99d39-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="99d39-184">V nové instanci aplikace Visual Studio otevřete řešení MarqueeControlTest.</span><span class="sxs-lookup"><span data-stu-id="99d39-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="99d39-185">Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="99d39-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="99d39-186">Soubor řešení MarqueeControlTest. sln bude uveden jako naposledy použitý soubor.</span><span class="sxs-lookup"><span data-stu-id="99d39-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="99d39-187">`DemoMarqueeControl` Otevřete v návrháři.</span><span class="sxs-lookup"><span data-stu-id="99d39-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="99d39-188">Instance ladění aplikace Visual Studio získá fokus a provádění se zastaví na zarážce.</span><span class="sxs-lookup"><span data-stu-id="99d39-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="99d39-189">Stisknutím klávesy **F5** pokračujte v relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="99d39-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="99d39-190">V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="99d39-191">Zbývající část tohoto článku se zaměřuje na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="99d39-192">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="99d39-192">Implement the Custom Control</span></span>

<span data-ttu-id="99d39-193">`MarqueeControl` Je a<xref:System.Windows.Forms.UserControl> s malým počtem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="99d39-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="99d39-194">Zveřejňuje dvě metody: `Start`, který spustí animaci běžící na hranice a `Stop`, která zastaví animaci.</span><span class="sxs-lookup"><span data-stu-id="99d39-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="99d39-195">`StartMarquee` `IMarqueeWidget` `StopMarquee` `Stop` `Start` Protože obsahuje podřízené ovládací prvky, které implementují rozhraní, a vyčíslení každého podřízeného ovládacího prvku a volání metod a v každém podřízeném ovládacím prvku, v uvedeném pořadí. `MarqueeControl` , který `IMarqueeWidget`implementuje.</span><span class="sxs-lookup"><span data-stu-id="99d39-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="99d39-196">Vzhled `MarqueeBorder` ovládacích prvků a `MarqueeText` je závislý na <xref:System.Windows.Forms.Control.OnLayout%2A> rozložení, takže `MarqueeControl` přepíše metodu a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> podřízených ovládacích prvků tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="99d39-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="99d39-197">Toto je rozsah `MarqueeControl` úprav.</span><span class="sxs-lookup"><span data-stu-id="99d39-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="99d39-198">Funkce modulu runtime jsou implementovány `MarqueeBorder` ovládacími prvky a `MarqueeText` a `MarqueeBorderDesigner` funkce v době návrhu jsou implementovány třídami a `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="99d39-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="99d39-199">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="99d39-199">To implement your custom control</span></span>

1. <span data-ttu-id="99d39-200">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-201">Implementujte metody `Stop`a. `Start`</span><span class="sxs-lookup"><span data-stu-id="99d39-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="99d39-202">Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="99d39-203">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="99d39-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="99d39-204">Bude hostovat dva druhy podřízeného ovládacího prvku `MarqueeBorder` : ovládací prvek a `MarqueeText` ovládací prvek. `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="99d39-205">`MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů.</span><span class="sxs-lookup"><span data-stu-id="99d39-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="99d39-206">Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat.</span><span class="sxs-lookup"><span data-stu-id="99d39-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="99d39-207">Rychlost, s níž jsou indikátory blesku ovládány vlastností s `UpdatePeriod`názvem.</span><span class="sxs-lookup"><span data-stu-id="99d39-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="99d39-208">Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="99d39-209">Dvě metody, které `StartMarquee` jsou `StopMarquee`volány a, určují, kdy se animace spouští a zastavuje.</span><span class="sxs-lookup"><span data-stu-id="99d39-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="99d39-210">`MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec.</span><span class="sxs-lookup"><span data-stu-id="99d39-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="99d39-211">Podobně jako `MarqueeBorder` u ovládacího prvku je rychlost, s jakou je text blikající, ovládána `UpdatePeriod` vlastností.</span><span class="sxs-lookup"><span data-stu-id="99d39-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="99d39-212">Ovládací prvek `StopMarquee` `MarqueeBorder` má také společné metody asovládacímprvkem.`StartMarquee` `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="99d39-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="99d39-213">V době návrhu `MarqueeControlRootDesigner` umožňuje, aby tyto dva typy ovládacích prvků byly přidány `MarqueeControl` do jakékoli kombinace.</span><span class="sxs-lookup"><span data-stu-id="99d39-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="99d39-214">Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="99d39-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="99d39-215">To umožňuje, `MarqueeControl` aby se zjistily podřízené ovládací prvky související s rámečkem a přidávají jim speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="99d39-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="99d39-216">K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objekty <xref:System.ComponentModel?displayProperty=nameWithType> z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="99d39-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="99d39-217">Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale v případě, `IMarqueeWidget` že je přítomen velký počet objektů, nemusí být jedno vlákno uživatelského rozhraní schopno s animací zůstat.</span><span class="sxs-lookup"><span data-stu-id="99d39-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="99d39-218">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="99d39-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="99d39-219">Přidejte do `MarqueeControlLibrary` projektu novou položku třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-220">Dejte novému zdrojovému souboru základní název "IMarqueeWidget".</span><span class="sxs-lookup"><span data-stu-id="99d39-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="99d39-221">Otevřete zdrojový soubor v **editoru kódu** a změňte deklaraci z `class` na: `interface` `IMarqueeWidget`</span><span class="sxs-lookup"><span data-stu-id="99d39-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="99d39-222">Přidejte následující kód do `IMarqueeWidget` rozhraní, aby bylo možné vystavit dvě metody a vlastnost, která zpracovává animaci běžícího výběru:</span><span class="sxs-lookup"><span data-stu-id="99d39-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="99d39-223">Přidejte do `MarqueeControlLibrary` projektu novou položku **vlastního ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="99d39-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-224">Dejte novému zdrojovému souboru základní název "MarqueeText".</span><span class="sxs-lookup"><span data-stu-id="99d39-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="99d39-225">Přetáhněte komponentu z **panelu nástrojů** na ovládacíprvek.`MarqueeText` <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="99d39-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="99d39-226">Tato součást umožní, aby `MarqueeText` se ovládací prvek sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="99d39-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="99d39-227">V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="99d39-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="99d39-228">Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> vyvolala událost a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="99d39-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="99d39-229">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="99d39-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="99d39-230">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="99d39-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-231">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="99d39-232">Změňte deklaraci `MarqueeText` na dědění z <xref:System.Windows.Forms.Label> a k implementaci `IMarqueeWidget` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="99d39-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="99d39-233">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="99d39-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="99d39-234">Pole určuje, zda má být text vykreslen v barvě dané `LightColor` vlastností. `isLit`</span><span class="sxs-lookup"><span data-stu-id="99d39-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="99d39-235">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="99d39-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="99d39-236">`StartMarquee` Metodya`StopMarquee` vyvolají<xref:System.ComponentModel.BackgroundWorker> komponentu a<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody pro spuštění a zastavení animace. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="99d39-237">Atributy a se<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> aplikují na vlastnost,takžesezobrazívevlastníčástioknoVlastnostinazvané"výběr".`UpdatePeriod` <xref:System.ComponentModel.CategoryAttribute.Category%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="99d39-238">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-238">Implement the property accessors.</span></span> <span data-ttu-id="99d39-239">Pro klienty vystavíte dvě vlastnosti: `LightColor` a `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="99d39-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="99d39-240">Atributy <xref:System.ComponentModel.CategoryAttribute.Category%2A> a<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na tyto vlastnosti, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".</span><span class="sxs-lookup"><span data-stu-id="99d39-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="99d39-241">Implementujte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> komponenty <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a.</span><span class="sxs-lookup"><span data-stu-id="99d39-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="99d39-242">Obslužná rutina `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>události v režimu spánku po dobu určenou v milisekundách vyvolá událost, dokud váš kód nezastaví animaci voláním. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="99d39-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="99d39-243">Obslužná <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> rutina události přepíná text mezi jeho světlý a tmavý stav, aby bylo možné podobu blikání.</span><span class="sxs-lookup"><span data-stu-id="99d39-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="99d39-244"><xref:System.Windows.Forms.Control.OnPaint%2A> Přepsat metodu pro povolení animace.</span><span class="sxs-lookup"><span data-stu-id="99d39-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="99d39-245">Stisknutím klávesy **F6** Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="99d39-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="99d39-246">Vytvoření podřízeného ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="99d39-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="99d39-247">Ovládací prvek je poněkud složitější `MarqueeText` než ovládací prvek. `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="99d39-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="99d39-248">Má více vlastností a další animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě je více zapojena.</span><span class="sxs-lookup"><span data-stu-id="99d39-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="99d39-249">V zásadě je poměrně podobný `MarqueeText` ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="99d39-250">Vzhledem k tomu, že <xref:System.Windows.Forms.Control.Layout> ovládacíprvekmůžemítpodřízenéovládacíprvky,musíznátudálosti.`MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="99d39-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="99d39-251">Vytvoření ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="99d39-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="99d39-252">Přidejte do `MarqueeControlLibrary` projektu novou položku **vlastního ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="99d39-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-253">Dejte novému zdrojovému souboru základní název "MarqueeBorder".</span><span class="sxs-lookup"><span data-stu-id="99d39-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="99d39-254">Přetáhněte komponentu z **panelu nástrojů** na ovládacíprvek.`MarqueeBorder` <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="99d39-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="99d39-255">Tato součást umožní, aby `MarqueeBorder` se ovládací prvek sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="99d39-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="99d39-256">V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="99d39-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="99d39-257">Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> vyvolala událost a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="99d39-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="99d39-258">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="99d39-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="99d39-259">V okně **vlastnosti** vyberte tlačítko **události** .</span><span class="sxs-lookup"><span data-stu-id="99d39-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="99d39-260">Připojte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.DoWork> pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události a.</span><span class="sxs-lookup"><span data-stu-id="99d39-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="99d39-261">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="99d39-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-262">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="99d39-263">Změňte deklaraci `MarqueeBorder` na dědění z <xref:System.Windows.Forms.Panel> a k implementaci `IMarqueeWidget` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99d39-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="99d39-264">Deklarujete dva výčty pro správu `MarqueeBorder` stavu ovládacího prvku: `MarqueeSpinDirection`, který určuje směr otočení světla kolem ohraničení a `MarqueeLightShape`určuje tvar světel (čtvercové nebo kruhové).</span><span class="sxs-lookup"><span data-stu-id="99d39-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="99d39-265">Tyto deklarace umístěte před `MarqueeBorder` deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="99d39-266">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="99d39-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="99d39-267">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="99d39-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="99d39-268">`StartMarquee` Metodya`StopMarquee` vyvolají<xref:System.ComponentModel.BackgroundWorker> komponentu a<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody pro spuštění a zastavení animace. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="99d39-269">Vzhledem k `MarqueeBorder` `StartMarquee` tomu, že ovládací prvek může obsahovat podřízené ovládací prvky, metoda vytvoří výčet všech `StartMarquee` podřízených ovládacích prvků `IMarqueeWidget`a volání, která implementují.</span><span class="sxs-lookup"><span data-stu-id="99d39-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="99d39-270">`StopMarquee` Metoda má podobnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="99d39-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="99d39-271">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-271">Implement the property accessors.</span></span> <span data-ttu-id="99d39-272">`MarqueeBorder` Ovládací prvek má několik vlastností pro řízení jeho vzhledu.</span><span class="sxs-lookup"><span data-stu-id="99d39-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="99d39-273">Implementujte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker> pro události <xref:System.ComponentModel.BackgroundWorker.DoWork> komponenty <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a.</span><span class="sxs-lookup"><span data-stu-id="99d39-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="99d39-274">Obslužná rutina `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>události v režimu spánku po dobu určenou v milisekundách vyvolá událost, dokud váš kód nezastaví animaci voláním. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="99d39-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="99d39-275">Obslužná rutina <xref:System.Windows.Forms.Control.Refresh%2A>událostizvýší pozici "základního" světla, ze kterého je stanoven světlý nebo tmavý stav ostatních světel, a volá metodu, která způsobí, že ovládací prvek provede překreslení sám sebe. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged></span><span class="sxs-lookup"><span data-stu-id="99d39-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="99d39-276">Implementujte pomocné metody `IsLit` a `DrawLight`.</span><span class="sxs-lookup"><span data-stu-id="99d39-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="99d39-277">`IsLit` Metoda určuje barvu světla na dané pozici.</span><span class="sxs-lookup"><span data-stu-id="99d39-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="99d39-278">Indikátory, které jsou "osvětlené" jsou vykresleny barvou `LightColor` dané vlastností a ty, které jsou "tmavé" jsou vykresleny v barvě dané `DarkColor` vlastností.</span><span class="sxs-lookup"><span data-stu-id="99d39-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="99d39-279">`DrawLight` Metoda nakreslí světlo pomocí příslušné barvy, tvaru a pozice.</span><span class="sxs-lookup"><span data-stu-id="99d39-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="99d39-280">Přepište metody <xref:System.Windows.Forms.Control.OnPaint%2A>a. <xref:System.Windows.Forms.Control.OnLayout%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="99d39-281">Metoda kreslí světla podél okrajů `MarqueeBorder` ovládacího prvku. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="99d39-282">Vzhledem k tomu, že `MarqueeBorder` metodazávisínarozměrechovládacíhoprvku,jenutnéjejzavolatpřikaždézměněrozložení.<xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="99d39-283">Chcete-li toho dosáhnout <xref:System.Windows.Forms.Control.OnLayout%2A> , přepište a zavolejte. <xref:System.Windows.Forms.Control.Refresh%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="99d39-284">Vytvoření vlastního návrháře pro stínové a filtrové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="99d39-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="99d39-285">`MarqueeControlRootDesigner` Třída poskytuje implementaci pro kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="99d39-286">Kromě tohoto návrháře, který pracuje na `MarqueeControl`, budete potřebovat vlastního návrháře, který je konkrétně přidružen `MarqueeBorder` k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="99d39-287">Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="99d39-288">Konkrétně bude "stínem" a filtrovat určité vlastnosti `MarqueeBorder` ovládacího prvku, změnou jejich interakce s návrhovým prostředím. `MarqueeBorderDesigner`</span><span class="sxs-lookup"><span data-stu-id="99d39-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="99d39-289">Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning".</span><span class="sxs-lookup"><span data-stu-id="99d39-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="99d39-290">Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.</span><span class="sxs-lookup"><span data-stu-id="99d39-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="99d39-291">V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> budou vlastnosti a <xref:System.Windows.Forms.Control.Enabled%2A> nastínované pomocí `MarqueeBorderDesigner`, což brání uživateli v tom, aby během návrhu byl `MarqueeBorder` ovládací prvek neviditelný nebo zakázán.</span><span class="sxs-lookup"><span data-stu-id="99d39-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="99d39-292">Návrháři mohou také přidávat a odebírat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="99d39-293">V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> bude vlastnost odebrána v době návrhu, `MarqueeBorder` protože ovládací prvek programově nastaví odsazení na základě velikosti světla určených `LightSize` vlastností.</span><span class="sxs-lookup"><span data-stu-id="99d39-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="99d39-294">Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner>, která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:</span><span class="sxs-lookup"><span data-stu-id="99d39-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="99d39-295">Při změně veřejného rozhraní komponenty pomocí těchto metod použijte tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="99d39-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="99d39-296">Přidat nebo odebrat položky pouze v `PreFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="99d39-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="99d39-297">Upravit existující položky pouze v `PostFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="99d39-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="99d39-298">Vždy volat základní implementaci nejprve v `PreFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="99d39-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="99d39-299">Vždy volat základní implementaci jako poslední v `PostFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="99d39-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="99d39-300">Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.</span><span class="sxs-lookup"><span data-stu-id="99d39-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="99d39-301"><xref:System.ComponentModel.Design.ComponentDesigner> Třída poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.</span><span class="sxs-lookup"><span data-stu-id="99d39-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="99d39-302">Vytvoření vlastního návrháře pro vlastnosti stínu a filtru</span><span class="sxs-lookup"><span data-stu-id="99d39-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="99d39-303">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="99d39-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="99d39-304">Dejte zdrojovému souboru základní název **MarqueeBorderDesigner**.</span><span class="sxs-lookup"><span data-stu-id="99d39-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="99d39-305">Otevřete zdrojový soubor MarqueeBorderDesigner v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="99d39-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-306">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="99d39-307">Změňte deklaraci `MarqueeBorderDesigner` na dědění z <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span><span class="sxs-lookup"><span data-stu-id="99d39-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="99d39-308">Vzhledem k `MarqueeBorder` tomu, že ovládací prvek může `MarqueeBorderDesigner` obsahovat podřízené <xref:System.Windows.Forms.Design.ParentControlDesigner>ovládací prvky, dědí z, který zpracovává interakci nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="99d39-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="99d39-309">Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="99d39-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="99d39-310">Implementujte vlastnosti <xref:System.Windows.Forms.Control.Visible%2A>a. <xref:System.Windows.Forms.Control.Enabled%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="99d39-311">Tyto implementace nastínují vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="99d39-312">Zpracovat změny součásti</span><span class="sxs-lookup"><span data-stu-id="99d39-312">Handle Component Changes</span></span>

<span data-ttu-id="99d39-313">Třída poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="99d39-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="99d39-314">Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="99d39-315">Váš kód bude implementovat dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="99d39-316">Když uživatelé navrhují `MarqueeControl` své instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="99d39-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="99d39-317">Prostředí pro dobu návrhu nabízí pohodlný službu, <xref:System.ComponentModel.Design.IComponentChangeService>která umožňuje sledovat změny stavu součásti.</span><span class="sxs-lookup"><span data-stu-id="99d39-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="99d39-318">Odkaz na tuto službu získáte dotazem na prostředí pomocí <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="99d39-319">Pokud je dotaz úspěšný, může Návrhář k <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> události připojit obslužnou rutinu a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="99d39-320">V případě `MarqueeControlRootDesigner` třídy <xref:System.Windows.Forms.Control.Refresh%2A> zavoláte metodu pro každý `IMarqueeWidget` objekt obsažený v `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="99d39-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="99d39-321">To způsobí, že `IMarqueeWidget` se objekt znovu překreslí, pokud dojde ke změně vlastností, jako <xref:System.Windows.Forms.Control.Size%2A> je jeho nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="99d39-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="99d39-322">Zpracování změn součástí</span><span class="sxs-lookup"><span data-stu-id="99d39-322">To handle component changes</span></span>

1. <span data-ttu-id="99d39-323">Otevřete zdrojový soubor v **editoru kódu** a přepište <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodu. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="99d39-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="99d39-324">Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz <xref:System.ComponentModel.Design.IComponentChangeService>na.</span><span class="sxs-lookup"><span data-stu-id="99d39-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="99d39-325">Implementujte obslužnou rutinu události. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="99d39-326">Otestujte typ odesílající komponenty a v případě, že se jedná o `IMarqueeWidget`, zavolejte svou <xref:System.Windows.Forms.Control.Refresh%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="99d39-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="99d39-327">Přidání příkazů návrháře do vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="99d39-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="99d39-328">Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="99d39-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="99d39-329">Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="99d39-330">Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="99d39-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="99d39-331">Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**.</span><span class="sxs-lookup"><span data-stu-id="99d39-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="99d39-332">Tyto příkazy vám umožní zobrazit chování `MarqueeControl` za běhu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="99d39-333">Tyto operace budou přidány do `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="99d39-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="99d39-334">Při vyvolání příkazu **Spustit test** , obslužná rutina `StartMarquee` události vyvolá metodu na `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="99d39-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="99d39-335">Při vyvolání příkazu **zastavit test** obslužná rutina `StopMarquee` události vyvolá metodu na `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="99d39-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="99d39-336">Implementace `StartMarquee` metod a `StopMarquee` volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget`, takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.</span><span class="sxs-lookup"><span data-stu-id="99d39-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="99d39-337">Přidání příkazů návrháře do vlastních návrhářů</span><span class="sxs-lookup"><span data-stu-id="99d39-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="99d39-338">Ve třídě přidejte obslužné rutiny události s `OnVerbRunTest` názvem `OnVerbStopTest`a. `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="99d39-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="99d39-339">Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře.</span><span class="sxs-lookup"><span data-stu-id="99d39-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="99d39-340">`MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection> dědí z své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="99d39-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="99d39-341">Vytvoříte dva nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidáte je do této kolekce <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> v metodě.</span><span class="sxs-lookup"><span data-stu-id="99d39-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="99d39-342">Vytvoření vlastního Editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="99d39-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="99d39-343">Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="99d39-344">To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="99d39-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="99d39-345">`MarqueeBorder` Ovládací prvek zveřejňuje v okno Vlastnosti několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="99d39-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="99d39-346">Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty.</span><span class="sxs-lookup"><span data-stu-id="99d39-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="99d39-347">K ilustraci použití editoru `MarqueeLightShape` typů uživatelského rozhraní bude mít vlastnost přidruženou <xref:System.Drawing.Design.UITypeEditor> třídu.</span><span class="sxs-lookup"><span data-stu-id="99d39-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="99d39-348">Vytvoření vlastního editoru typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="99d39-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="99d39-349">Otevřete zdrojový soubor v **editoru kódu.** `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="99d39-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="99d39-350">V definici `MarqueeBorder` třídy Deklarujte třídu s názvem `LightShapeEditor` , která je odvozena z <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="99d39-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="99d39-351">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s `editorService`názvem.</span><span class="sxs-lookup"><span data-stu-id="99d39-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="99d39-352">Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="99d39-353">Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, což oznamuje vývojovému prostředí, jak `LightShapeEditor`zobrazit.</span><span class="sxs-lookup"><span data-stu-id="99d39-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="99d39-354">Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="99d39-355">Tato implementace se dotazuje návrhového prostředí <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> pro objekt.</span><span class="sxs-lookup"><span data-stu-id="99d39-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="99d39-356">V případě úspěchu vytvoří `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="99d39-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="99d39-357">Metoda je vyvolána pro `LightShapeEditor`spuštění. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="99d39-358">Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="99d39-359">Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="99d39-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="99d39-360">Vlastnost podporuje dva typy lehkých tvarů: `Square` a `Circle`. `MarqueeLightShape`</span><span class="sxs-lookup"><span data-stu-id="99d39-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="99d39-361">Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="99d39-362">Váš <xref:System.Drawing.Design.UITypeEditor> vlastní ovládací prvek bude použit pro interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="99d39-363">Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="99d39-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="99d39-364"><xref:System.Windows.Forms.UserControl> Přidejte`MarqueeControlLibrary` do projektu novou položku.</span><span class="sxs-lookup"><span data-stu-id="99d39-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-365">Dejte novému zdrojovému souboru základní název **LightShapeSelectionControl**.</span><span class="sxs-lookup"><span data-stu-id="99d39-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="99d39-366">Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládací prvky ze `LightShapeSelectionControl` **sady nástrojů** na.</span><span class="sxs-lookup"><span data-stu-id="99d39-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="99d39-367">`squarePanel` Pojmenujte `circlePanel`je a.</span><span class="sxs-lookup"><span data-stu-id="99d39-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="99d39-368">Uspořádejte je vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="99d39-368">Arrange them side by side.</span></span> <span data-ttu-id="99d39-369">Nastavte vlastnost obou <xref:System.Windows.Forms.Panel> ovládacích prvků na **(60, 60).** <xref:System.Windows.Forms.Control.Size%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="99d39-370"><xref:System.Windows.Forms.Control.Location%2A> Nastavte vlastnost `squarePanel` ovládacího prvku na **(8, 10)** .</span><span class="sxs-lookup"><span data-stu-id="99d39-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="99d39-371"><xref:System.Windows.Forms.Control.Location%2A> Nastavte vlastnost `circlePanel` ovládacího prvku na **(80, 10)** .</span><span class="sxs-lookup"><span data-stu-id="99d39-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="99d39-372">Nakonec nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost `LightShapeSelectionControl` na **(150, 80)** .</span><span class="sxs-lookup"><span data-stu-id="99d39-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="99d39-373">Otevřete zdrojový soubor v **editoru kódu.** `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="99d39-374">V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="99d39-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="99d39-375">Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny `squarePanel` událostí `circlePanel` pro ovládací prvky a.</span><span class="sxs-lookup"><span data-stu-id="99d39-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="99d39-376">Tyto metody se <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> volají k ukončení vlastní <xref:System.Drawing.Design.UITypeEditor> relace úprav.</span><span class="sxs-lookup"><span data-stu-id="99d39-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="99d39-377">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s `editorService`názvem.</span><span class="sxs-lookup"><span data-stu-id="99d39-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="99d39-378">Deklarujte proměnnou `lightShapeValue`instance nazvanou. `MarqueeLightShape`</span><span class="sxs-lookup"><span data-stu-id="99d39-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="99d39-379">`squarePanel` `circlePanel` V konstruktoru připojte obslužné rutiny <xref:System.Windows.Forms.Control.Click> události<xref:System.Windows.Forms.Control.Click> k událostem ovládacích prvků a. `LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="99d39-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="99d39-380">Také definujte přetížení konstruktoru, které přiřadí `MarqueeLightShape` hodnotu z prostředí návrhu `lightShapeValue` k poli.</span><span class="sxs-lookup"><span data-stu-id="99d39-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="99d39-381">V metodě odpojte obslužné rutiny <xref:System.Windows.Forms.Control.Click>událostí. <xref:System.ComponentModel.Component.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="99d39-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="99d39-382">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="99d39-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="99d39-383">Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici <xref:System.ComponentModel.Component.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="99d39-384">Implementujte `LightShape` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99d39-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="99d39-385">Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99d39-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="99d39-386">Tato implementace Vykreslí vyplněný čtverec a kruh.</span><span class="sxs-lookup"><span data-stu-id="99d39-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="99d39-387">Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.</span><span class="sxs-lookup"><span data-stu-id="99d39-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="99d39-388">Testování vlastního ovládacího prvku v Návrháři</span><span class="sxs-lookup"><span data-stu-id="99d39-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="99d39-389">V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt.</span><span class="sxs-lookup"><span data-stu-id="99d39-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="99d39-390">Otestujte implementaci vytvořením ovládacího prvku, který dědí z `MarqueeControl` třídy a jeho použitím na formuláři.</span><span class="sxs-lookup"><span data-stu-id="99d39-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="99d39-391">Vytvoření vlastní implementace MarqueeControl</span><span class="sxs-lookup"><span data-stu-id="99d39-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="99d39-392">Otevřete `DemoMarqueeControl` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="99d39-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="99d39-393">Tím se `DemoMarqueeControl` vytvoří instance typu a zobrazí se v instanci `MarqueeControlRootDesigner` typu.</span><span class="sxs-lookup"><span data-stu-id="99d39-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="99d39-394">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se `MarqueeBorder` ovládací prvky a `MarqueeText` , které jsou k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="99d39-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="99d39-395">Přetáhněte instanci `MarqueeBorder` ovládacího prvku `DemoMarqueeControl` na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="99d39-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="99d39-396">Ukotvit tento `MarqueeBorder` ovládací prvek nadřazenému ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="99d39-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="99d39-397">Přetáhněte instanci `MarqueeText` ovládacího prvku `DemoMarqueeControl` na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="99d39-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="99d39-398">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="99d39-398">Build the solution.</span></span>

6. <span data-ttu-id="99d39-399">Kliknutím `DemoMarqueeControl` pravým tlačítkem myši na a z místní nabídky vyberte možnost **Spustit test** a spusťte animaci.</span><span class="sxs-lookup"><span data-stu-id="99d39-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="99d39-400">Kliknutím na **zastavit test** zastavte animaci.</span><span class="sxs-lookup"><span data-stu-id="99d39-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="99d39-401">Otevřete **Form1** v zobrazení Návrh.</span><span class="sxs-lookup"><span data-stu-id="99d39-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="99d39-402">Umístěte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="99d39-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="99d39-403">`startButton` Pojmenujte `stopButton`je a změňte <xref:System.Windows.Forms.Control.Text%2A> hodnoty vlastností na **Start** a **zastavit**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="99d39-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="99d39-404">Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny <xref:System.Windows.Forms.Button> událostí pro oba ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="99d39-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="99d39-405">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` dostupná pro výběr.</span><span class="sxs-lookup"><span data-stu-id="99d39-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="99d39-406">Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .</span><span class="sxs-lookup"><span data-stu-id="99d39-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="99d39-407">V obslužných rutinách `Start` `Stop` `DemoMarqueeControl`události volejte metody a na. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="99d39-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="99d39-408">`MarqueeControlTest` Nastavte projekt jako spouštěný projekt a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="99d39-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="99d39-409">Zobrazí se formulář, ve kterém se `DemoMarqueeControl`zobrazuje vaše.</span><span class="sxs-lookup"><span data-stu-id="99d39-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="99d39-410">Kliknutím na tlačítko **Start** spustíte animaci.</span><span class="sxs-lookup"><span data-stu-id="99d39-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="99d39-411">Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.</span><span class="sxs-lookup"><span data-stu-id="99d39-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="99d39-412">Další kroky</span><span class="sxs-lookup"><span data-stu-id="99d39-412">Next steps</span></span>

<span data-ttu-id="99d39-413">`MarqueeControlLibrary` Ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů.</span><span class="sxs-lookup"><span data-stu-id="99d39-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="99d39-414">Tuto ukázku můžete udělat několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="99d39-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="99d39-415">Změňte hodnoty `DemoMarqueeControl` vlastností v návrháři.</span><span class="sxs-lookup"><span data-stu-id="99d39-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="99d39-416">Chcete- `MarqueBorder` li vytvořit vnořený efekt, přidejte další ovládací prvky a ukotvěte je Dock v rámci jejich nadřazených instancí.</span><span class="sxs-lookup"><span data-stu-id="99d39-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="99d39-417">Experimentujte s různými nastaveními `UpdatePeriod` pro a vlastnosti související s osvětlením.</span><span class="sxs-lookup"><span data-stu-id="99d39-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="99d39-418">Vytvořte vlastní implementace `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="99d39-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="99d39-419">Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.</span><span class="sxs-lookup"><span data-stu-id="99d39-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="99d39-420">Dále upravte prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="99d39-420">Further customize the design-time experience.</span></span> <span data-ttu-id="99d39-421">Můžete zkusit vytvořit stín více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a <xref:System.Windows.Forms.Control.Visible%2A>a můžete přidat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99d39-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="99d39-422">Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="99d39-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="99d39-423">`MarqueeControl`Licenci.</span><span class="sxs-lookup"><span data-stu-id="99d39-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="99d39-424">Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy.</span><span class="sxs-lookup"><span data-stu-id="99d39-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="99d39-425">Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="99d39-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99d39-426">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99d39-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
