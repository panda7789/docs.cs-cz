---
title: Hostování ovládacího prvku model Windows Forms v subsystému WPF pomocí jazyka XAML
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 2c5764ac2dfd9f5747087cc76e3971c002f12b90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794190"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="d3ae2-102">Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML</span><span class="sxs-lookup"><span data-stu-id="d3ae2-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="d3ae2-103">poskytuje mnoho ovládacích prvků s bohatou sadou funkcí.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="d3ae2-104">Někdy ale můžete chtít použít model Windows Forms ovládací prvky na stránkách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3ae2-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="d3ae2-105">Například můžete mít významnou investici do stávajících model Windows Formsch ovládacích prvků, nebo můžete mít ovládací prvek model Windows Forms, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="d3ae2-106">V tomto návodu se dozvíte, jak hostovat model Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládacím prvku na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránce pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3ae2-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="d3ae2-107">Úplný výpis kódu úloh uvedených v tomto návodu naleznete v tématu [hostování ovládacího prvku model Windows Forms v prostředí WPF pomocí ukázky XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="d3ae2-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="d3ae2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3ae2-108">Prerequisites</span></span>  

<span data-ttu-id="d3ae2-109">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="d3ae2-110">Hostování ovládacího prvku model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3ae2-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="d3ae2-111">Hostování ovládacího prvku ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d3ae2-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="d3ae2-112">Vytvořte projekt aplikace WPF s názvem `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="d3ae2-113">Přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="d3ae2-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="d3ae2-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="d3ae2-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="d3ae2-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="d3ae2-116">Otevřete MainWindow. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="d3ae2-117">V elementu <xref:System.Windows.Window> přidejte následující mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="d3ae2-118">Mapování oboru názvů `wf` vytvoří odkaz na sestavení, které obsahuje ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="d3ae2-119">Do elementu <xref:System.Windows.Controls.Grid> přidejte následující XAML.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="d3ae2-120"><xref:System.Windows.Forms.MaskedTextBox> ovládací prvek je vytvořen jako podřízený ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="d3ae2-121">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d3ae2-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ae2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3ae2-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d3ae2-123">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3ae2-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="d3ae2-124">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="d3ae2-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="d3ae2-125">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="d3ae2-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="d3ae2-126">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3ae2-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="d3ae2-127">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="d3ae2-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="d3ae2-128">Hostování ovládacího prvku model Windows Forms v subsystému WPF pomocí ukázky XAML</span><span class="sxs-lookup"><span data-stu-id="d3ae2-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
