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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666250"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="7962a-102">Návod: Přiřazení obsahu WPF na model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7962a-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="7962a-103">Tento článek ukazuje, jak vybrat typy ovládacích prvků Windows Presentation Foundation (WPF), které chcete zobrazit ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7962a-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="7962a-104">Můžete vybrat jakýkoli typ ovládacího prvku WPF, který je součástí projektu.</span><span class="sxs-lookup"><span data-stu-id="7962a-104">You can select any WPF control types which are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7962a-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7962a-105">Prerequisites</span></span>

<span data-ttu-id="7962a-106">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7962a-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7962a-107">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="7962a-107">Create the project</span></span>

<span data-ttu-id="7962a-108">Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="7962a-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="7962a-109">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7962a-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="7962a-110">Vytvoření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="7962a-110">Create the WPF control types</span></span>

<span data-ttu-id="7962a-111">Po přidání typů ovládacích prvků WPF do projektu je můžete hostovat v různých <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvcích.</span><span class="sxs-lookup"><span data-stu-id="7962a-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="7962a-112">Přidejte do řešení nový <xref:System.Windows.Controls.UserControl> projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="7962a-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="7962a-113">Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7962a-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7962a-114">Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="7962a-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="7962a-115">V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="7962a-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="7962a-116">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="7962a-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="7962a-117">Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.TextBox.Text%2A> nastavte hodnotu vlastnosti na **hostovaný obsah.** <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7962a-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="7962a-118">Přidejte do projektu druhý <xref:System.Windows.Controls.UserControl> WPF.</span><span class="sxs-lookup"><span data-stu-id="7962a-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="7962a-119">Použijte výchozí název pro typ ovládacího prvku, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7962a-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="7962a-120">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="7962a-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="7962a-121">Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.TextBox.Text%2A> nastavte hodnotu vlastnosti na **hostovaný obsah 2.** <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7962a-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7962a-122">Obecně byste měli hostovat propracovanější obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="7962a-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="7962a-123"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek slouží pouze pro ilustrativní účely.</span><span class="sxs-lookup"><span data-stu-id="7962a-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="7962a-124">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="7962a-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="7962a-125">Vybrat ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="7962a-125">Select WPF controls</span></span>

<span data-ttu-id="7962a-126"><xref:System.Windows.Forms.Integration.ElementHost> Ovládacímu prvku, který je již hostitelem obsahu, můžete přiřadit jiný obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="7962a-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="7962a-127">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="7962a-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="7962a-128">Na **panelu nástrojů**poklikejte na `UserControl1` `UserControl1` vytvoření instance ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7962a-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="7962a-129">Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7962a-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="7962a-130">V panelu inteligentních značek pro `elementHost1`otevřete rozevírací seznam **Vybrat hostovaný obsah** .</span><span class="sxs-lookup"><span data-stu-id="7962a-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="7962a-131">V rozevíracím seznamu vyberte **UserControl2** .</span><span class="sxs-lookup"><span data-stu-id="7962a-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="7962a-132">Ovládací `elementHost1` prvek je nyní hostitelem instance `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="7962a-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="7962a-133">V okně **vlastnosti** potvrďte, že <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> vlastnost je nastavená na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="7962a-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="7962a-134">Ze **sady nástrojů**ve skupině **interoperability WPF** přetáhněte <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7962a-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="7962a-135">Výchozí název nového ovládacího prvku je `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="7962a-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="7962a-136">V panelu inteligentních značek pro `elementHost2`otevřete rozevírací seznam **Vybrat hostovaný obsah** .</span><span class="sxs-lookup"><span data-stu-id="7962a-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="7962a-137">V rozevíracím seznamu vyberte **UserControl1** .</span><span class="sxs-lookup"><span data-stu-id="7962a-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="7962a-138">Ovládací `elementHost2` prvek je nyní hostitelem instance `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="7962a-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="7962a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7962a-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7962a-140">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="7962a-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="7962a-141">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="7962a-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="7962a-142">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7962a-142">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
