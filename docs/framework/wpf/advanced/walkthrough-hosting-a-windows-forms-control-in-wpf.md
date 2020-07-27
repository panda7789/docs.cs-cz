---
title: Hostování ovládacího prvku model Windows Forms v subsystému WPF
description: Naučte se hostovat ovládací prvky model Windows Forms v Windows Presentation Foundation, které už poskytují mnoho ovládacích prvků s bohatou sadou funkcí.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164974"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="dc873-103">Návod: Hostování ovládacího prvku Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="dc873-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="dc873-104">poskytuje mnoho ovládacích prvků s bohatou sadou funkcí.</span><span class="sxs-lookup"><span data-stu-id="dc873-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="dc873-105">V některých případech však můžete chtít použít model Windows Forms ovládací prvky na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránkách.</span><span class="sxs-lookup"><span data-stu-id="dc873-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="dc873-106">Například můžete mít významnou investici do stávajících model Windows Formsch ovládacích prvků, nebo můžete mít ovládací prvek model Windows Forms, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="dc873-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="dc873-107">V tomto návodu se dozvíte, jak hostovat <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládací prvek model Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránce pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="dc873-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="dc873-108">Úplný výpis kódu úloh uvedených v tomto návodu naleznete v tématu [hostování ovládacího prvku model Windows Forms v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="dc873-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc873-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc873-109">Prerequisites</span></span>

<span data-ttu-id="dc873-110">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc873-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="dc873-111">Hostování ovládacího prvku model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc873-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="dc873-112">Hostování ovládacího prvku ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dc873-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="dc873-113">Vytvořte projekt aplikace WPF s názvem `HostingWfInWpf` .</span><span class="sxs-lookup"><span data-stu-id="dc873-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="dc873-114">Přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="dc873-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="dc873-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="dc873-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="dc873-116">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="dc873-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="dc873-117">Otevřete MainWindow. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="dc873-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="dc873-118">Pojmenujte <xref:System.Windows.Controls.Grid> element `grid1` .</span><span class="sxs-lookup"><span data-stu-id="dc873-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="dc873-119">V zobrazení zobrazení Návrh nebo XAML vyberte <xref:System.Windows.Window> prvek.</span><span class="sxs-lookup"><span data-stu-id="dc873-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="dc873-120">V okno Vlastnosti klikněte na kartu **události** .</span><span class="sxs-lookup"><span data-stu-id="dc873-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="dc873-121">Dvakrát klikněte na <xref:System.Windows.FrameworkElement.Loaded> událost.</span><span class="sxs-lookup"><span data-stu-id="dc873-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="dc873-122">Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> události.</span><span class="sxs-lookup"><span data-stu-id="dc873-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="dc873-123">V horní části souboru přidejte následující `Imports` `using` příkaz nebo.</span><span class="sxs-lookup"><span data-stu-id="dc873-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="dc873-124">Stiskněte **F5**, aby se aplikace sestavila a spustila.</span><span class="sxs-lookup"><span data-stu-id="dc873-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc873-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc873-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="dc873-126">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc873-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="dc873-127">Návod: Hostování ovládacího prvku Windows Forms ve WPF pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="dc873-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="dc873-128">Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="dc873-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="dc873-129">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc873-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="dc873-130">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="dc873-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="dc873-131">Hostování ovládacího prvku model Windows Forms v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="dc873-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
