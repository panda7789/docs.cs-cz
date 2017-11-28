---
title: "Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="c33d1-102">Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c33d1-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="c33d1-103">Tento návod ukazuje, jak můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složené řízení a hostitele v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a formulářů pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c33d1-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="c33d1-104">V tomto návodu budete implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> obsahující dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c33d1-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="c33d1-105"><xref:System.Windows.Controls.UserControl> Zobrazí trojrozměrné kuželový (3D).</span><span class="sxs-lookup"><span data-stu-id="c33d1-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="c33d1-106">Vykreslování 3D objekty je mnohem snazší s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c33d1-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="c33d1-107">Proto má smysl hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> třídy za účelem vytvoření 3D grafiky ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c33d1-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="c33d1-108">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="c33d1-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="c33d1-109">Vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="c33d1-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="c33d1-110">Vytvoření projektu hostitele Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c33d1-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="c33d1-111">Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="c33d1-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="c33d1-112">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [hostování 3D WPF složeného ovládacího prvku Windows Forms ukázka](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="c33d1-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c33d1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c33d1-113">Prerequisites</span></span>  
 <span data-ttu-id="c33d1-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="c33d1-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="c33d1-115">.</span><span class="sxs-lookup"><span data-stu-id="c33d1-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="c33d1-116">Vytváření UserControl</span><span class="sxs-lookup"><span data-stu-id="c33d1-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="c33d1-117">Chcete-li vytvořit UserControl</span><span class="sxs-lookup"><span data-stu-id="c33d1-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="c33d1-118">Vytvoření projektu knihovny ovládacích prvků WPF uživatele s názvem `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="c33d1-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="c33d1-119">Otevřete UserControl1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c33d1-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="c33d1-120">Generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="c33d1-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="c33d1-121">Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> obsahující dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c33d1-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="c33d1-122">První podřízený ovládací prvek je <xref:System.Windows.Controls.Label?displayProperty=nameWithType> řízení; druhý je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazí 3D kuželový.</span><span class="sxs-lookup"><span data-stu-id="c33d1-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="c33d1-123">Vytváření projektu hostitele Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c33d1-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="c33d1-124">Vytvoření projektu hostitele</span><span class="sxs-lookup"><span data-stu-id="c33d1-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="c33d1-125">Přidejte projekt aplikace Windows s názvem `WpfUserControlHost` k řešení.</span><span class="sxs-lookup"><span data-stu-id="c33d1-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="c33d1-126">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="c33d1-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="c33d1-127">V Průzkumníku řešení přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="c33d1-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="c33d1-128">Přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:</span><span class="sxs-lookup"><span data-stu-id="c33d1-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="c33d1-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="c33d1-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="c33d1-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="c33d1-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="c33d1-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="c33d1-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="c33d1-132">Přidat odkaz na `HostingWpfUserControlInWf` projektu.</span><span class="sxs-lookup"><span data-stu-id="c33d1-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="c33d1-133">V Průzkumníku řešení, nastavte `WpfUserControlHost` projekt jako spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="c33d1-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="c33d1-134">Hostování Windows Presentation Foundation UserControl</span><span class="sxs-lookup"><span data-stu-id="c33d1-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="c33d1-135">K hostování UserControl</span><span class="sxs-lookup"><span data-stu-id="c33d1-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="c33d1-136">V Návrháři formulářů Windows otevřete Form1.</span><span class="sxs-lookup"><span data-stu-id="c33d1-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="c33d1-137">V okně vlastností klikněte na tlačítko **události**a dvakrát <xref:System.Windows.Forms.Form.Load> událostí k vytvoření obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c33d1-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="c33d1-138">Editor kódu otevře nově vygenerovaný `Form1_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c33d1-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="c33d1-139">Nahraďte kód v Form1.cs následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="c33d1-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="c33d1-140">`Form1_Load` Obslužné rutiny události vytvoří instanci `UserControl1` a přidá itto <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku kolekce podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c33d1-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="c33d1-141"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="c33d1-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="c33d1-142">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c33d1-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33d1-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="c33d1-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c33d1-144">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="c33d1-144">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="c33d1-145">Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c33d1-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="c33d1-146">Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c33d1-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="c33d1-147">Hostování složeného ovládacího prvku WPF ve Windows Forms – ukázka</span><span class="sxs-lookup"><span data-stu-id="c33d1-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
