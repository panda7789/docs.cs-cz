---
title: 'Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním'
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
ms.openlocfilehash: 64624508a50eb6e28337baa1a3600298e2c83fd7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710742"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="802f1-102">Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním</span><span class="sxs-lookup"><span data-stu-id="802f1-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="802f1-103">Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování napsáním vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="802f1-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="802f1-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který se podobá **navigačním podokně** poskytované Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="802f1-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="802f1-105">Tyto úlohy jsou uvedené v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="802f1-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="802f1-106">Vytvoření projektu knihovny ovládacích prvků Windows.</span><span class="sxs-lookup"><span data-stu-id="802f1-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="802f1-107">Návrh StackView ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="802f1-108">Implementace vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="802f1-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="802f1-109">Až budete hotovi, budete mít opakovaně použitelné vlastní ovládací prvek s profesionální vzhled aplikace Microsoft Office® XP ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="802f1-110">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Vytvoření ovládacího prvku ToolStrip s profesionálním](how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="802f1-111">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="802f1-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="802f1-112">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="802f1-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="802f1-113">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="802f1-113">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="802f1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="802f1-114">Prerequisites</span></span>  
 <span data-ttu-id="802f1-115">K dokončení tohoto návodu budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="802f1-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="802f1-116">Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="802f1-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="802f1-117">Vytvoření projektu knihovny ovládacích prvků Windows</span><span class="sxs-lookup"><span data-stu-id="802f1-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="802f1-118">Prvním krokem je vytvoření projektu knihovny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="802f1-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="802f1-119">Vytvoření projektu knihovny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="802f1-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="802f1-120">Vytvořte nový projekt knihovny ovládacích prvků Windows s názvem `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="802f1-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="802f1-121">V **Průzkumníka řešení**, odstraňte výchozí ovládací prvek projektu tak, že odstraníte zdrojový soubor s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk.</span><span class="sxs-lookup"><span data-stu-id="802f1-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="802f1-122">Další informace najdete v tématu [jak: Odebrat, odstranit a vyloučit položky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="802f1-122">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="802f1-123">Přidat nový <xref:System.Windows.Forms.UserControl> položkou **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="802f1-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="802f1-124">Zadejte základní název nového zdrojového souboru `StackView`.</span><span class="sxs-lookup"><span data-stu-id="802f1-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="802f1-125">Návrh StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="802f1-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="802f1-126">`StackView` Složeného ovládacího prvku s jeden podřízený prvek je ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="802f1-127">Další informace o složených ovládacích prvků naleznete v tématu [typy Custom Controls](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-127">For more information about composite controls, see [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="802f1-128">Chcete-li navrhnout StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="802f1-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="802f1-129">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ToolStrip> ovládací prvek na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="802f1-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="802f1-130">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolStrip> ovládacího prvku vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="802f1-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="802f1-131">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="802f1-131">Property</span></span>|<span data-ttu-id="802f1-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="802f1-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="802f1-133">Název</span><span class="sxs-lookup"><span data-stu-id="802f1-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="802f1-134">CanOverflow.</span><span class="sxs-lookup"><span data-stu-id="802f1-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="802f1-135">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="802f1-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="802f1-136">Písma</span><span class="sxs-lookup"><span data-stu-id="802f1-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="802f1-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="802f1-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="802f1-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="802f1-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="802f1-139">Padding</span><span class="sxs-lookup"><span data-stu-id="802f1-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="802f1-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="802f1-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="802f1-141">V Návrháři formulářů Windows, klikněte na tlačítko <xref:System.Windows.Forms.ToolStrip> ovládacího prvku **přidat** tlačítko a přidat <xref:System.Windows.Forms.ToolStripButton> k `stackStrip` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="802f1-142">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolStripButton> ovládacího prvku vlastnosti podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="802f1-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="802f1-143">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="802f1-143">Property</span></span>|<span data-ttu-id="802f1-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="802f1-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="802f1-145">Název</span><span class="sxs-lookup"><span data-stu-id="802f1-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="802f1-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="802f1-146">CheckOnClick</span></span>|<span data-ttu-id="802f1-147">true</span><span class="sxs-lookup"><span data-stu-id="802f1-147">true</span></span>|  
    |<span data-ttu-id="802f1-148">– CheckState</span><span class="sxs-lookup"><span data-stu-id="802f1-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="802f1-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="802f1-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="802f1-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="802f1-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="802f1-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="802f1-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="802f1-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="802f1-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="802f1-153">Okraj</span><span class="sxs-lookup"><span data-stu-id="802f1-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="802f1-154">Padding</span><span class="sxs-lookup"><span data-stu-id="802f1-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="802f1-155">Text</span><span class="sxs-lookup"><span data-stu-id="802f1-155">Text</span></span>|<span data-ttu-id="802f1-156">**e-mailu**</span><span class="sxs-lookup"><span data-stu-id="802f1-156">**Mail**</span></span>|  
    |<span data-ttu-id="802f1-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="802f1-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="802f1-158">Opakujte krok 7 pro tři další <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="802f1-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="802f1-159">Ovládací prvky pojmenujte `calendarStackButton`, `contactsStackButton`, a `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="802f1-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="802f1-160">Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost **kalendáře**, **kontakty**, a **úlohy**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="802f1-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="802f1-161">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="802f1-161">Handling Events</span></span>  
 <span data-ttu-id="802f1-162">Dvě události jsou důležité, aby `StackView` ovládací prvek se chovají správně.</span><span class="sxs-lookup"><span data-stu-id="802f1-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="802f1-163">Zpracování <xref:System.Windows.Forms.UserControl.Load> událost pro umístění ovládacího prvku správně.</span><span class="sxs-lookup"><span data-stu-id="802f1-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="802f1-164">Zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událost pro každou <xref:System.Windows.Forms.ToolStripButton> poskytnout `StackView` řídit chování stavu podobně jako <xref:System.Windows.Forms.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="802f1-165">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="802f1-165">To handle events</span></span>  
  
1.  <span data-ttu-id="802f1-166">V Návrháři formulářů Windows, vyberte `StackView` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="802f1-167">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="802f1-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="802f1-168">Poklikáním na událost zatížení ke generování `StackView_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="802f1-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="802f1-169">V `StackView_Load` obslužná rutina události, zkopírujte a vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="802f1-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="802f1-170">V Návrháři formulářů Windows, vyberte `mailStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="802f1-171">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="802f1-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="802f1-172">Dvakrát klikněte na událost Click.</span><span class="sxs-lookup"><span data-stu-id="802f1-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="802f1-173">Generuje Návrhář formulářů Windows `mailStackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="802f1-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="802f1-174">Přejmenovat `mailStackButton_Click` obslužnou rutinu události `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="802f1-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="802f1-175">Další informace najdete v tématu [kódu symbol refaktoring pro přejmenování](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="802f1-175">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>  
  
9. <span data-ttu-id="802f1-176">Vložte následující kód do `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="802f1-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="802f1-177">V Návrháři formulářů Windows, vyberte `calendarStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="802f1-178">V **vlastnosti** okně, nastavte na hodnotu událost Click `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="802f1-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="802f1-179">Opakujte kroky 10 a 11 pro `contactsStackButton` a `tasksStackButton` ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="802f1-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="802f1-180">Definování ikony</span><span class="sxs-lookup"><span data-stu-id="802f1-180">Defining Icons</span></span>  
 <span data-ttu-id="802f1-181">Každý `StackView` má tlačítko přidružené ikonu.</span><span class="sxs-lookup"><span data-stu-id="802f1-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="802f1-182">Pro usnadnění práce jednotlivé ikony je vyjádřena jako řetězec s kódováním Base64, který je deserializován před <xref:System.Drawing.Bitmap> se vytvoří z něj.</span><span class="sxs-lookup"><span data-stu-id="802f1-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="802f1-183">V produkčním prostředí ukládat data rastrového obrázku jako prostředku a ikony se zobrazí v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="802f1-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="802f1-184">Další informace najdete v tématu [jak: Přidání obrázků na pozadí do formulářů Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="802f1-184">For more information, see [How to: Add Background Images to Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="802f1-185">Chcete-li definovat ikony</span><span class="sxs-lookup"><span data-stu-id="802f1-185">To define icons</span></span>  
  
1.  <span data-ttu-id="802f1-186">V editoru kódu vložte následující kód do `StackView` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="802f1-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="802f1-187">Tento kód inicializuje rastrové obrázky pro <xref:System.Windows.Forms.ToolStripButton> ikony.</span><span class="sxs-lookup"><span data-stu-id="802f1-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="802f1-188">Přidejte volání `InitializeImages` metoda ve `StackView` konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="802f1-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="802f1-189">Implementace vlastního Rendereru</span><span class="sxs-lookup"><span data-stu-id="802f1-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="802f1-190">Můžete přizpůsobit většinu prvků `StackView` řídit Moje implementace, která je odvozena z třídy <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="802f1-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="802f1-191">V tomto postupu budete implementovat <xref:System.Windows.Forms.ToolStripProfessionalRenderer> třídu, která přizpůsobí úchytu a vykreslí barevného přechodu pozadí <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="802f1-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="802f1-192">Implementace vlastního rendereru</span><span class="sxs-lookup"><span data-stu-id="802f1-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="802f1-193">Vložte následující kód do `StackView` definici ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="802f1-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="802f1-194">Toto je definice `StackRenderer` třídy, která přepisuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, a <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody k vytvoření vlastní vzhled.</span><span class="sxs-lookup"><span data-stu-id="802f1-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="802f1-195">V `StackView` konstruktoru ovládacího prvku, vytvořte novou instanci třídy `StackRenderer` třídy a přiřazení této instance `stackStrip` ovládacího prvku <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="802f1-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="802f1-196">Testování StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="802f1-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="802f1-197">`StackView` Ovládacího prvku je odvozena z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="802f1-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="802f1-198">Proto můžete otestovat ovládací prvek s **kontejner testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="802f1-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="802f1-199">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="802f1-200">K otestování StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="802f1-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="802f1-201">Stiskněte klávesu F5, aby projekt sestavil a spustila **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="802f1-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="802f1-202">Přesuňte ukazatel nad tlačítek `StackView` ovládací prvek a potom klikněte na tlačítko zobrazit vzhled vybraný stav.</span><span class="sxs-lookup"><span data-stu-id="802f1-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="802f1-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="802f1-203">Next Steps</span></span>  
 <span data-ttu-id="802f1-204">V tomto návodu vytvoříte opakovaně použitelné vlastní ovládací prvek s profesionální vzhled ovládacího prvku Office XP.</span><span class="sxs-lookup"><span data-stu-id="802f1-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="802f1-205">Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:</span><span class="sxs-lookup"><span data-stu-id="802f1-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="802f1-206">Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="802f1-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="802f1-207">Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-207">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="802f1-208">Vytvoření formuláře se automaticky vyplněná standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="802f1-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="802f1-209">Další informace najdete v tématu [názorný postup: Poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="802f1-210">Vytvoření více formuláře (MDI interface) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="802f1-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="802f1-211">Další informace najdete v tématu [jak: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="802f1-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802f1-212">Viz také:</span><span class="sxs-lookup"><span data-stu-id="802f1-212">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="802f1-213">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="802f1-213">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="802f1-214">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="802f1-214">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
