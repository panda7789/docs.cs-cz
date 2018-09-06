---
title: 'Návod: Změna vlastností hostovaného prvku WPF během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: 15cab9266af5840aa4b37a62b71bd5010b7a859a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741017"
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="1e4ff-102">Návod: Změna vlastností hostovaného prvku WPF během návrhu</span><span class="sxs-lookup"><span data-stu-id="1e4ff-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="1e4ff-103">Tento návod ukazuje, jak změnit hodnoty vlastností ovládací prvek Windows Presentation Foundation (WPF), který je hostován ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="1e4ff-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="1e4ff-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1e4ff-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-105">Create the project.</span></span>  
  
-   <span data-ttu-id="1e4ff-106">Vytvoření ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="1e4ff-107">Hostování ovládacích prvků WPF na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="1e4ff-108">WPF Designer pro Visual Studio použijte ke změně hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e4ff-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1e4ff-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1e4ff-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1e4ff-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e4ff-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e4ff-112">Prerequisites</span></span>  
 <span data-ttu-id="1e4ff-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="1e4ff-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="1e4ff-114">.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="1e4ff-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="1e4ff-115">Creating the Project</span></span>  
 <span data-ttu-id="1e4ff-116">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e4ff-117">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="1e4ff-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="1e4ff-118">To create the project</span></span>  
  
-   <span data-ttu-id="1e4ff-119">Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="1e4ff-120">Vytvoření ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="1e4ff-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="1e4ff-121">Po přidání ovládacího prvku WPF do projektu, můžete je nastavit na formuláři.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="1e4ff-122">Chcete-li vytvořit ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="1e4ff-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="1e4ff-123">Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="1e4ff-124">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="1e4ff-125">Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="1e4ff-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="1e4ff-126">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="1e4ff-127">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="1e4ff-128">Změny hodnot vlastností ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="1e4ff-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="1e4ff-129"><xref:System.Windows.Forms.Integration.ElementHost> Inteligentních značek umožňuje snadno změnit vlastnosti z prostředí WPF obsahu pomocí Návrháře WPF.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="1e4ff-130">K hostování ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="1e4ff-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="1e4ff-131">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="1e4ff-132">V **nástrojů**v **uživatelské ovládací prvky WPF** kartu, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="1e4ff-133">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="1e4ff-134">V **ElementHost úlohy** panelu inteligentních značek, vyberte **upravit hostovaný obsah**.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="1e4ff-135">UserControl1.xaml se otevře v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="1e4ff-136">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Red`.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="1e4ff-137">Sestavte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="1e4ff-138">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="1e4ff-139">Instance `UserControl1` má červené na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1e4ff-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4ff-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e4ff-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="1e4ff-141">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1e4ff-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="1e4ff-142">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="1e4ff-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="1e4ff-143">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="1e4ff-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="1e4ff-144">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="1e4ff-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="1e4ff-145">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="1e4ff-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="1e4ff-146">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1e4ff-146">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
