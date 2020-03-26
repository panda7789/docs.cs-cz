---
title: 'Návod: Lokalizace hybridní aplikace'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111111"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="dd2ea-102">Návod: Lokalizace hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="dd2ea-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="dd2ea-103">Tento návod ukazuje, jak lokalizovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky v hybridní aplikaci založené na formulářích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="dd2ea-104">Mezi úkoly znázorněné v tomto návodu patří:</span><span class="sxs-lookup"><span data-stu-id="dd2ea-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="dd2ea-105">Vytvoření hostitelského projektu windows forms.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="dd2ea-106">Přidání lokalizovatelného obsahu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-106">Adding localizable content.</span></span>

- <span data-ttu-id="dd2ea-107">Povolení lokalizace.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-107">Enabling localization.</span></span>

- <span data-ttu-id="dd2ea-108">Přiřazení identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="dd2ea-109">Použití nástroje LocBaml k vytvoření satelitní sestavy.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="dd2ea-110">Úplný seznam kódu úkolů znázorněných v tomto návodu naleznete v [tématu Lokalizace ukázky hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="dd2ea-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="dd2ea-111">Po dokončení budete mít lokalizované hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd2ea-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd2ea-112">Prerequisites</span></span>

<span data-ttu-id="dd2ea-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="dd2ea-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="dd2ea-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dd2ea-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="dd2ea-115">Vytvoření hostitelského projektu formulářů Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dd2ea-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="dd2ea-116">Prvním krokem je vytvoření projektu aplikace Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms a přidání prvku s obsahem, který budete lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="dd2ea-117">Vytvoření hostitelského projektu</span><span class="sxs-lookup"><span data-stu-id="dd2ea-117">To create the host project</span></span>

1. <span data-ttu-id="dd2ea-118">Vytvořte projekt aplikace `LocalizingWpfInWf` **WPF** s názvem .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="dd2ea-119">(File**New** > **New** > **Project** > **Visual C#** nebo Visual **Basic** > **Classic Desktop** > **WPF Application**).</span><span class="sxs-lookup"><span data-stu-id="dd2ea-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="dd2ea-120">Přidejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> prvek `SimpleControl` volaný do projektu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="dd2ea-121">Pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku `SimpleControl` umístěte prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="dd2ea-122">Další informace naleznete [v tématu Návod: Hostování kompozitního ovládacího prvku 3D WPF ve formulářích systému Windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dd2ea-122">For more information, see [Walkthrough: Hosting a 3D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="dd2ea-123">Přidání lokalizovatelného obsahu</span><span class="sxs-lookup"><span data-stu-id="dd2ea-123">Adding Localizable Content</span></span>

<span data-ttu-id="dd2ea-124">Dále přidáte ovládací prvek popisku formuláře [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému Windows a nastavíte obsah prvku na lokalizovatelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="dd2ea-125">Přidání lokalizovatelného obsahu</span><span class="sxs-lookup"><span data-stu-id="dd2ea-125">To add localizable content</span></span>

1. <span data-ttu-id="dd2ea-126">V **Průzkumníku řešení**poklepejte na **soubor SimpleControl.xaml** a otevřete jej v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="dd2ea-127">Nastavte obsah ovládacího <xref:System.Windows.Controls.Button> prvku pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="dd2ea-128">V **Průzkumníku řešení**poklepejte na **Formulář1** a otevřete jej v Návrháři formulářů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="dd2ea-129">Otevřete **panel nástrojů** a poklepáním na **Popisek** přidejte do formuláře ovládací prvek popisku.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="dd2ea-130">Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> její `"Hello"`vlastnosti na .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="dd2ea-131">Stisknutím **klávesy F5** vytvořte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="dd2ea-132">`SimpleControl` Prvek i ovládací prvek popisku zobrazují text **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="dd2ea-133">Povolení lokalizace</span><span class="sxs-lookup"><span data-stu-id="dd2ea-133">Enabling Localization</span></span>

<span data-ttu-id="dd2ea-134">Návrhář formulářů systému Windows poskytuje nastavení pro povolení lokalizace v satelitním sestavení.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="dd2ea-135">Povolení lokalizace</span><span class="sxs-lookup"><span data-stu-id="dd2ea-135">To enable localization</span></span>

1. <span data-ttu-id="dd2ea-136">V **Průzkumníku řešení**poklepejte na **Form1.cs** a otevřete jej v Návrháři formulářů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="dd2ea-137">V okně **Vlastnosti** nastavte hodnotu **lokalizovatelné vlastnosti** formuláře na `true`.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="dd2ea-138">V okně **Vlastnosti** nastavte hodnotu **Language** vlastnost **španělština (Španělsko)**.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="dd2ea-139">V Návrháři formulářů systému Windows vyberte ovládací prvek popisků.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="dd2ea-140">V okně **Vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> `"Hola"`vlastnosti na .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="dd2ea-141">Do projektu je přidán nový soubor prostředků s názvem Form1.es-ES.resx.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="dd2ea-142">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na **Form1.cs** a kliknutím na **Zobrazit kód** jej otevřete v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="dd2ea-143">Zkopírujte následující kód `Form1` do konstruktoru před `InitializeComponent`voláním .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="dd2ea-144">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku LocalizingWpfInWf** a klepněte na příkaz **Uvolnit projekt**.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="dd2ea-145">Název projektu je označen **(není k dispozici).**</span><span class="sxs-lookup"><span data-stu-id="dd2ea-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="dd2ea-146">Klepněte pravým tlačítkem myši na **localizingWpfInWf**a klepněte na příkaz **Upravit lokalizaciWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="dd2ea-147">Soubor projektu se otevře v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="dd2ea-148">Zkopírujte následující řádek `PropertyGroup` do prvního v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="dd2ea-149">Uložte soubor projektu a zavřete jej.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="dd2ea-150">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku LocalizingWpfInWf** a klepněte na příkaz **Znovu načíst projekt**.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="dd2ea-151">Přiřazení identifikátorů prostředků</span><span class="sxs-lookup"><span data-stu-id="dd2ea-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="dd2ea-152">Lokalizovatelný obsah můžete namapovat na sestavení prostředků pomocí identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="dd2ea-153">Aplikace MsBuild.exe automaticky přiřadí identifikátory prostředků, když zadáte `updateuid` možnost.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="dd2ea-154">Přiřazení identifikátorů prostředků</span><span class="sxs-lookup"><span data-stu-id="dd2ea-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="dd2ea-155">V nabídce Start otevřete příkazový řádek pro vývojáře pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="dd2ea-156">Pomocí následujícího příkazu přiřaďte identifikátory prostředků k lokalizovatelnému obsahu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="dd2ea-157">V **Průzkumníku řešení**poklepejte na **soubor SimpleControl.xaml** a otevřete jej v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="dd2ea-158">Uvidíte, že `msbuild` příkaz přidal `Uid` atribut do všech prvků.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="dd2ea-159">To usnadňuje lokalizaci prostřednictvím přiřazení identifikátorů prostředků.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="dd2ea-160">Stisknutím klávesy **F6** sestavíte řešení.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="dd2ea-161">Použití LocBaml k vytvoření satelitní hospo-</span><span class="sxs-lookup"><span data-stu-id="dd2ea-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="dd2ea-162">Lokalizovaný obsah je uložen v *satelitním sestavení*pouze pro prostředky .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="dd2ea-163">Pomocí nástroje příkazového řádku LocBaml.exe můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizované sestavení pro váš obsah.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="dd2ea-164">Chcete-li vytvořit satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="dd2ea-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="dd2ea-165">Zkopírujte soubor LocBaml.exe do složky obj\Debug projektu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="dd2ea-166">Další informace naleznete v [tématu Localize aplikace](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="dd2ea-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="dd2ea-167">V okně příkazového řádku extrahujte řetězce prostředků do dočasného souboru pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="dd2ea-168">Otevřete soubor temp.csv pomocí sady Visual Studio nebo jiného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="dd2ea-169">Nahraďte `"Hello"` řetězec jeho `"Hola"`španělským překladem .</span><span class="sxs-lookup"><span data-stu-id="dd2ea-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="dd2ea-170">Uložte soubor temp.csv.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="dd2ea-171">Ke generování lokalizovaného souboru prostředků použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="dd2ea-172">Soubor LocalizingWpfInWf.g.es-ES.resources je vytvořen ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="dd2ea-173">K vytvoření lokalizovaného satelitního sestavení použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="dd2ea-174">Soubor LocalizingWpfInWf.resources.dll je vytvořen ve složce obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="dd2ea-175">Zkopírujte soubor LocalizingWpfInWf.resources.dll do složky bin\Debug\es.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="dd2ea-176">Nahraďte existující soubor.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-176">Replace the existing file.</span></span>

8. <span data-ttu-id="dd2ea-177">Spusťte soubor LocalizingWpfInWf.exe, který je umístěn ve složce bin\Ladění projektu.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="dd2ea-178">Neobnovovat aplikaci nebo satelitní sestavení bude přepsáno.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="dd2ea-179">Aplikace zobrazuje lokalizované řetězce namísto anglických řetězců.</span><span class="sxs-lookup"><span data-stu-id="dd2ea-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd2ea-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd2ea-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="dd2ea-181">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="dd2ea-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="dd2ea-182">[Návod: Lokalizace formulářů systému Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd2ea-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="dd2ea-183">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd2ea-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
