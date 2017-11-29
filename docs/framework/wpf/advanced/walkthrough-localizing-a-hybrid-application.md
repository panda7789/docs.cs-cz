---
title: "Návod: Lokalizace hybridní aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e1425eafd0f1663aaf82185e0f32bf2a3bea509
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="d41d1-102">Návod: Lokalizace hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="d41d1-102">Walkthrough: Localizing a Hybrid Application</span></span>
<span data-ttu-id="d41d1-103">Tento návod ukazuje, jak k lokalizaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– na základě hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d41d1-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>  
  
 <span data-ttu-id="d41d1-104">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="d41d1-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d41d1-105">Vytváření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostitele projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>  
  
-   <span data-ttu-id="d41d1-106">Přidávání lokalizovatelný obsahu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-106">Adding localizable content.</span></span>  
  
-   <span data-ttu-id="d41d1-107">Povolení lokalizace.</span><span class="sxs-lookup"><span data-stu-id="d41d1-107">Enabling localization.</span></span>  
  
-   <span data-ttu-id="d41d1-108">Přiřazení identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="d41d1-108">Assigning resource identifiers.</span></span>  
  
-   <span data-ttu-id="d41d1-109">Pomocí nástroje LocBaml k vytvoření satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d41d1-109">Using the LocBaml tool to produce a satellite assembly.</span></span>  
  
 <span data-ttu-id="d41d1-110">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [lokalizace ukázku hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="d41d1-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=160015).</span></span>  
  
 <span data-ttu-id="d41d1-111">Jakmile budete hotovi, budete mít lokalizované hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d41d1-111">When you are finished, you will have a localized hybrid application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d41d1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d41d1-112">Prerequisites</span></span>  
 <span data-ttu-id="d41d1-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="d41d1-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="d41d1-114">.</span><span class="sxs-lookup"><span data-stu-id="d41d1-114">.</span></span>  
  
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="d41d1-115">Vytváření projektu hostitele Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d41d1-115">Creating the Windows Forms Host Project</span></span>  
 <span data-ttu-id="d41d1-116">Prvním krokem je vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace projekt a přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element s obsahem, který bude lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="d41d1-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="d41d1-117">Vytvoření projektu hostitele</span><span class="sxs-lookup"><span data-stu-id="d41d1-117">To create the host project</span></span>  
  
1.  <span data-ttu-id="d41d1-118">Vytvořte projekt aplikace WPF s názvem `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-118">Create a WPF Application project named `LocalizingWpfInWf`.</span></span> <span data-ttu-id="d41d1-119">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="d41d1-119">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="d41d1-120">Přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek s názvem `SimpleControl` do projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>  
  
3.  <span data-ttu-id="d41d1-121">Použití <xref:System.Windows.Forms.Integration.ElementHost> řízení umístit `SimpleControl` prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="d41d1-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="d41d1-122">Další informace najdete v tématu [návod: hostování 3D složených prvků grafického subsystému WPF v rozhraní Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d41d1-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>  
  
## <a name="adding-localizable-content"></a><span data-ttu-id="d41d1-123">Přidávání lokalizovatelný obsahu</span><span class="sxs-lookup"><span data-stu-id="d41d1-123">Adding Localizable Content</span></span>  
 <span data-ttu-id="d41d1-124">V dalším kroku přidáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] popisku ovládacího prvku a nastavte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu elementu lokalizovatelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d41d1-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>  
  
#### <a name="to-add-localizable-content"></a><span data-ttu-id="d41d1-125">Přidání možnosti lokalizace obsahu</span><span class="sxs-lookup"><span data-stu-id="d41d1-125">To add localizable content</span></span>  
  
1.  <span data-ttu-id="d41d1-126">V Průzkumníku řešení klikněte dvakrát na **SimpleControl.xaml** otevřít v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d41d1-126">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="d41d1-127">Nastavit obsah <xref:System.Windows.Controls.Button> řízení pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  <span data-ttu-id="d41d1-128">V Průzkumníku řešení klikněte dvakrát na **Form1** a otevře se v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="d41d1-128">In Solution Explorer, double-click **Form1** to open it in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="d41d1-129">Otevřete panel a dvakrát klikněte na **popisek** přidání ovládacího prvku popisek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d41d1-129">Open the Toolbox and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="d41d1-130">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>  
  
5.  <span data-ttu-id="d41d1-131">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d41d1-131">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="d41d1-132">Obě `SimpleControl` elementu a ovládací prvek popisek zobrazit text **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>  
  
## <a name="enabling-localization"></a><span data-ttu-id="d41d1-133">Povolení lokalizace</span><span class="sxs-lookup"><span data-stu-id="d41d1-133">Enabling Localization</span></span>  
 <span data-ttu-id="d41d1-134">Návrhář formulářů Windows poskytuje nastavení pro povolení lokalizace v satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d41d1-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>  
  
#### <a name="to-enable-localization"></a><span data-ttu-id="d41d1-135">Chcete-li povolit lokalizace</span><span class="sxs-lookup"><span data-stu-id="d41d1-135">To enable localization</span></span>  
  
1.  <span data-ttu-id="d41d1-136">V Průzkumníku řešení klikněte dvakrát na **Form1.cs** a otevře se v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="d41d1-136">In Solution Explorer, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d41d1-137">V okně vlastnosti nastavit hodnotu formuláře **Localizable** vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-137">In the Properties window, set the value of the form's **Localizable** property to `true`.</span></span>  
  
3.  <span data-ttu-id="d41d1-138">V okně vlastností nastavte hodnotu **jazyk** vlastnost **Španělština (Španělsko)**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-138">In the Properties window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>  
  
4.  <span data-ttu-id="d41d1-139">V Návrháři formulářů Windows vyberte ovládací prvek popisek.</span><span class="sxs-lookup"><span data-stu-id="d41d1-139">In the Windows Forms Designer, select the label control.</span></span>  
  
5.  <span data-ttu-id="d41d1-140">V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-140">In the Properties window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>  
  
     <span data-ttu-id="d41d1-141">Nový soubor prostředků s názvem Form1.es ES.resx se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>  
  
6.  <span data-ttu-id="d41d1-142">V Průzkumníku řešení klikněte pravým tlačítkem na **Form1.cs** a klikněte na tlačítko **kód zobrazení** a otevře se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-142">In Solution Explorer, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>  
  
7.  <span data-ttu-id="d41d1-143">Zkopírujte následující kód do `Form1` konstruktoru, předchozích volání `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  <span data-ttu-id="d41d1-144">V Průzkumníku řešení klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-144">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>  
  
     <span data-ttu-id="d41d1-145">Označený název projektu **(není k dispozici)**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-145">The project name is labeled **(unavailable)**.</span></span>  
  
9. <span data-ttu-id="d41d1-146">Klikněte pravým tlačítkem na **LocalizingWpfInWf**a klikněte na tlačítko **upravit LocalizingWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>  
  
     <span data-ttu-id="d41d1-147">Soubor projektu se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-147">The project file opens in the Code Editor.</span></span>  
  
10. <span data-ttu-id="d41d1-148">Zkopírujte následující řádek do první `PropertyGroup` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. <span data-ttu-id="d41d1-149">Uložte soubor projektu a zavřete ho.</span><span class="sxs-lookup"><span data-stu-id="d41d1-149">Save the project file and close it.</span></span>  
  
12. <span data-ttu-id="d41d1-150">V Průzkumníku řešení klikněte pravým tlačítkem na **LocalizingWpfInWf** a klikněte na tlačítko **znovu načíst projekt**.</span><span class="sxs-lookup"><span data-stu-id="d41d1-150">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>  
  
## <a name="assigning-resource-identifiers"></a><span data-ttu-id="d41d1-151">Přiřazení identifikátory prostředků</span><span class="sxs-lookup"><span data-stu-id="d41d1-151">Assigning Resource Identifiers</span></span>  
 <span data-ttu-id="d41d1-152">Lokalizovatelný obsah můžete namapovat k sestavení prostředků pomocí identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="d41d1-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="d41d1-153">Když zadáte MsBuild.exe aplikace automaticky přiřadí identifikátory prostředků `updateuid` možnost.</span><span class="sxs-lookup"><span data-stu-id="d41d1-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>  
  
#### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="d41d1-154">Přiřadit identifikátory prostředků</span><span class="sxs-lookup"><span data-stu-id="d41d1-154">To assign resource identifiers</span></span>  
  
1.  <span data-ttu-id="d41d1-155">Z nabídky Start otevřít [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d41d1-155">From the Start Menu, open the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="d41d1-156">Pomocí následujícího příkazu přiřaďte lokalizovatelný obsah identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="d41d1-156">Use the following command to assign resource identifiers to your localizable content.</span></span>  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  <span data-ttu-id="d41d1-157">V Průzkumníku řešení klikněte dvakrát na **SimpleControl.xaml** a otevře se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-157">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="d41d1-158">Zobrazí se `msbuild` příkaz přidala `Uid` atribut všechny elementy.</span><span class="sxs-lookup"><span data-stu-id="d41d1-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="d41d1-159">To usnadňuje lokalizaci pomocí přidělování identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="d41d1-159">This facilitates localization through the assignment of resource identifiers.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  <span data-ttu-id="d41d1-160">Stiskněte klávesu F6 sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="d41d1-160">Press F6 to build the solution.</span></span>  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="d41d1-161">Pomocí LocBaml k vytvoření satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="d41d1-161">Using LocBaml to Produce a Satellite Assembly</span></span>  
 <span data-ttu-id="d41d1-162">Lokalizovaný obsah uložený v jen prostředků *satelitní sestavení*.</span><span class="sxs-lookup"><span data-stu-id="d41d1-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="d41d1-163">Pomocí nástroje příkazového řádku LocBaml.exe k vytvoření lokalizované sestavení pro vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="d41d1-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  
  
#### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="d41d1-164">K vytvoření satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="d41d1-164">To produce a satellite assembly</span></span>  
  
1.  <span data-ttu-id="d41d1-165">Zkopírujte LocBaml.exe do složky obj\Debug vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="d41d1-166">Další informace najdete v tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="d41d1-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>  
  
2.  <span data-ttu-id="d41d1-167">V okně příkazového řádku použijte následující příkaz k extrakci řetězce prostředků do dočasného souboru.</span><span class="sxs-lookup"><span data-stu-id="d41d1-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  <span data-ttu-id="d41d1-168">Otevřete soubor temp.csv s [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] nebo jiném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="d41d1-168">Open the temp.csv file with [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] or another text editor.</span></span> <span data-ttu-id="d41d1-169">Nahraďte řetězec `"Hello"` s jeho španělské překlad `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="d41d1-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>  
  
4.  <span data-ttu-id="d41d1-170">Uložte soubor temp.csv.</span><span class="sxs-lookup"><span data-stu-id="d41d1-170">Save the temp.csv file.</span></span>  
  
5.  <span data-ttu-id="d41d1-171">Pomocí následujícího příkazu vygenerujte soubor lokalizovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="d41d1-171">Use the following command to generate the localized resource file.</span></span>  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     <span data-ttu-id="d41d1-172">Soubor LocalizingWpfInWf.g.es ES.resources se vytvoří ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="d41d1-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>  
  
6.  <span data-ttu-id="d41d1-173">Použijte následující příkaz k vytvoření lokalizované satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d41d1-173">Use the following command to build the localized satellite assembly.</span></span>  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     <span data-ttu-id="d41d1-174">Soubor LocalizingWpfInWf.resources.dll se vytvoří ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="d41d1-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>  
  
7.  <span data-ttu-id="d41d1-175">Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky bin\Debug\es ES projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="d41d1-176">Nahraďte existující soubor.</span><span class="sxs-lookup"><span data-stu-id="d41d1-176">Replace the existing file.</span></span>  
  
8.  <span data-ttu-id="d41d1-177">Spusťte LocalizingWpfInWf.exe, který je umístěný ve složce bin\Debug vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="d41d1-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="d41d1-178">Znovu sestavit aplikaci nebo satelitní sestavení budou přepsány.</span><span class="sxs-lookup"><span data-stu-id="d41d1-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>  
  
     <span data-ttu-id="d41d1-179">Aplikace obsahuje lokalizované řetězce místo anglické řetězce.</span><span class="sxs-lookup"><span data-stu-id="d41d1-179">The application shows the localized strings instead of the English strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41d1-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="d41d1-180">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d41d1-181">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="d41d1-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [<span data-ttu-id="d41d1-182">Návod: Lokalizace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d41d1-182">Walkthrough: Localizing Windows Forms</span></span>](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [<span data-ttu-id="d41d1-183">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="d41d1-183">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
