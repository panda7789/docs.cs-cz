---
title: 'Kurz: analýza klasifikace mínění-Binary'
description: V tomto kurzu se dozvíte, jak vytvořit aplikaci Razor Pages, která klasifikuje mínění z komentářů k webu a provede příslušnou akci. Binární mínění klasifikátoru používá tvůrce modelů v aplikaci Visual Studio.
ms.date: 09/30/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ce64f0d11b1da65e460235fdabc2b07e05ffcbe4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700914"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="33efe-104">Kurz: analýza mínění komentářů k webu ve webové aplikaci pomocí Tvůrce modelů ML.NET</span><span class="sxs-lookup"><span data-stu-id="33efe-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="33efe-105">Naučte se analyzovat mínění z komentářů v reálném čase uvnitř webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="33efe-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="33efe-106">V tomto kurzu se dozvíte, jak vytvořit aplikaci ASP.NET Core Razor Pages, která klasifikuje mínění z komentářů k webům v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="33efe-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="33efe-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="33efe-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="33efe-108">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="33efe-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="33efe-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="33efe-110">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="33efe-110">Choose a scenario</span></span>
> - <span data-ttu-id="33efe-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-111">Load the data</span></span>
> - <span data-ttu-id="33efe-112">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-112">Train the model</span></span>
> - <span data-ttu-id="33efe-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-113">Evaluate the model</span></span>
> - <span data-ttu-id="33efe-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="33efe-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="33efe-115">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="33efe-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="33efe-116">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="33efe-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="33efe-117">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="33efe-117">Pre-requisites</span></span>

<span data-ttu-id="33efe-118">Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="33efe-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="33efe-119">Vytvoření aplikace Razor Pages</span><span class="sxs-lookup"><span data-stu-id="33efe-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="33efe-120">Vytvořte **aplikaci ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="33efe-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="33efe-121">Otevřete Visual Studio a v řádku nabídek vyberte **soubor > nový > projekt** .</span><span class="sxs-lookup"><span data-stu-id="33efe-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="33efe-122">V dialogovém okně Nový projekt vyberte uzel  **C# vizuálu** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="33efe-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="33efe-123">Pak vyberte šablonu projektu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="33efe-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="33efe-124">Do textového pole **název** zadejte "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="33efe-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="33efe-125">Zaškrtávací políčko **vytvořit adresář pro řešení** by mělo být ve výchozím nastavení zaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="33efe-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="33efe-126">Pokud tomu tak není, ověřte ji.</span><span class="sxs-lookup"><span data-stu-id="33efe-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="33efe-127">Klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="33efe-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="33efe-128">Zvolte **Webová aplikace** v okně, které zobrazuje různé typy ASP.NET Core projektů, a pak vyberte tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="33efe-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="33efe-129">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-129">Prepare and understand the data</span></span>

<span data-ttu-id="33efe-130">Stáhněte si [datovou sadu Detox Wikipedii](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="33efe-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="33efe-131">Po otevření webové stránky klikněte na ni pravým tlačítkem myši, vyberte **Uložit jako** a uložte soubor kdekoli v počítači.</span><span class="sxs-lookup"><span data-stu-id="33efe-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="33efe-132">Každý řádek v datové sadě *Wikipedii-Detox-250-line-data. TSV* představuje jinou revizi, kterou si uživatel na Wikipedii nanechal.</span><span class="sxs-lookup"><span data-stu-id="33efe-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="33efe-133">První sloupec představuje mínění textu (0 je non-toxický, 1 je toxický) a druhý sloupec představuje komentář, který opustil uživatel.</span><span class="sxs-lookup"><span data-stu-id="33efe-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="33efe-134">Sloupce jsou oddělené kartami.</span><span class="sxs-lookup"><span data-stu-id="33efe-134">The columns are separated by tabs.</span></span> <span data-ttu-id="33efe-135">Data vypadají jako následující:</span><span class="sxs-lookup"><span data-stu-id="33efe-135">The data looks like the following:</span></span>

| <span data-ttu-id="33efe-136">mínění</span><span class="sxs-lookup"><span data-stu-id="33efe-136">Sentiment</span></span> | <span data-ttu-id="33efe-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="33efe-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="33efe-138">první</span><span class="sxs-lookup"><span data-stu-id="33efe-138">1</span></span> | <span data-ttu-id="33efe-139">= = HRUBÉ = = Dude, jste hrubé nahráli obrázek Carl, nebo jiný.</span><span class="sxs-lookup"><span data-stu-id="33efe-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="33efe-140">první</span><span class="sxs-lookup"><span data-stu-id="33efe-140">1</span></span> | <span data-ttu-id="33efe-141">= = OK!</span><span class="sxs-lookup"><span data-stu-id="33efe-141">== OK!</span></span> <span data-ttu-id="33efe-142">= = IM VANDALIZE VOLNĚ ŽIJÍCÍ NA WIKIWEBU A POTOM!!!</span><span class="sxs-lookup"><span data-stu-id="33efe-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="33efe-143">0,8</span><span class="sxs-lookup"><span data-stu-id="33efe-143">0</span></span> | <span data-ttu-id="33efe-144">Doufám, že vám to pomůže.</span><span class="sxs-lookup"><span data-stu-id="33efe-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="33efe-145">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="33efe-145">Choose a scenario</span></span>

![Průvodce tvůrcem modelů v aplikaci Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="33efe-147">Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="33efe-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="33efe-148">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt *SentimentRazor* a vyberte **Přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="33efe-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="33efe-149">V této ukázce je scénář analýzou mínění.</span><span class="sxs-lookup"><span data-stu-id="33efe-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="33efe-150">V kroku *scénář* nástroje Tvůrce modelů vyberte **Analýza mínění** scénář.</span><span class="sxs-lookup"><span data-stu-id="33efe-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="33efe-151">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-151">Load the data</span></span>

<span data-ttu-id="33efe-152">Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve formátu `csv` nebo `tsv`.</span><span class="sxs-lookup"><span data-stu-id="33efe-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="33efe-153">V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat **soubor** .</span><span class="sxs-lookup"><span data-stu-id="33efe-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="33efe-154">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů vyhledejte a vyberte soubor *Wikipedii-Detox-250-line-data. TSV* .</span><span class="sxs-lookup"><span data-stu-id="33efe-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="33efe-155">V rozevíracím seznamu **sloupec pro předpověď (popisek)** vyberte **mínění** .</span><span class="sxs-lookup"><span data-stu-id="33efe-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="33efe-156">Ponechte výchozí hodnoty rozevíracího seznamu **vstupních sloupců (funkce)** .</span><span class="sxs-lookup"><span data-stu-id="33efe-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="33efe-157">Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="33efe-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="33efe-158">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-158">Train the model</span></span>

<span data-ttu-id="33efe-159">Úkolem strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="33efe-159">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="33efe-160">V průběhu procesu školení modelů vlacích sestavuje samostatné modely pomocí různých binárních algoritmů klasifikace a nastavení, aby bylo možné najít nejlepší model pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="33efe-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="33efe-161">Čas potřebný ke školení modelu je úměrný množství dat.</span><span class="sxs-lookup"><span data-stu-id="33efe-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="33efe-162">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="33efe-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="33efe-163">I když tvůrce modelů nastaví hodnotu **času na vlak (sekundy)** až 10 sekund, narůstá na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="33efe-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="33efe-164">Školení po delší dobu umožňuje tvůrci modelů prozkoumat větší počet algoritmů a kombinaci parametrů při hledání nejlepšího modelu.</span><span class="sxs-lookup"><span data-stu-id="33efe-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="33efe-165">Vyberte **Spustit školení**.</span><span class="sxs-lookup"><span data-stu-id="33efe-165">Select **Start Training**.</span></span>

    <span data-ttu-id="33efe-166">V průběhu procesu školení se data o průběhu zobrazují v části `Progress` kroku výukového programu.</span><span class="sxs-lookup"><span data-stu-id="33efe-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="33efe-167">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="33efe-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="33efe-168">Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="33efe-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="33efe-169">Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.</span><span class="sxs-lookup"><span data-stu-id="33efe-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="33efe-170">Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="33efe-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="33efe-171">Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="33efe-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="33efe-172">Po dokončení školení vyberte odkaz **vyhodnotit** , který se přesune k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="33efe-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="33efe-173">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-173">Evaluate the model</span></span>

<span data-ttu-id="33efe-174">Výsledkem kroku školení bude jeden model, který má nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="33efe-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="33efe-175">V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v **nejlepším záznamu modelu** spolu se metrikami v **nejvyšší přesnosti modelu**.</span><span class="sxs-lookup"><span data-stu-id="33efe-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="33efe-176">Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="33efe-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="33efe-177">Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat.</span><span class="sxs-lookup"><span data-stu-id="33efe-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="33efe-178">V opačném případě vyberte odkaz **kód** , který se přesune k poslednímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="33efe-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="33efe-179">Přidejte kód, který provede předpovědi</span><span class="sxs-lookup"><span data-stu-id="33efe-179">Add the code to make predictions</span></span>

<span data-ttu-id="33efe-180">V důsledku školicího procesu se vytvoří dva projekty.</span><span class="sxs-lookup"><span data-stu-id="33efe-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="33efe-181">Odkaz na školený model</span><span class="sxs-lookup"><span data-stu-id="33efe-181">Reference the trained model</span></span>

1. <span data-ttu-id="33efe-182">V kroku *kód* nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="33efe-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="33efe-183">Následující projekty by se měly zobrazit v **Průzkumník řešení**:</span><span class="sxs-lookup"><span data-stu-id="33efe-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="33efe-184">*SentimentRazorML. ConsoleApp*: Konzolová aplikace .NET Core, která obsahuje kód pro školení a předpověď modelu.</span><span class="sxs-lookup"><span data-stu-id="33efe-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="33efe-185">*SentimentRazorML. model*: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu a také uloženou verzi modelu nejlepšího provádění během školení.</span><span class="sxs-lookup"><span data-stu-id="33efe-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="33efe-186">Pro tento kurz je použit pouze projekt *SentimentRazorML. model* , protože předpovědi bude vytvořen ve webové aplikaci *SentimentRazor* , nikoli v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="33efe-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="33efe-187">I když se *SentimentRazorML. ConsoleApp* nebude používat pro vyhodnocování, dá se použít k reučení modelu pomocí nových dat později.</span><span class="sxs-lookup"><span data-stu-id="33efe-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="33efe-188">Přeškolení je mimo rámec tohoto kurzu, ale.</span><span class="sxs-lookup"><span data-stu-id="33efe-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="33efe-189">Konfigurace PredictionEngine fondu</span><span class="sxs-lookup"><span data-stu-id="33efe-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="33efe-190">Chcete-li udělat jednu předpověď, je nutné vytvořit [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="33efe-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="33efe-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="33efe-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="33efe-192">Kromě toho musíte vytvořit instanci, která je všude, kde je to potřeba v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="33efe-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="33efe-193">Jak vaše aplikace roste, tento proces může být nespravovatelný.</span><span class="sxs-lookup"><span data-stu-id="33efe-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="33efe-194">Pro zlepšení výkonu a zabezpečení vlákna použijte kombinaci injektáže a `PredictionEnginePool`, která vytvoří [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) objektů [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="33efe-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="33efe-195">Nainstalujte balíček NuGet *Microsoft.Extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="33efe-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="33efe-196">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="33efe-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="33efe-197">Jako zdroj balíčku vyberte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="33efe-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="33efe-198">Vyberte kartu **Procházet** a vyhledejte **Microsoft.Extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="33efe-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="33efe-199">Vyberte balíček v seznamu a klikněte na tlačítko **instalovat** .</span><span class="sxs-lookup"><span data-stu-id="33efe-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="33efe-200">V dialogovém okně **Náhled změn** klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="33efe-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="33efe-201">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, v dialogu pro **přijetí licence** vyberte tlačítko **přijmout** .</span><span class="sxs-lookup"><span data-stu-id="33efe-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="33efe-202">Otevřete soubor *Startup.cs* v projektu *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="33efe-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="33efe-203">Přidejte následující příkazy using pro odkazování na balíček NuGet *Microsoft.Extensions.ml* a projekt *SentimentRazorML. model* :</span><span class="sxs-lookup"><span data-stu-id="33efe-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="33efe-204">Vytvořte globální proměnnou pro uložení umístění trained modelového souboru.</span><span class="sxs-lookup"><span data-stu-id="33efe-204">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="33efe-205">Soubor modelu je uložen v adresáři buildu spolu se soubory sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="33efe-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="33efe-206">Aby byl přístup snazší, vytvořte pomocnou metodu nazvanou `GetAbsolutePath` po metodě `Configure`.</span><span class="sxs-lookup"><span data-stu-id="33efe-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }    
    ```

1. <span data-ttu-id="33efe-207">K nastavení `_modelPath` použijte metodu `GetAbsolutePath` v konstruktoru třídy `Startup`.</span><span class="sxs-lookup"><span data-stu-id="33efe-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="33efe-208">Nakonfigurujte `PredictionEnginePool` pro aplikaci v metodě `ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="33efe-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="33efe-209">Vytvořit obslužnou rutinu analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="33efe-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="33efe-210">Předpovědi se provede uvnitř hlavní stránky aplikace.</span><span class="sxs-lookup"><span data-stu-id="33efe-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="33efe-211">Proto metoda, která přijímá vstup uživatele a používá `PredictionEnginePool` k vrácení předpovědi, je nutné přidat.</span><span class="sxs-lookup"><span data-stu-id="33efe-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="33efe-212">Otevřete soubor *index.cshtml.cs* umístěný v adresáři *stránky* a přidejte následující příkazy using:</span><span class="sxs-lookup"><span data-stu-id="33efe-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="33efe-213">Aby bylo možné použít `PredictionEnginePool` nakonfigurované ve třídě `Startup`, je nutné ji vložit do konstruktoru modelu, kde jej chcete použít.</span><span class="sxs-lookup"><span data-stu-id="33efe-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="33efe-214">Přidejte proměnnou pro odkazování na `PredictionEnginePool` uvnitř třídy `IndexModel`.</span><span class="sxs-lookup"><span data-stu-id="33efe-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="33efe-215">Vytvořte konstruktor ve třídě `IndexModel` a do něj vloží službu `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="33efe-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }    
    ```

1. <span data-ttu-id="33efe-216">Vytvořte obslužnou rutinu metody, která používá `PredictionEnginePool` k provedení předpovědi ze vstupu uživatele přijatého z webové stránky.</span><span class="sxs-lookup"><span data-stu-id="33efe-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="33efe-217">Pod metodou `OnGet` vytvořte novou metodu nazvanou `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="33efe-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="33efe-218">Uvnitř metody `OnGetAnalyzeSentiment` vrátí *neutrální* mínění, pokud je vstup od uživatele prázdný nebo má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="33efe-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="33efe-219">Když je zadaný platný vstup, vytvoří se nová instance `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="33efe-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="33efe-220">K předvídání mínění použijte `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="33efe-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="33efe-221">Převeďte předpokládanou hodnotu `bool` na toxické nebo netoxické pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="33efe-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="33efe-222">Nakonec vraťte mínění zpět na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="33efe-222">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="33efe-223">Konfigurace webové stránky</span><span class="sxs-lookup"><span data-stu-id="33efe-223">Configure the web page</span></span>

<span data-ttu-id="33efe-224">Výsledky vrácené `OnGetAnalyzeSentiment` budou dynamicky zobrazeny na webové stránce `Index`.</span><span class="sxs-lookup"><span data-stu-id="33efe-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="33efe-225">Otevřete soubor *index. cshtml* v adresáři *stránky* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="33efe-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="33efe-226">Pak na konec stránky *. CSS* v adresáři *wwwroot\css* přidejte kód CSS stylu:</span><span class="sxs-lookup"><span data-stu-id="33efe-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="33efe-227">Pak přidejte kód, který odešle vstupy z webové stránky do obslužné rutiny `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="33efe-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="33efe-228">V souboru *site. js* umístěném v adresáři *wwwroot\js* vytvořte funkci s názvem `getSentiment`, která vytvoří požadavek GET http s uživatelským vstupem k obslužné rutině `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="33efe-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="33efe-229">Níže přidejte další funkci s názvem `updateMarker`, aby se dynamicky aktualizovala pozice značky na webové stránce, protože mínění je předpokládaná.</span><span class="sxs-lookup"><span data-stu-id="33efe-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="33efe-230">Vytvořte funkci obslužné rutiny události nazvanou `updateSentiment` pro získání vstupu od uživatele, odešlete ji do funkce `OnGetAnalyzeSentiment` pomocí funkce `getSentiment` a aktualizujte značku pomocí funkce `updateMarker`.</span><span class="sxs-lookup"><span data-stu-id="33efe-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="33efe-231">Nakonec zaregistrujte obslužnou rutinu události a navažte ji k elementu `textarea` s atributem `id=Message`.</span><span class="sxs-lookup"><span data-stu-id="33efe-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="33efe-232">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="33efe-232">Run the application</span></span>

<span data-ttu-id="33efe-233">Teď, když je vaše aplikace nastavená, spusťte aplikaci, která by se měla spustit ve vašem prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="33efe-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="33efe-234">Až se aplikace spustí, zadejte *Tvůrce modelů.*</span><span class="sxs-lookup"><span data-stu-id="33efe-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="33efe-235">do textové oblasti.</span><span class="sxs-lookup"><span data-stu-id="33efe-235">into the text area.</span></span> <span data-ttu-id="33efe-236">Zobrazený předpokládaný mínění by neměl být *toxický*.</span><span class="sxs-lookup"><span data-stu-id="33efe-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Spuštění okna s předpokládaným oknem mínění](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="33efe-238">Pokud potřebujete odkazovat na projekty generované tvůrcem modelů později v jiném řešení, můžete je najít v adresáři `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="33efe-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="33efe-239">Další kroky</span><span class="sxs-lookup"><span data-stu-id="33efe-239">Next steps</span></span>

<span data-ttu-id="33efe-240">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="33efe-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="33efe-241">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="33efe-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="33efe-242">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="33efe-243">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="33efe-243">Choose a scenario</span></span>
> - <span data-ttu-id="33efe-244">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="33efe-244">Load the data</span></span>
> - <span data-ttu-id="33efe-245">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-245">Train the model</span></span>
> - <span data-ttu-id="33efe-246">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="33efe-246">Evaluate the model</span></span>
> - <span data-ttu-id="33efe-247">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="33efe-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="33efe-248">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="33efe-248">Additional Resources</span></span>

<span data-ttu-id="33efe-249">Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="33efe-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="33efe-250">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="33efe-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="33efe-251">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="33efe-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="33efe-252">Metriky modelu binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="33efe-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
