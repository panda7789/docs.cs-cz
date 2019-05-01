---
title: 'Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 90d0e2f3c6ebab070809a4813c87da3539fd14f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032185"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="c6a3c-102">Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="c6a3c-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="c6a3c-103">poskytuje bohaté prostředí pro vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="c6a3c-104">Pokud však máte značné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být efektivnější opakovaně používat alespoň některé tohoto kódu v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace namísto jeho přepsání úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="c6a3c-105">Nejběžnější scénář je, pokud máte existující ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="c6a3c-106">V některých případech nemusí mít i přístup ke zdrojovému kódu pro tyto ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="c6a3c-107">poskytuje jednoduchý postup pro hostování těchto ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c6a3c-108">Například můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] u většiny vašich programování při hostování vaší specializované <xref:System.Windows.Forms.DataGridView> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="c6a3c-109">Tento názorný postup vás provede jednotlivými kroky, který je hostitelem složený ovládací prvek Windows Forms pro zadávání dat v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c6a3c-110">Složený ovládací prvek je zabalený ve knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="c6a3c-111">Tento obecný postup je možné rozšířit na složitější aplikace a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="c6a3c-112">Tento názorný postup je navržený jako téměř identické v vzhled a funkce, které [názorný postup: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c6a3c-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="c6a3c-113">Hlavní rozdíl je, že je obrácený scénáři hostování.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="c6a3c-114">Návod je rozdělen do dvou částí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="c6a3c-115">V první části stručně popisuje implementaci složeného ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="c6a3c-116">Druhá část podrobně probírají postupy hostování složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace přijímat události z ovládacího prvku a přístup k některé z vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="c6a3c-117">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="c6a3c-118">Implementace složeného ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="c6a3c-119">Implementace hostitelskou aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="c6a3c-120">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování Windows Forms složeného ovládacího prvku v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="c6a3c-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6a3c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6a3c-121">Prerequisites</span></span>  

<span data-ttu-id="c6a3c-122">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="c6a3c-123">Implementace složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6a3c-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="c6a3c-124">Složeného ovládacího prvku Windows Forms použitý v tomto příkladu je jednoduché zadávání dat formuláře.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="c6a3c-125">Tento formulář přebírá uživatelské jméno a adresa a pak se vraťte tyto informace do hostitele používá vlastní událost.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="c6a3c-126">Následující obrázek ukazuje ovládací prvek vykreslené.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="c6a3c-127">Následující obrázek ukazuje složeného ovládacího prvku formuláře Windows:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Snímek obrazovky, který ukazuje jednoduchý ovládací prvek Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="c6a3c-129">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c6a3c-129">Creating the Project</span></span>  
 <span data-ttu-id="c6a3c-130">Ke spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-130">To start the project:</span></span>  
  
1. <span data-ttu-id="c6a3c-131">Spuštění [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="c6a3c-132">V okně kategorii, vyberte **Knihovna ovládacích prvků Windows Forms** šablony.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="c6a3c-133">Název nového projektu `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="c6a3c-134">K umístění, zadejte jednoduše pojmenované složku nejvyšší úrovně, například `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="c6a3c-135">Hostitelská aplikace později, budou umístili do této složky.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="c6a3c-136">Klikněte na tlačítko **OK** pro vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-136">Click **OK** to create the project.</span></span> <span data-ttu-id="c6a3c-137">Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="c6a3c-138">V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="c6a3c-139">Váš projekt by měl zahrnovat odkazy na tyto systémové knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="c6a3c-140">Pokud některý z těchto knihoven DLL nejsou zahrnuty ve výchozím nastavení, můžete je přidáte do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="c6a3c-141">Systém</span><span class="sxs-lookup"><span data-stu-id="c6a3c-141">System</span></span>  
  
- <span data-ttu-id="c6a3c-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="c6a3c-142">System.Data</span></span>  
  
- <span data-ttu-id="c6a3c-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="c6a3c-143">System.Drawing</span></span>  
  
- <span data-ttu-id="c6a3c-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="c6a3c-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="c6a3c-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="c6a3c-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="c6a3c-146">Přidávání ovládacích prvků do formuláře</span><span class="sxs-lookup"><span data-stu-id="c6a3c-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="c6a3c-147">Chcete-li přidat ovládací prvky do formuláře:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="c6a3c-148">Otevřít `MyControl1` v návrháři.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="c6a3c-149">Přidat pět <xref:System.Windows.Forms.Label> ovládací prvky a jejich odpovídající <xref:System.Windows.Forms.TextBox> ovládací prvky, velikost a uspořádání stejně jako v předchozí ilustraci ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="c6a3c-150">V tomto příkladu <xref:System.Windows.Forms.TextBox> jsou pojmenovány ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="c6a3c-151">Přidejte dva <xref:System.Windows.Forms.Button> kontrolní prvky **OK** a **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="c6a3c-152">V tomto příkladu jsou názvy tlačítek `btnOK` a `btnCancel`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="c6a3c-153">Implementace podpůrný kód</span><span class="sxs-lookup"><span data-stu-id="c6a3c-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="c6a3c-154">Otevřete formulář v zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-154">Open the form in code view.</span></span> <span data-ttu-id="c6a3c-155">Ovládací prvek vrátí shromážděná data do svého hostitele vyvoláním vlastní `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="c6a3c-156">Data je obsažen v objektu argumentu události.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="c6a3c-157">Následující kód ukazuje deklaraci události a delegátem.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="c6a3c-158">Přidejte následující kód, který `MyControl1` třídy.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="c6a3c-159">`MyControlEventArgs` Třída obsahuje informace, který se má vrátit k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="c6a3c-160">Přidejte následující třídu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="c6a3c-161">Pokud uživatel klikne **OK** nebo **zrušit** tlačítko, <xref:System.Windows.Forms.Control.Click> vytvoření obslužné rutiny událostí `MyControlEventArgs` objekt, který obsahuje data a vyvolá `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="c6a3c-162">Jediný rozdíl mezi dvě obslužné rutiny je argument události `IsOK` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="c6a3c-163">Tato vlastnost umožňuje určit, které tlačítko došlo ke kliknutí na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="c6a3c-164">Je nastavený na `true` pro **OK** tlačítko, a `false` pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="c6a3c-165">Následující kód ukazuje dvě tlačítka obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="c6a3c-166">Přidejte následující kód, který `MyControl1` třídy.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="c6a3c-167">Poskytuje tak sestavení silným názvem a vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="c6a3c-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="c6a3c-168">Pro toto sestavení může odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="c6a3c-169">Chcete-li vytvořit silným názvem, vytvořit soubor klíče se Sn.exe a přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="c6a3c-170">Otevřít [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="c6a3c-171">Chcete-li tak učinit, klikněte na tlačítko **spustit** nabídky a pak vyberte **všechny programy nebo Microsoft Studio 2010 a Visual Studio Tools/Visual příkazový řádek Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="c6a3c-172">Otevře se okno konzoly s proměnnými přizpůsobené prostředí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="c6a3c-173">Na příkazovém řádku, použijte `cd` příkazu přejděte do složky vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="c6a3c-174">Generovat soubor s klíčem s názvem MyControls.snk spuštěním následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="c6a3c-175">Zahrnout soubor klíče ve vašem projektu, klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="c6a3c-176">V Návrháři projektu, klikněte na tlačítko **podepisování** kartu, vyberte **podepsat sestavení** zaškrtněte políčko a potom přejděte k vašemu souboru s klíčem.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="c6a3c-177">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-177">Build the solution.</span></span> <span data-ttu-id="c6a3c-178">Sestavení vytvoří knihovnu DLL s názvem MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="c6a3c-179">Implementace hostitele aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c6a3c-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="c6a3c-180">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostovat aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku na hostitele `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="c6a3c-181">Aplikace zpracovává `OnButtonClick` události přijímat data z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="c6a3c-182">Má také kolekce, která vám umožní změnit některé vlastnosti ovládacího prvku z přepínačů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c6a3c-183">Následující obrázek ukazuje dokončenou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="c6a3c-184">Následující obrázek ukazuje hotové aplikace včetně ovládací prvek vložený do aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Snímek obrazovky zobrazující ovládací prvek vložený na stránce WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="c6a3c-186">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c6a3c-186">Creating the Project</span></span>
 <span data-ttu-id="c6a3c-187">Ke spuštění projektu:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-187">To start the project:</span></span>

1. <span data-ttu-id="c6a3c-188">Otevřít [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a vyberte **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="c6a3c-189">V okně kategorii, vyberte **aplikace WPF** šablony.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="c6a3c-190">Název nového projektu `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="c6a3c-191">Pro umístění zadejte stejnou složku nejvyšší úrovně, obsahující projekt MyControls.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="c6a3c-192">Klikněte na tlačítko **OK** pro vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="c6a3c-193">Musíte také přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="c6a3c-194">Klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="c6a3c-195">Klikněte na tlačítko **Procházet** kartu a přejděte do složky, která obsahuje MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="c6a3c-196">V tomto návodu je této složky MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="c6a3c-197">Vyberte MyControls.dll a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="c6a3c-198">Přidáte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="c6a3c-199">Implementace základní rozložení</span><span class="sxs-lookup"><span data-stu-id="c6a3c-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="c6a3c-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hostitele je příslušná aplikace implementovaná v souboru MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="c6a3c-201">Tento soubor obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód, který definuje rozložení a hostuje ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="c6a3c-202">Aplikaci je rozdělené do tří oblastí:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="c6a3c-203">**Vlastností ovládacího prvku** panel, který obsahuje kolekci prvků přepínačů, můžete použít k úpravě různé vlastnosti objektu hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="c6a3c-204">**Dat z ovládacího prvku** panel, který obsahuje několik <xref:System.Windows.Controls.TextBlock> prvky, které zobrazují data vrácená z hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="c6a3c-205">Hostované samotný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-205">The hosted control itself.</span></span>

 <span data-ttu-id="c6a3c-206">Základní rozložení je znázorněno v následující XAML.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="c6a3c-207">Kód, který je nutný k hostiteli `MyControl1` vynecháte z tohoto příkladu, ale bude prodiskutována později.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="c6a3c-208">XAML v souboru MainWindow.xaml nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="c6a3c-209">Pokud používáte Visual Basic, změňte třídu `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="c6a3c-210">První <xref:System.Windows.Controls.StackPanel> prvek obsahuje několik sad <xref:System.Windows.Controls.RadioButton> ovládací prvky, které vám umožní změnit různé výchozí vlastnosti hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="c6a3c-211">Který je následován <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, které hostitele `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="c6a3c-212">Finální <xref:System.Windows.Controls.StackPanel> prvek obsahuje několik <xref:System.Windows.Controls.TextBlock> prvky, které zobrazují data, která je vrácena hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="c6a3c-213">Pořadí prvků a <xref:System.Windows.Controls.DockPanel.Dock%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení atributů vložit hostovaného ovládacího prvku do okna s žádné mezery ani narušení.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="c6a3c-214">Hostování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c6a3c-214">Hosting the Control</span></span>
 <span data-ttu-id="c6a3c-215">Následující upravená verze předchozího XAML se zaměřuje na prvky, které jsou potřeba k hostiteli `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="c6a3c-216">`xmlns` Vytvoří odkaz na atribut mapování oboru názvů `MyControls` obor názvů, který obsahuje hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="c6a3c-217">Toto mapování umožňuje představují `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="c6a3c-218">Dva prvky v XAML zpracování hostování:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="c6a3c-219">`WindowsFormsHost` představuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, který můžete použít k hostování ovládacího prvku Windows Forms v umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="c6a3c-220">`mcl:MyControl1`, která představuje `MyControl1`, se přidá do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené kolekce.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="c6a3c-221">V důsledku toho je tento ovládací prvek Windows Forms vykreslit jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna a může komunikovat s ovládacím prvkem z aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="c6a3c-222">Implementace souboru kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="c6a3c-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="c6a3c-223">Použití modelu code-behind souboru, soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs, obsahuje kód procedury, která implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="c6a3c-224">Primární úlohy jsou:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-224">The primary tasks are:</span></span>

- <span data-ttu-id="c6a3c-225">Připojení obslužnou rutinu události pro `MyControl1`společnosti `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="c6a3c-226">Úprava různé vlastnosti objektu `MyControl1`podle nastavení kolekce přepínačů.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="c6a3c-227">Zobrazení dat shromažďovaných ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="c6a3c-228">Inicializace aplikace</span><span class="sxs-lookup"><span data-stu-id="c6a3c-228">Initializing the Application</span></span>
 <span data-ttu-id="c6a3c-229">Inicializační kód je obsažen v obslužné rutině události pro okna <xref:System.Windows.FrameworkElement.Loaded> událostí a připojí obslužnou rutinu události ovládacího prvku `OnButtonClick` událostí.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="c6a3c-230">V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="c6a3c-231">Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] popsané dříve přidanými `MyControl1` k <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené elementu kolekce, můžete přetypovat <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> získat odkaz na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="c6a3c-232">Potom můžete tento odkaz připojte obslužné rutiny události pro `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="c6a3c-233">Kromě toho, že odkaz na tento ovládací prvek, <xref:System.Windows.Forms.Integration.WindowsFormsHost> vystavuje určitý počet vlastností ovládacího prvku, které můžete upravit z aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="c6a3c-234">Inicializační kód přiřadí tyto hodnoty privátní globálních proměnných pro pozdější použití v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="c6a3c-235">Takže můžete snadno přístup k typům v `MyControls` knihovny DLL, přidejte následující `Imports` nebo `using` příkaz do horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="c6a3c-236">Zpracování události OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="c6a3c-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="c6a3c-237">`MyControl1` Vyvolá `OnButtonClick` událost, když uživatel klikne na tlačítko buď z tlačítek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="c6a3c-238">Přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="c6a3c-239">Data do textových polí je zabalena do `MyControlEventArgs` objektu.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="c6a3c-240">Pokud uživatel klikne **OK** tlačítko, obslužná rutina události, extrahuje data a zobrazí jej v panelu níže `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="c6a3c-241">Úprava vlastností ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c6a3c-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="c6a3c-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zpřístupňuje řadu hostované ovládací prvek výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="c6a3c-243">V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby lépe odpovídaly styl vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="c6a3c-244">Sadu tlačítek možností v levém panelu povolit uživateli změnit několik vlastností barev a písma.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="c6a3c-245">Má obslužné rutiny pro každou sadu tlačítek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která zjistí tlačítko Možnosti uživatele a změní vlastnost odpovídající na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="c6a3c-246">Přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="c6a3c-247">Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-247">Build and run the application.</span></span> <span data-ttu-id="c6a3c-248">Přidejte nějaký text do složeného ovládacího prvku Windows Forms a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="c6a3c-249">Text se zobrazí v popiscích.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-249">The text appears in the labels.</span></span> <span data-ttu-id="c6a3c-250">Klikněte na různé přepínače a vidět její účinek na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a3c-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a3c-251">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6a3c-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c6a3c-252">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6a3c-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c6a3c-253">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c6a3c-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="c6a3c-254">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6a3c-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
