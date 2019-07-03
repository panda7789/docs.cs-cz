---
title: Předvídání cen prostřednictvím regrese s Tvůrce modelu
description: Tento kurz ukazuje, jak sestavit pomocí Tvůrce modelu ML.NET k předvídání cen, konkrétně tarify taxislužby města New York regresní model.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539625"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="686eb-103">Předvídání cen prostřednictvím regrese s Tvůrce modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="686eb-104">Další informace o použití Tvůrce modelu ML.NET k sestavení [regresní model](../resources/glossary.md#regression) předpovídat ceny.</span><span class="sxs-lookup"><span data-stu-id="686eb-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="686eb-105">Konzolové aplikace .NET, který v tomto kurzu vyvinete předpovídá podle historických dat. tarif taxislužby města New York tarify taxislužby.</span><span class="sxs-lookup"><span data-stu-id="686eb-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="686eb-106">Šablonu predikce ceny Tvůrce modelu lze použít pro jakýkoli scénář vyžaduje hodnotu číselné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="686eb-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="686eb-107">Ukázkové scénáře zahrnují: organizace predikce ceny, předpověď poptávky a prognózy prodeje.</span><span class="sxs-lookup"><span data-stu-id="686eb-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="686eb-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="686eb-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="686eb-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="686eb-110">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="686eb-110">Choose a scenario</span></span>
> * <span data-ttu-id="686eb-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-111">Load the data</span></span>
> * <span data-ttu-id="686eb-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-112">Train the model</span></span>
> * <span data-ttu-id="686eb-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-113">Evaluate the model</span></span>
> * <span data-ttu-id="686eb-114">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="686eb-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="686eb-115">Tvůrce modelu je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="686eb-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="686eb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="686eb-116">Pre-requisites</span></span>

<span data-ttu-id="686eb-117">Seznam požadavků a pokyny k instalaci, přejděte [Tvůrce modelu Průvodce instalací](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="686eb-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="686eb-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="686eb-118">Create a console application</span></span>

1. <span data-ttu-id="686eb-119">Vytvoření **konzolovou aplikaci .NET Core** nazývá "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="686eb-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="686eb-120">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="686eb-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="686eb-121">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="686eb-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="686eb-122">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte balíček, v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="686eb-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="686eb-123">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="686eb-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="686eb-124">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="686eb-125">Vytvořte adresář *Data* ve vašem projektu a ukládat soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="686eb-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="686eb-126">Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) dat nastavit a uložit ho. tím *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="686eb-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="686eb-127">Tato datová sada se používá k natrénování a vyhodnocení modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="686eb-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="686eb-128">Tato datová sada je původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="686eb-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="686eb-129">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *taxislužby. tarif train.csv* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="686eb-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="686eb-130">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="686eb-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="686eb-131">Každý řádek `taxi-fare-train.csv` datová sada obsahuje podrobné informace o cesty taxislužby.</span><span class="sxs-lookup"><span data-stu-id="686eb-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="686eb-132">Otevřít **taxislužby. tarif train.csv** datové sady</span><span class="sxs-lookup"><span data-stu-id="686eb-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="686eb-133">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="686eb-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="686eb-134">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="686eb-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="686eb-135">**rate_code:** Typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="686eb-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="686eb-136">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="686eb-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="686eb-137">**trip_time_in_secs:** Dobu trvání cesty.</span><span class="sxs-lookup"><span data-stu-id="686eb-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="686eb-138">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="686eb-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="686eb-139">V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách.</span><span class="sxs-lookup"><span data-stu-id="686eb-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="686eb-140">Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="686eb-141">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="686eb-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="686eb-142">**payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="686eb-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="686eb-143">**fare_amount:** Celkový počet taxislužby tarif placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="686eb-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="686eb-144">`label` Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="686eb-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="686eb-145">Když provádíte úlohu regrese, cílem je předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="686eb-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="686eb-146">V tomto scénáři predikce ceny se očekává náklady jízdní taxislužby.</span><span class="sxs-lookup"><span data-stu-id="686eb-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="686eb-147">Proto **fare_amount** popisek.</span><span class="sxs-lookup"><span data-stu-id="686eb-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="686eb-148">Identifikovanou `features` jsou vstupy, poskytují model k predikci `label`.</span><span class="sxs-lookup"><span data-stu-id="686eb-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="686eb-149">V takovém případě zbývající sloupce, které se používají jako vstupy nebo funkce odhadnout množství tarif.</span><span class="sxs-lookup"><span data-stu-id="686eb-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="686eb-150">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="686eb-150">Choose a scenario</span></span>

<span data-ttu-id="686eb-151">K natrénování modelu, musíte vybrat ze seznamu dostupných strojového učení scénáře, které poskytuje tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="686eb-152">V takovém případě je scénář `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="686eb-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="686eb-153">Rozsáhlejší seznam najdete [Tvůrce modelu přehledovém článku](../automate-training-with-model-builder.md#scenarios).</span><span class="sxs-lookup"><span data-stu-id="686eb-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="686eb-154">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu a vyberte **přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="686eb-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="686eb-155">V kroku scénář nástroj Tvůrce modelu, vyberte *predikce ceny* scénář.</span><span class="sxs-lookup"><span data-stu-id="686eb-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="686eb-156">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-156">Load the data</span></span>

<span data-ttu-id="686eb-157">Tvůrce modelu přijme data ze dvou zdrojů, databáze SQL serveru nebo souboru csv nebo tsv místního souboru.</span><span class="sxs-lookup"><span data-stu-id="686eb-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="686eb-158">Další informace o požadavky na formát dat, navštivte následující [odkaz](../how-to-guides/install-model-builder.md#limitations).</span><span class="sxs-lookup"><span data-stu-id="686eb-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="686eb-159">V kroku data nástroj Tvůrce modelu, vyberte *souboru* z rozevíracího seznamu datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="686eb-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="686eb-160">Vyberte tlačítko vedle *vyberte soubor* textové pole a použití Průzkumníka souborů a procházet a vybrat *taxislužby. tarif test.csv* v *Data* adresáře</span><span class="sxs-lookup"><span data-stu-id="686eb-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="686eb-161">Zvolte *fare_amount* v *popisek nebo sloupec, který se Predict* rozevírací seznam a přejděte ke kroku trénování nástroje Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="686eb-162">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-162">Train the model</span></span>

<span data-ttu-id="686eb-163">Strojové učení úlohy využívají k tréninku modelu predikce ceny v tomto kurzu je regrese.</span><span class="sxs-lookup"><span data-stu-id="686eb-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="686eb-164">Během procesu trénování modelu trénovat Tvůrce modelu samostatných modelů pomocí různých regrese algoritmů a nastavení najít nejvýkonnějšího modelu pro datové sady.</span><span class="sxs-lookup"><span data-stu-id="686eb-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="686eb-165">Objem dat úměrné čas potřebný k natrénování modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="686eb-166">Vyberte odpovídající hodnotu pomocí tohoto grafu jako vodítko `Time to train (seconds)` pole:</span><span class="sxs-lookup"><span data-stu-id="686eb-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="686eb-167">\* Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="686eb-167">\*Dataset Size</span></span>  | <span data-ttu-id="686eb-168">Typ datové sady</span><span class="sxs-lookup"><span data-stu-id="686eb-168">Dataset Type</span></span>       | <span data-ttu-id="686eb-169">Střední Čas k trénování \*</span><span class="sxs-lookup"><span data-stu-id="686eb-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="686eb-170">0 - 10 Mb</span><span class="sxs-lookup"><span data-stu-id="686eb-170">0 - 10 Mb</span></span>     | <span data-ttu-id="686eb-171">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="686eb-171">Numeric and Text</span></span>   | <span data-ttu-id="686eb-172">10 sekund</span><span class="sxs-lookup"><span data-stu-id="686eb-172">10 sec</span></span>
<span data-ttu-id="686eb-173">10 - 100 Mb</span><span class="sxs-lookup"><span data-stu-id="686eb-173">10 - 100 Mb</span></span>   | <span data-ttu-id="686eb-174">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="686eb-174">Numeric and Text</span></span>   | <span data-ttu-id="686eb-175">10 minut</span><span class="sxs-lookup"><span data-stu-id="686eb-175">10 min</span></span>
<span data-ttu-id="686eb-176">100 – 500 mb</span><span class="sxs-lookup"><span data-stu-id="686eb-176">100 - 500 Mb</span></span>  | <span data-ttu-id="686eb-177">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="686eb-177">Numeric and Text</span></span>   | <span data-ttu-id="686eb-178">30 min</span><span class="sxs-lookup"><span data-stu-id="686eb-178">30 min</span></span>
<span data-ttu-id="686eb-179">500 - 1 Gb</span><span class="sxs-lookup"><span data-stu-id="686eb-179">500 - 1 Gb</span></span>    | <span data-ttu-id="686eb-180">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="686eb-180">Numeric and Text</span></span>   | <span data-ttu-id="686eb-181">60 min</span><span class="sxs-lookup"><span data-stu-id="686eb-181">60 min</span></span>
<span data-ttu-id="686eb-182">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="686eb-182">1 Gb+</span></span>         | <span data-ttu-id="686eb-183">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="686eb-183">Numeric and Text</span></span>   | <span data-ttu-id="686eb-184">3 hodiny +</span><span class="sxs-lookup"><span data-stu-id="686eb-184">3 hour+</span></span>

1. <span data-ttu-id="686eb-185">Protože školení datový soubor je větší než 10MB, použijte jako hodnotu pro 600 sekund (10 minut) *čas pro učení (v sekundách)* .</span><span class="sxs-lookup"><span data-stu-id="686eb-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="686eb-186">Vyberte *spustit Trénovací*.</span><span class="sxs-lookup"><span data-stu-id="686eb-186">Select *Start Training*.</span></span>

<span data-ttu-id="686eb-187">V průběhu procesu trénování průběh data se zobrazí v `Progress` část krok trénování.</span><span class="sxs-lookup"><span data-stu-id="686eb-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="686eb-188">Stav se zobrazí stav dokončení procesu trénování.</span><span class="sxs-lookup"><span data-stu-id="686eb-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="686eb-189">Největší přesností zobrazí přesnost nejvýkonnějšího modelu zatím objevila Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="686eb-190">Vyšší přesnost znamená, že model více správně předpovědět na testovací data.</span><span class="sxs-lookup"><span data-stu-id="686eb-190">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="686eb-191">Nejlepší algoritmus zobrazí název algoritmu nejlépe provádí provést zatím objevila Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="686eb-192">Poslední algoritmus zobrazí název algoritmu Tvůrce modelu naposledy použité pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="686eb-193">Po dokončení školení přejděte ke kroku vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="686eb-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="686eb-194">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-194">Evaluate the model</span></span>

<span data-ttu-id="686eb-195">Výsledek kroku školení bude jeden model, který měl nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="686eb-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="686eb-196">V kroku vyhodnotit nástroj Tvůrce modelu, bude obsahovat výstupní sekce algoritmus používaný serverem nejvýkonnějšího modelu v *nejlepší Model* položka společně s metrikami v *nejlepší kvalita modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="686eb-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="686eb-197">Kromě toho souhrnnou tabulku obsahující pěti hlavních modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="686eb-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="686eb-198">Navštivte následující odkaz na další informace o [vyhodnocení modelu metriky](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span><span class="sxs-lookup"><span data-stu-id="686eb-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="686eb-199">Pokud si nejste spokojeni s metriky přesnosti, zvýšit množství času pro trénování modelu nebo používat další data jsou některé snadných způsobů, jak vyzkoušet a zlepšit přesnost modelu.</span><span class="sxs-lookup"><span data-stu-id="686eb-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="686eb-200">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="686eb-200">Use the model for predictions</span></span>

<span data-ttu-id="686eb-201">Dva projekty budou vytvořeny v důsledku procesu trénování.</span><span class="sxs-lookup"><span data-stu-id="686eb-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="686eb-202">TaxiFarePredictionML.ConsoleApp: Aplikace konzoly .NET, která obsahuje kód modelu školení a spotřebu.</span><span class="sxs-lookup"><span data-stu-id="686eb-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="686eb-203">TaxiFarePredictionML.Model: .NET Standard knihovny tříd obsahující datové modely, které definujete schéma vstupní a výstupní modelování dat, jakož i trvalou verzí nejvýkonnějšího modelu během cvičení.</span><span class="sxs-lookup"><span data-stu-id="686eb-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="686eb-204">V části kódu nástroj Tvůrce modelu vyberte **přidány projekty** přidat projekty do řešení.</span><span class="sxs-lookup"><span data-stu-id="686eb-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
2. <span data-ttu-id="686eb-205">V Průzkumníku řešení klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="686eb-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="686eb-206">Vyberte **Přidat > existující položku**.</span><span class="sxs-lookup"><span data-stu-id="686eb-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="686eb-207">Soubor typu z rozevíracího seznamu vyberte `All Files`, přejděte *TaxiFarePredictionML.Model* projekt adresář a zaškrtnout možnost `MLModel.zip` souboru.</span><span class="sxs-lookup"><span data-stu-id="686eb-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="686eb-208">Klikněte pravým tlačítkem na naposledy přidané `MLModel.zip` a vyberte možnost *vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="686eb-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="686eb-209">Kopírovat do výstupního adresáře možnosti, vyberte *kopírovat, pokud je novější* z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="686eb-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
3. <span data-ttu-id="686eb-210">Klikněte pravým tlačítkem na *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="686eb-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="686eb-211">Potom **Přidat > odkaz**.</span><span class="sxs-lookup"><span data-stu-id="686eb-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="686eb-212">Zvolte **projektů > řešení** uzlu a ze seznamu, zkontrolujte *TaxiFarePredictionML.Model* projektu a vyberte OK.</span><span class="sxs-lookup"><span data-stu-id="686eb-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="686eb-213">Otevřít *Program.cs* soubor *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="686eb-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="686eb-214">Přidejte následující příkazy using:</span><span class="sxs-lookup"><span data-stu-id="686eb-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="686eb-215">Přidat `ConsumeModel` metodu `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="686eb-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="686eb-216">`ConsumeModel` Vytvoří `PredictionEngine` na základě modelu generovaných Tvůrce Model k predikci na nová data a je vytisknout na konzole.</span><span class="sxs-lookup"><span data-stu-id="686eb-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

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

7. <span data-ttu-id="686eb-217">Přidejte následující kód, který `Main` metoda a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="686eb-217">Add the following code to the `Main` method and run the application.</span></span>

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

    <span data-ttu-id="686eb-218">Výstup vygenerovaný program by měl vypadat podobně jako v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="686eb-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="686eb-219">Pokud potřebujete odkazovat na vygenerované projekty později uvnitř jiné řešení, najdete je uvnitř `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáře.</span><span class="sxs-lookup"><span data-stu-id="686eb-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="686eb-220">Další kroky</span><span class="sxs-lookup"><span data-stu-id="686eb-220">Next Steps</span></span>

<span data-ttu-id="686eb-221">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="686eb-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="686eb-222">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="686eb-223">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="686eb-223">Choose a scenario</span></span>
> * <span data-ttu-id="686eb-224">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="686eb-224">Load the data</span></span>
> * <span data-ttu-id="686eb-225">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-225">Train the model</span></span>
> * <span data-ttu-id="686eb-226">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="686eb-226">Evaluate the model</span></span>
> * <span data-ttu-id="686eb-227">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="686eb-227">Use the model for predictions</span></span>

<span data-ttu-id="686eb-228">Přejděte k některé z některého z těchto článků se naučíte, jak model nasadit.</span><span class="sxs-lookup"><span data-stu-id="686eb-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="686eb-229">Nasazení modelu do služby Azure Functions</span><span class="sxs-lookup"><span data-stu-id="686eb-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="686eb-230">Nasazení modelu pro webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="686eb-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
