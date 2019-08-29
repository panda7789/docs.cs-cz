---
title: Předpověď cen pomocí regrese pomocí Tvůrce modelů
description: V tomto kurzu se naučíte, jak vytvořit regresní model pomocí Tvůrce modelů ML.NET pro předpověď cen, konkrétně v New Yorku City taxislužby tarifs.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1bdbe31e16408da2d7dfe17941c90a022f3d8c32
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107146"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="b5dc4-103">Předpověď cen pomocí regrese pomocí Tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="b5dc4-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="b5dc4-104">Naučte se používat Tvůrce modelů ML.NET k vytvoření regresního modelu () pro předpověď cen.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="b5dc4-105">Aplikace konzoly .NET, kterou vyvíjíte v tomto kurzu, předpovídá taxislužby tarify na základě historických dat o taxislužby tarifech z historických Praha.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="b5dc4-106">Šablona předpovědi ceny tvůrce modelů se dá použít pro libovolný scénář, který vyžaduje hodnotu číselné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="b5dc4-107">Mezi příklady scénářů patří: předpověď ceny na pracovišti, Předpověď poptávky a prognózování prodeje.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="b5dc4-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b5dc4-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="b5dc4-110">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="b5dc4-110">Choose a scenario</span></span>
> - <span data-ttu-id="b5dc4-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-111">Load the data</span></span>
> - <span data-ttu-id="b5dc4-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-112">Train the model</span></span>
> - <span data-ttu-id="b5dc4-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-113">Evaluate the model</span></span>
> - <span data-ttu-id="b5dc4-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="b5dc4-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="b5dc4-115">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b5dc4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5dc4-116">Pre-requisites</span></span>

<span data-ttu-id="b5dc4-117">Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="b5dc4-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b5dc4-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="b5dc4-118">Create a console application</span></span>

1. <span data-ttu-id="b5dc4-119">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="b5dc4-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b5dc4-120">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="b5dc4-121">Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="b5dc4-122">Sada dat, která se používá ke studiu a vyhodnocení modelu Machine Learning, je původně ze sady dat NYC TLC taxislužby Trip.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    <span data-ttu-id="b5dc4-123">Datovou sadu stáhnete tak, že přejdete na [odkaz ke stažení taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="b5dc4-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    <span data-ttu-id="b5dc4-124">Po načtení stránky klikněte pravým tlačítkem myši kamkoli na stránku a vyberte **Uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    <span data-ttu-id="b5dc4-125">Pomocí **dialogového okna Uložit jako** uložte soubor do složky *data* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="b5dc4-126">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *taxi-Fare-Train. csv* a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="b5dc4-127">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="b5dc4-128">Každý řádek v `taxi-fare-train.csv` datové sadě obsahuje podrobnosti o cestách provedených taxislužby.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="b5dc4-129">Otevřete sadu dat **taxi-Fare-Train. csv.**</span><span class="sxs-lookup"><span data-stu-id="b5dc4-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="b5dc4-130">Poskytnutá datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="b5dc4-131">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="b5dc4-132">**rate_code:** Typ rychlosti taxislužby Trip je funkce.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="b5dc4-133">**passenger_count:** Počet cestujících na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="b5dc4-134">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-134">**trip_time_in_secs:** The amount of time the trip took.</span></span>
    - <span data-ttu-id="b5dc4-135">**trip_distance:** Vzdálenost na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="b5dc4-136">**payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="b5dc4-137">**fare_amount:** Celková částka taxislužby jízdné je štítek.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="b5dc4-138">`label` Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="b5dc4-139">Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="b5dc4-140">V tomto scénáři odhadu cen se předpokládá, že náklady na taxislužby jízdní část budou předpovězeny.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="b5dc4-141">Proto je **fare_amount** jmenovka.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="b5dc4-142">Identifikované `features` jsou vstupy, které modelu poskytnete pro `label`předpověď.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="b5dc4-143">V tomto případě se zbytek sloupců používá jako funkce nebo vstupy pro předpověď množství tarifů.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="b5dc4-144">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="b5dc4-144">Choose a scenario</span></span>

<span data-ttu-id="b5dc4-145">Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="b5dc4-146">V tomto případě je `Price Prediction`to scénář.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-146">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="b5dc4-147">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt *TaxiFarePrediction* a vyberte **Přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="b5dc4-148">V kroku scénář nástroje Tvůrce modelů vyberte možnost scénář *předpovědi cen* .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b5dc4-149">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-149">Load the data</span></span>

<span data-ttu-id="b5dc4-150">Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve formátu CSV nebo TSV.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="b5dc4-151">V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat *soubor* .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="b5dc4-152">Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů Procházejte a vyberte soubor *taxi-Fare-test. csv* v *datovém* adresáři.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="b5dc4-153">V rozevíracím seznamu *popisek nebo sloupec* vyberte *fare_amount* a přejděte do kroku výuka nástroje Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b5dc4-154">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-154">Train the model</span></span>

<span data-ttu-id="b5dc4-155">Úkol strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je regrese.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="b5dc4-156">V průběhu procesu školení modelů vlacích sestaví model modelování samostatné modely pomocí různých regresních algoritmů a nastavení, které pro datovou sadu vyhledají nejlepší model provádění.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="b5dc4-157">Čas potřebný ke školení modelu je úměrný množství dat.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="b5dc4-158">Tento graf použijte jako vodítko pro výběr vhodné hodnoty pro `Time to train (seconds)` pole:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="b5dc4-159">\* Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="b5dc4-159">\*Dataset Size</span></span>  | <span data-ttu-id="b5dc4-160">Typ datové sady</span><span class="sxs-lookup"><span data-stu-id="b5dc4-160">Dataset Type</span></span>       | <span data-ttu-id="b5dc4-161">Střední Čas do výuky \*</span><span class="sxs-lookup"><span data-stu-id="b5dc4-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="b5dc4-162">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="b5dc4-162">0 - 10 Mb</span></span>     | <span data-ttu-id="b5dc4-163">Číslice a text</span><span class="sxs-lookup"><span data-stu-id="b5dc4-163">Numeric and Text</span></span>   | <span data-ttu-id="b5dc4-164">10 sekund</span><span class="sxs-lookup"><span data-stu-id="b5dc4-164">10 sec</span></span>
<span data-ttu-id="b5dc4-165">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="b5dc4-165">10 - 100 Mb</span></span>   | <span data-ttu-id="b5dc4-166">Číslice a text</span><span class="sxs-lookup"><span data-stu-id="b5dc4-166">Numeric and Text</span></span>   | <span data-ttu-id="b5dc4-167">10 min</span><span class="sxs-lookup"><span data-stu-id="b5dc4-167">10 min</span></span>
<span data-ttu-id="b5dc4-168">100 – 500 MB</span><span class="sxs-lookup"><span data-stu-id="b5dc4-168">100 - 500 Mb</span></span>  | <span data-ttu-id="b5dc4-169">Číslice a text</span><span class="sxs-lookup"><span data-stu-id="b5dc4-169">Numeric and Text</span></span>   | <span data-ttu-id="b5dc4-170">30 min</span><span class="sxs-lookup"><span data-stu-id="b5dc4-170">30 min</span></span>
<span data-ttu-id="b5dc4-171">500 - 1 Gb</span><span class="sxs-lookup"><span data-stu-id="b5dc4-171">500 - 1 Gb</span></span>    | <span data-ttu-id="b5dc4-172">Číslice a text</span><span class="sxs-lookup"><span data-stu-id="b5dc4-172">Numeric and Text</span></span>   | <span data-ttu-id="b5dc4-173">60 min.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-173">60 min</span></span>
<span data-ttu-id="b5dc4-174">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="b5dc4-174">1 Gb+</span></span>         | <span data-ttu-id="b5dc4-175">Číslice a text</span><span class="sxs-lookup"><span data-stu-id="b5dc4-175">Numeric and Text</span></span>   | <span data-ttu-id="b5dc4-176">3 hodiny +</span><span class="sxs-lookup"><span data-stu-id="b5dc4-176">3 hour+</span></span>

1. <span data-ttu-id="b5dc4-177">Vzhledem k tomu, že soubor školicích dat je větší než 10 MB, jako hodnota *Time to vlak (sekundy)* použijte 600 sekund (10 minut).</span><span class="sxs-lookup"><span data-stu-id="b5dc4-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="b5dc4-178">Vyberte *Spustit školení*.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-178">Select *Start Training*.</span></span>

<span data-ttu-id="b5dc4-179">V průběhu procesu školení se data o průběhu zobrazují v `Progress` části kroku výuka.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="b5dc4-180">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="b5dc4-181">Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="b5dc4-182">Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="b5dc4-183">Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="b5dc4-184">Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="b5dc4-185">Po dokončení školení přejděte k kroku vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="b5dc4-186">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-186">Evaluate the model</span></span>

<span data-ttu-id="b5dc4-187">Výsledkem kroku školení bude jeden model, který má nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="b5dc4-188">V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v *nejlepším záznamu modelu* spolu se metrikami v *nejlepší kvalitě modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="b5dc4-189">Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-189">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="b5dc4-190">Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="b5dc4-191">V opačném případě přejděte do kroku Code (kód).</span><span class="sxs-lookup"><span data-stu-id="b5dc4-191">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="b5dc4-192">Přidejte kód, který provede předpovědi</span><span class="sxs-lookup"><span data-stu-id="b5dc4-192">Add the code to make predictions</span></span>

<span data-ttu-id="b5dc4-193">V důsledku školicího procesu se vytvoří dva projekty.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="b5dc4-194">TaxiFarePredictionML.ConsoleApp: Konzolová aplikace .NET Core, která obsahuje kód pro školení a spotřebu modelu.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="b5dc4-195">TaxiFarePredictionML.Model: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu a také trvalou verzi modelu nejlepšího provádění během školení.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="b5dc4-196">V kroku kód nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="b5dc4-197">Klikněte pravým tlačítkem na projekt *TaxiFarePrediction* .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="b5dc4-198">Pak **přidejte odkaz >** .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="b5dc4-199">Zvolte **projekty > uzel řešení** a ze seznamu zaškrtněte projekt *TaxiFarePredictionML. model* a vyberte OK.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="b5dc4-200">Otevřete soubor *program.cs* v projektu *TaxiFarePrediction* .</span><span class="sxs-lookup"><span data-stu-id="b5dc4-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="b5dc4-201">Přidejte následující příkazy using pro odkazování na balíček NuGet *Microsoft.ml* a projekt *TaxiFarePredictionML. model* :</span><span class="sxs-lookup"><span data-stu-id="b5dc4-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="b5dc4-202">`ConsumeModel` Přidejte metodu`Program` do třídy.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-202">Add the `ConsumeModel` method to the `Program` class.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

    <span data-ttu-id="b5dc4-203">Načte školený model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) vytvoří pro model a použije ho k tomu, aby se předpovědi na nová data. `ConsumeModel`</span><span class="sxs-lookup"><span data-stu-id="b5dc4-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

1. <span data-ttu-id="b5dc4-204">Chcete-li vytvořit předpovědi pro nová data pomocí modelu, vytvořte novou instanci `ModelInput` třídy a `ConsumeModel` použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="b5dc4-205">Všimněte si, že částka tarifů není součástí vstupu.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="b5dc4-206">Důvodem je to, že model vygeneruje předpověď pro něj.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="b5dc4-207">Do `Main` metody přidejte následující kód a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-207">Add the following code to the `Main` method and run the application</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="b5dc4-208">Výstup generovaný programem by měl vypadat podobně jako následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="b5dc4-209">Pokud potřebujete odkazovat na vygenerované projekty později v jiném řešení, můžete je vyhledat v `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáři.</span><span class="sxs-lookup"><span data-stu-id="b5dc4-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5dc4-210">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5dc4-210">Next Steps</span></span>

<span data-ttu-id="b5dc4-211">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="b5dc4-212">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-212">Prepare and understand the data</span></span>
> - <span data-ttu-id="b5dc4-213">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="b5dc4-213">Choose a scenario</span></span>
> - <span data-ttu-id="b5dc4-214">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="b5dc4-214">Load the data</span></span>
> - <span data-ttu-id="b5dc4-215">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-215">Train the model</span></span>
> - <span data-ttu-id="b5dc4-216">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-216">Evaluate the model</span></span>
> - <span data-ttu-id="b5dc4-217">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="b5dc4-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b5dc4-218">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="b5dc4-218">Additional Resources</span></span>

<span data-ttu-id="b5dc4-219">Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="b5dc4-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="b5dc4-220">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="b5dc4-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="b5dc4-221">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="b5dc4-221">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="b5dc4-222">Metriky regresního modelu</span><span class="sxs-lookup"><span data-stu-id="b5dc4-222">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="b5dc4-223">Sada dat pro cestu NYC TLC taxislužby</span><span class="sxs-lookup"><span data-stu-id="b5dc4-223">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
