---
title: 'Kurz: Analyzovat klasifikaci mínění-Binary'
description: V tomto kurzu se dozvíte, jak vytvořit aplikaci Razor Pages, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Binární mínění klasifikátoru používá tvůrce modelů v aplikaci Visual Studio.
ms.date: 09/26/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0878a9318e7c60be29eeac9fb4efd47e408ab660
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332570"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="c8dab-104">Kurz: Analýza mínění komentářů k webu ve webové aplikaci pomocí Tvůrce modelů ML.NET</span><span class="sxs-lookup"><span data-stu-id="c8dab-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="c8dab-105">Naučte se analyzovat mínění z komentářů v reálném čase uvnitř webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8dab-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="c8dab-106">V tomto kurzu se dozvíte, jak vytvořit aplikaci ASP.NET Core Razor Pages, která klasifikuje mínění z komentářů k webům v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="c8dab-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="c8dab-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="c8dab-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c8dab-108">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c8dab-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="c8dab-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="c8dab-110">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="c8dab-110">Choose a scenario</span></span>
> - <span data-ttu-id="c8dab-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-111">Load the data</span></span>
> - <span data-ttu-id="c8dab-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-112">Train the model</span></span>
> - <span data-ttu-id="c8dab-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-113">Evaluate the model</span></span>
> - <span data-ttu-id="c8dab-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="c8dab-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="c8dab-115">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="c8dab-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="c8dab-116">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="c8dab-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="c8dab-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8dab-117">Pre-requisites</span></span>

<span data-ttu-id="c8dab-118">Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="c8dab-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="c8dab-119">Vytvoření aplikace Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c8dab-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="c8dab-120">Vytvořte **aplikaci ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="c8dab-121">Otevřete Visual Studio a v řádku nabídek vyberte **soubor > nový > projekt** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="c8dab-122">V dialogovém okně Nový projekt vyberte uzel  **C# vizuálu** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="c8dab-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="c8dab-123">Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="c8dab-124">Do textového pole **název** zadejte "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="c8dab-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="c8dab-125">Zaškrtávací políčko **vytvořit adresář pro řešení** by mělo být ve výchozím nastavení zaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="c8dab-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="c8dab-126">Pokud tomu tak není, ověřte ji.</span><span class="sxs-lookup"><span data-stu-id="c8dab-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="c8dab-127">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="c8dab-128">Zvolte **Webová aplikace** v okně, které zobrazuje různé typy ASP.NET Core projektů, a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c8dab-129">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-129">Prepare and understand the data</span></span>

<span data-ttu-id="c8dab-130">Stáhněte si [datovou sadu Detox Wikipedii](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="c8dab-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="c8dab-131">Po otevření webové stránky klikněte na ni pravým tlačítkem myši, vyberte **Uložit jako** a uložte soubor kdekoli v počítači.</span><span class="sxs-lookup"><span data-stu-id="c8dab-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="c8dab-132">Každý řádek v datové sadě *Wikipedii-Detox-250-line-data. TSV* představuje jinou revizi, kterou si uživatel na Wikipedii nanechal.</span><span class="sxs-lookup"><span data-stu-id="c8dab-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="c8dab-133">První sloupec představuje mínění textu (0 je non-toxický, 1 je toxický) a druhý sloupec představuje komentář, který opustil uživatel.</span><span class="sxs-lookup"><span data-stu-id="c8dab-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="c8dab-134">Sloupce jsou oddělené kartami.</span><span class="sxs-lookup"><span data-stu-id="c8dab-134">The columns are separated by tabs.</span></span> <span data-ttu-id="c8dab-135">Data vypadají jako následující:</span><span class="sxs-lookup"><span data-stu-id="c8dab-135">The data looks like the following:</span></span>

| <span data-ttu-id="c8dab-136">Mínění</span><span class="sxs-lookup"><span data-stu-id="c8dab-136">Sentiment</span></span> | <span data-ttu-id="c8dab-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="c8dab-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="c8dab-138">1</span><span class="sxs-lookup"><span data-stu-id="c8dab-138">1</span></span> | <span data-ttu-id="c8dab-139">= = HRUBÉ = = Dude, jste hrubé nahráli obrázek Carl, nebo jiný.</span><span class="sxs-lookup"><span data-stu-id="c8dab-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="c8dab-140">1</span><span class="sxs-lookup"><span data-stu-id="c8dab-140">1</span></span> | <span data-ttu-id="c8dab-141">= = OK!</span><span class="sxs-lookup"><span data-stu-id="c8dab-141">== OK!</span></span> <span data-ttu-id="c8dab-142">= = IM VANDALIZE VOLNĚ ŽIJÍCÍ NA WIKIWEBU A POTOM!!!</span><span class="sxs-lookup"><span data-stu-id="c8dab-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="c8dab-143">0</span><span class="sxs-lookup"><span data-stu-id="c8dab-143">0</span></span> | <span data-ttu-id="c8dab-144">Doufám, že vám to pomůže.</span><span class="sxs-lookup"><span data-stu-id="c8dab-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="c8dab-145">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="c8dab-145">Choose a scenario</span></span>

![Průvodce tvůrcem modelů v aplikaci Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="c8dab-147">Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="c8dab-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="c8dab-148">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *SentimentRazor* a vyberte **Přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="c8dab-149">V této ukázce je scénář analýzou mínění.</span><span class="sxs-lookup"><span data-stu-id="c8dab-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="c8dab-150">V kroku *scénář* nástroje Tvůrce modelů vyberte **Analýza mínění** scénář.</span><span class="sxs-lookup"><span data-stu-id="c8dab-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c8dab-151">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-151">Load the data</span></span>

<span data-ttu-id="c8dab-152">Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve `csv` formátu nebo. `tsv`</span><span class="sxs-lookup"><span data-stu-id="c8dab-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="c8dab-153">V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat **soubor** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="c8dab-154">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů vyhledejte a vyberte soubor *Wikipedii-Detox-250-line-data. TSV* .</span><span class="sxs-lookup"><span data-stu-id="c8dab-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="c8dab-155">V rozevíracím seznamu **sloupec pro předpověď (popisek)** vyberte **mínění** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="c8dab-156">Ponechte výchozí hodnoty rozevíracího seznamu **vstupních sloupců (funkce)** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="c8dab-157">Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="c8dab-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c8dab-158">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-158">Train the model</span></span>

<span data-ttu-id="c8dab-159">Úkolem strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="c8dab-159">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="c8dab-160">V průběhu procesu školení modelů vlacích sestavuje samostatné modely pomocí různých binárních algoritmů klasifikace a nastavení, aby bylo možné najít nejlepší model pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="c8dab-161">Čas potřebný ke školení modelu je úměrný množství dat.</span><span class="sxs-lookup"><span data-stu-id="c8dab-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="c8dab-162">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c8dab-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="c8dab-163">I když tvůrce modelů nastaví hodnotu **času na vlak (sekundy)** až 10 sekund, narůstá na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="c8dab-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="c8dab-164">Školení po delší dobu umožňuje tvůrci modelů prozkoumat větší počet algoritmů a kombinaci parametrů při hledání nejlepšího modelu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="c8dab-165">Vyberte **Spustit školení**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-165">Select **Start Training**.</span></span>

    <span data-ttu-id="c8dab-166">V průběhu procesu školení se data o průběhu zobrazují v `Progress` části kroku výuka.</span><span class="sxs-lookup"><span data-stu-id="c8dab-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="c8dab-167">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="c8dab-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="c8dab-168">Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="c8dab-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="c8dab-169">Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.</span><span class="sxs-lookup"><span data-stu-id="c8dab-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="c8dab-170">Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="c8dab-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="c8dab-171">Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="c8dab-172">Po dokončení školení vyberte odkaz **vyhodnotit** , který se přesune k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="c8dab-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="c8dab-173">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-173">Evaluate the model</span></span>

<span data-ttu-id="c8dab-174">Výsledkem kroku školení bude jeden model, který má nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="c8dab-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="c8dab-175">V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v **nejlepším záznamu modelu** spolu se metrikami v **nejlepší kvalitě modelu (RSquared)** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Quality (RSquared)**.</span></span> <span data-ttu-id="c8dab-176">Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="c8dab-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="c8dab-177">Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat.</span><span class="sxs-lookup"><span data-stu-id="c8dab-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="c8dab-178">V opačném případě vyberte odkaz **kód** , který se přesune k poslednímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="c8dab-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="c8dab-179">Přidejte kód, který provede předpovědi</span><span class="sxs-lookup"><span data-stu-id="c8dab-179">Add the code to make predictions</span></span>

<span data-ttu-id="c8dab-180">V důsledku školicího procesu se vytvoří dva projekty.</span><span class="sxs-lookup"><span data-stu-id="c8dab-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="c8dab-181">Odkaz na školený model</span><span class="sxs-lookup"><span data-stu-id="c8dab-181">Reference the trained model</span></span>

1. <span data-ttu-id="c8dab-182">V kroku *kód* nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="c8dab-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="c8dab-183">Následující projekty by se měly zobrazit v **Průzkumník řešení**:</span><span class="sxs-lookup"><span data-stu-id="c8dab-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="c8dab-184">*SentimentRazorML. ConsoleApp*: Konzolová aplikace .NET Core, která obsahuje kód pro školení a předpověď modelu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="c8dab-185">*SentimentRazorML. model*: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu a také uloženou verzi nejlepšího modelu provádění během školení.</span><span class="sxs-lookup"><span data-stu-id="c8dab-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="c8dab-186">Pro tento kurz je použit pouze projekt *SentimentRazorML. model* , protože předpovědi bude vytvořen ve webové aplikaci *SentimentRazor* , nikoli v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="c8dab-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="c8dab-187">I když se *SentimentRazorML. ConsoleApp* nebude používat pro vyhodnocování, dá se použít k reučení modelu pomocí nových dat později.</span><span class="sxs-lookup"><span data-stu-id="c8dab-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="c8dab-188">Přeškolení je mimo rámec tohoto kurzu, ale.</span><span class="sxs-lookup"><span data-stu-id="c8dab-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="c8dab-189">Konfigurace PredictionEngine fondu</span><span class="sxs-lookup"><span data-stu-id="c8dab-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="c8dab-190">Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="c8dab-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="c8dab-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="c8dab-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c8dab-192">Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8dab-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="c8dab-193">Jak vaše aplikace roste, tento proces může být nespravovatelný.</span><span class="sxs-lookup"><span data-stu-id="c8dab-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="c8dab-194">Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c8dab-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="c8dab-195">Nainstalujte balíček NuGet *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="c8dab-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="c8dab-196">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="c8dab-197">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="c8dab-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="c8dab-198">Vyberte kartu **Procházet** a vyhledejte **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="c8dab-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="c8dab-199">Vyberte balíček v seznamu a klikněte na tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="c8dab-200">V dialogovém okně **Náhled změn** klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="c8dab-201">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="c8dab-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="c8dab-202">Otevřete soubor *Startup.cs* v projektu *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="c8dab-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="c8dab-203">Přidejte následující příkazy using pro odkazování na balíček NuGet *Microsoft.Extensions.ml* a projekt *SentimentRazorML. model* :</span><span class="sxs-lookup"><span data-stu-id="c8dab-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]

1. <span data-ttu-id="c8dab-204">Vytvořte globální proměnnou pro uložení umístění trained modelového souboru.</span><span class="sxs-lookup"><span data-stu-id="c8dab-204">Create a global variable to store the location of the trained model file.</span></span>

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. <span data-ttu-id="c8dab-205">Soubor modelu je uložen v adresáři buildu spolu se soubory sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8dab-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="c8dab-206">Aby byl přístup snazší, vytvořte pomocnou metodu volanou `GetAbsolutePath` `Configure` za metodou.</span><span class="sxs-lookup"><span data-stu-id="c8dab-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. <span data-ttu-id="c8dab-207">Použijte metodu v konstruktoru`_modelPath`třídypronastavení. `Startup` `GetAbsolutePath`</span><span class="sxs-lookup"><span data-stu-id="c8dab-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. <span data-ttu-id="c8dab-208">Nakonfigurujte pro aplikaci v `ConfigureServices`metodě: `PredictionEnginePool`</span><span class="sxs-lookup"><span data-stu-id="c8dab-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="c8dab-209">Vytvořit obslužnou rutinu analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="c8dab-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="c8dab-210">Předpovědi se provede uvnitř hlavní stránky aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8dab-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="c8dab-211">Proto metoda, která přijímá vstup uživatele a používá `PredictionEnginePool` k vrácení předpovědi, je nutné přidat.</span><span class="sxs-lookup"><span data-stu-id="c8dab-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="c8dab-212">Otevřete soubor *index.cshtml.cs* umístěný v adresáři *stránky* a přidejte následující příkazy using:</span><span class="sxs-lookup"><span data-stu-id="c8dab-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    <span data-ttu-id="c8dab-213">Aby bylo možné použít `PredictionEnginePool` konfiguraci `Startup` ve třídě, je nutné ji vložit do konstruktoru modelu, kde jej chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c8dab-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="c8dab-214">Přidejte proměnnou pro odkazování `PredictionEnginePool` `IndexModel` uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="c8dab-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. <span data-ttu-id="c8dab-215">Vytvořte ve `IndexModel` třídě konstruktor a `PredictionEnginePool` založit do něj službu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. <span data-ttu-id="c8dab-216">Vytvořte obslužnou rutinu metody, která `PredictionEnginePool` používá k vytvoření předpovědi ze vstupu uživatele přijatého z webové stránky.</span><span class="sxs-lookup"><span data-stu-id="c8dab-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="c8dab-217">`OnGet` Pod metodou vytvořte novou metodu s názvem.`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="c8dab-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="c8dab-218">V rámci metody vrátí neutrální mínění, pokud je vstup od uživatele prázdný nebo má hodnotu null. `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="c8dab-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)]

    1. <span data-ttu-id="c8dab-219">Když je zadaný platný vstup, vytvoří se nová instance `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="c8dab-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)]

    1. <span data-ttu-id="c8dab-220">`PredictionEnginePool` Použijte k předpovídání mínění.</span><span class="sxs-lookup"><span data-stu-id="c8dab-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)]

    1. <span data-ttu-id="c8dab-221">Převeďte předpovězenou `bool` hodnotu na toxické nebo netoxické pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="c8dab-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. <span data-ttu-id="c8dab-222">Nakonec vraťte mínění zpět na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="c8dab-222">Finally, return the sentiment back to the web page.</span></span>

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a><span data-ttu-id="c8dab-223">Konfigurace webové stránky</span><span class="sxs-lookup"><span data-stu-id="c8dab-223">Configure the web page</span></span>

<span data-ttu-id="c8dab-224">Výsledky vrácené nástrojem `OnGetAnalyzeSentiment` budou dynamicky zobrazeny `Index` na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="c8dab-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="c8dab-225">Otevřete soubor *index. cshtml* v adresáři *stránky* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c8dab-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="c8dab-226">Pak na konec stránky *. CSS* v adresáři *wwwroot\css* přidejte kód CSS stylu:</span><span class="sxs-lookup"><span data-stu-id="c8dab-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="c8dab-227">Pak přidejte kód, který odešle vstupy z webové stránky do `OnGetAnalyzeSentiment` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c8dab-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="c8dab-228">V souboru *site. js* v adresáři *wwwroot\js* vytvořte funkci s názvem `getSentiment` , která vytvoří požadavek GET http `OnGetAnalyzeSentiment` s uživatelským vstupem k obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="c8dab-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="c8dab-229">Níže přidejte další funkci nazvanou `updateMarker` , která dynamicky aktualizuje pozici značky na webové stránce, protože mínění je předpovězeno.</span><span class="sxs-lookup"><span data-stu-id="c8dab-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="c8dab-230">Vytvořte funkci obslužné rutiny události `updateSentiment` volanou k získání vstupu z uživatele, odešlete ji `OnGetAnalyzeSentiment` funkci pomocí `getSentiment` funkce a aktualizujte značku pomocí `updateMarker` funkce.</span><span class="sxs-lookup"><span data-stu-id="c8dab-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="c8dab-231">Nakonec zaregistrujte obslužnou rutinu události a navažte `textarea` ji na element `id=Message` s atributem.</span><span class="sxs-lookup"><span data-stu-id="c8dab-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="c8dab-232">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="c8dab-232">Run the application</span></span>

<span data-ttu-id="c8dab-233">Teď, když je vaše aplikace nastavená, spusťte aplikaci, která by se měla spustit ve vašem prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="c8dab-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="c8dab-234">Až se aplikace spustí, zadejte *Tvůrce modelů.*</span><span class="sxs-lookup"><span data-stu-id="c8dab-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="c8dab-235">do textové oblasti.</span><span class="sxs-lookup"><span data-stu-id="c8dab-235">into the text area.</span></span> <span data-ttu-id="c8dab-236">Zobrazený předpokládaný mínění by neměl být *toxický*.</span><span class="sxs-lookup"><span data-stu-id="c8dab-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Spuštění okna s předpokládaným oknem mínění](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="c8dab-238">Pokud potřebujete odkazovat na projekty vygenerované tvůrcem modelu později v jiném řešení, můžete je najít v `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáři.</span><span class="sxs-lookup"><span data-stu-id="c8dab-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8dab-239">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c8dab-239">Next steps</span></span>

<span data-ttu-id="c8dab-240">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="c8dab-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c8dab-241">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c8dab-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="c8dab-242">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="c8dab-243">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="c8dab-243">Choose a scenario</span></span>
> - <span data-ttu-id="c8dab-244">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c8dab-244">Load the data</span></span>
> - <span data-ttu-id="c8dab-245">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-245">Train the model</span></span>
> - <span data-ttu-id="c8dab-246">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="c8dab-246">Evaluate the model</span></span>
> - <span data-ttu-id="c8dab-247">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="c8dab-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c8dab-248">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="c8dab-248">Additional Resources</span></span>

<span data-ttu-id="c8dab-249">Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="c8dab-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="c8dab-250">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="c8dab-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="c8dab-251">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c8dab-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="c8dab-252">Metriky modelu binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="c8dab-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
