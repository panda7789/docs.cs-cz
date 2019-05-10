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
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211242"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="c5b37-102">Návod: Přiřazení obsahu WPF ve Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="c5b37-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="c5b37-103">Tento názorný postup ukazují, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c5b37-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="c5b37-104">Můžete vybrat všechny typy ovládacích prvků WPF, které jsou zahrnuty ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-104">You can select any WPF control types which are included in your project.</span></span>

<span data-ttu-id="c5b37-105">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c5b37-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="c5b37-106">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-106">Create the project.</span></span>

- <span data-ttu-id="c5b37-107">Vytvořte typy ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="c5b37-107">Create the WPF control types.</span></span>

- <span data-ttu-id="c5b37-108">Vyberte ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="c5b37-108">Select WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c5b37-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5b37-109">Prerequisites</span></span>

<span data-ttu-id="c5b37-110">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="c5b37-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c5b37-111">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c5b37-111">Create the project</span></span>

<span data-ttu-id="c5b37-112">Otevřít Visual Studio a vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-112">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="c5b37-113">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c5b37-113">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="c5b37-114">Vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c5b37-114">Create the WPF control types</span></span>

<span data-ttu-id="c5b37-115">Po přidání typy ovládacích prvků WPF k projektu, můžete je hostujte v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c5b37-115">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

## <a name="create-wpf-control-types"></a><span data-ttu-id="c5b37-116">Vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c5b37-116">Create WPF control types</span></span>

1. <span data-ttu-id="c5b37-117">Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="c5b37-117">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c5b37-118">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c5b37-119">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c5b37-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c5b37-120">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="c5b37-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="c5b37-121">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c5b37-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="c5b37-122">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="c5b37-123">Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.</span><span class="sxs-lookup"><span data-stu-id="c5b37-123">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="c5b37-124">Přidejte druhý WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-124">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="c5b37-125">Použití výchozího názvu pro typ ovládacího prvku `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-125">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="c5b37-126">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

7. <span data-ttu-id="c5b37-127">Přidat <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostovaný obsah 2**.</span><span class="sxs-lookup"><span data-stu-id="c5b37-127">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

 <span data-ttu-id="c5b37-128">**Poznámka:** obecně byste neměli hostit složitější obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="c5b37-128">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="c5b37-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek se tady používá pouze pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="c5b37-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

1. <span data-ttu-id="c5b37-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c5b37-130">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="c5b37-131">Vyberte ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="c5b37-131">Select WPF controls</span></span>

<span data-ttu-id="c5b37-132">Můžete přiřadit jiný obsah WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek, který je již hostování obsahu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-132">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="c5b37-133">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="c5b37-133">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="c5b37-134">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c5b37-134">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="c5b37-135">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-135">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="c5b37-136">Na panelu inteligentních značek `elementHost1`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-136">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="c5b37-137">Vyberte **UserControl2** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-137">Select **UserControl2** from the drop-down list box.</span></span>

     <span data-ttu-id="c5b37-138">`elementHost1` Ovládací prvek nyní hostitelem instance `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-138">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="c5b37-139">V **vlastnosti** okno, ujistěte se, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="c5b37-139">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="c5b37-140">Z **nástrojů**v **interoperabilita WPF** skupiny tak, že přetáhnete <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c5b37-140">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

     <span data-ttu-id="c5b37-141">Výchozí název pro nový ovládací prvek je `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="c5b37-141">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="c5b37-142">Na panelu inteligentních značek `elementHost2`, otevřete **vyberte hostovaný obsah** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-142">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="c5b37-143">Vyberte **UserControl1** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-143">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="c5b37-144">`elementHost2` Ovládací prvek nyní hostitelem instance `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="c5b37-144">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5b37-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5b37-145">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c5b37-146">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="c5b37-146">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c5b37-147">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c5b37-147">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c5b37-148">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5b37-148">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
