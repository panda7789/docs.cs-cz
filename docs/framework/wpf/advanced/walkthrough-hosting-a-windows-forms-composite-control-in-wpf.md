---
title: Hostování složeného ovládacího prvku model Windows Forms v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22eb323d1c1921832630d1d1b30463b4ecb7d1fd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794234"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="66739-102">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="66739-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="66739-103">poskytuje bohatou prostředí pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="66739-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="66739-104">Nicméně pokud máte významnou investici do model Windows Forms kódu, může být efektivnější znovu použít alespoň část kódu v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a nemusíte ho přepsat od nuly.</span><span class="sxs-lookup"><span data-stu-id="66739-104">However, when you have a substantial investment in Windows Forms code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="66739-105">Nejběžnějším scénářem je, když máte existující model Windows Forms ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="66739-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="66739-106">V některých případech nemusíte mít ani přístup ke zdrojovému kódu pro tyto ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="66739-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="66739-107">poskytuje jednoduchý postup pro hostování takových ovládacích prvků v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66739-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="66739-108">Můžete například použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro většinu programování a při hostování specializovaných <xref:System.Windows.Forms.DataGridView>ch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="66739-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="66739-109">Tento názorný postup vás provede aplikací, která je hostitelem model Windows Forms složeného ovládacího prvku pro provádění zadávání dat v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66739-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="66739-110">Složený ovládací prvek je zabalen v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="66739-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="66739-111">Tento obecný postup se dá rozšířit na složitější aplikace a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="66739-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="66739-112">Tento návod je téměř identický v zobrazení a funkcionalita pro [Návod: hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="66739-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="66739-113">Hlavním rozdílem je, že hostující scénář je obrácený.</span><span class="sxs-lookup"><span data-stu-id="66739-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="66739-114">Návod je rozdělen do dvou částí.</span><span class="sxs-lookup"><span data-stu-id="66739-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="66739-115">První část stručně popisuje implementaci složeného ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="66739-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="66739-116">Druhá část podrobně popisuje, jak hostovat složený ovládací prvek v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], přijímat události z ovládacího prvku a přistupovat k některým vlastnostem ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="66739-117">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="66739-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="66739-118">Implementace složeného ovládacího prvku model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66739-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="66739-119">Implementace hostitelské aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="66739-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="66739-120">Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete v tématu [hostování model Windows Forms složeného ovládacího prvku v UKÁZCE WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="66739-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66739-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66739-121">Prerequisites</span></span>  

<span data-ttu-id="66739-122">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66739-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="66739-123">Implementace složeného ovládacího prvku model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66739-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="66739-124">Model Windows Forms složený ovládací prvek použitý v tomto příkladu je jednoduchý formulář pro zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="66739-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="66739-125">Tento formulář přebírá jméno a adresu uživatele a pak používá vlastní událost k vrácení těchto informací hostiteli.</span><span class="sxs-lookup"><span data-stu-id="66739-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="66739-126">Následující ilustrace znázorňuje vykreslený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="66739-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="66739-127">Následující obrázek ukazuje model Windows Forms složený ovládací prvek:</span><span class="sxs-lookup"><span data-stu-id="66739-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Snímek obrazovky, který zobrazuje jednoduchý ovládací prvek model Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="66739-129">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="66739-129">Creating the Project</span></span>  
 <span data-ttu-id="66739-130">Spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="66739-130">To start the project:</span></span>  
  
1. <span data-ttu-id="66739-131">Spusťte Visual Studio a otevřete dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="66739-131">Launch Visual Studio, and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="66739-132">V kategorii okna vyberte šablonu **Knihovna ovládacích prvků model Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="66739-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="66739-133">Pojmenujte nový projekt `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="66739-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="66739-134">Pro umístění zadejte pohodlně pojmenovanou složku nejvyšší úrovně, například `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="66739-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="66739-135">Později vložíte hostitelskou aplikaci do této složky.</span><span class="sxs-lookup"><span data-stu-id="66739-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="66739-136">Kliknutím na tlačítko **OK** vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="66739-136">Click **OK** to create the project.</span></span> <span data-ttu-id="66739-137">Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="66739-138">V Průzkumník řešení přejmenujte `UserControl1` na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="66739-139">Projekt by měl mít odkazy na následující systémové knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="66739-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="66739-140">Pokud některá z těchto knihoven DLL není ve výchozím nastavení součástí, přidejte je do projektu.</span><span class="sxs-lookup"><span data-stu-id="66739-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="66739-141">Systém</span><span class="sxs-lookup"><span data-stu-id="66739-141">System</span></span>  
  
- <span data-ttu-id="66739-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="66739-142">System.Data</span></span>  
  
- <span data-ttu-id="66739-143">System. Drawing</span><span class="sxs-lookup"><span data-stu-id="66739-143">System.Drawing</span></span>  
  
- <span data-ttu-id="66739-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="66739-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="66739-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="66739-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="66739-146">Přidávání ovládacích prvků do formuláře</span><span class="sxs-lookup"><span data-stu-id="66739-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="66739-147">Chcete-li přidat ovládací prvky do formuláře:</span><span class="sxs-lookup"><span data-stu-id="66739-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="66739-148">Otevřete `MyControl1` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="66739-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="66739-149">Přidejte pět ovládacích prvků <xref:System.Windows.Forms.Label> a jejich odpovídající <xref:System.Windows.Forms.TextBox> ovládací prvky, velikost a uspořádání tak, jak jsou na předchozím obrázku, ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="66739-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="66739-150">V příkladu jsou ovládací prvky <xref:System.Windows.Forms.TextBox> pojmenovány:</span><span class="sxs-lookup"><span data-stu-id="66739-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="66739-151">Přidejte dva ovládací prvky <xref:System.Windows.Forms.Button> označené jako **OK** a **Zrušit**.</span><span class="sxs-lookup"><span data-stu-id="66739-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="66739-152">V příkladu jsou názvy tlačítek `btnOK` a `btnCancel`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="66739-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="66739-153">Implementace podpůrného kódu</span><span class="sxs-lookup"><span data-stu-id="66739-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="66739-154">Otevřete formulář v zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="66739-154">Open the form in code view.</span></span> <span data-ttu-id="66739-155">Ovládací prvek vrátí shromážděná data do hostitele tím, že vyvyvolává vlastní událost `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="66739-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="66739-156">Data jsou obsažena v objektu argumentu události.</span><span class="sxs-lookup"><span data-stu-id="66739-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="66739-157">Následující kód ukazuje deklaraci události a delegáta.</span><span class="sxs-lookup"><span data-stu-id="66739-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="66739-158">Do třídy `MyControl1` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66739-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="66739-159">Třída `MyControlEventArgs` obsahuje informace, které mají být vráceny do hostitele.</span><span class="sxs-lookup"><span data-stu-id="66739-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="66739-160">Do formuláře přidejte následující třídu.</span><span class="sxs-lookup"><span data-stu-id="66739-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="66739-161">Když uživatel klikne na tlačítko **OK** nebo **Storno** , obslužná rutina události <xref:System.Windows.Forms.Control.Click> vytvoří objekt `MyControlEventArgs`, který obsahuje data a vyvolá událost `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="66739-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="66739-162">Jediným rozdílem mezi těmito dvěma obslužnými rutinami je vlastnost `IsOK` argumentu události.</span><span class="sxs-lookup"><span data-stu-id="66739-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="66739-163">Tato vlastnost umožňuje hostiteli určit, na které tlačítko bylo kliknuto.</span><span class="sxs-lookup"><span data-stu-id="66739-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="66739-164">Pro tlačítko **OK** je nastaveno na `true` a `false` pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="66739-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="66739-165">Následující kód ukazuje dvě obslužné rutiny tlačítek.</span><span class="sxs-lookup"><span data-stu-id="66739-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="66739-166">Do třídy `MyControl1` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66739-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="66739-167">Předání sestavení silnému názvu a sestavení sestavení</span><span class="sxs-lookup"><span data-stu-id="66739-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="66739-168">Aby toto sestavení odkazovalo na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci, musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="66739-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="66739-169">Chcete-li vytvořit silný název, vytvořte soubor klíče s SN. exe a přidejte jej do projektu.</span><span class="sxs-lookup"><span data-stu-id="66739-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="66739-170">Otevřete příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66739-170">Open a Visual Studio command prompt.</span></span> <span data-ttu-id="66739-171">Provedete to tak, že kliknete na nabídku **Start** a pak vyberete **všechny programy/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span><span class="sxs-lookup"><span data-stu-id="66739-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="66739-172">Tím se spustí okno konzoly s přizpůsobenými proměnnými prostředí.</span><span class="sxs-lookup"><span data-stu-id="66739-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="66739-173">Na příkazovém řádku použijte příkaz `cd` pro přechod do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="66739-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="66739-174">Spuštěním následujícího příkazu vygenerujte soubor klíče s názvem MyControls. snk.</span><span class="sxs-lookup"><span data-stu-id="66739-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="66739-175">Chcete-li zahrnout soubor klíče do projektu, klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a potom klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="66739-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="66739-176">V Návrháři projektu klikněte na kartu **podepisování** , zaškrtněte políčko **podepsat sestavení** a potom přejděte k souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="66739-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="66739-177">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="66739-177">Build the solution.</span></span> <span data-ttu-id="66739-178">Sestavení vytvoří knihovnu DLL s názvem MyControls. dll.</span><span class="sxs-lookup"><span data-stu-id="66739-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="66739-179">Implementace hostitelské aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="66739-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="66739-180">Hostitelská aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> k hostování `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="66739-181">Aplikace zpracovává událost `OnButtonClick` pro příjem dat z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="66739-182">Má také kolekci přepínačů, které umožňují změnit některé z vlastností ovládacího prvku z aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66739-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="66739-183">Na následujícím obrázku je znázorněna dokončená aplikace.</span><span class="sxs-lookup"><span data-stu-id="66739-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="66739-184">Následující obrázek ukazuje kompletní aplikaci, včetně ovládacího prvku vloženého do aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="66739-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Snímek obrazovky, který zobrazuje ovládací prvek vložený na stránce WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="66739-186">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="66739-186">Creating the Project</span></span>
 <span data-ttu-id="66739-187">Spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="66739-187">To start the project:</span></span>

1. <span data-ttu-id="66739-188">Otevřete Visual Studio a vyberte **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="66739-188">Open Visual Studio, and select **New Project**.</span></span>

2. <span data-ttu-id="66739-189">V kategorii okna vyberte šablonu **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="66739-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="66739-190">Pojmenujte nový projekt `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="66739-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="66739-191">Pro umístění zadejte stejnou složku nejvyšší úrovně, která obsahuje projekt MyControls.</span><span class="sxs-lookup"><span data-stu-id="66739-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="66739-192">Kliknutím na tlačítko **OK** vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="66739-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="66739-193">Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a další sestavení.</span><span class="sxs-lookup"><span data-stu-id="66739-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="66739-194">Klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="66739-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="66739-195">Klikněte na kartu **Procházet** a přejděte do složky, která obsahuje MyControls. dll.</span><span class="sxs-lookup"><span data-stu-id="66739-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="66739-196">Pro tento návod je tato složka MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="66739-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="66739-197">Vyberte MyControls. dll a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="66739-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="66739-198">Přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="66739-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="66739-199">Implementace základního rozložení</span><span class="sxs-lookup"><span data-stu-id="66739-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="66739-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hostitelské aplikace je implementována v souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="66739-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="66739-201">Tento soubor obsahuje kód [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], který definuje rozložení a hostuje ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="66739-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="66739-202">Aplikace je rozdělená do tří oblastí:</span><span class="sxs-lookup"><span data-stu-id="66739-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="66739-203">Panel **vlastností ovládacího prvku** , který obsahuje kolekci přepínačů, které lze použít k úpravě různých vlastností hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="66739-204">**Data z ovládacích** panelů, která obsahují několik <xref:System.Windows.Controls.TextBlock> prvků, které zobrazují data vrácená z hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="66739-205">Samotný hostující ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="66739-205">The hosted control itself.</span></span>

 <span data-ttu-id="66739-206">Základní rozložení je znázorněno v následujícím kódu XAML.</span><span class="sxs-lookup"><span data-stu-id="66739-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="66739-207">Značky, které jsou potřebné pro hostování `MyControl1`, jsou v tomto příkladu vynechány, ale budou popsány později.</span><span class="sxs-lookup"><span data-stu-id="66739-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="66739-208">Nahraďte XAML v souboru MainWindow. XAML následujícím.</span><span class="sxs-lookup"><span data-stu-id="66739-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="66739-209">Pokud používáte Visual Basic, změňte třídu na `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="66739-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="66739-210">První prvek <xref:System.Windows.Controls.StackPanel> obsahuje několik sad <xref:System.Windows.Controls.RadioButton> ovládacích prvků, které umožňují upravit různé výchozí vlastnosti hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="66739-211">Následuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, který hostuje `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="66739-212">Konečný element <xref:System.Windows.Controls.StackPanel> obsahuje několik <xref:System.Windows.Controls.TextBlock> prvků, které zobrazují data, která jsou vrácena hostovaným ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="66739-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="66739-213">Pořadí prvků a nastavení atributu <xref:System.Windows.Controls.DockPanel.Dock%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vloží hostovaný ovládací prvek do okna bez mezer nebo zkreslení.</span><span class="sxs-lookup"><span data-stu-id="66739-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="66739-214">Hostování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="66739-214">Hosting the Control</span></span>
 <span data-ttu-id="66739-215">Následující upravená verze předchozího XAML se zaměřuje na prvky, které jsou potřeba pro hostování `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="66739-216">Atribut mapování oboru názvů `xmlns` vytvoří odkaz na obor názvů `MyControls`, který obsahuje hostovaný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="66739-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="66739-217">Toto mapování vám umožní znázornit `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="66739-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="66739-218">Dva prvky v jazyce XAML zpracovávají hostování:</span><span class="sxs-lookup"><span data-stu-id="66739-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="66739-219">`WindowsFormsHost` představuje prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>, který umožňuje hostovat ovládací prvek model Windows Forms v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66739-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="66739-220">`mcl:MyControl1`, která představuje `MyControl1`, je přidána do podřízené kolekce elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="66739-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="66739-221">V důsledku toho je tento ovládací prvek model Windows Forms vykreslen jako součást okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a můžete komunikovat s ovládacím prvkem z aplikace.</span><span class="sxs-lookup"><span data-stu-id="66739-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="66739-222">Implementace souboru kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="66739-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="66739-223">Soubor kódu na pozadí MainWindow. XAML. vb nebo MainWindow.xaml.cs obsahuje procedurální kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="66739-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="66739-224">Primární úlohy jsou:</span><span class="sxs-lookup"><span data-stu-id="66739-224">The primary tasks are:</span></span>

- <span data-ttu-id="66739-225">Připojení obslužné rutiny události k události `MyControl1``OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="66739-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="66739-226">Úprava různých vlastností `MyControl1`na základě toho, jak jsou nastaveny kolekce přepínačů.</span><span class="sxs-lookup"><span data-stu-id="66739-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="66739-227">Zobrazení dat shromažďovaných ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="66739-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="66739-228">Inicializuje se aplikace.</span><span class="sxs-lookup"><span data-stu-id="66739-228">Initializing the Application</span></span>
 <span data-ttu-id="66739-229">Inicializační kód je obsažen v obslužné rutině události pro událost <xref:System.Windows.FrameworkElement.Loaded> okna a připojí obslužnou rutinu události k události `OnButtonClick` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="66739-230">V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs přidejte následující kód do třídy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="66739-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="66739-231">Vzhledem k tomu, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] popsané dříve přidali `MyControl1` do kolekce podřízených elementů <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, můžete přetypovat <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> a získat odkaz na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="66739-232">Pak můžete použít tento odkaz k připojení obslužné rutiny události k `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="66739-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="66739-233">Kromě poskytnutí odkazu na samotný ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> zpřístupňuje řadu vlastností ovládacího prvku, které lze manipulovat z aplikace.</span><span class="sxs-lookup"><span data-stu-id="66739-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="66739-234">Inicializační kód přiřadí tyto hodnoty privátním globálním proměnným pro pozdější použití v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66739-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="66739-235">Aby bylo možné snadno přistupovat k typům v knihovně DLL `MyControls`, přidejte následující `Imports` nebo příkaz `using` na začátek souboru.</span><span class="sxs-lookup"><span data-stu-id="66739-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="66739-236">Zpracování události OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="66739-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="66739-237">`MyControl1` vyvolá událost `OnButtonClick`, když uživatel klikne na kterékoli z tlačítek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="66739-238">Do třídy `MainWindow` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66739-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="66739-239">Data v textových polích se zabalí do objektu `MyControlEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="66739-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="66739-240">Pokud uživatel klikne na tlačítko **OK** , obslužná rutina události extrahuje data a zobrazí je na panelu níže `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="66739-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="66739-241">Úprava vlastností ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="66739-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="66739-242">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zveřejňuje několik výchozích vlastností hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="66739-243">V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby odpovídal stylu vaší aplikace přesněji.</span><span class="sxs-lookup"><span data-stu-id="66739-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="66739-244">Sady přepínačů na levém panelu umožňují uživateli upravovat několik vlastností barev a písem.</span><span class="sxs-lookup"><span data-stu-id="66739-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="66739-245">Každá sada tlačítek obsahuje obslužnou rutinu pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, která detekuje výběr přepínačů uživatele a mění odpovídající vlastnost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="66739-246">Do třídy `MainWindow` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="66739-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="66739-247">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="66739-247">Build and run the application.</span></span> <span data-ttu-id="66739-248">Do složeného ovládacího prvku model Windows Forms přidejte nějaký text a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="66739-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="66739-249">Text se zobrazí v popiscích.</span><span class="sxs-lookup"><span data-stu-id="66739-249">The text appears in the labels.</span></span> <span data-ttu-id="66739-250">Kliknutím na jiné přepínače zobrazíte efekt na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="66739-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66739-251">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66739-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="66739-252">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66739-252">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="66739-253">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="66739-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="66739-254">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66739-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
