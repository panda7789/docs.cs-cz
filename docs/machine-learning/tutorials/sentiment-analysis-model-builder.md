---
title: 'Kurz: Analýza mínění - binární klasifikace'
description: Tento kurz ukazuje, jak vytvořit aplikaci Razor Pages, která klasifikuje mínění z komentářů na webu a provede příslušnou akci. Binární třídění mínění používá Model Builder v sadě Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 98c9f28ca4ce6365ed4cf4ff1566a33dbe8f35ca
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438233"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="6d054-104">Kurz: Analýza mínění komentářů na webových stránkách ve webové aplikaci pomocí ML.NET Model Builder</span><span class="sxs-lookup"><span data-stu-id="6d054-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="6d054-105">Naučte se analyzovat mínění z komentářů v reálném čase uvnitř webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d054-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="6d054-106">Tento kurz ukazuje, jak vytvořit aplikaci ASP.NET Core Razor Pages, která klasifikuje mínění z komentářů na webu v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="6d054-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="6d054-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="6d054-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="6d054-108">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6d054-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="6d054-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="6d054-110">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="6d054-110">Choose a scenario</span></span>
> - <span data-ttu-id="6d054-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-111">Load the data</span></span>
> - <span data-ttu-id="6d054-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-112">Train the model</span></span>
> - <span data-ttu-id="6d054-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-113">Evaluate the model</span></span>
> - <span data-ttu-id="6d054-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6d054-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="6d054-115">Tvůrce modelů je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="6d054-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="6d054-116">Zdrojový kód pro tento kurz najdete v úložišti [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)</span><span class="sxs-lookup"><span data-stu-id="6d054-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="6d054-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d054-117">Pre-requisites</span></span>

<span data-ttu-id="6d054-118">Seznam předpokladů a pokynů k instalaci naleznete v [instalační příručce výrobce modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="6d054-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="6d054-119">Vytvoření aplikace Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6d054-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="6d054-120">Vytvořte **aplikaci ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="6d054-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="6d054-121">Otevřete Visual Studio a z panelu nabídek vyberte **Soubor > Nový > Project.**</span><span class="sxs-lookup"><span data-stu-id="6d054-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="6d054-122">V dialogovém okně Nový projekt vyberte uzel **Visual C#** následovaný **webovým** uzlem.</span><span class="sxs-lookup"><span data-stu-id="6d054-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="6d054-123">Pak vyberte šablonu projektu **ASP.NET core webová aplikace.**</span><span class="sxs-lookup"><span data-stu-id="6d054-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="6d054-124">Do textového pole **Název** zadejte "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="6d054-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="6d054-125">Ujistěte se, že **umístit řešení a projekt ve stejném adresáři** je **nezaškrtnuté** (VS 2019) nebo **vytvořit adresář pro řešení** je **zaškrtnuto** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="6d054-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="6d054-126">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6d054-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="6d054-127">V okně, které zobrazuje různé typy ASP.NET základní projekty, zvolte **Webová aplikace** a pak vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="6d054-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6d054-128">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-128">Prepare and understand the data</span></span>

<span data-ttu-id="6d054-129">Stáhnout [Wikipedia detox datový soubor](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="6d054-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="6d054-130">Po otevření webové stránky klikněte pravým tlačítkem myši na stránku a vyberte **Uložit jako** a soubor uložte kdekoli v počítači.</span><span class="sxs-lookup"><span data-stu-id="6d054-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="6d054-131">Každý řádek v datové sadě *wikipedia-detox-250-line-data.tsv* představuje jinou recenzi, kterou uživatel zanechal na Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="6d054-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="6d054-132">První sloupec představuje mínění textu (0 je netoxický, 1 je toxický) a druhý sloupec představuje komentář, který uživatel zanechal.</span><span class="sxs-lookup"><span data-stu-id="6d054-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="6d054-133">Sloupce jsou odděleny kartami.</span><span class="sxs-lookup"><span data-stu-id="6d054-133">The columns are separated by tabs.</span></span> <span data-ttu-id="6d054-134">Data vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="6d054-134">The data looks like the following:</span></span>

| <span data-ttu-id="6d054-135">Mínění</span><span class="sxs-lookup"><span data-stu-id="6d054-135">Sentiment</span></span> | <span data-ttu-id="6d054-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="6d054-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="6d054-137">1</span><span class="sxs-lookup"><span data-stu-id="6d054-137">1</span></span> | <span data-ttu-id="6d054-138">==RUDE== Dude, ty jsou hrubý nahrát, že carl obrázek zpět, nebo jinak.</span><span class="sxs-lookup"><span data-stu-id="6d054-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="6d054-139">1</span><span class="sxs-lookup"><span data-stu-id="6d054-139">1</span></span> | <span data-ttu-id="6d054-140">== OK!</span><span class="sxs-lookup"><span data-stu-id="6d054-140">== OK!</span></span> <span data-ttu-id="6d054-141">== IM chystá vandalize wild ones WIKI pak!!!</span><span class="sxs-lookup"><span data-stu-id="6d054-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="6d054-142">0</span><span class="sxs-lookup"><span data-stu-id="6d054-142">0</span></span> | <span data-ttu-id="6d054-143">Doufám, že to pomůže.</span><span class="sxs-lookup"><span data-stu-id="6d054-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="6d054-144">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="6d054-144">Choose a scenario</span></span>

![Průvodce tvůrcem modelů v sadě Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="6d054-146">Chcete-li trénovat model, musíte vybrat ze seznamu dostupných scénářů strojového učení poskytovaných tvůrcem modelů.</span><span class="sxs-lookup"><span data-stu-id="6d054-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="6d054-147">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *SentimentRazor* a vyberte **přidat** > **strojové učení**.</span><span class="sxs-lookup"><span data-stu-id="6d054-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="6d054-148">Pro tuto ukázku je scénář analýza mínění.</span><span class="sxs-lookup"><span data-stu-id="6d054-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="6d054-149">V kroku *scénáře* nástroje Tvůrce modelů vyberte scénář **Analýzy mínění.**</span><span class="sxs-lookup"><span data-stu-id="6d054-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6d054-150">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-150">Load the data</span></span>

<span data-ttu-id="6d054-151">Tvůrce modelů přijímá data ze dvou zdrojů, databáze serveru `csv` `tsv` SQL Server nebo místního souboru ve formátu nebo formátu.</span><span class="sxs-lookup"><span data-stu-id="6d054-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="6d054-152">V datovém kroku nástroje Tvůrce modelů vyberte **Soubor** z rozevíracího souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6d054-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="6d054-153">Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů procházejte a vyberte soubor *wikipedia-detox-250-line-data.tsv.*</span><span class="sxs-lookup"><span data-stu-id="6d054-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="6d054-154">V rozevíracím **seznamu Sloupce zvolte Mínění, které chcete předpovědět (Popisek).** **Sentiment**</span><span class="sxs-lookup"><span data-stu-id="6d054-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="6d054-155">Ponechte výchozí hodnoty pro rozevírací seznam **Vstupní sloupce (Funkce).**</span><span class="sxs-lookup"><span data-stu-id="6d054-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="6d054-156">Vyberte spojení **Vlak,** chcete-li přejít k dalšímu kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="6d054-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="6d054-157">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-157">Train the model</span></span>

<span data-ttu-id="6d054-158">Úloha strojového učení použitá k trénování modelu analýzy mínění v tomto kurzu je binární klasifikace.</span><span class="sxs-lookup"><span data-stu-id="6d054-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="6d054-159">Během procesu školení modelu Model Builder trénuje samostatné modely pomocí různých binárních klasifikačních algoritmů a nastavení, aby našel nejvýkonnější model pro vaši datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="6d054-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="6d054-160">Doba potřebná pro vyškolení modelu je úměrná množství dat.</span><span class="sxs-lookup"><span data-stu-id="6d054-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="6d054-161">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas pro trénování (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6d054-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="6d054-162">Přestože Model Builder nastaví hodnotu **Čas trénovat (sekundy)** na 10 sekund, zvyšte ji na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="6d054-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="6d054-163">Školení pro delší časové zpracování umožňuje Model Builder prozkoumat větší počet algoritmů a kombinace parametrů při hledání nejlepší model.</span><span class="sxs-lookup"><span data-stu-id="6d054-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="6d054-164">Vyberte **možnost Zahájit trénink**.</span><span class="sxs-lookup"><span data-stu-id="6d054-164">Select **Start Training**.</span></span>

    <span data-ttu-id="6d054-165">V průběhu tréninkového procesu se `Progress` údaje o průběhu zobrazují v části kroku vlaku.</span><span class="sxs-lookup"><span data-stu-id="6d054-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="6d054-166">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="6d054-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="6d054-167">Nejlepší přesnost zobrazuje přesnost nejvýkonnějšího modelu, který dosud našel Model Builder.</span><span class="sxs-lookup"><span data-stu-id="6d054-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="6d054-168">Vyšší přesnost znamená, že model byl na testovacích datech předpovězen správněji.</span><span class="sxs-lookup"><span data-stu-id="6d054-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="6d054-169">Nejlepší algoritmus zobrazí název nejvýkonnějšíalgoritmus u kterého našel Model Builder tak daleko.</span><span class="sxs-lookup"><span data-stu-id="6d054-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="6d054-170">Poslední algoritmus zobrazí název algoritmu, který byl naposledy použit tvůrcem modelů k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="6d054-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="6d054-171">Po dokončení tréninku vyberte odkaz **vyhodnocení** a přejděte k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="6d054-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="6d054-172">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-172">Evaluate the model</span></span>

<span data-ttu-id="6d054-173">Výsledkem tréninkového kroku bude jeden model, který měl nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="6d054-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="6d054-174">V kroku vyhodnocení nástroje Tvůrce modelů bude výstupní část obsahovat algoritmus používaný nejvýkonnějším modelem v položce **Nejlepší model** spolu s metrikami v **kategorii Nejlepší přesnost modelu**.</span><span class="sxs-lookup"><span data-stu-id="6d054-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="6d054-175">Kromě toho souhrnná tabulka obsahující prvních pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="6d054-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="6d054-176">Pokud nejste spokojeni s metrikami přesnosti, některé jednoduché způsoby, jak se pokusit zlepšit přesnost modelu, jsou prodloužení doby pro trénování modelu nebo použití více dat.</span><span class="sxs-lookup"><span data-stu-id="6d054-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="6d054-177">V opačném případě vyberte odkaz **kódu,** který chcete přesunout do posledního kroku v nástroji Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="6d054-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="6d054-178">Přidání kódu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="6d054-178">Add the code to make predictions</span></span>

<span data-ttu-id="6d054-179">V důsledku procesu školení budou vytvořeny dva projekty.</span><span class="sxs-lookup"><span data-stu-id="6d054-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="6d054-180">Odkaz na trénovaný model</span><span class="sxs-lookup"><span data-stu-id="6d054-180">Reference the trained model</span></span>

1. <span data-ttu-id="6d054-181">V kroku *kódu* nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="6d054-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="6d054-182">V **Průzkumníku řešení**by se měly objevit následující projekty :</span><span class="sxs-lookup"><span data-stu-id="6d054-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="6d054-183">*SentimentRazorML.ConsoleApp*: Aplikace .NET Core Console, která obsahuje model školení a předpověď kódu.</span><span class="sxs-lookup"><span data-stu-id="6d054-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="6d054-184">*SentimentRazorML.Model*: Knihovna tříd .NET Standard obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, stejně jako uloženou verzi nejvýkonnějšího modelu během trénování.</span><span class="sxs-lookup"><span data-stu-id="6d054-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="6d054-185">Pro účely tohoto kurzu pouze *SentimentRazorML.Model* projektu se používá, protože předpovědi budou provedeny ve webové aplikaci *SentimentRazor* spíše než v konzoli.</span><span class="sxs-lookup"><span data-stu-id="6d054-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="6d054-186">Přestože *SentimentRazorML.ConsoleApp* nebude použit pro vyhodnocování, lze jej použít k přeškolit model pomocí nových dat později.</span><span class="sxs-lookup"><span data-stu-id="6d054-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="6d054-187">Rekvalifikace je mimo rozsah tohoto kurzu ačkoli.</span><span class="sxs-lookup"><span data-stu-id="6d054-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="6d054-188">Konfigurace fondu PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="6d054-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="6d054-189">Chcete-li provést jednu předpověď, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)musíte vytvořit .</span><span class="sxs-lookup"><span data-stu-id="6d054-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="6d054-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)není bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="6d054-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="6d054-191">Navíc je nutné vytvořit instanci všude, kde je potřeba v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d054-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="6d054-192">Jak vaše aplikace roste, tento proces může být nezvladatelný.</span><span class="sxs-lookup"><span data-stu-id="6d054-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="6d054-193">Pro zvýšení výkonu a bezpečnosti podprocesů použijte `PredictionEnginePool` kombinaci vkládání [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) závislostí a služby, která vytvoří objekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pro použití v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6d054-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="6d054-194">Nainstalujte *balíček Microsoft.Extensions.ML* NuGet:</span><span class="sxs-lookup"><span data-stu-id="6d054-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="6d054-195">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **příkaz Spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6d054-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="6d054-196">Jako zdroj balíčku zvolte "nuget.org".</span><span class="sxs-lookup"><span data-stu-id="6d054-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="6d054-197">Vyberte kartu **Procházet** a vyhledejte **Microsoft.Extensions.ML**.</span><span class="sxs-lookup"><span data-stu-id="6d054-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="6d054-198">Vyberte balíček v seznamu a vyberte tlačítko **Instalovat.**</span><span class="sxs-lookup"><span data-stu-id="6d054-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="6d054-199">Výběr tlačítka **OK** v dialogovém okně **Náhled změn**</span><span class="sxs-lookup"><span data-stu-id="6d054-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="6d054-200">Pokud souhlasíte s licenčními podmínkami pro uvedené balíčky, vyberte v dialogovém okně **Přijetí licence** tlačítko **Souhlasím.**</span><span class="sxs-lookup"><span data-stu-id="6d054-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="6d054-201">Otevřete soubor *Startup.cs* v projektu *SentimentRazor.*</span><span class="sxs-lookup"><span data-stu-id="6d054-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="6d054-202">Přidejte následující příkazy pomocí odkazování na *Microsoft.Extensions.ML* NuGet balíček a *SentimentRazorML.Model* projektu:</span><span class="sxs-lookup"><span data-stu-id="6d054-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="6d054-203">Vytvořte globální proměnnou pro uložení umístění trénovaného souboru modelu.</span><span class="sxs-lookup"><span data-stu-id="6d054-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="6d054-204">Soubor modelu je uložen v adresáři sestavení vedle souborů sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d054-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="6d054-205">Chcete-li usnadnit přístup, vytvořte `GetAbsolutePath` pomocnou `Configure` metodu volanou po metodě</span><span class="sxs-lookup"><span data-stu-id="6d054-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="6d054-206">Pomocí `GetAbsolutePath` metody v `Startup` konstruktoru třídy nastavte `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="6d054-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="6d054-207">Nakonfigurujte `PredictionEnginePool` pro `ConfigureServices` vaši aplikaci v metodě:</span><span class="sxs-lookup"><span data-stu-id="6d054-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="6d054-208">Vytvoření obslužné rutiny analýzy mínění</span><span class="sxs-lookup"><span data-stu-id="6d054-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="6d054-209">Předpovědi budou provedeny uvnitř hlavní stránky aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d054-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="6d054-210">Proto je třeba přidat metodu, `PredictionEnginePool` která přebírá vstup uživatele a používá k vrácení předpověď.</span><span class="sxs-lookup"><span data-stu-id="6d054-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="6d054-211">Otevřete *soubor Index.cshtml.cs* umístěný v adresáři *Stránky* a přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="6d054-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="6d054-212">Chcete-li použít `PredictionEnginePool` nakonfigurované ve `Startup` třídě, musíte jej vložit do konstruktoru modelu, kde jej chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6d054-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="6d054-213">Přidejte proměnnou, `PredictionEnginePool` která `IndexModel` odkazuje na vnitřní třídu.</span><span class="sxs-lookup"><span data-stu-id="6d054-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="6d054-214">Vytvořte konstruktor `IndexModel` ve třídě `PredictionEnginePool` a vložte do něj službu.</span><span class="sxs-lookup"><span data-stu-id="6d054-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="6d054-215">Vytvořte obslužnou rutinu `PredictionEnginePool` metody, která používá k vytváření předpovědí z uživatelského vstupu přijatého z webové stránky.</span><span class="sxs-lookup"><span data-stu-id="6d054-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="6d054-216">Pod `OnGet` metodou vytvořte novou metodu nazvanou`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="6d054-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="6d054-217">Uvnitř `OnGetAnalyzeSentiment` metody vrátí *neutrální* mínění, pokud je vstup od uživatele prázdný nebo null.</span><span class="sxs-lookup"><span data-stu-id="6d054-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="6d054-218">Daný platný vstup, vytvořit novou `ModelInput`instanci .</span><span class="sxs-lookup"><span data-stu-id="6d054-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="6d054-219">Použijte `PredictionEnginePool` k předvídání mínění.</span><span class="sxs-lookup"><span data-stu-id="6d054-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="6d054-220">Převeďte `bool` předpokládanou hodnotu na toxickou nebo netoxickou pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="6d054-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="6d054-221">Nakonec vraťte sentiment zpět na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="6d054-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="6d054-222">Konfigurace webové stránky</span><span class="sxs-lookup"><span data-stu-id="6d054-222">Configure the web page</span></span>

<span data-ttu-id="6d054-223">Výsledky vrácené `OnGetAnalyzeSentiment` bude dynamicky zobrazí na `Index` webové stránce.</span><span class="sxs-lookup"><span data-stu-id="6d054-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="6d054-224">Otevřete soubor *Index.cshtml* v adresáři *Stránky* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6d054-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="6d054-225">Dále přidejte kód stylů css na konec stránky *site.css* v adresáři *wwwroot\css:*</span><span class="sxs-lookup"><span data-stu-id="6d054-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="6d054-226">Poté přidejte kód pro odeslání vstupů z `OnGetAnalyzeSentiment` webové stránky do obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6d054-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="6d054-227">V souboru *site.js* umístěném v adresáři *wwwroot\js* vytvořte funkci volanou `getSentiment` `OnGetAnalyzeSentiment` pro vytvoření požadavku GET HTTP se vstupem uživatele do obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6d054-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="6d054-228">Pod tím přidejte `updateMarker` další funkci volanou k dynamické aktualizaci pozice značky na webové stránce podle předpovědi mínění.</span><span class="sxs-lookup"><span data-stu-id="6d054-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="6d054-229">Vytvořte volanou `updateSentiment` funkci obslužné rutiny `OnGetAnalyzeSentiment` události, `getSentiment` abyste získali vstup `updateMarker` od uživatele, odešlete ji do funkce pomocí funkce a aktualizujte značku pomocí funkce.</span><span class="sxs-lookup"><span data-stu-id="6d054-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="6d054-230">Nakonec zaregistrujte obslužnou `textarea` rutinu `id=Message` události a spojte ji s elementem s atributem.</span><span class="sxs-lookup"><span data-stu-id="6d054-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="6d054-231">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="6d054-231">Run the application</span></span>

<span data-ttu-id="6d054-232">Nyní, když je vaše aplikace nastavena, spusťte aplikaci, která by měla být spuštěna ve vašem prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="6d054-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="6d054-233">Když se aplikace spustí, zadejte *Model Builder je v pohodě!*</span><span class="sxs-lookup"><span data-stu-id="6d054-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="6d054-234">do textové oblasti.</span><span class="sxs-lookup"><span data-stu-id="6d054-234">into the text area.</span></span> <span data-ttu-id="6d054-235">Zobrazený předpokládaný názor by neměl být *toxický*.</span><span class="sxs-lookup"><span data-stu-id="6d054-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Spuštěné okno s předpovídaným oknem mínění](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="6d054-237">Pokud potřebujete odkazovat na projekty generované tvůrcem modelů později uvnitř jiného `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` řešení, můžete je najít uvnitř adresáře.</span><span class="sxs-lookup"><span data-stu-id="6d054-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d054-238">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6d054-238">Next steps</span></span>

<span data-ttu-id="6d054-239">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="6d054-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6d054-240">Vytvoření aplikace ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6d054-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="6d054-241">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="6d054-242">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="6d054-242">Choose a scenario</span></span>
> - <span data-ttu-id="6d054-243">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="6d054-243">Load the data</span></span>
> - <span data-ttu-id="6d054-244">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-244">Train the model</span></span>
> - <span data-ttu-id="6d054-245">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="6d054-245">Evaluate the model</span></span>
> - <span data-ttu-id="6d054-246">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="6d054-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6d054-247">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6d054-247">Additional Resources</span></span>

<span data-ttu-id="6d054-248">Další informace o tématech uvedených v tomto kurzu naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="6d054-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="6d054-249">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="6d054-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="6d054-250">Binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="6d054-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="6d054-251">Binární klasifikace model metriky</span><span class="sxs-lookup"><span data-stu-id="6d054-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
