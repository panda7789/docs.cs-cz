---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 281afad0c0de856ca67abc74c65aff0e7afc3e01
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976506"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="8ff9f-102">Návod: Lokalizace hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="8ff9f-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="8ff9f-103">V tomto návodu se dozvíte, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]hybridní aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="8ff9f-104">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="8ff9f-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="8ff9f-105">Vytváří se projekt hostitele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ff9f-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

- <span data-ttu-id="8ff9f-106">Přidává se Lokalizovatelný obsah.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-106">Adding localizable content.</span></span>

- <span data-ttu-id="8ff9f-107">Povoluje se lokalizace.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-107">Enabling localization.</span></span>

- <span data-ttu-id="8ff9f-108">Přiřazení identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="8ff9f-109">Použití nástroje LocBaml k vytvoření satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="8ff9f-110">Úplný výpis kódu úloh, které jsou znázorněné v tomto návodu, najdete v tématu [lokalizace ukázky hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="8ff9f-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="8ff9f-111">Po dokončení budete mít lokalizovanou hybridní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ff9f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ff9f-112">Prerequisites</span></span>

<span data-ttu-id="8ff9f-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="8ff9f-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="8ff9f-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8ff9f-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="8ff9f-115">Vytváří se projekt hostitele model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="8ff9f-116">Prvním krokem je vytvoření projektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace a přidání prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s obsahem, který budete lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="8ff9f-117">Vytvoření hostitelského projektu</span><span class="sxs-lookup"><span data-stu-id="8ff9f-117">To create the host project</span></span>

1. <span data-ttu-id="8ff9f-118">Vytvořte projekt **aplikace WPF** s názvem `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="8ff9f-119">(**Soubor** > **nové** > **projektu** > **vizuálu C#**  nebo **Visual Basic** > **klasické desktopové** > **WPF aplikace**).</span><span class="sxs-lookup"><span data-stu-id="8ff9f-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="8ff9f-120">Přidejte do projektu prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> s názvem `SimpleControl`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="8ff9f-121">Pomocí ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> umístěte `SimpleControl` prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="8ff9f-122">Další informace najdete v tématu [Návod: hostování složeného ovládacího prvku 3D WPF v model Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8ff9f-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="8ff9f-123">Přidávání Lokalizovatelnýho obsahu</span><span class="sxs-lookup"><span data-stu-id="8ff9f-123">Adding Localizable Content</span></span>

<span data-ttu-id="8ff9f-124">Dále přidáte ovládací prvek popisek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a nastavíte obsah elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na Lokalizovatelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="8ff9f-125">Přidání lokalizovatelné obsahu</span><span class="sxs-lookup"><span data-stu-id="8ff9f-125">To add localizable content</span></span>

1. <span data-ttu-id="8ff9f-126">V **Průzkumník řešení**poklikejte na **SimpleControl. XAML** a otevře se v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="8ff9f-127">Obsah ovládacího prvku <xref:System.Windows.Controls.Button> nastavte pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="8ff9f-128">V **Průzkumník řešení**dvakrát klikněte na **Form1** a otevřete ho v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="8ff9f-129">Otevřete **sadu nástrojů** a dvojitým kliknutím na položku **popisek** přidejte ovládací prvek popisek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="8ff9f-130">Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A> na `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="8ff9f-131">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="8ff9f-132">Prvek `SimpleControl` i ovládací prvek popisek zobrazí text **"Hello"** .</span><span class="sxs-lookup"><span data-stu-id="8ff9f-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="8ff9f-133">Povolení lokalizace</span><span class="sxs-lookup"><span data-stu-id="8ff9f-133">Enabling Localization</span></span>

<span data-ttu-id="8ff9f-134">Návrhář formulářů poskytuje nastavení pro povolení lokalizace v satelitním sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="8ff9f-135">Povolení lokalizace</span><span class="sxs-lookup"><span data-stu-id="8ff9f-135">To enable localization</span></span>

1. <span data-ttu-id="8ff9f-136">V **Průzkumník řešení**dvakrát klikněte na **Form1.cs** a otevřete ji v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="8ff9f-137">V okně **vlastnosti** nastavte hodnotu vlastnosti **localize** formuláře na `true`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="8ff9f-138">V okně **vlastnosti** nastavte hodnotu vlastnosti **Language** na **španělština (Španělsko)** .</span><span class="sxs-lookup"><span data-stu-id="8ff9f-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="8ff9f-139">V Návrhář formulářů vyberte ovládací prvek popisek.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="8ff9f-140">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A> na `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="8ff9f-141">Do projektu se přidá nový soubor prostředků s názvem Form1.es-ES. resx.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="8ff9f-142">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a kliknutím na **Zobrazit kód** ho otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="8ff9f-143">Zkopírujte následující kód do konstruktoru `Form1` před voláním `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="8ff9f-144">V **Průzkumník řešení**klikněte pravým tlačítkem myši na **LocalizingWpfInWf** a klikněte na **Uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="8ff9f-145">Název projektu je označený **(není k dispozici)** .</span><span class="sxs-lookup"><span data-stu-id="8ff9f-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="8ff9f-146">Klikněte pravým tlačítkem na **LocalizingWpfInWf**a pak klikněte na **Upravit LocalizingWpfInWf. csproj**.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="8ff9f-147">Soubor projektu se otevře v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="8ff9f-148">Zkopírujte následující řádek do prvního `PropertyGroup` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="8ff9f-149">Uložte soubor projektu a zavřete ho.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="8ff9f-150">V **Průzkumník řešení**klikněte pravým tlačítkem myši na **LocalizingWpfInWf** a klikněte na **znovu načíst projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="8ff9f-151">Přiřazení identifikátorů prostředků</span><span class="sxs-lookup"><span data-stu-id="8ff9f-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="8ff9f-152">Lokalizovatelné obsahy můžete mapovat na sestavení prostředků pomocí identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="8ff9f-153">Když zadáte možnost `updateuid`, aplikace MsBuild. exe automaticky přiřadí identifikátory prostředků.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="8ff9f-154">Přiřazení identifikátorů prostředků</span><span class="sxs-lookup"><span data-stu-id="8ff9f-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="8ff9f-155">V nabídce Start otevřete Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="8ff9f-156">K přiřazení identifikátorů prostředků k lokalizovatelnýmu obsahu použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="8ff9f-157">V **Průzkumník řešení**poklikejte na **SimpleControl. XAML** a otevře se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="8ff9f-158">Uvidíte, že příkaz `msbuild` přidal atribut `Uid` do všech prvků.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="8ff9f-159">To usnadňuje lokalizaci prostřednictvím přiřazení identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="8ff9f-160">Stisknutím klávesy **F6** Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="8ff9f-161">Použití LocBaml k vytvoření satelitního sestavení</span><span class="sxs-lookup"><span data-stu-id="8ff9f-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="8ff9f-162">Lokalizovaný obsah je uložený v *satelitním sestavení*pouze pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="8ff9f-163">Použijte nástroj příkazového řádku LocBaml. exe k vytvoření lokalizovaného sestavení pro váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="8ff9f-164">Vytvoření satelitního sestavení</span><span class="sxs-lookup"><span data-stu-id="8ff9f-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="8ff9f-165">Zkopírujte LocBaml. exe do složky obj\Debug vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="8ff9f-166">Další informace najdete v tématu [lokalizace aplikace](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="8ff9f-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="8ff9f-167">V okně příkazového řádku použijte následující příkaz k extrakci řetězců prostředků do dočasného souboru.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="8ff9f-168">Otevřete soubor Temp. csv pomocí sady Visual Studio nebo jiného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="8ff9f-169">Nahraďte řetězec `"Hello"` jeho španělským překladem `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="8ff9f-170">Uložte soubor Temp. csv.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="8ff9f-171">K vygenerování lokalizovaného souboru prostředků použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="8ff9f-172">Soubor LocalizingWpfInWf.g.es-ES. Resources se vytvoří ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="8ff9f-173">K sestavení lokalizovaného satelitního sestavení použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="8ff9f-174">Ve složce obj\Debug se vytvoří soubor LocalizingWpfInWf. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="8ff9f-175">Zkopírujte soubor LocalizingWpfInWf. Resources. dll do složky bin\Debug\es-ES projektu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="8ff9f-176">Nahraďte existující soubor.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-176">Replace the existing file.</span></span>

8. <span data-ttu-id="8ff9f-177">Spusťte LocalizingWpfInWf. exe, který je umístěný ve složce bin\Debug vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="8ff9f-178">Znovu sestavte aplikaci nebo satelitní sestavení bude přepsáno.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="8ff9f-179">Aplikace zobrazuje lokalizované řetězce místo anglických řetězců.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ff9f-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ff9f-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="8ff9f-181">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="8ff9f-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="8ff9f-182">[Návod: lokalizace model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ff9f-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="8ff9f-183">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ff9f-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
