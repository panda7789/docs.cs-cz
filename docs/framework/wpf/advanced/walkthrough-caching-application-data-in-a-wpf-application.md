---
title: Ukládat data aplikací do mezipaměti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: b7d999f94e2f2ae410a16e537d51c0f890def4e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728057"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="753eb-102">Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="753eb-103">Ukládání do mezipaměti umožňuje ukládat data v paměti pro rychlý přístup.</span><span class="sxs-lookup"><span data-stu-id="753eb-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="753eb-104">Po opětovném přístup k datům mohou aplikace získat data z mezipaměti, nikoli načíst je z původního zdroje.</span><span class="sxs-lookup"><span data-stu-id="753eb-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="753eb-105">To může zvýšit výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="753eb-105">This can improve performance and scalability.</span></span> <span data-ttu-id="753eb-106">Ukládání do mezipaměti navíc zpřístupňuje data v případě, že zdroj dat není dočasně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="753eb-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="753eb-107">.NET Framework poskytuje třídy, které umožňují používat ukládání do mezipaměti v aplikacích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="753eb-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="753eb-108">Tyto třídy jsou umístěny v oboru názvů <xref:System.Runtime.Caching>.</span><span class="sxs-lookup"><span data-stu-id="753eb-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="753eb-109">Obor názvů <xref:System.Runtime.Caching> je v .NET Framework 4 nový.</span><span class="sxs-lookup"><span data-stu-id="753eb-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="753eb-110">Tento obor názvů zpřístupňuje ukládání do mezipaměti pro všechny .NET Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="753eb-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="753eb-111">V předchozích verzích .NET Framework bylo ukládání do mezipaměti k dispozici pouze v oboru názvů <xref:System.Web> a proto je vyžadována závislost na třídách ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="753eb-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="753eb-112">V tomto návodu se dozvíte, jak používat funkce ukládání do mezipaměti, které jsou k dispozici v .NET Framework jako součást [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="753eb-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="753eb-113">V tomto návodu ukládáte obsah textového souboru do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="753eb-114">Tento návod obsahuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="753eb-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="753eb-115">Vytvoření projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="753eb-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="753eb-116">Přidání odkazu na .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="753eb-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="753eb-117">Inicializuje se mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="753eb-117">Initializing a cache.</span></span>

- <span data-ttu-id="753eb-118">Přidání položky mezipaměti, která obsahuje obsah textového souboru.</span><span class="sxs-lookup"><span data-stu-id="753eb-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="753eb-119">Poskytnutí zásad vyřazení pro položku mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="753eb-120">Monitorování cesty k souboru uloženého v mezipaměti a oznamování instance mezipaměti o změnách monitorované položky.</span><span class="sxs-lookup"><span data-stu-id="753eb-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="753eb-121">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="753eb-121">Prerequisites</span></span>
 <span data-ttu-id="753eb-122">Aby bylo možné dokončit tento návod, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="753eb-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="753eb-123">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="753eb-123">Visual Studio 2010.</span></span>

- <span data-ttu-id="753eb-124">Textový soubor, který obsahuje malé množství textu.</span><span class="sxs-lookup"><span data-stu-id="753eb-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="753eb-125">(Obsah textového souboru se zobrazí v okně se zprávou.) Kód, který je znázorněn v návodu, předpokládá, že pracujete s následujícím souborem:</span><span class="sxs-lookup"><span data-stu-id="753eb-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="753eb-126">V tomto návodu ale můžete použít libovolný textový soubor a udělat drobné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="753eb-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="753eb-127">Vytvoření projektu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="753eb-128">Začnete vytvořením projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="753eb-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="753eb-129">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-129">To create a WPF application</span></span>

1. <span data-ttu-id="753eb-130">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="753eb-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="753eb-131">V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="753eb-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="753eb-132">Zobrazí se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="753eb-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="753eb-133">V části **Nainstalované šablony**vyberte programovací jazyk, který chcete použít (**Visual Basic** nebo **vizuál C#** ).</span><span class="sxs-lookup"><span data-stu-id="753eb-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="753eb-134">V dialogovém okně **Nový projekt** vyberte **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="753eb-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="753eb-135">Pokud nevidíte šablonu **aplikace WPF** , ujistěte se, že cílíte na verzi .NET Framework, která podporuje WPF.</span><span class="sxs-lookup"><span data-stu-id="753eb-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="753eb-136">V dialogovém okně **Nový projekt** vyberte ze seznamu položku .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="753eb-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="753eb-137">Do textového pole **název** zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="753eb-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="753eb-138">Můžete například zadat **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="753eb-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="753eb-139">Zaškrtněte políčko **vytvořit adresář pro řešení** .</span><span class="sxs-lookup"><span data-stu-id="753eb-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="753eb-140">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="753eb-140">Click **OK**.</span></span>

     <span data-ttu-id="753eb-141">Návrhář WPF se otevře v **návrhovém** zobrazení a zobrazí soubor MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="753eb-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="753eb-142">Visual Studio vytvoří složku **moje projekt** , soubor Application. XAML a soubor MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="753eb-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="753eb-143">Cílení na .NET Framework a přidání odkazu na sestavení pro ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="753eb-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="753eb-144">Ve výchozím nastavení aplikace WPF cílí na profil klienta .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="753eb-144">By default, WPF applications target the .NET Framework 4 Client Profile.</span></span> <span data-ttu-id="753eb-145">Chcete-li použít obor názvů <xref:System.Runtime.Caching> v aplikaci WPF, musí aplikace cílit na .NET Framework 4 (nikoli na profil klienta .NET Framework 4) a musí zahrnovat odkaz na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="753eb-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the .NET Framework 4 Client Profile) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="753eb-146">Dalším krokem je proto změnit cíl .NET Framework a přidat odkaz na obor názvů <xref:System.Runtime.Caching>.</span><span class="sxs-lookup"><span data-stu-id="753eb-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="753eb-147">Postup změny cíle .NET Framework se liší v projektu Visual Basic a ve vizuálním C# projektu.</span><span class="sxs-lookup"><span data-stu-id="753eb-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="753eb-148">Změna cílového .NET Framework v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="753eb-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="753eb-149">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="753eb-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="753eb-150">Zobrazí se okno Vlastnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="753eb-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="753eb-151">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="753eb-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="753eb-152">V dolní části okna klikněte na možnost **Pokročilé možnosti kompilace...** .</span><span class="sxs-lookup"><span data-stu-id="753eb-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="753eb-153">Zobrazí se dialogové okno **Upřesnit nastavení kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="753eb-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="753eb-154">V seznamu **cílové rozhraní (všechny konfigurace)** vyberte .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="753eb-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="753eb-155">(Nevybírejte .NET Framework 4 profil klienta.)</span><span class="sxs-lookup"><span data-stu-id="753eb-155">(Do not select .NET Framework 4 Client Profile.)</span></span>

5. <span data-ttu-id="753eb-156">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="753eb-156">Click **OK**.</span></span>

     <span data-ttu-id="753eb-157">Zobrazí se dialogové okno **změnit cílovou architekturu** .</span><span class="sxs-lookup"><span data-stu-id="753eb-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="753eb-158">V dialogovém okně **změnit cílovou architekturu** klikněte na tlačítko **Ano**.</span><span class="sxs-lookup"><span data-stu-id="753eb-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="753eb-159">Projekt je uzavřený a pak se znovu otevřel.</span><span class="sxs-lookup"><span data-stu-id="753eb-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="753eb-160">Pomocí následujících kroků přidejte odkaz na sestavení pro ukládání do mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="753eb-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="753eb-161">V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="753eb-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="753eb-162">Vyberte kartu **.NET** , vyberte `System.Runtime.Caching`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="753eb-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="753eb-163">Změna cílového .NET Framework ve vizuálním C# projektu</span><span class="sxs-lookup"><span data-stu-id="753eb-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="753eb-164">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="753eb-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="753eb-165">Zobrazí se okno Vlastnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="753eb-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="753eb-166">Klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="753eb-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="753eb-167">V seznamu **cílové rozhraní** vyberte .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="753eb-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="753eb-168">(Nevybírejte **.NET Framework 4 profil klienta**.)</span><span class="sxs-lookup"><span data-stu-id="753eb-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="753eb-169">Pomocí následujících kroků přidejte odkaz na sestavení pro ukládání do mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="753eb-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="753eb-170">Klikněte pravým tlačítkem na složku **odkazy** a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="753eb-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="753eb-171">Vyberte kartu **.NET** , vyberte `System.Runtime.Caching`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="753eb-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="753eb-172">Přidání tlačítka do okna WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="753eb-173">Dále přidáte ovládací prvek tlačítko a vytvoříte obslužnou rutinu události pro událost `Click` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="753eb-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="753eb-174">Později přidáte kód, takže když kliknete na tlačítko, obsah textového souboru se uloží do mezipaměti a zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="753eb-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="753eb-175">Přidání ovládacího prvku tlačítko</span><span class="sxs-lookup"><span data-stu-id="753eb-175">To add a button control</span></span>

1. <span data-ttu-id="753eb-176">V **Průzkumník řešení**dvakrát klikněte na soubor MainWindow. XAML a otevřete ho.</span><span class="sxs-lookup"><span data-stu-id="753eb-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="753eb-177">Z **panelu nástrojů**v části **běžné ovládací prvky WPF**přetáhněte ovládací prvek `Button` do okna `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="753eb-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="753eb-178">V okně **vlastnosti** nastavte vlastnost `Content` ovládacího prvku `Button`, aby se **získala mezipaměť**.</span><span class="sxs-lookup"><span data-stu-id="753eb-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="753eb-179">Inicializuje se mezipaměť a zapíše do mezipaměti záznam.</span><span class="sxs-lookup"><span data-stu-id="753eb-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="753eb-180">V dalším kroku přidáte kód, který provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="753eb-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="753eb-181">Vytvořte instanci třídy cache – to znamená, že vytvoříte instanci nového objektu <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="753eb-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="753eb-182">Určuje, že mezipaměť používá objekt <xref:System.Runtime.Caching.HostFileChangeMonitor> ke sledování změn v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="753eb-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="753eb-183">Přečtěte si textový soubor a zapíšete jeho obsah do mezipaměti jako položku mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="753eb-184">Zobrazí obsah textového souboru v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="753eb-185">Vytvoření objektu mezipaměti</span><span class="sxs-lookup"><span data-stu-id="753eb-185">To create the cache object</span></span>

1. <span data-ttu-id="753eb-186">Dvakrát klikněte na tlačítko, které jste právě přidali, aby se vytvořila obslužná rutina události v souboru MainWindow.xaml.cs nebo MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="753eb-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="753eb-187">V horní části souboru (před deklarací třídy) přidejte následující příkazy `Imports` (Visual Basic) nebo `using` (C#):</span><span class="sxs-lookup"><span data-stu-id="753eb-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="753eb-188">V obslužné rutině události přidejte následující kód pro vytvoření instance objektu Cache:</span><span class="sxs-lookup"><span data-stu-id="753eb-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="753eb-189">Třída <xref:System.Runtime.Caching.ObjectCache> je vestavěná třída, která poskytuje mezipaměť objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="753eb-190">Přidejte následující kód pro čtení obsahu položky mezipaměti s názvem `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="753eb-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="753eb-191">Přidejte následující kód a ověřte, zda položka mezipaměti s názvem `filecontents` existuje:</span><span class="sxs-lookup"><span data-stu-id="753eb-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="753eb-192">Pokud zadaná položka mezipaměti neexistuje, musíte si přečíst textový soubor a přidat ho jako položku mezipaměti do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="753eb-193">V bloku `if/then` přidejte následující kód pro vytvoření nového objektu <xref:System.Runtime.Caching.CacheItemPolicy>, který určuje, že položka mezipaměti vyprší po 10 sekundách.</span><span class="sxs-lookup"><span data-stu-id="753eb-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="753eb-194">Pokud nejsou k dispozici žádné informace o vyřazení nebo vypršení platnosti, výchozí hodnota je <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, což znamená, že položky mezipaměti bez vypršení platnosti vyprší pouze v absolutním čase.</span><span class="sxs-lookup"><span data-stu-id="753eb-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="753eb-195">Místo toho vyprší platnost položek mezipaměti pouze v případě, že dojde k tlaku na paměť.</span><span class="sxs-lookup"><span data-stu-id="753eb-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="753eb-196">V souladu s osvědčeným postupem byste vždy měli explicitně zadat absolutní nebo klouzavé vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="753eb-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="753eb-197">Do bloku `if/then` a za kód, který jste přidali v předchozím kroku, přidejte následující kód, který vytvoří kolekci pro cesty k souborům, které chcete monitorovat, a přidejte cestu k textovému souboru do kolekce:</span><span class="sxs-lookup"><span data-stu-id="753eb-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > <span data-ttu-id="753eb-198">Pokud textový soubor, který chcete použít, není `c:\cache\cacheText.txt`, zadejte cestu, kde je textový soubor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="753eb-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="753eb-199">Po kódu, který jste přidali v předchozím kroku, přidejte následující kód pro přidání nového objektu <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekce monitorování změn pro položku mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="753eb-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="753eb-200">Objekt <xref:System.Runtime.Caching.HostFileChangeMonitor> sleduje cestu k textovému souboru a upozorní mezipaměť, pokud dojde k provedeným změnám.</span><span class="sxs-lookup"><span data-stu-id="753eb-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="753eb-201">V tomto příkladu vyprší platnost položky mezipaměti, pokud dojde ke změně obsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="753eb-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="753eb-202">Po kódu, který jste přidali v předchozím kroku, přidejte následující kód, který přečte obsah textového souboru:</span><span class="sxs-lookup"><span data-stu-id="753eb-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="753eb-203">Časové razítko pro datum a čas je přidané, takže budete moct zobrazit, kdy vyprší platnost položky mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="753eb-204">Po kódu, který jste přidali v předchozím kroku, přidejte následující kód pro vložení obsahu souboru do objektu mezipaměti jako instanci <xref:System.Runtime.Caching.CacheItem>:</span><span class="sxs-lookup"><span data-stu-id="753eb-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="753eb-205">Informace o tom, jak by měla být položka mezipaměti vyřazena, zadáte předáním <xref:System.Runtime.Caching.CacheItemPolicy> objektu, který jste vytvořili dříve jako parametr.</span><span class="sxs-lookup"><span data-stu-id="753eb-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="753eb-206">Po bloku `if/then` přidejte následující kód, který zobrazí obsah souboru v mezipaměti v okně se zprávou:</span><span class="sxs-lookup"><span data-stu-id="753eb-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="753eb-207">V nabídce **sestavení** klikněte na **sestavit WPFCaching** a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="753eb-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="753eb-208">Testování ukládání do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="753eb-209">Nyní můžete aplikaci otestovat.</span><span class="sxs-lookup"><span data-stu-id="753eb-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="753eb-210">Testování ukládání do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="753eb-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="753eb-211">Stiskněte klávesy CTRL+F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="753eb-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="753eb-212">Zobrazí se okno `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="753eb-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="753eb-213">Klikněte na **získat mezipaměť**.</span><span class="sxs-lookup"><span data-stu-id="753eb-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="753eb-214">Obsah uložený v mezipaměti z textového souboru se zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="753eb-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="753eb-215">Všimněte si časového razítka v souboru.</span><span class="sxs-lookup"><span data-stu-id="753eb-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="753eb-216">Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .</span><span class="sxs-lookup"><span data-stu-id="753eb-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="753eb-217">Časové razítko je beze změny.</span><span class="sxs-lookup"><span data-stu-id="753eb-217">The timestamp is unchanged.</span></span> <span data-ttu-id="753eb-218">To znamená, že se zobrazí obsah uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="753eb-219">Počkejte 10 sekund nebo více a pak znovu klikněte na **načíst mezipaměť** .</span><span class="sxs-lookup"><span data-stu-id="753eb-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="753eb-220">Tentokrát se zobrazí nové časové razítko.</span><span class="sxs-lookup"><span data-stu-id="753eb-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="753eb-221">To znamená, že zásada umožňuje vypršení platnosti položky mezipaměti a zobrazí se nový obsah uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="753eb-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="753eb-222">V textovém editoru otevřete textový soubor, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="753eb-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="753eb-223">Zatím žádné změny neprovádějte.</span><span class="sxs-lookup"><span data-stu-id="753eb-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="753eb-224">Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .</span><span class="sxs-lookup"><span data-stu-id="753eb-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="753eb-225">Všimněte si časového razítka znovu.</span><span class="sxs-lookup"><span data-stu-id="753eb-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="753eb-226">Proveďte změnu v textovém souboru a pak soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="753eb-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="753eb-227">Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .</span><span class="sxs-lookup"><span data-stu-id="753eb-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="753eb-228">Toto okno se zprávou obsahuje aktualizovaný obsah z textového souboru a nové časové razítko.</span><span class="sxs-lookup"><span data-stu-id="753eb-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="753eb-229">To znamená, že sledování změn v hostitelském souboru vyřadí položku mezipaměti hned po změně souboru, a to i v případě, že nevypršela absolutní doba časového limitu.</span><span class="sxs-lookup"><span data-stu-id="753eb-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    > <span data-ttu-id="753eb-230">Dobu vyřazení můžete zvýšit na 20 sekund nebo více, aby bylo možné provést změnu v souboru více času.</span><span class="sxs-lookup"><span data-stu-id="753eb-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="753eb-231">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="753eb-231">Code Example</span></span>
 <span data-ttu-id="753eb-232">Po dokončení tohoto návodu se kód projektu, který jste vytvořili, podobá následujícímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="753eb-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="753eb-233">Viz také</span><span class="sxs-lookup"><span data-stu-id="753eb-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="753eb-234">Ukládání do vyrovnávací paměti v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="753eb-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
