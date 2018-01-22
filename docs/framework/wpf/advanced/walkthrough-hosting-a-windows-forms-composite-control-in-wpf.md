---
title: "Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF"
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
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f332461bd5abb5e3fca705a8a5fd363c3d33296
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="fab63-102">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="fab63-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="fab63-103">poskytuje bohaté prostředí pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="fab63-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="fab63-104">Pokud však máte významné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být efektivnější opakovaně používat alespoň některé tento kód v vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace místo přepsání od začátku.</span><span class="sxs-lookup"><span data-stu-id="fab63-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="fab63-105">Nejběžnější scénáře je, pokud máte existující [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="fab63-105">The most common scenario is when you have existing [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] controls.</span></span> <span data-ttu-id="fab63-106">V některých případech nemusí mít ani přístup ke zdrojovému kódu pro tyto ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="fab63-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="fab63-107">Poskytuje přehledné postup pro hostování těchto ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="fab63-108">Například můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro většinu vaše programování při hostování vaší specializované <xref:System.Windows.Forms.DataGridView> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="fab63-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="fab63-109">Tento názorný postup vás provede jednotlivými kroky aplikace který je hostitelem [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] složeného ovládacího prvku k zadávání dat v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-109">This walkthrough steps you through an application that hosts a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="fab63-110">Knihovny DLL je součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="fab63-111">Tento postup Obecné lze rozšířit na složitější aplikace a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="fab63-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="fab63-112">Tento názorný postup je navržený jako téměř shodná v vzhled a funkce [návod: hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fab63-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="fab63-113">Základní rozdíl je, že je obrácený scénáři pro hostování.</span><span class="sxs-lookup"><span data-stu-id="fab63-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="fab63-114">Průvodce je rozdělené na dvě části.</span><span class="sxs-lookup"><span data-stu-id="fab63-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="fab63-115">V první části stručně popisuje provádění [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-115">The first section briefly describes the implementation of the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control.</span></span> <span data-ttu-id="fab63-116">Druhá část podrobně probírají řešení pro hostování složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, přijímat události z ovládacího prvku a získat přístup k některým vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="fab63-117">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="fab63-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="fab63-118">Implementace složeného ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fab63-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="fab63-119">Implementace hostitelskou aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="fab63-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="fab63-120">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [hostování ovládacího prvku Windows Forms složené v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="fab63-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fab63-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fab63-121">Prerequisites</span></span>  
 <span data-ttu-id="fab63-122">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="fab63-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="fab63-123">.</span><span class="sxs-lookup"><span data-stu-id="fab63-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="fab63-124">Implementace složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fab63-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="fab63-125">[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Složeného ovládacího prvku použité v tomto příkladu je jednoduchý zadávání dat formuláře.</span><span class="sxs-lookup"><span data-stu-id="fab63-125">The [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="fab63-126">Tento formulář přebírá uživatelské jméno a adresa a pak používá vlastní události vrátit tyto informace k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="fab63-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="fab63-127">Následující obrázek znázorňuje vykreslené ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="fab63-128">![Ovládací prvek Windows Forms jednoduché](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="fab63-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="fab63-129">Složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fab63-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="fab63-130">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fab63-130">Creating the Project</span></span>  
 <span data-ttu-id="fab63-131">Spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="fab63-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="fab63-132">Spusťte [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fab63-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="fab63-133">V okně kategorii, vyberte **knihovny ovládacích prvků Windows Forms** šablony.</span><span class="sxs-lookup"><span data-stu-id="fab63-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="fab63-134">Název nového projektu `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="fab63-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="fab63-135">K umístění, zadejte pohodlně složka s názvem nejvyšší úrovně, jako například `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="fab63-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="fab63-136">Později umístíte hostitelskou aplikaci v této složce.</span><span class="sxs-lookup"><span data-stu-id="fab63-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="fab63-137">Klikněte na tlačítko **OK** a vytvořte tak projekt.</span><span class="sxs-lookup"><span data-stu-id="fab63-137">Click **OK** to create the project.</span></span> <span data-ttu-id="fab63-138">Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="fab63-139">V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="fab63-140">Projekt by měl mít odkazy na následující systémové knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="fab63-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="fab63-141">Pokud některý z těchto knihoven DLL se ve výchozím nastavení neobsahuje, přidejte je do projektu.</span><span class="sxs-lookup"><span data-stu-id="fab63-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="fab63-142">Systém</span><span class="sxs-lookup"><span data-stu-id="fab63-142">System</span></span>  
  
-   <span data-ttu-id="fab63-143">System.Data</span><span class="sxs-lookup"><span data-stu-id="fab63-143">System.Data</span></span>  
  
-   <span data-ttu-id="fab63-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="fab63-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="fab63-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="fab63-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="fab63-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="fab63-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="fab63-147">Přidávání ovládacích prvků do formuláře</span><span class="sxs-lookup"><span data-stu-id="fab63-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="fab63-148">K přidávání ovládacích prvků formuláře:</span><span class="sxs-lookup"><span data-stu-id="fab63-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="fab63-149">Otevřete `MyControl1` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="fab63-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="fab63-150">Přidat pět <xref:System.Windows.Forms.Label> ovládací prvky a jejich odpovídajících <xref:System.Windows.Forms.TextBox> ovládací prvky, velikosti a uspořádané jako v předchozí ilustraci na formuláři.</span><span class="sxs-lookup"><span data-stu-id="fab63-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="fab63-151">V příkladu <xref:System.Windows.Forms.TextBox> jsou pojmenované ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="fab63-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="fab63-152">Přidejte dva <xref:System.Windows.Forms.Button> ovládací prvky s názvem bez přípony **OK** a **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="fab63-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="fab63-153">V příkladu jsou názvy tlačítko `btnOK` a `btnCancel`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fab63-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="fab63-154">Implementace podpůrné kódu</span><span class="sxs-lookup"><span data-stu-id="fab63-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="fab63-155">Otevřete formulář v zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="fab63-155">Open the form in code view.</span></span> <span data-ttu-id="fab63-156">Ovládací prvek vrátí shromážděná data do jeho hostitel zvýšením vlastní `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="fab63-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="fab63-157">Data jsou obsaženy v objektu argumentu události.</span><span class="sxs-lookup"><span data-stu-id="fab63-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="fab63-158">Následující kód ukazuje deklaraci události a delegáta.</span><span class="sxs-lookup"><span data-stu-id="fab63-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="fab63-159">Přidejte následující kód, který `MyControl1` třídy.</span><span class="sxs-lookup"><span data-stu-id="fab63-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="fab63-160">`MyControlEventArgs` Třída obsahuje informace, které mají být vráceny do hostitele.</span><span class="sxs-lookup"><span data-stu-id="fab63-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="fab63-161">Přidejte následující třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="fab63-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="fab63-162">Když uživatel klikne **OK** nebo **zrušit** tlačítko <xref:System.Windows.Forms.Control.Click> vytvoření obslužné rutiny událostí `MyControlEventArgs` objekt, který obsahuje data a vyvolá `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="fab63-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="fab63-163">Jediným rozdílem mezi dvě obslužné rutiny je argumentu události `IsOK` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fab63-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="fab63-164">Tato vlastnost umožňuje určit, které tlačítko bylo kliknuto hostiteli.</span><span class="sxs-lookup"><span data-stu-id="fab63-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="fab63-165">Je nastaven na hodnotu `true` pro **OK** tlačítko a `false` pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fab63-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="fab63-166">Následující kód ukazuje dva tlačítko obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="fab63-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="fab63-167">Přidejte následující kód, který `MyControl1` třídy.</span><span class="sxs-lookup"><span data-stu-id="fab63-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="fab63-168">Poskytnutí sestavení silným názvem a vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="fab63-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="fab63-169">Pro toto sestavení do odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, musí mít silným názvem.</span><span class="sxs-lookup"><span data-stu-id="fab63-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="fab63-170">Chcete-li vytvořit silným názvem, vytvořte soubor klíče s Sn.exe a přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="fab63-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="fab63-171">Otevřete [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fab63-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="fab63-172">Chcete-li to provést, klikněte na tlačítko **spustit** nabídce a potom vyberte **všechny programy nebo Microsoft Visual Studio 2010 nebo Visual Studio nástroje/Visual Studio – příkazový řádek**.</span><span class="sxs-lookup"><span data-stu-id="fab63-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="fab63-173">Spustí se do okna konzoly s proměnné přizpůsobené prostředí.</span><span class="sxs-lookup"><span data-stu-id="fab63-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="fab63-174">Na příkazovém řádku použít `cd` příkazu přejděte do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="fab63-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="fab63-175">Generovat soubor klíče s názvem MyControls.snk spuštěním následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="fab63-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="fab63-176">Zahrnout soubor klíče ve vašem projektu, klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fab63-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="fab63-177">V Návrháři projektu, klikněte na tlačítko **podpisování** vyberte **podepsání sestavení** zaškrtněte políčko a potom vyhledejte soubor s klíčem.</span><span class="sxs-lookup"><span data-stu-id="fab63-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="fab63-178">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="fab63-178">Build the solution.</span></span> <span data-ttu-id="fab63-179">Sestavení způsobí knihovny DLL s názvem MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="fab63-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="fab63-180">Implementace hostitelskou aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="fab63-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="fab63-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostitele používá aplikace <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení hostitele `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="fab63-182">Obslužné rutiny aplikace `OnButtonClick` událostí pro příjem dat z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="fab63-183">Je také kolekce tlačítek možností, které vám umožní změnit některé vlastnosti ovládacího prvku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="fab63-184">Následující obrázek znázorňuje dokončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="fab63-185">![Ovládací prvek vložený na stránce WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="fab63-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="fab63-186">Hotové aplikace zobrazuje ovládacího prvku vloženy do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="fab63-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="fab63-187">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="fab63-187">Creating the Project</span></span>  
 <span data-ttu-id="fab63-188">Spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="fab63-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="fab63-189">Otevřete [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a vyberte **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fab63-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="fab63-190">V okně kategorii, vyberte **aplikaci WPF** šablony.</span><span class="sxs-lookup"><span data-stu-id="fab63-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="fab63-191">Název nového projektu `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="fab63-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="fab63-192">K umístění zadejte stejné nejvyšší úrovně složku, která obsahuje MyControls projektu.</span><span class="sxs-lookup"><span data-stu-id="fab63-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="fab63-193">Klikněte na tlačítko **OK** a vytvořte tak projekt.</span><span class="sxs-lookup"><span data-stu-id="fab63-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="fab63-194">Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="fab63-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="fab63-195">Název projektu v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="fab63-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="fab63-196">Klikněte **Procházet** kartě a přejděte do složky, která obsahuje MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="fab63-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="fab63-197">V tomto návodu je této složky MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="fab63-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="fab63-198">Vyberte MyControls.dll a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fab63-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="fab63-199">Přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="fab63-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="fab63-200">Implementace základní rozložení</span><span class="sxs-lookup"><span data-stu-id="fab63-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="fab63-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hostitele aplikací je implementována ve MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fab63-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="fab63-202">Tento soubor obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód, který definuje rozložení a hostuje [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span> <span data-ttu-id="fab63-203">Aplikace je rozdělené do tří oblastí:</span><span class="sxs-lookup"><span data-stu-id="fab63-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="fab63-204">**– Vlastnosti ovládacích prvků** panel, který obsahuje kolekci přepínačů, který můžete použít k úpravě různé vlastnosti hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="fab63-205">**Dat z ovládacího prvku** panel, který obsahuje několik <xref:System.Windows.Controls.TextBlock> elementy, které zobrazují data vrácená z hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="fab63-206">Hostované samotném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="fab63-207">Základní rozložení se zobrazí v následujícím XAML.</span><span class="sxs-lookup"><span data-stu-id="fab63-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="fab63-208">Kód, který je nutný k hostiteli `MyControl1` v tomto příkladu vynecháte, ale bude probírat později.</span><span class="sxs-lookup"><span data-stu-id="fab63-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="fab63-209">Nahraďte XAML v MainWindow.xaml následující.</span><span class="sxs-lookup"><span data-stu-id="fab63-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="fab63-210">Pokud používáte Visual Basic, změňte třídu k `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="fab63-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="fab63-211">První <xref:System.Windows.Controls.StackPanel> element obsahuje několik sad <xref:System.Windows.Controls.RadioButton> ovládací prvky, které vám umožní změnit různé výchozí vlastnosti hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="fab63-212">Které následuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, které hostitele `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="fab63-213">Konečné <xref:System.Windows.Controls.StackPanel> element obsahuje několik <xref:System.Windows.Controls.TextBlock> elementy, které zobrazují data, která je vrácena hostované řízení.</span><span class="sxs-lookup"><span data-stu-id="fab63-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="fab63-214">Řazení elementů a <xref:System.Windows.Controls.DockPanel.Dock%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení atributů vložit hostovaného ovládacího prvku do okna s žádné mezery ani narušení.</span><span class="sxs-lookup"><span data-stu-id="fab63-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="fab63-215">Hostování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fab63-215">Hosting the Control</span></span>  
 <span data-ttu-id="fab63-216">Následující upravenou verzi předchozí XAML se zaměřuje na elementy, které jsou potřebné k hostiteli `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="fab63-217">`xmlns` Vytvoří odkaz na atribut mapování oboru názvů `MyControls` obor názvů, který obsahuje hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="fab63-218">Toto mapování umožňuje představují `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="fab63-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="fab63-219">Dva elementy v XAML zpracování, který je hostitelem:</span><span class="sxs-lookup"><span data-stu-id="fab63-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="fab63-220">`WindowsFormsHost`představuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, který vám umožňuje hostitele [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] řídit ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="fab63-221">`mcl:MyControl1`, které představuje `MyControl1`, je přidán do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="fab63-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="fab63-222">V důsledku toho to [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] vykreslení ovládacího prvku v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okno a může komunikovat s ovládacím prvkem z aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-222">As a result, this [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="fab63-223">Implementace souboru kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="fab63-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="fab63-224">Soubor modelu code-behind, MainWindow.xaml.vb nebo MainWindow.xaml.cs, obsahuje procedurální kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="fab63-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="fab63-225">Primární úlohy jsou:</span><span class="sxs-lookup"><span data-stu-id="fab63-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="fab63-226">Připojení obslužné rutiny události pro `MyControl1`na `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="fab63-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="fab63-227">Úprava vlastností různých `MyControl1`, závislosti na tom, jak jsou nastavené kolekci přepínačů.</span><span class="sxs-lookup"><span data-stu-id="fab63-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="fab63-228">Zobrazení dat shromažďovaných pomocí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fab63-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="fab63-229">Inicializace aplikace</span><span class="sxs-lookup"><span data-stu-id="fab63-229">Initializing the Application</span></span>  
 <span data-ttu-id="fab63-230">Inicializace kódu je součástí obslužné rutiny události pro okna <xref:System.Windows.FrameworkElement.Loaded> událostí a připojí obslužné rutiny události ovládacího prvku `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="fab63-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="fab63-231">V MainWindow.xaml.vb nebo MainWindow.xaml.cs, přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="fab63-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="fab63-232">Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] popsané dříve přidané `MyControl1` k <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené elementu kolekce, můžete převést <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> získat odkaz na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="fab63-233">Pak můžete tento odkaz připojit obslužné rutiny události pro `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="fab63-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="fab63-234">Kromě odkaz na tento ovládací prvek, <xref:System.Windows.Forms.Integration.WindowsFormsHost> vystavuje určitý počet vlastností ovládacího prvku, které můžete upravit z aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="fab63-235">Kód inicializace přiřadí tyto hodnoty privátní globálních proměnných pro pozdější použití v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fab63-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="fab63-236">Tak, aby měli snadný přístup typy v `MyControls` knihovny DLL, přidejte následující `Imports` nebo `using` příkaz do horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="fab63-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="fab63-237">Zpracování události OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="fab63-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="fab63-238">`MyControl1`Vyvolá `OnButtonClick` událost, když uživatel klikne na některý z ovládacího prvku tlačítka.</span><span class="sxs-lookup"><span data-stu-id="fab63-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="fab63-239">Přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="fab63-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="fab63-240">Data v textových polích je zabalit do `MyControlEventArgs` objektu.</span><span class="sxs-lookup"><span data-stu-id="fab63-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="fab63-241">Pokud uživatel klikne **OK** tlačítko, obslužné rutiny události extrahuje data a zobrazí v panelu níže `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="fab63-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="fab63-242">Úprava vlastností ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fab63-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="fab63-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zveřejňuje řadu hostované ovládacího prvku výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fab63-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="fab63-244">V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby lépe odpovídaly styl vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fab63-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="fab63-245">Sady tlačítek možností v levém panelu povolit uživatelům změnit několik vlastností barev a písem.</span><span class="sxs-lookup"><span data-stu-id="fab63-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="fab63-246">Má obslužná rutina pro každou sadu tlačítek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která zjišťuje uživatele možnost tlačítko Výběr a změní odpovídající vlastnost na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fab63-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="fab63-247">Přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="fab63-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="fab63-248">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fab63-248">Build and run the application.</span></span> <span data-ttu-id="fab63-249">Přidejte nějaký text složeného ovládacího prvku Windows Forms a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fab63-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="fab63-250">Text se zobrazí v štítky.</span><span class="sxs-lookup"><span data-stu-id="fab63-250">The text appears in the labels.</span></span> <span data-ttu-id="fab63-251">Klikněte na tlačítko různé přepínače zobrazíte vliv na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fab63-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab63-252">Viz také</span><span class="sxs-lookup"><span data-stu-id="fab63-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="fab63-253">WPF Designer</span><span class="sxs-lookup"><span data-stu-id="fab63-253">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="fab63-254">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="fab63-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="fab63-255">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fab63-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
