---
title: 'Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211761"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="57e81-102">Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem</span><span class="sxs-lookup"><span data-stu-id="57e81-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>

<span data-ttu-id="57e81-103">Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování napsáním vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="57e81-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>

<span data-ttu-id="57e81-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který se podobá **navigačním podokně** poskytované Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="57e81-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="57e81-105">Tyto úlohy jsou uvedené v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="57e81-105">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="57e81-106">Vytvoření projektu knihovny ovládacích prvků Windows.</span><span class="sxs-lookup"><span data-stu-id="57e81-106">Creating a Windows Control Library project.</span></span>

- <span data-ttu-id="57e81-107">Návrh StackView ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-107">Designing the StackView Control.</span></span>

- <span data-ttu-id="57e81-108">Implementace vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="57e81-108">Implementing a Custom Renderer.</span></span>

<span data-ttu-id="57e81-109">Až budete hotovi, budete mít opakovaně použitelné vlastní ovládací prvek s profesionální vzhled aplikace Microsoft Office® XP ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>

<span data-ttu-id="57e81-110">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Vytvoření ovládacího prvku ToolStrip s profesionálním](how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57e81-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57e81-111">Prerequisites</span></span>

<span data-ttu-id="57e81-112">Visual Studio k dokončení tohoto návodu budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="57e81-112">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="57e81-113">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="57e81-113">Create the control library project</span></span>

1. <span data-ttu-id="57e81-114">V sadě Visual Studio vytvořte nový projekt knihovny ovládacích prvků Windows s názvem `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="57e81-114">In Visual Studio, create a new Windows Control Library project named `StackViewLibrary`.</span></span>

2. <span data-ttu-id="57e81-115">V **Průzkumníka řešení**, odstraňte výchozí ovládací prvek projektu tak, že odstraníte zdrojový soubor s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk.</span><span class="sxs-lookup"><span data-stu-id="57e81-115">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

     <span data-ttu-id="57e81-116">Další informace najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="57e81-116">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="57e81-117">Přidat nový <xref:System.Windows.Forms.UserControl> položkou **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="57e81-117">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="57e81-118">Zadejte základní název nového zdrojového souboru `StackView`.</span><span class="sxs-lookup"><span data-stu-id="57e81-118">Give the new source file a base name of `StackView`.</span></span>

## <a name="design-the-stackview-control"></a><span data-ttu-id="57e81-119">Návrh StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="57e81-119">Design the StackView control</span></span>

<span data-ttu-id="57e81-120">`StackView` Složeného ovládacího prvku s jeden podřízený prvek je ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-120">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="57e81-121">Další informace o složených ovládacích prvků naleznete v tématu [typy Custom Controls](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-121">For more information about composite controls, see [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

1. <span data-ttu-id="57e81-122">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ToolStrip> ovládací prvek na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="57e81-122">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>

2. <span data-ttu-id="57e81-123">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolStrip> ovládacího prvku vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="57e81-123">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>

    |<span data-ttu-id="57e81-124">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="57e81-124">Property</span></span>|<span data-ttu-id="57e81-125">Value</span><span class="sxs-lookup"><span data-stu-id="57e81-125">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="57e81-126">Name</span><span class="sxs-lookup"><span data-stu-id="57e81-126">Name</span></span>|`stackStrip`|
    |<span data-ttu-id="57e81-127">CanOverflow.</span><span class="sxs-lookup"><span data-stu-id="57e81-127">CanOverflow</span></span>|`false`|
    |<span data-ttu-id="57e81-128">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="57e81-128">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |<span data-ttu-id="57e81-129">Písma</span><span class="sxs-lookup"><span data-stu-id="57e81-129">Font</span></span>|`Tahoma, 10pt, style=Bold`|
    |<span data-ttu-id="57e81-130">GripStyle</span><span class="sxs-lookup"><span data-stu-id="57e81-130">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |<span data-ttu-id="57e81-131">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="57e81-131">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |<span data-ttu-id="57e81-132">Padding</span><span class="sxs-lookup"><span data-stu-id="57e81-132">Padding</span></span>|`0, 7, 0, 0`|
    |<span data-ttu-id="57e81-133">RenderMode</span><span class="sxs-lookup"><span data-stu-id="57e81-133">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. <span data-ttu-id="57e81-134">V Návrháři formulářů Windows, klikněte na tlačítko <xref:System.Windows.Forms.ToolStrip> ovládacího prvku **přidat** tlačítko a přidat <xref:System.Windows.Forms.ToolStripButton> k `stackStrip` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-134">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>

4. <span data-ttu-id="57e81-135">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolStripButton> ovládacího prvku vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="57e81-135">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>

    |<span data-ttu-id="57e81-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="57e81-136">Property</span></span>|<span data-ttu-id="57e81-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="57e81-137">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="57e81-138">Name</span><span class="sxs-lookup"><span data-stu-id="57e81-138">Name</span></span>|`mailStackButton`|
    |<span data-ttu-id="57e81-139">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="57e81-139">CheckOnClick</span></span>|<span data-ttu-id="57e81-140">true</span><span class="sxs-lookup"><span data-stu-id="57e81-140">true</span></span>|
    |<span data-ttu-id="57e81-141">– CheckState</span><span class="sxs-lookup"><span data-stu-id="57e81-141">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|
    |<span data-ttu-id="57e81-142">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="57e81-142">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |<span data-ttu-id="57e81-143">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="57e81-143">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |<span data-ttu-id="57e81-144">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="57e81-144">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |<span data-ttu-id="57e81-145">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="57e81-145">ImageTransparentColor</span></span>|`238, 238, 238`|
    |<span data-ttu-id="57e81-146">Okraj</span><span class="sxs-lookup"><span data-stu-id="57e81-146">Margin</span></span>|`0, 0, 0, 0`|
    |<span data-ttu-id="57e81-147">Padding</span><span class="sxs-lookup"><span data-stu-id="57e81-147">Padding</span></span>|`3, 3, 3, 3`|
    |<span data-ttu-id="57e81-148">Text</span><span class="sxs-lookup"><span data-stu-id="57e81-148">Text</span></span>|<span data-ttu-id="57e81-149">**e-mailu**</span><span class="sxs-lookup"><span data-stu-id="57e81-149">**Mail**</span></span>|
    |<span data-ttu-id="57e81-150">TextAlign</span><span class="sxs-lookup"><span data-stu-id="57e81-150">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. <span data-ttu-id="57e81-151">Opakujte krok 7 pro tři další <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="57e81-151">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

     <span data-ttu-id="57e81-152">Ovládací prvky pojmenujte `calendarStackButton`, `contactsStackButton`, a `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="57e81-152">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="57e81-153">Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost **kalendáře**, **kontakty**, a **úlohy**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="57e81-153">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>

## <a name="handle-events"></a><span data-ttu-id="57e81-154">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="57e81-154">Handle events</span></span>

<span data-ttu-id="57e81-155">Dvě události jsou důležité, aby `StackView` ovládací prvek se chovají správně.</span><span class="sxs-lookup"><span data-stu-id="57e81-155">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="57e81-156">Zpracování <xref:System.Windows.Forms.UserControl.Load> událost pro umístění ovládacího prvku správně.</span><span class="sxs-lookup"><span data-stu-id="57e81-156">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="57e81-157">Zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událost pro každou <xref:System.Windows.Forms.ToolStripButton> poskytnout `StackView` řídit chování stavu podobně jako <xref:System.Windows.Forms.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-157">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>

1. <span data-ttu-id="57e81-158">V Návrháři formulářů Windows, vyberte `StackView` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-158">In the Windows Forms Designer, select the `StackView` control.</span></span>

2. <span data-ttu-id="57e81-159">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="57e81-159">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="57e81-160">Poklikáním na událost zatížení ke generování `StackView_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="57e81-160">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>

4. <span data-ttu-id="57e81-161">V `StackView_Load` obslužná rutina události, zkopírujte a vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="57e81-161">In the `StackView_Load` event handler, copy and paste the following code.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. <span data-ttu-id="57e81-162">V Návrháři formulářů Windows, vyberte `mailStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-162">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>

6. <span data-ttu-id="57e81-163">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="57e81-163">In the **Properties** window, click **Events**.</span></span>

7. <span data-ttu-id="57e81-164">Dvakrát klikněte na událost Click.</span><span class="sxs-lookup"><span data-stu-id="57e81-164">Double-click the Click event.</span></span>

     <span data-ttu-id="57e81-165">Generuje Návrhář formulářů Windows `mailStackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="57e81-165">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>

8. <span data-ttu-id="57e81-166">Přejmenovat `mailStackButton_Click` obslužnou rutinu události `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="57e81-166">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>

     <span data-ttu-id="57e81-167">Další informace najdete v tématu [kódu symbol refaktoring pro přejmenování](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="57e81-167">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

9. <span data-ttu-id="57e81-168">Vložte následující kód do `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="57e81-168">Insert the following code into the `stackButton_Click` event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. <span data-ttu-id="57e81-169">V Návrháři formulářů Windows, vyberte `calendarStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-169">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>

11. <span data-ttu-id="57e81-170">V **vlastnosti** okně, nastavte na hodnotu událost Click `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="57e81-170">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>

12. <span data-ttu-id="57e81-171">Opakujte kroky 10 a 11 pro `contactsStackButton` a `tasksStackButton` ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="57e81-171">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>

## <a name="define-icons"></a><span data-ttu-id="57e81-172">Definování ikony</span><span class="sxs-lookup"><span data-stu-id="57e81-172">Define icons</span></span>

<span data-ttu-id="57e81-173">Každý `StackView` má tlačítko přidružené ikonu.</span><span class="sxs-lookup"><span data-stu-id="57e81-173">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="57e81-174">Pro usnadnění práce jednotlivé ikony je vyjádřena jako řetězec s kódováním Base64, který je deserializován před <xref:System.Drawing.Bitmap> se vytvoří z něj.</span><span class="sxs-lookup"><span data-stu-id="57e81-174">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="57e81-175">V produkčním prostředí ukládat data rastrového obrázku jako prostředku a ikony se zobrazí v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="57e81-175">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="57e81-176">Další informace najdete v tématu [jak: Přidání obrázků na pozadí do formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="57e81-176">For more information, see [How to: Add Background Images to Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span></span>

1. <span data-ttu-id="57e81-177">V editoru kódu vložte následující kód do `StackView` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="57e81-177">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="57e81-178">Tento kód inicializuje rastrové obrázky pro <xref:System.Windows.Forms.ToolStripButton> ikony.</span><span class="sxs-lookup"><span data-stu-id="57e81-178">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. <span data-ttu-id="57e81-179">Přidejte volání `InitializeImages` metoda ve `StackView` konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="57e81-179">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a><span data-ttu-id="57e81-180">Implementace vlastního rendereru</span><span class="sxs-lookup"><span data-stu-id="57e81-180">Implement a custom renderer</span></span>

<span data-ttu-id="57e81-181">Můžete přizpůsobit většinu prvků `StackView` řídit Moje implementace, která je odvozena z třídy <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="57e81-181">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="57e81-182">V tomto postupu budete implementovat <xref:System.Windows.Forms.ToolStripProfessionalRenderer> třídu, která přizpůsobí úchytu a vykreslí barevného přechodu pozadí <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="57e81-182">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

1. <span data-ttu-id="57e81-183">Vložte následující kód do `StackView` definici ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="57e81-183">Insert the following code into the `StackView` control definition.</span></span>

     <span data-ttu-id="57e81-184">Toto je definice `StackRenderer` třídy, která přepisuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, a <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody k vytvoření vlastní vzhled.</span><span class="sxs-lookup"><span data-stu-id="57e81-184">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. <span data-ttu-id="57e81-185">V `StackView` konstruktoru ovládacího prvku, vytvořte novou instanci třídy `StackRenderer` třídy a přiřazení této instance `stackStrip` ovládacího prvku <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="57e81-185">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a><span data-ttu-id="57e81-186">Testování StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="57e81-186">Test the StackView control</span></span>

<span data-ttu-id="57e81-187">`StackView` Ovládacího prvku je odvozena z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="57e81-187">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="57e81-188">Proto můžete otestovat ovládací prvek s **kontejner testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="57e81-188">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="57e81-189">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-189">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

1. <span data-ttu-id="57e81-190">Stisknutím klávesy **F5** projekt sestavit a spustit **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="57e81-190">Press **F5** to build the project and start the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="57e81-191">Přesuňte ukazatel nad tlačítek `StackView` ovládací prvek a potom klikněte na tlačítko zobrazit vzhled vybraný stav.</span><span class="sxs-lookup"><span data-stu-id="57e81-191">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>

## <a name="next-steps"></a><span data-ttu-id="57e81-192">Další kroky</span><span class="sxs-lookup"><span data-stu-id="57e81-192">Next steps</span></span>

<span data-ttu-id="57e81-193">V tomto návodu vytvoříte opakovaně použitelné vlastní ovládací prvek s profesionální vzhled ovládacího prvku Office XP.</span><span class="sxs-lookup"><span data-stu-id="57e81-193">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="57e81-194">Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:</span><span class="sxs-lookup"><span data-stu-id="57e81-194">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="57e81-195">Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="57e81-195">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="57e81-196">Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-196">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="57e81-197">Vytvoření formuláře se automaticky vyplněná standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="57e81-197">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="57e81-198">Další informace najdete v tématu [názorný postup: Poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-198">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="57e81-199">Vytvoření více formuláře (MDI interface) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="57e81-199">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="57e81-200">Další informace najdete v tématu [jak: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="57e81-200">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57e81-201">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57e81-201">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="57e81-202">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="57e81-202">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="57e81-203">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="57e81-203">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
