---
title: Vytvoření ovládacího prvku, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu
description: Naučte se, jak vytvořit vlastního návrháře vlastního ovládacího prvku v model Windows Forms, který využívá funkce pro dobu návrhu.
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
ms.openlocfilehash: 03c04578ecb01b689f58d41a46eef5793fb1182c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613907"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="a124c-103">Návod: vytvoření ovládacího prvku, který bude využívat funkce pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="a124c-103">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="a124c-104">Prostředí pro návrh vlastního ovládacího prvku lze zvýšit vytvořením přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-104">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="a124c-105">Tento článek ukazuje, jak vytvořit vlastního návrháře vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-105">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="a124c-106">Implementujete `MarqueeControl` typ a přidruženou třídu návrháře s názvem `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="a124c-106">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="a124c-107">`MarqueeControl`Typ implementuje zobrazení podobné textu v kino s animovanými indikátory a blikající text.</span><span class="sxs-lookup"><span data-stu-id="a124c-107">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="a124c-108">Návrhář pro tento ovládací prvek komunikuje s vývojovým prostředím, aby poskytoval vlastní prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-108">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="a124c-109">Pomocí vlastního návrháře můžete sestavit vlastní `MarqueeControl` implementaci s animovanými indikátory a blikající text v mnoha kombinacích.</span><span class="sxs-lookup"><span data-stu-id="a124c-109">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="a124c-110">Můžete použít sestavený ovládací prvek na formuláři, stejně jako jakýkoli jiný ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a124c-110">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="a124c-111">Až budete s tímto návodem hotový, váš vlastní ovládací prvek bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="a124c-111">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Aplikace, která zobrazuje text a tlačítka Spustit a zastavit](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="a124c-113">Úplný výpis kódu naleznete v tématu [How to: Create a model Windows Forms Control, který využívá funkce pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a124c-113">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a124c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a124c-114">Prerequisites</span></span>

<span data-ttu-id="a124c-115">Aby bylo možné dokončit tento návod, budete potřebovat aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a124c-115">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a124c-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="a124c-116">Create the project</span></span>

<span data-ttu-id="a124c-117">Prvním krokem je vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a124c-117">The first step is to create the application project.</span></span> <span data-ttu-id="a124c-118">Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-118">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="a124c-119">V aplikaci Visual Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte jej **MarqueeControlTest**.</span><span class="sxs-lookup"><span data-stu-id="a124c-119">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="a124c-120">Vytvořit projekt knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="a124c-120">Create the control library project</span></span>

1. <span data-ttu-id="a124c-121">Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a124c-121">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="a124c-122">Pojmenujte projekt **MarqueeControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="a124c-122">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="a124c-123">Pomocí **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1. vb" v závislosti na zvoleném jazyce.</span><span class="sxs-lookup"><span data-stu-id="a124c-123">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="a124c-124">Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-124">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-125">Dejte novému zdrojovému souboru základní název **MarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="a124c-125">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="a124c-126">Pomocí **Průzkumník řešení**vytvořte v projektu novou složku `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-126">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="a124c-127">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="a124c-127">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="a124c-128">Pojmenujte ho **MarqueeControlRootDesigner**.</span><span class="sxs-lookup"><span data-stu-id="a124c-128">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="a124c-129">Budete muset použít typy ze sestavení System. design, takže přidejte tento odkaz do `MarqueeControlLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="a124c-129">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="a124c-130">Odkaz na projekt vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a124c-130">Reference the Custom Control Project</span></span>

<span data-ttu-id="a124c-131">`MarqueeControlTest`K otestování vlastního ovládacího prvku použijete projekt.</span><span class="sxs-lookup"><span data-stu-id="a124c-131">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="a124c-132">Testovací projekt se při přidání odkazu na projekt do sestavení změní na vlastní ovládací prvek `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-132">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="a124c-133">V `MarqueeControlTest` projektu přidejte odkaz na projekt do `MarqueeControlLibrary` sestavení.</span><span class="sxs-lookup"><span data-stu-id="a124c-133">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="a124c-134">Nezapomeňte použít kartu **projekty** v dialogovém okně **Přidat odkaz** namísto odkazování na `MarqueeControlLibrary` sestavení přímo.</span><span class="sxs-lookup"><span data-stu-id="a124c-134">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="a124c-135">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="a124c-135">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="a124c-136">Vlastní ovládací prvek bude odvozen z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-136">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="a124c-137">To umožňuje vašemu ovládacímu prvku, aby obsahoval další ovládací prvky, a poskytuje vašemu ovládacímu prvku skvělou výchozí funkčnost.</span><span class="sxs-lookup"><span data-stu-id="a124c-137">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="a124c-138">Vlastní ovládací prvek bude mít přidružený vlastní Návrhář.</span><span class="sxs-lookup"><span data-stu-id="a124c-138">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="a124c-139">To vám umožní vytvořit jedinečné vývojové prostředí, které se přizpůsobí speciálně pro váš vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a124c-139">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="a124c-140">K přidružení ovládacího prvku ke svému návrháři použijte <xref:System.ComponentModel.DesignerAttribute> třídu.</span><span class="sxs-lookup"><span data-stu-id="a124c-140">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="a124c-141">Vzhledem k tomu, že vyvíjíte celé chování vlastního ovládacího prvku v době návrhu, bude vlastní Návrhář implementovat <xref:System.ComponentModel.Design.IRootDesigner> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a124c-141">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="a124c-142">Definování vlastního ovládacího prvku a jeho vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="a124c-142">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="a124c-143">Otevřete `MarqueeControl` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-143">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-144">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-144">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="a124c-145">Přidejte <xref:System.ComponentModel.DesignerAttribute> do `MarqueeControl` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-145">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="a124c-146">Tím přiřadíte vlastní ovládací prvek ke svému návrháři.</span><span class="sxs-lookup"><span data-stu-id="a124c-146">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="a124c-147">Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-147">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-148">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-148">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="a124c-149">Změňte deklaraci `MarqueeControlRootDesigner` na dědění z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-149">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="a124c-150">Použijte <xref:System.ComponentModel.ToolboxItemFilterAttribute> pro určení interakce návrháře pomocí **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a124c-150">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a124c-151">Definice pro třídu byla `MarqueeControlRootDesigner` uzavřená v oboru názvů s názvem MarqueeControlLibrary. Design.</span><span class="sxs-lookup"><span data-stu-id="a124c-151">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="a124c-152">Tato deklarace umístí návrháře ve speciálním oboru názvů vyhrazeném pro typy související s návrhem.</span><span class="sxs-lookup"><span data-stu-id="a124c-152">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="a124c-153">Definujte konstruktor pro `MarqueeControlRootDesigner` třídu.</span><span class="sxs-lookup"><span data-stu-id="a124c-153">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="a124c-154">Vloží <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz do těla konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a124c-154">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="a124c-155">To bude užitečné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="a124c-155">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="a124c-156">Vytvoření instance vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a124c-156">Create an instance of your custom control</span></span>

1. <span data-ttu-id="a124c-157">Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlTest` .</span><span class="sxs-lookup"><span data-stu-id="a124c-157">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="a124c-158">Dejte novému zdrojovému souboru základní název **DemoMarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="a124c-158">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="a124c-159">Otevřete `DemoMarqueeControl` soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-159">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-160">V horní části souboru importujte `MarqueeControlLibrary` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-160">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="a124c-161">Změňte deklaraci `DemoMarqueeControl` na dědění z `MarqueeControl` třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-161">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="a124c-162">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="a124c-162">Build the project.</span></span>

5. <span data-ttu-id="a124c-163">Otevřete Form1 v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="a124c-163">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="a124c-164">V **sadě nástrojů** Najděte kartu **komponenty MarqueeControlTest** a otevřete ji.</span><span class="sxs-lookup"><span data-stu-id="a124c-164">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="a124c-165">Přetáhněte `DemoMarqueeControl` z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a124c-165">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="a124c-166">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="a124c-166">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="a124c-167">Nastavení projektu pro ladění v době návrhu</span><span class="sxs-lookup"><span data-stu-id="a124c-167">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="a124c-168">Při vývoji vlastního prostředí v době návrhu bude nutné ladit ovládací prvky a komponenty.</span><span class="sxs-lookup"><span data-stu-id="a124c-168">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="a124c-169">Existuje jednoduchý způsob, jak nastavit projekt tak, aby umožňoval ladění v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-169">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="a124c-170">Další informace naleznete v tématu [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="a124c-170">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="a124c-171">Klikněte pravým tlačítkem na `MarqueeControlLibrary` projekt a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a124c-171">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="a124c-172">V dialogovém okně **stránky vlastností MarqueeControlLibrary** vyberte stránku **ladění** .</span><span class="sxs-lookup"><span data-stu-id="a124c-172">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="a124c-173">V části **spouštěcí akce** vyberte **spustit externí program**.</span><span class="sxs-lookup"><span data-stu-id="a124c-173">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="a124c-174">Budete ladit samostatnou instanci sady Visual Studio, takže kliknutím na tlačítko se třemi tečkami ( ![ ...) v okno Vlastnosti sady Visual Studio ](./media/visual-studio-ellipsis-button.png) ) můžete procházet prostředí IDE sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a124c-174">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="a124c-175">Název spustitelného souboru je devenv.exe a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019 \\ \<edition>\Common7\IDE\devenv.exe*.</span><span class="sxs-lookup"><span data-stu-id="a124c-175">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="a124c-176">Kliknutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a124c-176">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="a124c-177">Klikněte pravým tlačítkem na projekt MarqueeControlLibrary a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.</span><span class="sxs-lookup"><span data-stu-id="a124c-177">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="a124c-178">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="a124c-178">Checkpoint</span></span>

<span data-ttu-id="a124c-179">Nyní jste připraveni ladit chování vlastního ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-179">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="a124c-180">Jakmile zjistíte, že je prostředí ladění správně nastavené, otestujete přidružení mezi vlastním ovládacím prvkem a vlastním návrhářem.</span><span class="sxs-lookup"><span data-stu-id="a124c-180">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="a124c-181">Otestování ladicího prostředí a přidružení návrháře</span><span class="sxs-lookup"><span data-stu-id="a124c-181">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="a124c-182">Otevřete zdrojový soubor MarqueeControlRootDesigner v **editoru kódu** a umístěte zarážku na <xref:System.Diagnostics.Trace.WriteLine%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="a124c-182">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="a124c-183">Stisknutím klávesy **F5** spusťte relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="a124c-183">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="a124c-184">Vytvoří se nová instance sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a124c-184">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="a124c-185">V nové instanci aplikace Visual Studio otevřete řešení MarqueeControlTest.</span><span class="sxs-lookup"><span data-stu-id="a124c-185">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="a124c-186">Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="a124c-186">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="a124c-187">Soubor řešení MarqueeControlTest. sln bude uveden jako naposledy použitý soubor.</span><span class="sxs-lookup"><span data-stu-id="a124c-187">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="a124c-188">Otevřete `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="a124c-188">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="a124c-189">Instance ladění aplikace Visual Studio získá fokus a provádění se zastaví na zarážce.</span><span class="sxs-lookup"><span data-stu-id="a124c-189">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="a124c-190">Stisknutím klávesy **F5** pokračujte v relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="a124c-190">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="a124c-191">V tomto okamžiku je vše pro vývoj a ladění vlastního ovládacího prvku a jeho přidruženého vlastního návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-191">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="a124c-192">Zbývající část tohoto článku se zaměřuje na podrobnosti o implementaci funkcí ovládacího prvku a návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-192">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="a124c-193">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a124c-193">Implement the Custom Control</span></span>

<span data-ttu-id="a124c-194">`MarqueeControl`Je a <xref:System.Windows.Forms.UserControl> s malým počtem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="a124c-194">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="a124c-195">Zveřejňuje dvě metody: `Start` , který spustí animaci běžící na hranice a `Stop` , která zastaví animaci.</span><span class="sxs-lookup"><span data-stu-id="a124c-195">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="a124c-196">Protože `MarqueeControl` obsahuje podřízené ovládací prvky, které implementují rozhraní a vyčíslení `IMarqueeWidget` `Start` každého podřízeného ovládacího prvku a `Stop` volání `StartMarquee` `StopMarquee` metod a, v uvedeném pořadí, v každém podřízeném ovládacím prvku, který implementuje `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="a124c-196">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="a124c-197">Vzhled `MarqueeBorder` `MarqueeText` ovládacích prvků a je závislý na rozložení, takže `MarqueeControl` přepíše <xref:System.Windows.Forms.Control.OnLayout%2A> metodu a volání <xref:System.Windows.Forms.Control.PerformLayout%2A> podřízených ovládacích prvků tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a124c-197">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="a124c-198">Toto je rozsah `MarqueeControl` úprav.</span><span class="sxs-lookup"><span data-stu-id="a124c-198">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="a124c-199">Funkce modulu runtime jsou implementovány `MarqueeBorder` `MarqueeText` ovládacími prvky a a funkce v době návrhu jsou implementovány `MarqueeBorderDesigner` `MarqueeControlRootDesigner` třídami a.</span><span class="sxs-lookup"><span data-stu-id="a124c-199">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="a124c-200">Implementace vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a124c-200">To implement your custom control</span></span>

1. <span data-ttu-id="a124c-201">Otevřete `MarqueeControl` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-201">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-202">Implementujte `Start` `Stop` metody a.</span><span class="sxs-lookup"><span data-stu-id="a124c-202">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="a124c-203">Přepsat <xref:System.Windows.Forms.Control.OnLayout%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-203">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="a124c-204">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a124c-204">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="a124c-205">`MarqueeControl`Bude hostovat dva druhy podřízeného ovládacího prvku: `MarqueeBorder` ovládací prvek a `MarqueeText` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a124c-205">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="a124c-206">`MarqueeBorder`: Tento ovládací prvek vykreslí ohraničení "světel" kolem jeho okrajů.</span><span class="sxs-lookup"><span data-stu-id="a124c-206">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="a124c-207">Světla se zobrazí v sekvenci, takže se zdají kolem ohraničení pohybovat.</span><span class="sxs-lookup"><span data-stu-id="a124c-207">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="a124c-208">Rychlost, s níž jsou indikátory blesku ovládány vlastností s názvem `UpdatePeriod` .</span><span class="sxs-lookup"><span data-stu-id="a124c-208">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="a124c-209">Některé další vlastní vlastnosti určují další aspekty vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-209">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="a124c-210">Dvě metody, které jsou volány `StartMarquee` a `StopMarquee` , určují, kdy se animace spouští a zastavuje.</span><span class="sxs-lookup"><span data-stu-id="a124c-210">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="a124c-211">`MarqueeText`: Tento ovládací prvek vykreslí blikající řetězec.</span><span class="sxs-lookup"><span data-stu-id="a124c-211">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="a124c-212">Podobně jako u `MarqueeBorder` ovládacího prvku je rychlost, s jakou je text blikající, ovládána `UpdatePeriod` vlastností.</span><span class="sxs-lookup"><span data-stu-id="a124c-212">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="a124c-213">`MarqueeText`Ovládací prvek má také `StartMarquee` `StopMarquee` společné metody a s `MarqueeBorder` ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="a124c-213">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="a124c-214">V době návrhu umožňuje, aby `MarqueeControlRootDesigner` tyto dva typy ovládacích prvků byly přidány do `MarqueeControl` jakékoli kombinace.</span><span class="sxs-lookup"><span data-stu-id="a124c-214">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="a124c-215">Společné funkce těchto dvou ovládacích prvků jsou přihlédnuto do rozhraní s názvem `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="a124c-215">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="a124c-216">To umožňuje, `MarqueeControl` aby se zjistily podřízené ovládací prvky související s rámečkem a přidávají jim speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="a124c-216">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="a124c-217">K implementaci funkce periodické animace budete používat <xref:System.ComponentModel.BackgroundWorker> objekty z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a124c-217">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a124c-218">Můžete použít <xref:System.Windows.Forms.Timer> objekty, ale `IMarqueeWidget` v případě, že je přítomen velký počet objektů, nemusí být jedno vlákno uživatelského rozhraní schopno s animací zůstat.</span><span class="sxs-lookup"><span data-stu-id="a124c-218">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="a124c-219">Vytvoření podřízeného ovládacího prvku pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a124c-219">To create a child control for your custom control</span></span>

1. <span data-ttu-id="a124c-220">Přidejte do projektu novou položku třídy `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-220">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-221">Dejte novému zdrojovému souboru základní název "IMarqueeWidget".</span><span class="sxs-lookup"><span data-stu-id="a124c-221">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="a124c-222">Otevřete `IMarqueeWidget` zdrojový soubor v **editoru kódu** a změňte deklaraci z `class` na `interface` :</span><span class="sxs-lookup"><span data-stu-id="a124c-222">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="a124c-223">Přidejte následující kód do rozhraní, `IMarqueeWidget` aby bylo možné vystavit dvě metody a vlastnost, která zpracovává animaci běžícího výběru:</span><span class="sxs-lookup"><span data-stu-id="a124c-223">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="a124c-224">Přidejte do projektu novou položku **vlastního ovládacího prvku** `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-224">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-225">Dejte novému zdrojovému souboru základní název "MarqueeText".</span><span class="sxs-lookup"><span data-stu-id="a124c-225">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="a124c-226">Přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu z **panelu nástrojů** na `MarqueeText` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a124c-226">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="a124c-227">Tato součást umožní, aby se `MarqueeText` ovládací prvek sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="a124c-227">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="a124c-228">V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="a124c-228">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="a124c-229">Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně vyvolala <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a124c-229">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="a124c-230">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="a124c-230">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="a124c-231">Otevřete `MarqueeText` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-231">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-232">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-232">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="a124c-233">Změňte deklaraci `MarqueeText` na dědění z <xref:System.Windows.Forms.Label> a k implementaci `IMarqueeWidget` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="a124c-233">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="a124c-234">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a124c-234">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="a124c-235">`isLit`Pole určuje, zda má být text vykreslen v barvě dané `LightColor` vlastností.</span><span class="sxs-lookup"><span data-stu-id="a124c-235">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="a124c-236">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="a124c-236">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="a124c-237">`StartMarquee`Metody a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker> komponentu <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody pro spuštění a zastavení animace.</span><span class="sxs-lookup"><span data-stu-id="a124c-237">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="a124c-238"><xref:System.ComponentModel.CategoryAttribute.Category%2A>Atributy a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na `UpdatePeriod` vlastnost, takže se zobrazí ve vlastní části okno Vlastnosti nazvané "výběr".</span><span class="sxs-lookup"><span data-stu-id="a124c-238">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="a124c-239">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-239">Implement the property accessors.</span></span> <span data-ttu-id="a124c-240">Pro klienty vystavíte dvě vlastnosti: `LightColor` a `DarkColor` .</span><span class="sxs-lookup"><span data-stu-id="a124c-240">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="a124c-241"><xref:System.ComponentModel.CategoryAttribute.Category%2A>Atributy a <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> se aplikují na tyto vlastnosti, takže se vlastnosti zobrazí ve vlastní části okno Vlastnosti s názvem "výběr".</span><span class="sxs-lookup"><span data-stu-id="a124c-241">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="a124c-242">Implementujte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> události komponenty a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .</span><span class="sxs-lookup"><span data-stu-id="a124c-242">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="a124c-243"><xref:System.ComponentModel.BackgroundWorker.DoWork>Obslužná rutina události v režimu spánku po dobu určenou v milisekundách `UpdatePeriod` vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="a124c-243">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="a124c-244"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Obslužná rutina události přepíná text mezi jeho světlý a tmavý stav, aby bylo možné podobu blikání.</span><span class="sxs-lookup"><span data-stu-id="a124c-244">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="a124c-245">Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu pro povolení animace.</span><span class="sxs-lookup"><span data-stu-id="a124c-245">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="a124c-246">Stisknutím klávesy **F6** Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a124c-246">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="a124c-247">Vytvoření podřízeného ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="a124c-247">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="a124c-248">`MarqueeBorder`Ovládací prvek je poněkud složitější než `MarqueeText` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a124c-248">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="a124c-249">Má více vlastností a další animace v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě je více zapojena.</span><span class="sxs-lookup"><span data-stu-id="a124c-249">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="a124c-250">V zásadě je poměrně podobný `MarqueeText` ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-250">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="a124c-251">Vzhledem k tomu `MarqueeBorder` , že ovládací prvek může mít podřízené ovládací prvky, musí znát <xref:System.Windows.Forms.Control.Layout> události.</span><span class="sxs-lookup"><span data-stu-id="a124c-251">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="a124c-252">Vytvoření ovládacího prvku MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="a124c-252">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="a124c-253">Přidejte do projektu novou položku **vlastního ovládacího prvku** `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-253">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-254">Dejte novému zdrojovému souboru základní název "MarqueeBorder".</span><span class="sxs-lookup"><span data-stu-id="a124c-254">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="a124c-255">Přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu z **panelu nástrojů** na `MarqueeBorder` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a124c-255">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="a124c-256">Tato součást umožní, aby se `MarqueeBorder` ovládací prvek sám aktualizoval asynchronně.</span><span class="sxs-lookup"><span data-stu-id="a124c-256">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="a124c-257">V okně **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker> komponentu `WorkerReportsProgress` a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="a124c-257">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="a124c-258">Tato nastavení umožňují, <xref:System.ComponentModel.BackgroundWorker> aby součást pravidelně vyvolala <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost a zrušila asynchronní aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a124c-258">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="a124c-259">Další informace najdete v tématu [Komponenta BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="a124c-259">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="a124c-260">V okně **vlastnosti** vyberte tlačítko **události** .</span><span class="sxs-lookup"><span data-stu-id="a124c-260">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="a124c-261">Připojte obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.DoWork> pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události a.</span><span class="sxs-lookup"><span data-stu-id="a124c-261">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="a124c-262">Otevřete `MarqueeBorder` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-262">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-263">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-263">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="a124c-264">Změňte deklaraci `MarqueeBorder` na dědění z <xref:System.Windows.Forms.Panel> a k implementaci `IMarqueeWidget` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a124c-264">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="a124c-265">Deklarujete dva výčty pro správu `MarqueeBorder` stavu ovládacího prvku: `MarqueeSpinDirection` , který určuje směr otočení světla kolem ohraničení a `MarqueeLightShape` určuje tvar světel (čtvercové nebo kruhové).</span><span class="sxs-lookup"><span data-stu-id="a124c-265">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="a124c-266">Tyto deklarace umístěte před `MarqueeBorder` deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-266">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="a124c-267">Deklarovat proměnné instance, které odpovídají vystaveným vlastnostem a inicializovat je v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a124c-267">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="a124c-268">Implementujte rozhraní `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="a124c-268">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="a124c-269">`StartMarquee`Metody a `StopMarquee` vyvolají <xref:System.ComponentModel.BackgroundWorker> komponentu <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody pro spuštění a zastavení animace.</span><span class="sxs-lookup"><span data-stu-id="a124c-269">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="a124c-270">Vzhledem k tomu `MarqueeBorder` , že ovládací prvek může obsahovat podřízené ovládací prvky, `StartMarquee` Metoda vytvoří výčet všech podřízených ovládacích prvků a volání `StartMarquee` , která implementují `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="a124c-270">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="a124c-271">`StopMarquee`Metoda má podobnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="a124c-271">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="a124c-272">Implementujte přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-272">Implement the property accessors.</span></span> <span data-ttu-id="a124c-273">`MarqueeBorder`Ovládací prvek má několik vlastností pro řízení jeho vzhledu.</span><span class="sxs-lookup"><span data-stu-id="a124c-273">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="a124c-274">Implementujte obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> události komponenty a <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> .</span><span class="sxs-lookup"><span data-stu-id="a124c-274">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="a124c-275"><xref:System.ComponentModel.BackgroundWorker.DoWork>Obslužná rutina události v režimu spánku po dobu určenou v milisekundách `UpdatePeriod` vyvolá <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událost, dokud váš kód nezastaví animaci voláním <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="a124c-275">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="a124c-276"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>Obslužná rutina události zvýší pozici "základního" světla, ze kterého je stanoven světlý nebo tmavý stav ostatních světel, a volá <xref:System.Windows.Forms.Control.Refresh%2A> metodu, která způsobí, že ovládací prvek provede překreslení sám sebe.</span><span class="sxs-lookup"><span data-stu-id="a124c-276">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="a124c-277">Implementujte pomocné metody `IsLit` a `DrawLight` .</span><span class="sxs-lookup"><span data-stu-id="a124c-277">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="a124c-278">`IsLit`Metoda určuje barvu světla na dané pozici.</span><span class="sxs-lookup"><span data-stu-id="a124c-278">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="a124c-279">Indikátory, které jsou "osvětlené" jsou vykresleny barvou dané `LightColor` vlastností a ty, které jsou "tmavé" jsou vykresleny v barvě dané `DarkColor` vlastností.</span><span class="sxs-lookup"><span data-stu-id="a124c-279">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="a124c-280">`DrawLight`Metoda nakreslí světlo pomocí příslušné barvy, tvaru a pozice.</span><span class="sxs-lookup"><span data-stu-id="a124c-280">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="a124c-281">Přepište <xref:System.Windows.Forms.Control.OnLayout%2A> <xref:System.Windows.Forms.Control.OnPaint%2A> metody a.</span><span class="sxs-lookup"><span data-stu-id="a124c-281">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="a124c-282"><xref:System.Windows.Forms.Control.OnPaint%2A>Metoda kreslí světla podél okrajů `MarqueeBorder` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-282">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="a124c-283">Vzhledem k tomu <xref:System.Windows.Forms.Control.OnPaint%2A> , že metoda závisí na rozměrech `MarqueeBorder` ovládacího prvku, je nutné jej zavolat při každé změně rozložení.</span><span class="sxs-lookup"><span data-stu-id="a124c-283">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="a124c-284">Chcete-li toho dosáhnout, přepište <xref:System.Windows.Forms.Control.OnLayout%2A> a zavolejte <xref:System.Windows.Forms.Control.Refresh%2A> .</span><span class="sxs-lookup"><span data-stu-id="a124c-284">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="a124c-285">Vytvoření vlastního návrháře pro stínové a filtrové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a124c-285">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="a124c-286">`MarqueeControlRootDesigner`Třída poskytuje implementaci pro kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-286">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="a124c-287">Kromě tohoto návrháře, který pracuje na `MarqueeControl` , budete potřebovat vlastního návrháře, který je konkrétně přidružen k `MarqueeBorder` ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-287">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="a124c-288">Tento návrhář poskytuje vlastní chování, které je vhodné v kontextu vlastního kořenového návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-288">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="a124c-289">Konkrétně `MarqueeBorderDesigner` bude "stínem" a filtrovat určité vlastnosti `MarqueeBorder` ovládacího prvku, změnou jejich interakce s návrhovým prostředím.</span><span class="sxs-lookup"><span data-stu-id="a124c-289">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="a124c-290">Zachytávání volání vlastnosti objektu komponenty se označují jako "stíning".</span><span class="sxs-lookup"><span data-stu-id="a124c-290">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="a124c-291">Umožňuje návrháři sledovat hodnotu nastavenou uživatelem a volitelně předat tuto hodnotu do navržené součásti.</span><span class="sxs-lookup"><span data-stu-id="a124c-291">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="a124c-292">V tomto příkladu <xref:System.Windows.Forms.Control.Visible%2A> <xref:System.Windows.Forms.Control.Enabled%2A> budou vlastnosti a nastínované pomocí `MarqueeBorderDesigner` , což brání uživateli v tom, aby `MarqueeBorder` během návrhu byl ovládací prvek neviditelný nebo zakázán.</span><span class="sxs-lookup"><span data-stu-id="a124c-292">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="a124c-293">Návrháři mohou také přidávat a odebírat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-293">Designers can also add and remove properties.</span></span> <span data-ttu-id="a124c-294">V tomto příkladu <xref:System.Windows.Forms.Control.Padding%2A> bude vlastnost odebrána v době návrhu, protože `MarqueeBorder` ovládací prvek programově nastaví odsazení na základě velikosti světla určených `LightSize` vlastností.</span><span class="sxs-lookup"><span data-stu-id="a124c-294">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="a124c-295">Základní třída pro `MarqueeBorderDesigner` je <xref:System.ComponentModel.Design.ComponentDesigner> , která má metody, které mohou měnit atributy, vlastnosti a události vystavené ovládacím prvkem v době návrhu:</span><span class="sxs-lookup"><span data-stu-id="a124c-295">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="a124c-296">Při změně veřejného rozhraní komponenty pomocí těchto metod použijte tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="a124c-296">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="a124c-297">Přidat nebo odebrat položky pouze v `PreFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="a124c-297">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="a124c-298">Upravit existující položky pouze v `PostFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="a124c-298">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="a124c-299">Vždy volat základní implementaci nejprve v `PreFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="a124c-299">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="a124c-300">Vždy volat základní implementaci jako poslední v `PostFilter` metodách</span><span class="sxs-lookup"><span data-stu-id="a124c-300">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="a124c-301">Dodržování těchto pravidel zajišťuje, že všichni návrháři v prostředí návrhu mají konzistentní zobrazení všech navržených komponent.</span><span class="sxs-lookup"><span data-stu-id="a124c-301">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="a124c-302"><xref:System.ComponentModel.Design.ComponentDesigner>Třída poskytuje slovník pro správu hodnot stínových vlastností, což zbavuje nutnost vytváření specifických proměnných instance.</span><span class="sxs-lookup"><span data-stu-id="a124c-302">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="a124c-303">Vytvoření vlastního návrháře pro vlastnosti stínu a filtru</span><span class="sxs-lookup"><span data-stu-id="a124c-303">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="a124c-304">Klikněte pravým tlačítkem na složku **návrhu** a přidejte novou třídu.</span><span class="sxs-lookup"><span data-stu-id="a124c-304">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="a124c-305">Dejte zdrojovému souboru základní název **MarqueeBorderDesigner**.</span><span class="sxs-lookup"><span data-stu-id="a124c-305">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="a124c-306">Otevřete zdrojový soubor MarqueeBorderDesigner v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-306">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-307">V horní části souboru importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-307">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="a124c-308">Změňte deklaraci `MarqueeBorderDesigner` na dědění z <xref:System.Windows.Forms.Design.ParentControlDesigner> .</span><span class="sxs-lookup"><span data-stu-id="a124c-308">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="a124c-309">Vzhledem k tomu, že `MarqueeBorder` ovládací prvek může obsahovat podřízené ovládací prvky, `MarqueeBorderDesigner` dědí z <xref:System.Windows.Forms.Design.ParentControlDesigner> , který zpracovává interakci nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="a124c-309">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="a124c-310">Přepsat základní implementaci <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> .</span><span class="sxs-lookup"><span data-stu-id="a124c-310">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="a124c-311">Implementujte <xref:System.Windows.Forms.Control.Enabled%2A> <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="a124c-311">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="a124c-312">Tyto implementace nastínují vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-312">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="a124c-313">Zpracovat změny součásti</span><span class="sxs-lookup"><span data-stu-id="a124c-313">Handle Component Changes</span></span>

<span data-ttu-id="a124c-314">`MarqueeControlRootDesigner`Třída poskytuje vlastní prostředí pro dobu návrhu pro vaše `MarqueeControl` instance.</span><span class="sxs-lookup"><span data-stu-id="a124c-314">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="a124c-315">Většina funkcí návrhu je děděna z <xref:System.Windows.Forms.Design.DocumentDesigner> třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-315">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="a124c-316">Váš kód bude implementovat dvě konkrétní vlastní nastavení: zpracování změn součástí a přidávání operací návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-316">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="a124c-317">Když uživatelé navrhují své `MarqueeControl` instance, váš kořenový Návrhář bude sledovat změny `MarqueeControl` a jeho podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a124c-317">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="a124c-318">Prostředí pro dobu návrhu nabízí pohodlný službu, která umožňuje <xref:System.ComponentModel.Design.IComponentChangeService> sledovat změny stavu součásti.</span><span class="sxs-lookup"><span data-stu-id="a124c-318">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="a124c-319">Odkaz na tuto službu získáte dotazem na prostředí pomocí <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a124c-319">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="a124c-320">Pokud je dotaz úspěšný, může Návrhář k události připojit obslužnou rutinu <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> a provést jakékoli úkoly, aby zachovaly konzistentní stav v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-320">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="a124c-321">V případě `MarqueeControlRootDesigner` třídy zavoláte <xref:System.Windows.Forms.Control.Refresh%2A> metodu pro každý `IMarqueeWidget` objekt obsažený v `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-321">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="a124c-322">To způsobí, že se `IMarqueeWidget` objekt znovu překreslí, pokud dojde ke změně vlastností, jako je jeho nadřazený prvek <xref:System.Windows.Forms.Control.Size%2A> .</span><span class="sxs-lookup"><span data-stu-id="a124c-322">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="a124c-323">Zpracování změn součástí</span><span class="sxs-lookup"><span data-stu-id="a124c-323">To handle component changes</span></span>

1. <span data-ttu-id="a124c-324">Otevřete `MarqueeControlRootDesigner` zdrojový soubor v **editoru kódu** a přepište <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-324">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="a124c-325">Zavolejte základní implementaci <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> a dotaz na <xref:System.ComponentModel.Design.IComponentChangeService> .</span><span class="sxs-lookup"><span data-stu-id="a124c-325">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="a124c-326">Implementujte <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="a124c-326">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="a124c-327">Otestujte typ odesílající komponenty a v případě, že se jedná o `IMarqueeWidget` , zavolejte svou <xref:System.Windows.Forms.Control.Refresh%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-327">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="a124c-328">Přidání příkazů návrháře do vlastního návrháře</span><span class="sxs-lookup"><span data-stu-id="a124c-328">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="a124c-329">Příkaz návrháře je příkaz nabídky propojený s obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="a124c-329">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="a124c-330">Příkazy návrháře jsou přidány do místní nabídky součásti v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-330">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="a124c-331">Další informace naleznete v tématu <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="a124c-331">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="a124c-332">Do návrháře přidáte dva příkazy návrháře: **Spusťte test** a **zastavte test**.</span><span class="sxs-lookup"><span data-stu-id="a124c-332">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="a124c-333">Tyto příkazy vám umožní zobrazit chování za běhu v době `MarqueeControl` návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-333">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="a124c-334">Tyto operace budou přidány do `MarqueeControlRootDesigner` .</span><span class="sxs-lookup"><span data-stu-id="a124c-334">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="a124c-335">Při vyvolání příkazu **Spustit test** , obslužná rutina události vyvolá `StartMarquee` metodu na `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-335">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="a124c-336">Při vyvolání příkazu **zastavit test** obslužná rutina události vyvolá `StopMarquee` metodu na `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-336">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="a124c-337">Implementace `StartMarquee` `StopMarquee` metod a volá tyto metody pro obsažené ovládací prvky, které implementují `IMarqueeWidget` , takže všechny obsažené `IMarqueeWidget` ovládací prvky se také účastní testu.</span><span class="sxs-lookup"><span data-stu-id="a124c-337">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="a124c-338">Přidání příkazů návrháře do vlastních návrhářů</span><span class="sxs-lookup"><span data-stu-id="a124c-338">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="a124c-339">Ve `MarqueeControlRootDesigner` třídě přidejte obslužné rutiny události s názvem `OnVerbRunTest` a `OnVerbStopTest` .</span><span class="sxs-lookup"><span data-stu-id="a124c-339">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="a124c-340">Připojte tyto obslužné rutiny událostí ke svým odpovídajícím slovesům návrháře.</span><span class="sxs-lookup"><span data-stu-id="a124c-340">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="a124c-341">`MarqueeControlRootDesigner`dědí <xref:System.ComponentModel.Design.DesignerVerbCollection> z své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a124c-341">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="a124c-342">Vytvoříte dva nové <xref:System.ComponentModel.Design.DesignerVerb> objekty a přidáte je do této kolekce v <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="a124c-342">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="a124c-343">Vytvoření vlastního Editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="a124c-343">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="a124c-344">Když pro uživatele vytvoříte vlastní prostředí pro dobu návrhu, často je žádoucí vytvořit vlastní interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-344">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="a124c-345">To můžete provést vytvořením <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="a124c-345">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="a124c-346">`MarqueeBorder`Ovládací prvek zveřejňuje v okno Vlastnosti několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="a124c-346">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="a124c-347">Dvě z těchto vlastností `MarqueeSpinDirection` a `MarqueeLightShape` jsou reprezentovány výčty.</span><span class="sxs-lookup"><span data-stu-id="a124c-347">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="a124c-348">K ilustraci použití Editoru typů uživatelského rozhraní `MarqueeLightShape` bude mít vlastnost přidruženou <xref:System.Drawing.Design.UITypeEditor> třídu.</span><span class="sxs-lookup"><span data-stu-id="a124c-348">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="a124c-349">Vytvoření vlastního editoru typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a124c-349">To create a custom UI type editor</span></span>

1. <span data-ttu-id="a124c-350">Otevřete `MarqueeBorder` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-350">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="a124c-351">V definici `MarqueeBorder` třídy Deklarujte třídu `LightShapeEditor` s názvem, která je odvozena z <xref:System.Drawing.Design.UITypeEditor> .</span><span class="sxs-lookup"><span data-stu-id="a124c-351">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="a124c-352">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s názvem `editorService` .</span><span class="sxs-lookup"><span data-stu-id="a124c-352">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="a124c-353">Přepsat <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-353">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="a124c-354">Tato implementace vrátí <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown> , což oznamuje vývojovému prostředí, jak zobrazit `LightShapeEditor` .</span><span class="sxs-lookup"><span data-stu-id="a124c-354">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="a124c-355">Přepsat <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-355">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="a124c-356">Tato implementace se dotazuje návrhového prostředí pro <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> objekt.</span><span class="sxs-lookup"><span data-stu-id="a124c-356">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="a124c-357">V případě úspěchu vytvoří `LightShapeSelectionControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-357">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="a124c-358"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>Metoda je vyvolána pro spuštění `LightShapeEditor` .</span><span class="sxs-lookup"><span data-stu-id="a124c-358">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="a124c-359">Návratová hodnota z tohoto vyvolání se vrátí do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-359">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="a124c-360">Vytvoření ovládacího prvku zobrazení pro vlastní editor UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="a124c-360">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="a124c-361">`MarqueeLightShape`Vlastnost podporuje dva typy lehkých tvarů: `Square` a `Circle` .</span><span class="sxs-lookup"><span data-stu-id="a124c-361">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="a124c-362">Vytvoříte vlastní ovládací prvek, který bude použit výhradně pro účely grafického zobrazení těchto hodnot v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-362">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="a124c-363">Váš vlastní ovládací prvek bude použit <xref:System.Drawing.Design.UITypeEditor> pro interakci s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-363">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="a124c-364">Vytvoření ovládacího prvku zobrazení pro vlastní Editor typů uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a124c-364">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="a124c-365">Přidejte <xref:System.Windows.Forms.UserControl> do projektu novou položku `MarqueeControlLibrary` .</span><span class="sxs-lookup"><span data-stu-id="a124c-365">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-366">Dejte novému zdrojovému souboru základní název **LightShapeSelectionControl**.</span><span class="sxs-lookup"><span data-stu-id="a124c-366">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="a124c-367">Přetáhněte dva <xref:System.Windows.Forms.Panel> ovládací prvky ze **sady nástrojů** na `LightShapeSelectionControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-367">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="a124c-368">Pojmenujte je `squarePanel` a `circlePanel` .</span><span class="sxs-lookup"><span data-stu-id="a124c-368">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="a124c-369">Uspořádejte je vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="a124c-369">Arrange them side by side.</span></span> <span data-ttu-id="a124c-370">Nastavte <xref:System.Windows.Forms.Control.Size%2A> vlastnost obou <xref:System.Windows.Forms.Panel> ovládacích prvků na **(60, 60)**.</span><span class="sxs-lookup"><span data-stu-id="a124c-370">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="a124c-371">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `squarePanel` ovládacího prvku na **(8, 10)**.</span><span class="sxs-lookup"><span data-stu-id="a124c-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="a124c-372">Nastavte <xref:System.Windows.Forms.Control.Location%2A> vlastnost `circlePanel` ovládacího prvku na **(80, 10)**.</span><span class="sxs-lookup"><span data-stu-id="a124c-372">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="a124c-373">Nakonec nastavte vlastnost na <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` **(150, 80)**.</span><span class="sxs-lookup"><span data-stu-id="a124c-373">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="a124c-374">Otevřete `LightShapeSelectionControl` zdrojový soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="a124c-374">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="a124c-375">V horní části souboru importujte <xref:System.Windows.Forms.Design?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="a124c-375">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="a124c-376">Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro `squarePanel` `circlePanel` ovládací prvky a.</span><span class="sxs-lookup"><span data-stu-id="a124c-376">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="a124c-377">Tyto metody <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> se volají k ukončení vlastní <xref:System.Drawing.Design.UITypeEditor> relace úprav.</span><span class="sxs-lookup"><span data-stu-id="a124c-377">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="a124c-378">Deklarujte <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> proměnnou instance s názvem `editorService` .</span><span class="sxs-lookup"><span data-stu-id="a124c-378">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="a124c-379">Deklarujte `MarqueeLightShape` proměnnou instance nazvanou `lightShapeValue` .</span><span class="sxs-lookup"><span data-stu-id="a124c-379">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="a124c-380">V `LightShapeSelectionControl` konstruktoru připojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události k `squarePanel` `circlePanel` událostem ovládacích prvků a <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="a124c-380">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="a124c-381">Také definujte přetížení konstruktoru, které přiřadí `MarqueeLightShape` hodnotu z prostředí návrhu k `lightShapeValue` poli.</span><span class="sxs-lookup"><span data-stu-id="a124c-381">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="a124c-382">V <xref:System.ComponentModel.Component.Dispose%2A> metodě odpojte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="a124c-382">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="a124c-383">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="a124c-383">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="a124c-384">Otevřete soubor LightShapeSelectionControl.Designer.cs nebo LightShapeSelectionControl. Designer. vb a odeberte výchozí definici <xref:System.ComponentModel.Component.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a124c-384">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="a124c-385">Implementujte `LightShape` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a124c-385">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="a124c-386">Přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="a124c-386">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="a124c-387">Tato implementace Vykreslí vyplněný čtverec a kruh.</span><span class="sxs-lookup"><span data-stu-id="a124c-387">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="a124c-388">Tím se také zvýrazní vybraná hodnota vykreslením ohraničení kolem jednoho obrazce nebo druhého.</span><span class="sxs-lookup"><span data-stu-id="a124c-388">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="a124c-389">Testování vlastního ovládacího prvku v Návrháři</span><span class="sxs-lookup"><span data-stu-id="a124c-389">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="a124c-390">V tomto okamžiku můžete sestavit `MarqueeControlLibrary` projekt.</span><span class="sxs-lookup"><span data-stu-id="a124c-390">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="a124c-391">Otestujte implementaci vytvořením ovládacího prvku, který dědí z `MarqueeControl` třídy a jeho použitím na formuláři.</span><span class="sxs-lookup"><span data-stu-id="a124c-391">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="a124c-392">Vytvoření vlastní implementace MarqueeControl</span><span class="sxs-lookup"><span data-stu-id="a124c-392">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="a124c-393">Otevřete `DemoMarqueeControl` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="a124c-393">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="a124c-394">Tím se vytvoří instance `DemoMarqueeControl` typu a zobrazí se v instanci `MarqueeControlRootDesigner` typu.</span><span class="sxs-lookup"><span data-stu-id="a124c-394">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="a124c-395">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlLibrary** . Zobrazí se `MarqueeBorder` ovládací prvky a, které `MarqueeText` jsou k dispozici pro výběr.</span><span class="sxs-lookup"><span data-stu-id="a124c-395">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="a124c-396">Přetáhněte instanci `MarqueeBorder` ovládacího prvku na `DemoMarqueeControl` návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="a124c-396">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="a124c-397">Ukotvit tento `MarqueeBorder` ovládací prvek nadřazenému ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="a124c-397">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="a124c-398">Přetáhněte instanci `MarqueeText` ovládacího prvku na `DemoMarqueeControl` návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="a124c-398">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="a124c-399">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a124c-399">Build the solution.</span></span>

6. <span data-ttu-id="a124c-400">Kliknutím pravým tlačítkem myši na `DemoMarqueeControl` a z místní nabídky vyberte možnost **Spustit test** a spusťte animaci.</span><span class="sxs-lookup"><span data-stu-id="a124c-400">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="a124c-401">Kliknutím na **zastavit test** zastavte animaci.</span><span class="sxs-lookup"><span data-stu-id="a124c-401">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="a124c-402">Otevřete **Form1** v zobrazení Návrh.</span><span class="sxs-lookup"><span data-stu-id="a124c-402">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="a124c-403">Umístěte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a124c-403">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="a124c-404">Pojmenujte je `startButton` a `stopButton` změňte <xref:System.Windows.Forms.Control.Text%2A> hodnoty vlastností na **Start** a **zastavit**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a124c-404">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="a124c-405">Implementujte <xref:System.Windows.Forms.Control.Click> obslužné rutiny událostí pro oba <xref:System.Windows.Forms.Button> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a124c-405">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="a124c-406">V **sadě nástrojů**otevřete kartu **součásti MarqueeControlTest** . Zobrazí se `DemoMarqueeControl` dostupná pro výběr.</span><span class="sxs-lookup"><span data-stu-id="a124c-406">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="a124c-407">Přetáhněte instanci `DemoMarqueeControl` na návrhovou plochu **Form1** .</span><span class="sxs-lookup"><span data-stu-id="a124c-407">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="a124c-408">V <xref:System.Windows.Forms.Control.Click> obslužných rutinách události volejte `Start` `Stop` metody a na `DemoMarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-408">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="a124c-409">Nastavte `MarqueeControlTest` projekt jako spouštěný projekt a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="a124c-409">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="a124c-410">Zobrazí se formulář, ve kterém se zobrazuje vaše `DemoMarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-410">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="a124c-411">Kliknutím na tlačítko **Start** spustíte animaci.</span><span class="sxs-lookup"><span data-stu-id="a124c-411">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="a124c-412">Mělo by se zobrazit blikání textu a indikátory pohybu kolem ohraničení.</span><span class="sxs-lookup"><span data-stu-id="a124c-412">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a124c-413">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a124c-413">Next steps</span></span>

<span data-ttu-id="a124c-414">`MarqueeControlLibrary`Ukazuje jednoduchou implementaci vlastních ovládacích prvků a přidružených návrhářů.</span><span class="sxs-lookup"><span data-stu-id="a124c-414">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="a124c-415">Tuto ukázku můžete udělat několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="a124c-415">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="a124c-416">Změňte hodnoty vlastností `DemoMarqueeControl` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="a124c-416">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="a124c-417">`MarqueBorder`Chcete-li vytvořit vnořený efekt, přidejte další ovládací prvky a ukotvěte je Dock v rámci jejich nadřazených instancí.</span><span class="sxs-lookup"><span data-stu-id="a124c-417">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="a124c-418">Experimentujte s různými nastaveními pro `UpdatePeriod` a vlastnosti související s osvětlením.</span><span class="sxs-lookup"><span data-stu-id="a124c-418">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="a124c-419">Vytvořte vlastní implementace `IMarqueeWidget` .</span><span class="sxs-lookup"><span data-stu-id="a124c-419">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="a124c-420">Mohli byste například vytvořit Flash "Neon Sign" nebo animované znaménko s více obrázky.</span><span class="sxs-lookup"><span data-stu-id="a124c-420">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="a124c-421">Dále upravte prostředí pro dobu návrhu.</span><span class="sxs-lookup"><span data-stu-id="a124c-421">Further customize the design-time experience.</span></span> <span data-ttu-id="a124c-422">Můžete zkusit vytvořit stín více vlastností než <xref:System.Windows.Forms.Control.Enabled%2A> a a <xref:System.Windows.Forms.Control.Visible%2A> můžete přidat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a124c-422">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="a124c-423">Přidejte nové příkazy návrháře, abyste zjednodušili běžné úkoly, jako je například ukotvení podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a124c-423">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="a124c-424">Licenci `MarqueeControl` .</span><span class="sxs-lookup"><span data-stu-id="a124c-424">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="a124c-425">Určuje, jak jsou ovládací prvky serializovány a jak jsou pro ně generovány kódy.</span><span class="sxs-lookup"><span data-stu-id="a124c-425">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="a124c-426">Další informace naleznete v tématu [generování a kompilace dynamického zdrojového kódu](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="a124c-426">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a124c-427">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a124c-427">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
