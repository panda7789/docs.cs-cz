---
title: 'Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: d8f37431279cc22b8e9c131f860b5de82f35af2e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591202"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="dad75-102">Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="dad75-103">Ukládání do mezipaměti umožňuje uložit data do paměti pro rychlý přístup.</span><span class="sxs-lookup"><span data-stu-id="dad75-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="dad75-104">Když je znovu přístupu k datům, aplikacím můžete získat data z mezipaměti namísto načítání z původního zdroje.</span><span class="sxs-lookup"><span data-stu-id="dad75-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="dad75-105">Tím lze vylepšit výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="dad75-105">This can improve performance and scalability.</span></span> <span data-ttu-id="dad75-106">Navíc umožňuje ukládání dat do mezipaměti k dispozici při zdroj dat je dočasně nedostupný.</span><span class="sxs-lookup"><span data-stu-id="dad75-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="dad75-107">Rozhraní .NET Framework poskytuje třídy, které vám umožní používat ukládání do mezipaměti v aplikacích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dad75-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="dad75-108">Tyto třídy se nacházejí v <xref:System.Runtime.Caching> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dad75-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="dad75-109"><xref:System.Runtime.Caching> Obor názvů je novinkou [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dad75-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="dad75-110">Tento obor názvů umožňuje ukládání do mezipaměti je k dispozici pro všechny aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dad75-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="dad75-111">V předchozích verzích rozhraní .NET Framework, ukládání do mezipaměti byla k dispozici pouze ve <xref:System.Web> obor názvů a proto požadovaná závislost na třídách technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dad75-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="dad75-112">Tento návod ukazuje, jak používat ukládání do mezipaměti, která je k dispozici v rozhraní .NET Framework jako součást funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="dad75-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="dad75-113">V tomto návodu můžete ukládat do mezipaměti obsah textového souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="dad75-114">Tento návod obsahuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="dad75-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="dad75-115">Vytvoření projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="dad75-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="dad75-116">Přidání odkazu na [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dad75-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>

- <span data-ttu-id="dad75-117">Inicializuje se mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="dad75-117">Initializing a cache.</span></span>

- <span data-ttu-id="dad75-118">Přidává se položka v mezipaměti, který obsahuje obsah textového souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="dad75-119">Poskytování zásadu vyřazení pro položku mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="dad75-120">Monitorování cestu k souboru v mezipaměti a upozornit na instanci mezipaměti se změní na maximální počet monitorovaných položek.</span><span class="sxs-lookup"><span data-stu-id="dad75-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dad75-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dad75-121">Prerequisites</span></span>
 <span data-ttu-id="dad75-122">K dokončení tohoto návodu budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="dad75-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="dad75-123">Microsoft Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="dad75-123">Microsoft Visual Studio 2010.</span></span>

- <span data-ttu-id="dad75-124">Textový soubor, který obsahuje malé množství textu.</span><span class="sxs-lookup"><span data-stu-id="dad75-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="dad75-125">(Obsah textového souboru se zobrazí v okně se zprávou.) Kód popsaných v tomto návodu se předpokládá, že pracujete s následující soubor:</span><span class="sxs-lookup"><span data-stu-id="dad75-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="dad75-126">Můžete však použít libovolný textový soubor a dělat malé změny kódu v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="dad75-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="dad75-127">Vytvoření projektu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="dad75-128">Začněte vytvořením projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="dad75-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="dad75-129">Vytvoření aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-129">To create a WPF application</span></span>

1. <span data-ttu-id="dad75-130">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dad75-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="dad75-131">V **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="dad75-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="dad75-132">**Nový projekt** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dad75-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="dad75-133">V části **nainstalované šablony**, vyberte programovací jazyk, který chcete použít (**jazyka Visual Basic** nebo **Visual C#**).</span><span class="sxs-lookup"><span data-stu-id="dad75-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="dad75-134">V **nový projekt** dialogu **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="dad75-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dad75-135">Pokud se nezobrazí **aplikace WPF** šablonu, ujistěte se, zda cílíte na verzi rozhraní .NET Framework, která podporuje WPF.</span><span class="sxs-lookup"><span data-stu-id="dad75-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="dad75-136">V **nový projekt** dialogu [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="dad75-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>

5. <span data-ttu-id="dad75-137">V **název** textové pole, zadejte název pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="dad75-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="dad75-138">Například můžete zadat **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="dad75-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="dad75-139">Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="dad75-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="dad75-140">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="dad75-140">Click **OK**.</span></span>

     <span data-ttu-id="dad75-141">Otevře se Návrhář WPF v **návrhu** zobrazení a zobrazí soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="dad75-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="dad75-142">Visual Studio vytvoří **Můj projekt** složka, soubor Application.xaml a souboru MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="dad75-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="dad75-143">Cílení na rozhraní .NET Framework a přidání odkazu na ukládání do mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="dad75-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="dad75-144">Ve výchozím nastavení, cílové aplikace WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dad75-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="dad75-145">Použít <xref:System.Runtime.Caching> oboru názvů v aplikaci WPF, aplikace musí cílit [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (není [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) a musí obsahovat odkaz na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dad75-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="dad75-146">Proto, dalším krokem je změnit cílové rozhraní .NET Framework a přidejte odkaz na <xref:System.Runtime.Caching> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dad75-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
>  <span data-ttu-id="dad75-147">Postup pro změnu cílové rozhraní .NET Framework se liší v projektu jazyka Visual Basic a v projektu jazyka Visual C#.</span><span class="sxs-lookup"><span data-stu-id="dad75-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="dad75-148">Chcete-li změnit cílové rozhraní .NET Framework v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dad75-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="dad75-149">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="dad75-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="dad75-150">Zobrazí se okno Vlastnosti pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dad75-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="dad75-151">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="dad75-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="dad75-152">V dolní části okna klikněte na tlačítko **Upřesnit možnosti kompilace...** .</span><span class="sxs-lookup"><span data-stu-id="dad75-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="dad75-153">**Pokročilé nastavení kompilátoru** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dad75-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="dad75-154">V **cílového rozhraní (všechny konfigurace)** seznamu vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dad75-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="dad75-155">(Nesmí být zvolen [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="dad75-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>

5. <span data-ttu-id="dad75-156">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="dad75-156">Click **OK**.</span></span>

     <span data-ttu-id="dad75-157">**Změnit cílový rámec** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dad75-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="dad75-158">V **změnit cílový rámec** dialogové okno, klikněte na tlačítko **Ano**.</span><span class="sxs-lookup"><span data-stu-id="dad75-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="dad75-159">Projekt je uzavřen a pak znovu otevřelo.</span><span class="sxs-lookup"><span data-stu-id="dad75-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="dad75-160">Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="dad75-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="dad75-161">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="dad75-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="dad75-162">Vyberte **.NET** kartu, vyberte možnost `System.Runtime.Caching`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="dad75-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="dad75-163">Chcete-li změnit cílové rozhraní .NET Framework v projektu jazyka Visual C#</span><span class="sxs-lookup"><span data-stu-id="dad75-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="dad75-164">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="dad75-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="dad75-165">Zobrazí se okno Vlastnosti pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dad75-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="dad75-166">Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="dad75-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="dad75-167">V **Cílová architektura** seznamu vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dad75-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="dad75-168">(Nesmí být zvolen **rozhraní .NET Framework 4 Client Profile**.)</span><span class="sxs-lookup"><span data-stu-id="dad75-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="dad75-169">Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="dad75-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="dad75-170">Klikněte pravým tlačítkem myši **odkazy** složku a pak klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="dad75-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="dad75-171">Vyberte **.NET** kartu, vyberte možnost `System.Runtime.Caching`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="dad75-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="dad75-172">Přidání tlačítka do okna WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="dad75-173">V dalším kroku přidáte ovládací prvek button a vytvořit obslužnou rutinu události pro tlačítka `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="dad75-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="dad75-174">Kód, který později přidáte tak, aby po kliknutí na tlačítko, jsou uložené v mezipaměti a zobrazí obsah textového souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="dad75-175">Chcete-li přidat ovládací prvek button</span><span class="sxs-lookup"><span data-stu-id="dad75-175">To add a button control</span></span>

1. <span data-ttu-id="dad75-176">V **Průzkumníka řešení**, poklikejte na soubor MainWindow.xaml a otevřete ho.</span><span class="sxs-lookup"><span data-stu-id="dad75-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="dad75-177">Z **nástrojů**v části **běžných ovládacích prvků WPF**, přetáhněte `Button` ovládací prvek `MainWindow` okna.</span><span class="sxs-lookup"><span data-stu-id="dad75-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="dad75-178">V **vlastnosti** okno, nastaveno `Content` vlastnost `Button` mít pod kontrolou **získat mezipaměti**.</span><span class="sxs-lookup"><span data-stu-id="dad75-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="dad75-179">Inicializace mezipaměti a ukládání do mezipaměti položku</span><span class="sxs-lookup"><span data-stu-id="dad75-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="dad75-180">V dalším kroku přidáte kód k provádění následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="dad75-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="dad75-181">Vytvoření instance třídy mezipaměti – to znamená, že jste se vytvořit novou instanci <xref:System.Runtime.Caching.MemoryCache> objektu.</span><span class="sxs-lookup"><span data-stu-id="dad75-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="dad75-182">Určete, že mezipaměť používá <xref:System.Runtime.Caching.HostFileChangeMonitor> objektů pro sledování změn v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="dad75-183">Čtení textového souboru a jeho obsah v mezipaměti jako položka v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="dad75-184">Zobrazte obsah v mezipaměti textového souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="dad75-185">Chcete-li vytvořit objekt mezipaměti</span><span class="sxs-lookup"><span data-stu-id="dad75-185">To create the cache object</span></span>

1. <span data-ttu-id="dad75-186">Dvakrát klikněte na tlačítko, které jste právě přidali, chcete-li vytvořit obslužnou rutinu události v souboru MainWindow.xaml.cs nebo soubor MainWindow.Xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="dad75-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="dad75-187">V horní části souboru (před deklaraci třídy), přidejte následující `Imports` (Visual Basic) nebo `using` příkazy (C#):</span><span class="sxs-lookup"><span data-stu-id="dad75-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="dad75-188">V obslužné rutině události přidejte následující kód k vytvoření instance objektu mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="dad75-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="dad75-189"><xref:System.Runtime.Caching.ObjectCache> Třída je integrované třídu, která poskytuje mezipaměti objektů v paměti do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="dad75-190">Přidejte následující kód k načtení obsahu položky mezipaměti s názvem `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="dad75-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="dad75-191">Přidejte následující kód, který zkontrolujte, zda položka mezipaměti s názvem `filecontents` existuje:</span><span class="sxs-lookup"><span data-stu-id="dad75-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="dad75-192">Určená položka mezipaměti neexistuje, musíte přečíst textový soubor a přidejte jej jako položka v mezipaměti do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="dad75-193">V `if/then` blokovat, přidejte následující kód k vytvoření nového <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který určuje, že položka mezipaměti vyprší po 10 sekundách.</span><span class="sxs-lookup"><span data-stu-id="dad75-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="dad75-194">Pokud je k dispozici žádné informace o vyřazení nebo vypršení platnosti, výchozí hodnota je <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, což znamená, že položky mezipaměti nikdy nevyprší závislosti pouze na absolutním čase.</span><span class="sxs-lookup"><span data-stu-id="dad75-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="dad75-195">Místo toho platnost položky mezipaměti pouze v případě nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="dad75-196">Jako osvědčený postup byste měli vždy explicitně poskytnout buď absolutní, nebo klouzavé vypršení platnosti.</span><span class="sxs-lookup"><span data-stu-id="dad75-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="dad75-197">Uvnitř `if/then` blokovat a následující kód, kterou jste přidali v předchozím kroku, přidejte následující kód k vytvoření kolekce pro cesty k souborům, které chcete monitorovat a přidejte cestu k souboru text do kolekce:</span><span class="sxs-lookup"><span data-stu-id="dad75-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  <span data-ttu-id="dad75-198">Pokud není textový soubor, který chcete použít `c:\cache\cacheText.txt`, zadejte cestu k umístění textového souboru, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="dad75-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="dad75-199">Následující kód, který jste přidali v předchozím kroku, přidejte následující kód přidejte nový <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekce změnu monitoruje položky mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="dad75-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="dad75-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> Objekt cesta k souboru text sleduje a upozorní mezipaměti, pokud dojde ke změnám.</span><span class="sxs-lookup"><span data-stu-id="dad75-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="dad75-201">V tomto příkladu položky uložené v mezipaměti vyprší, pokud se změní obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="dad75-202">Následující kód, který jste přidali v předchozím kroku přidejte následující kód k načtení obsahu textového souboru:</span><span class="sxs-lookup"><span data-stu-id="dad75-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="dad75-203">Časové razítko data a času je přidán, takže budete moci zobrazit, když vyprší platnost položky mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="dad75-204">Následující kód, který jste přidali v předchozím kroku, přidejte následující kód k vložení obsahu souboru do objektu mezipaměti jako <xref:System.Runtime.Caching.CacheItem> instance:</span><span class="sxs-lookup"><span data-stu-id="dad75-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="dad75-205">Zadejte informace o tom, jak položka mezipaměti by měla být vyřazena předáním <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který jste vytvořili dříve jako parametr.</span><span class="sxs-lookup"><span data-stu-id="dad75-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="dad75-206">Po `if/then` blokovat, přidejte následující kód k zobrazení obsahu v mezipaměti souborů v okně se zprávou:</span><span class="sxs-lookup"><span data-stu-id="dad75-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="dad75-207">V **sestavení** nabídky, klikněte na tlačítko **sestavení WPFCaching** k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="dad75-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="dad75-208">Testování ukládání do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="dad75-209">Teď můžete aplikaci otestovat.</span><span class="sxs-lookup"><span data-stu-id="dad75-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="dad75-210">K testování ukládání do mezipaměti v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="dad75-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="dad75-211">Stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dad75-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="dad75-212">`MainWindow` Se zobrazí okno.</span><span class="sxs-lookup"><span data-stu-id="dad75-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="dad75-213">Klikněte na tlačítko **získat mezipaměti**.</span><span class="sxs-lookup"><span data-stu-id="dad75-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="dad75-214">Obsah uložený v mezipaměti z textového souboru se zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="dad75-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="dad75-215">Všimněte si, že časové razítko souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="dad75-216">Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.</span><span class="sxs-lookup"><span data-stu-id="dad75-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="dad75-217">Časové razítko je beze změny.</span><span class="sxs-lookup"><span data-stu-id="dad75-217">The timestamp is unchanged.</span></span> <span data-ttu-id="dad75-218">To znamená, že je zobrazen obsah uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="dad75-219">Počkejte 10 sekund nebo informace a pak klikněte na tlačítko **získat mezipaměti** znovu.</span><span class="sxs-lookup"><span data-stu-id="dad75-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="dad75-220">Tentokrát se zobrazí nové časové razítko.</span><span class="sxs-lookup"><span data-stu-id="dad75-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="dad75-221">To znamená, že umožňují zásady vypršení platnosti položky mezipaměti a zobrazí se nový obsah uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="dad75-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="dad75-222">V textovém editoru otevřete textový soubor, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="dad75-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="dad75-223">Ještě neprovádějte žádné změny.</span><span class="sxs-lookup"><span data-stu-id="dad75-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="dad75-224">Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.</span><span class="sxs-lookup"><span data-stu-id="dad75-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="dad75-225">Všimněte si, že časové razítko znovu.</span><span class="sxs-lookup"><span data-stu-id="dad75-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="dad75-226">Proveďte změnu do textového souboru a pak soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="dad75-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="dad75-227">Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.</span><span class="sxs-lookup"><span data-stu-id="dad75-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="dad75-228">Toto okno se zprávou obsahuje aktualizovaný obsah z textového souboru a nové časové razítko.</span><span class="sxs-lookup"><span data-stu-id="dad75-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="dad75-229">To znamená, že sledování změn souboru hostitele vyřazení položka mezipaměti okamžitě při změně souboru i v případě, kdyby absolutní časový limit vypršel.</span><span class="sxs-lookup"><span data-stu-id="dad75-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dad75-230">Vám může prodloužit dobu vyřazení na 20 sekund nebo více a více času, abyste provedli změnu v souboru.</span><span class="sxs-lookup"><span data-stu-id="dad75-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="dad75-231">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="dad75-231">Code Example</span></span>
 <span data-ttu-id="dad75-232">Po dokončení tohoto návodu, kód, který jste vytvořili projekt bude vypadat podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="dad75-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="dad75-233">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dad75-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="dad75-234">Ukládání do vyrovnávací paměti v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dad75-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
