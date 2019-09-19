---
title: 'Kurz: Analyzovat klasifikaci mínění-Binary'
description: V tomto kurzu se dozvíte, jak vytvořit aplikaci Razor Pages, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Binární mínění klasifikátoru používá tvůrce modelů v aplikaci Visual Studio.
ms.date: 09/13/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6184e097daf4604173db9e2a34606e68eb0fdc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054319"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="6a3df-104">Kurz: Analýza mínění komentářů k webu ve webové aplikaci pomocí Tvůrce modelů ML.NET</span><span class="sxs-lookup"><span data-stu-id="6a3df-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="6a3df-105">Naučte se analyzovat mínění z komentářů v reálném čase uvnitř webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a3df-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="6a3df-106">V tomto kurzu se dozvíte, jak vytvořit aplikaci ASP.NET Core Razor Pages, která klasifikuje mínění z komentářů k webům v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="6a3df-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="6a3df-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="6a3df-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="6a3df-108">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6a3df-108">Create an ASP.NET Core Razor Pages application</span></span>
> * <span data-ttu-id="6a3df-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="6a3df-110">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="6a3df-110">Choose a scenario</span></span>
> * <span data-ttu-id="6a3df-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-111">Load the data</span></span>
> * <span data-ttu-id="6a3df-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-112">Train the model</span></span>
> * <span data-ttu-id="6a3df-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-113">Evaluate the model</span></span>
> * <span data-ttu-id="6a3df-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6a3df-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="6a3df-115">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="6a3df-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="6a3df-116">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="6a3df-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="6a3df-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a3df-117">Pre-requisites</span></span>

<span data-ttu-id="6a3df-118">Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="6a3df-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="6a3df-119">Vytvoření aplikace Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6a3df-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="6a3df-120">Vytvořte **aplikaci ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="6a3df-121">Otevřete Visual Studio a v řádku nabídek vyberte **soubor > nový > projekt** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span> 
    1. <span data-ttu-id="6a3df-122">V dialogovém okně Nový projekt vyberte uzel  **C# vizuálu** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="6a3df-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> 
    1. <span data-ttu-id="6a3df-123">Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-123">Then select the **ASP.NET Core Web Application** project template.</span></span> 
    1. <span data-ttu-id="6a3df-124">Do textového pole **název** zadejte "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="6a3df-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="6a3df-125">Zaškrtávací políčko **vytvořit adresář pro řešení** by mělo být ve výchozím nastavení zaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="6a3df-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="6a3df-126">Pokud tomu tak není, ověřte ji.</span><span class="sxs-lookup"><span data-stu-id="6a3df-126">If that's not the case, check it.</span></span> 
    1. <span data-ttu-id="6a3df-127">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="6a3df-128">Zvolte **Webová aplikace** v okně, které zobrazuje různé typy ASP.NET Core projektů, a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6a3df-129">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-129">Prepare and understand the data</span></span>

<span data-ttu-id="6a3df-130">Stáhněte si [datovou sadu Detox Wikipedii](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="6a3df-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="6a3df-131">Po otevření webové stránky klikněte na ni pravým tlačítkem myši, vyberte **Uložit jako** a uložte soubor kdekoli v počítači.</span><span class="sxs-lookup"><span data-stu-id="6a3df-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span> 

<span data-ttu-id="6a3df-132">Každý řádek v datové sadě *Wikipedii-Detox-250-line-data. TSV* představuje jinou revizi, kterou si uživatel na Wikipedii nanechal.</span><span class="sxs-lookup"><span data-stu-id="6a3df-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="6a3df-133">První sloupec představuje mínění textu (0 je non-toxický, 1 je toxický) a druhý sloupec představuje komentář, který opustil uživatel.</span><span class="sxs-lookup"><span data-stu-id="6a3df-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="6a3df-134">Sloupce jsou oddělené kartami.</span><span class="sxs-lookup"><span data-stu-id="6a3df-134">The columns are separated by tabs.</span></span> <span data-ttu-id="6a3df-135">Data vypadají jako následující:</span><span class="sxs-lookup"><span data-stu-id="6a3df-135">The data looks like the following:</span></span>

| <span data-ttu-id="6a3df-136">Mínění</span><span class="sxs-lookup"><span data-stu-id="6a3df-136">Sentiment</span></span> | <span data-ttu-id="6a3df-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="6a3df-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="6a3df-138">1</span><span class="sxs-lookup"><span data-stu-id="6a3df-138">1</span></span> | <span data-ttu-id="6a3df-139">= = HRUBÉ = = Dude, jste hrubé nahráli obrázek Carl, nebo jiný.</span><span class="sxs-lookup"><span data-stu-id="6a3df-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="6a3df-140">1</span><span class="sxs-lookup"><span data-stu-id="6a3df-140">1</span></span> | <span data-ttu-id="6a3df-141">= = OK!</span><span class="sxs-lookup"><span data-stu-id="6a3df-141">== OK!</span></span> <span data-ttu-id="6a3df-142">= = IM VANDALIZE VOLNĚ ŽIJÍCÍ NA WIKIWEBU A POTOM!!!</span><span class="sxs-lookup"><span data-stu-id="6a3df-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="6a3df-143">0</span><span class="sxs-lookup"><span data-stu-id="6a3df-143">0</span></span> | <span data-ttu-id="6a3df-144">Doufám, že vám to pomůže.</span><span class="sxs-lookup"><span data-stu-id="6a3df-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="6a3df-145">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="6a3df-145">Choose a scenario</span></span>

![](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="6a3df-146">Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="6a3df-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> 

1. <span data-ttu-id="6a3df-147">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *SentimentRazor* a vyberte **Přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="6a3df-148">V této ukázce je scénář analýzou mínění.</span><span class="sxs-lookup"><span data-stu-id="6a3df-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="6a3df-149">V kroku *scénář* nástroje Tvůrce modelů vyberte **Analýza mínění** scénář.</span><span class="sxs-lookup"><span data-stu-id="6a3df-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6a3df-150">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-150">Load the data</span></span>

<span data-ttu-id="6a3df-151">Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve `csv` formátu nebo. `tsv`</span><span class="sxs-lookup"><span data-stu-id="6a3df-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="6a3df-152">V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat **soubor** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="6a3df-153">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů vyhledejte a vyberte soubor *Wikipedii-Detox-250-line-data. TSV* .</span><span class="sxs-lookup"><span data-stu-id="6a3df-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="6a3df-154">Výběr **mínění** v rozevíracím seznamu **popisek nebo sloupec pro předpověď**</span><span class="sxs-lookup"><span data-stu-id="6a3df-154">Choose **Sentiment** in the **Label or Column to Predict** dropdown</span></span>
1. <span data-ttu-id="6a3df-155">Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="6a3df-155">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="6a3df-156">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-156">Train the model</span></span>

<span data-ttu-id="6a3df-157">Úkolem strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="6a3df-157">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="6a3df-158">V průběhu procesu školení modelů vlacích sestavuje samostatné modely pomocí různých binárních algoritmů klasifikace a nastavení, aby bylo možné najít nejlepší model pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-158">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="6a3df-159">Čas potřebný ke školení modelu je úměrný množství dat.</span><span class="sxs-lookup"><span data-stu-id="6a3df-159">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="6a3df-160">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6a3df-160">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span> 

1. <span data-ttu-id="6a3df-161">I když tvůrce modelů nastaví hodnotu **času na vlak (sekundy)** až 10 sekund, narůstá na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="6a3df-161">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="6a3df-162">Školení po delší dobu umožňuje tvůrci modelů prozkoumat větší počet algoritmů a kombinaci parametrů při hledání nejlepšího modelu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-162">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="6a3df-163">Vyberte **Spustit školení**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-163">Select **Start Training**.</span></span>

    <span data-ttu-id="6a3df-164">V průběhu procesu školení se data o průběhu zobrazují v `Progress` části kroku výuka.</span><span class="sxs-lookup"><span data-stu-id="6a3df-164">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="6a3df-165">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="6a3df-165">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="6a3df-166">Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="6a3df-166">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="6a3df-167">Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.</span><span class="sxs-lookup"><span data-stu-id="6a3df-167">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="6a3df-168">Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="6a3df-168">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="6a3df-169">Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-169">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="6a3df-170">Po dokončení školení vyberte odkaz **vyhodnotit** , který se přesune k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="6a3df-170">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="6a3df-171">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-171">Evaluate the model</span></span>

<span data-ttu-id="6a3df-172">Výsledkem kroku školení bude jeden model, který má nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="6a3df-172">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="6a3df-173">V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v **nejlepším záznamu modelu** spolu se metrikami v **nejlepší kvalitě modelu (RSquared)** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-173">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Quality (RSquared)**.</span></span> <span data-ttu-id="6a3df-174">Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="6a3df-174">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="6a3df-175">Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat.</span><span class="sxs-lookup"><span data-stu-id="6a3df-175">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="6a3df-176">V opačném případě vyberte odkaz **kód** , který se přesune k poslednímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="6a3df-176">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="6a3df-177">Přidejte kód, který provede předpovědi</span><span class="sxs-lookup"><span data-stu-id="6a3df-177">Add the code to make predictions</span></span>

<span data-ttu-id="6a3df-178">V důsledku školicího procesu se vytvoří dva projekty.</span><span class="sxs-lookup"><span data-stu-id="6a3df-178">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="6a3df-179">Odkaz na školený model</span><span class="sxs-lookup"><span data-stu-id="6a3df-179">Reference the trained model</span></span>

1. <span data-ttu-id="6a3df-180">V kroku *kód* nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="6a3df-180">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="6a3df-181">Následující projekty by se měly zobrazit v **Průzkumník řešení**:</span><span class="sxs-lookup"><span data-stu-id="6a3df-181">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="6a3df-182">*SentimentRazorML. ConsoleApp*: Konzolová aplikace .NET Core, která obsahuje kód pro školení a předpověď modelu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-182">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="6a3df-183">*SentimentRazorML. model*: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu a také trvalou verzi modelu nejlepšího provádění během školení.</span><span class="sxs-lookup"><span data-stu-id="6a3df-183">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

    <span data-ttu-id="6a3df-184">Pro tento kurz je použit pouze projekt *SentimentRazorML. model* , protože předpovědi bude vytvořen ve webové aplikaci *SentimentRazor* , nikoli v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="6a3df-184">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="6a3df-185">I když se *SentimentRazorML. ConsoleApp* nebude používat pro vyhodnocování, dá se použít k reučení modelu pomocí nových dat později.</span><span class="sxs-lookup"><span data-stu-id="6a3df-185">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="6a3df-186">Přeškolení je mimo rámec tohoto kurzu, ale.</span><span class="sxs-lookup"><span data-stu-id="6a3df-186">Retraining is outside the scope of this tutorial though.</span></span>

1. <span data-ttu-id="6a3df-187">Chcete-li použít trained model uvnitř vaší aplikace Razor Pages, přidejte odkaz na projekt *SentimentRazorML. model* .</span><span class="sxs-lookup"><span data-stu-id="6a3df-187">To use the trained model inside your Razor Pages application, add a reference to the *SentimentRazorML.Model* project.</span></span>

    1. <span data-ttu-id="6a3df-188">Klikněte pravým tlačítkem na projekt **SentimentRazor** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-188">Right-click **SentimentRazor** project.</span></span> 
    1. <span data-ttu-id="6a3df-189">Vyberte **přidat > odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-189">Select **Add > Reference**.</span></span> 
    1. <span data-ttu-id="6a3df-190">Vyberte **projekty > uzel řešení** a ze seznamu ověřte projekt **SentimentRazorML. model** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-190">Choose the **Projects > Solution** node and from the list, check the **SentimentRazorML.Model** project.</span></span>
    1. <span data-ttu-id="6a3df-191">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-191">Select **OK**.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="6a3df-192">Konfigurace PredictionEngine fondu</span><span class="sxs-lookup"><span data-stu-id="6a3df-192">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="6a3df-193">K provedení jedné předpovědi použijte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="6a3df-193">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="6a3df-194">Aby bylo možné použít [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) aplikaci v aplikaci, je nutné ji v případě potřeby vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6a3df-194">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application, you must create it when it's needed.</span></span> <span data-ttu-id="6a3df-195">V takovém případě je osvědčeným postupem použití injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="6a3df-195">In that case, a best practice to consider is dependency injection.</span></span>

> [!WARNING]
> <span data-ttu-id="6a3df-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="6a3df-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="6a3df-197">Pro zlepšení výkonu a bezpečnosti vláken použijte `PredictionEnginePool` službu, která [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) vytvoří `PredictionEngine` objekty pro použití aplikací.</span><span class="sxs-lookup"><span data-stu-id="6a3df-197">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="6a3df-198">Další informace o [vytváření a používání `PredictionEngine` fondů objektů v ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)najdete v tomto blogovém příspěvku.</span><span class="sxs-lookup"><span data-stu-id="6a3df-198">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

1. <span data-ttu-id="6a3df-199">Nainstalujte balíček NuGet *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="6a3df-199">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="6a3df-200">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-200">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> 
    1. <span data-ttu-id="6a3df-201">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="6a3df-201">Choose "nuget.org" as the Package source.</span></span> 
    1. <span data-ttu-id="6a3df-202">Vyberte kartu **Procházet** a vyhledejte **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="6a3df-202">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span> 
    1. <span data-ttu-id="6a3df-203">Vyberte balíček v seznamu a klikněte na tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-203">Select the package in the list, and select the **Install** button.</span></span> 
    1. <span data-ttu-id="6a3df-204">V dialogovém okně **Náhled změn** klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-204">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="6a3df-205">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="6a3df-205">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> 

1. <span data-ttu-id="6a3df-206">Otevřete soubor *Startup.cs* v projektu *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="6a3df-206">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="6a3df-207">Přidejte následující příkazy using pro odkazování na balíček NuGet *Microsoft.Extensions.ml* a projekt *SentimentRazorML. model* :</span><span class="sxs-lookup"><span data-stu-id="6a3df-207">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]        

1. <span data-ttu-id="6a3df-208">Vytvořte globální proměnnou pro uložení umístění trained modelového souboru.</span><span class="sxs-lookup"><span data-stu-id="6a3df-208">Create a global variable to store the location of the trained model file.</span></span>

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. <span data-ttu-id="6a3df-209">Soubor modelu je uložen v adresáři buildu spolu se soubory sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a3df-209">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="6a3df-210">Aby byl přístup snazší, vytvořte pomocnou metodu volanou `GetAbsolutePath` `Configure` za metodou.</span><span class="sxs-lookup"><span data-stu-id="6a3df-210">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. <span data-ttu-id="6a3df-211">Použijte metodu v konstruktoru`_modelPath`třídypronastavení. `Startup` `GetAbsolutePath`</span><span class="sxs-lookup"><span data-stu-id="6a3df-211">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. <span data-ttu-id="6a3df-212">Nakonfigurujte pro aplikaci v `ConfigureServices`metodě: `PredictionEnginePool`</span><span class="sxs-lookup"><span data-stu-id="6a3df-212">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="6a3df-213">Vytvořit obslužnou rutinu analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="6a3df-213">Create sentiment analysis handler</span></span>

<span data-ttu-id="6a3df-214">Předpovědi se provede uvnitř hlavní stránky aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a3df-214">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="6a3df-215">Proto metoda, která přijímá vstup uživatele a používá `PredictionEnginePool` k vrácení předpovědi, je nutné přidat.</span><span class="sxs-lookup"><span data-stu-id="6a3df-215">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="6a3df-216">Otevřete soubor *index.cshtml.cs* umístěný v adresáři *stránky* a přidejte následující příkazy using:</span><span class="sxs-lookup"><span data-stu-id="6a3df-216">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    <span data-ttu-id="6a3df-217">Aby bylo možné použít `PredictionEnginePool` konfiguraci `Startup` ve třídě, je nutné ji vložit do konstruktoru modelu, kde jej chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6a3df-217">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span> 

1. <span data-ttu-id="6a3df-218">Přidejte proměnnou pro odkazování `PredictionEnginePool` `IndexModel` uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="6a3df-218">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. <span data-ttu-id="6a3df-219">Vytvořte ve `IndexModel` třídě konstruktor a `PredictionEnginePool` založit do něj službu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-219">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. <span data-ttu-id="6a3df-220">Vytvořte obslužnou rutinu metody, která `PredictionEnginePool` používá k vytvoření předpovědi ze vstupu uživatele přijatého z webové stránky.</span><span class="sxs-lookup"><span data-stu-id="6a3df-220">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="6a3df-221">`OnGet` Pod metodou vytvořte novou metodu s názvem.`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="6a3df-221">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="6a3df-222">V rámci metody vrátí neutrální mínění, pokud je vstup od uživatele prázdný nebo má hodnotu null. `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="6a3df-222">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)] 
    
    1. <span data-ttu-id="6a3df-223">Když je zadaný platný vstup, vytvoří se nová instance `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="6a3df-223">Given a valid input, create a new instance of `ModelInput`.</span></span> 

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)] 

    1. <span data-ttu-id="6a3df-224">`PredictionEnginePool` Použijte k předpovídání mínění.</span><span class="sxs-lookup"><span data-stu-id="6a3df-224">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)] 

    1. <span data-ttu-id="6a3df-225">Převeďte předpovězenou `bool` hodnotu na toxické nebo netoxické pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="6a3df-225">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. <span data-ttu-id="6a3df-226">Nakonec vraťte mínění zpět na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="6a3df-226">Finally, return the sentiment back to the web page.</span></span>

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a><span data-ttu-id="6a3df-227">Konfigurace webové stránky</span><span class="sxs-lookup"><span data-stu-id="6a3df-227">Configure the web page</span></span>

<span data-ttu-id="6a3df-228">Výsledky vrácené nástrojem `OnGetAnalyzeSentiment` budou dynamicky zobrazeny `Index` na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="6a3df-228">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="6a3df-229">Otevřete soubor *index. cshtml* v adresáři *stránky* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6a3df-229">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span> 

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="6a3df-230">Pak na konec stránky *. CSS* v adresáři *wwwroot\css* přidejte kód CSS stylu:</span><span class="sxs-lookup"><span data-stu-id="6a3df-230">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="6a3df-231">Pak přidejte kód, který odešle vstupy z webové stránky do `OnGetAnalyzeSentiment` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6a3df-231">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="6a3df-232">V souboru *site. js* v adresáři *wwwroot\js* vytvořte funkci s názvem `getSentiment` , která vytvoří požadavek GET http `OnGetAnalyzeSentiment` s uživatelským vstupem k obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="6a3df-232">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="6a3df-233">Níže přidejte další funkci nazvanou `updateMarker` , která dynamicky aktualizuje pozici značky na webové stránce, protože mínění je předpovězeno.</span><span class="sxs-lookup"><span data-stu-id="6a3df-233">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="6a3df-234">Vytvořte funkci obslužné rutiny události `updateSentiment` volanou k získání vstupu z uživatele, odešlete ji `OnGetAnalyzeSentiment` funkci pomocí `getSentiment` funkce a aktualizujte značku pomocí `updateMarker` funkce.</span><span class="sxs-lookup"><span data-stu-id="6a3df-234">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="6a3df-235">Nakonec zaregistrujte obslužnou rutinu události a navažte `textarea` ji na element `id=Message` s atributem.</span><span class="sxs-lookup"><span data-stu-id="6a3df-235">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="6a3df-236">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="6a3df-236">Run the application</span></span>

<span data-ttu-id="6a3df-237">Teď, když je vaše aplikace nastavená, spusťte aplikaci, která by se měla spustit ve vašem prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="6a3df-237">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="6a3df-238">Až se aplikace spustí, zadejte *Tvůrce modelů.*</span><span class="sxs-lookup"><span data-stu-id="6a3df-238">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="6a3df-239">do textové oblasti.</span><span class="sxs-lookup"><span data-stu-id="6a3df-239">into the text area.</span></span> <span data-ttu-id="6a3df-240">Zobrazený předpokládaný mínění by neměl být *toxický*.</span><span class="sxs-lookup"><span data-stu-id="6a3df-240">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="6a3df-241">Pokud potřebujete odkazovat na projekty vygenerované tvůrcem modelu později v jiném řešení, můžete je najít v `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáři.</span><span class="sxs-lookup"><span data-stu-id="6a3df-241">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6a3df-242">Další postup</span><span class="sxs-lookup"><span data-stu-id="6a3df-242">Next steps</span></span>

<span data-ttu-id="6a3df-243">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="6a3df-243">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6a3df-244">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6a3df-244">Create an ASP.NET Core Razor Pages application</span></span>
> * <span data-ttu-id="6a3df-245">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-245">Prepare and understand the data</span></span>
> * <span data-ttu-id="6a3df-246">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="6a3df-246">Choose a scenario</span></span>
> * <span data-ttu-id="6a3df-247">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6a3df-247">Load the data</span></span>
> * <span data-ttu-id="6a3df-248">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-248">Train the model</span></span>
> * <span data-ttu-id="6a3df-249">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6a3df-249">Evaluate the model</span></span>
> * <span data-ttu-id="6a3df-250">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6a3df-250">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6a3df-251">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="6a3df-251">Additional Resources</span></span>

<span data-ttu-id="6a3df-252">Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="6a3df-252">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="6a3df-253">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="6a3df-253">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="6a3df-254">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="6a3df-254">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="6a3df-255">Metriky modelu binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="6a3df-255">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)