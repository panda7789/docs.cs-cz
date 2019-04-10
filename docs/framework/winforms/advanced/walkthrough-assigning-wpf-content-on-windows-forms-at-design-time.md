---
title: 'Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: b4efef869c96ddb4e58445e45ecad12b5658f9f4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343342"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="fa1e1-102">Návod: Přiřazení obsahu WPF v modelu Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="fa1e1-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="fa1e1-103">Tento názorný postup ukazují, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="fa1e1-104">Můžete vybrat všechny typy ovládacích prvků WPF, které jsou zahrnuty ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-104">You can select any WPF control types which are included in your project.</span></span>

 <span data-ttu-id="fa1e1-105">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="fa1e1-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="fa1e1-106">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-106">Create the project.</span></span>

-   <span data-ttu-id="fa1e1-107">Vytvořte typy ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-107">Create the WPF control types.</span></span>

-   <span data-ttu-id="fa1e1-108">Vyberte ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-108">Select WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="fa1e1-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fa1e1-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fa1e1-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="fa1e1-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fa1e1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa1e1-112">Prerequisites</span></span>  
 <span data-ttu-id="fa1e1-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="fa1e1-113">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="fa1e1-114">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-114">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="fa1e1-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fa1e1-115">Creating the Project</span></span>  
 <span data-ttu-id="fa1e1-116">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa1e1-117">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="fa1e1-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fa1e1-118">To create the project</span></span>  
  
-   <span data-ttu-id="fa1e1-119">Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="fa1e1-120">Vytváření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="fa1e1-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="fa1e1-121">Po přidání typy ovládacích prvků WPF k projektu, můžete je hostujte v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="fa1e1-122">Chcete-li vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="fa1e1-122">To create WPF control types</span></span>  
  
1. <span data-ttu-id="fa1e1-123">Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="fa1e1-124">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="fa1e1-125">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="fa1e1-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="fa1e1-126">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="fa1e1-127">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fa1e1-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="fa1e1-128">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="fa1e1-129">Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5. <span data-ttu-id="fa1e1-130">Přidejte druhý WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="fa1e1-131">Použití výchozího názvu pro typ ovládacího prvku `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6. <span data-ttu-id="fa1e1-132">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7. <span data-ttu-id="fa1e1-133">Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostovaný obsah 2**.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="fa1e1-134">**Poznámka:** obecně byste neměli hostit složitější obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="fa1e1-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek se tady používá pouze pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1. <span data-ttu-id="fa1e1-136">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="fa1e1-137">Výběr ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="fa1e1-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="fa1e1-138">Můžete přiřadit jiný obsah WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek, který je již hostování obsahu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="fa1e1-139">Chcete-li vybrat ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="fa1e1-139">To select WPF controls</span></span>  
  
1. <span data-ttu-id="fa1e1-140">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="fa1e1-141">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="fa1e1-142">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3. <span data-ttu-id="fa1e1-143">Na panelu inteligentních značek `elementHost1`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4. <span data-ttu-id="fa1e1-144">Vyberte **UserControl2** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="fa1e1-145">`elementHost1` Ovládací prvek nyní hostitelem instance `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5. <span data-ttu-id="fa1e1-146">V **vlastnosti** okno, ujistěte se, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6. <span data-ttu-id="fa1e1-147">Z **nástrojů**v **interoperabilita WPF** skupiny tak, že přetáhnete <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="fa1e1-148">Výchozí název pro nový ovládací prvek je `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-148">The default name for the new control is `elementHost2`.</span></span>  
  
7. <span data-ttu-id="fa1e1-149">Na panelu inteligentních značek `elementHost2`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8. <span data-ttu-id="fa1e1-150">Vyberte **UserControl1** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="fa1e1-151">`elementHost2` Ovládací prvek nyní hostitelem instance `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="fa1e1-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1e1-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa1e1-152">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="fa1e1-153">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="fa1e1-153">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="fa1e1-154">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="fa1e1-154">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="fa1e1-155">Návrh XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa1e1-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
