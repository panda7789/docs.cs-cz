---
title: Předvídání cen prostřednictvím regrese s Tvůrce modelu
description: Tento kurz ukazuje, jak sestavit pomocí Tvůrce modelu ML.NET k předvídání cen, konkrétně tarify taxislužby města New York regresní model.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d8c901a10c91c8a6c16ca59516b633a99785ebac
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238571"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="0c61d-103">Předvídání cen prostřednictvím regrese s Tvůrce modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="0c61d-104">Další informace o použití Tvůrce modelu ML.NET sestavit regrese model() předpovídat ceny.</span><span class="sxs-lookup"><span data-stu-id="0c61d-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="0c61d-105">Konzolové aplikace .NET, který v tomto kurzu vyvinete předpovídá podle historických dat. tarif taxislužby města New York tarify taxislužby.</span><span class="sxs-lookup"><span data-stu-id="0c61d-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="0c61d-106">Šablonu predikce ceny Tvůrce modelu lze použít pro jakýkoli scénář vyžaduje hodnotu číselné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="0c61d-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="0c61d-107">Ukázkové scénáře zahrnují: organizace predikce ceny, předpověď poptávky a prognózy prodeje.</span><span class="sxs-lookup"><span data-stu-id="0c61d-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="0c61d-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="0c61d-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0c61d-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="0c61d-110">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="0c61d-110">Choose a scenario</span></span>
> * <span data-ttu-id="0c61d-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-111">Load the data</span></span>
> * <span data-ttu-id="0c61d-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-112">Train the model</span></span>
> * <span data-ttu-id="0c61d-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-113">Evaluate the model</span></span>
> * <span data-ttu-id="0c61d-114">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="0c61d-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="0c61d-115">Tvůrce modelu je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="0c61d-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0c61d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c61d-116">Pre-requisites</span></span>

<span data-ttu-id="0c61d-117">Seznam požadavků a pokyny k instalaci, přejděte [Tvůrce modelu Průvodce instalací](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="0c61d-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0c61d-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="0c61d-118">Create a console application</span></span>

1. <span data-ttu-id="0c61d-119">Vytvoření **konzolovou aplikaci .NET Core** nazývá "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="0c61d-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0c61d-120">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="0c61d-121">Vytvořte adresář *Data* ve vašem projektu a ukládat soubory datové sady.</span><span class="sxs-lookup"><span data-stu-id="0c61d-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="0c61d-122">Sada dat používá k natrénování a vyhodnocení modelů strojového učení je původně cesty taxíkem TLC NYC datové sady.</span><span class="sxs-lookup"><span data-stu-id="0c61d-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span> 

    <span data-ttu-id="0c61d-123">Stáhnout sady dat, přejděte [odkaz ke stažení taxislužby. tarif train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="0c61d-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span> 
    
    <span data-ttu-id="0c61d-124">Když se stránka načte, klikněte pravým tlačítkem kamkoli na stránku a vyberte **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="0c61d-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span> 
    
    <span data-ttu-id="0c61d-125">Použití **uložit jako dialogové okno** k uložení souboru v *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="0c61d-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span> 
    
1. <span data-ttu-id="0c61d-126">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *taxislužby. tarif train.csv* a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0c61d-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="0c61d-127">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="0c61d-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="0c61d-128">Každý řádek `taxi-fare-train.csv` datová sada obsahuje podrobné informace o cesty taxislužby.</span><span class="sxs-lookup"><span data-stu-id="0c61d-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="0c61d-129">Otevřít **taxislužby. tarif train.csv** datové sady</span><span class="sxs-lookup"><span data-stu-id="0c61d-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="0c61d-130">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="0c61d-130">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="0c61d-131">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="0c61d-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="0c61d-132">**rate_code:** Typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="0c61d-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="0c61d-133">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="0c61d-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="0c61d-134">**trip_time_in_secs:** Dobu trvání cesty.</span><span class="sxs-lookup"><span data-stu-id="0c61d-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> 
    * <span data-ttu-id="0c61d-135">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="0c61d-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="0c61d-136">**payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="0c61d-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="0c61d-137">**fare_amount:** Celkový počet taxislužby tarif placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="0c61d-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="0c61d-138">`label` Je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="0c61d-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="0c61d-139">Když provádíte úlohu regrese, cílem je předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="0c61d-140">V tomto scénáři predikce ceny se očekává náklady jízdní taxislužby.</span><span class="sxs-lookup"><span data-stu-id="0c61d-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="0c61d-141">Proto **fare_amount** popisek.</span><span class="sxs-lookup"><span data-stu-id="0c61d-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="0c61d-142">Identifikovanou `features` jsou vstupy, poskytují model k predikci `label`.</span><span class="sxs-lookup"><span data-stu-id="0c61d-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="0c61d-143">V takovém případě zbývající sloupce, které se používají jako vstupy nebo funkce odhadnout množství tarif.</span><span class="sxs-lookup"><span data-stu-id="0c61d-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="0c61d-144">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="0c61d-144">Choose a scenario</span></span>

<span data-ttu-id="0c61d-145">K natrénování modelu, musíte vybrat ze seznamu dostupných strojového učení scénáře, které poskytuje tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="0c61d-146">V takovém případě je scénář `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="0c61d-146">In this case, the scenario is `Price Prediction`.</span></span> 

1. <span data-ttu-id="0c61d-147">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *TaxiFarePrediction* projektu a vyberte **přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="0c61d-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="0c61d-148">V kroku scénář nástroj Tvůrce modelu, vyberte *predikce ceny* scénář.</span><span class="sxs-lookup"><span data-stu-id="0c61d-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0c61d-149">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-149">Load the data</span></span>

<span data-ttu-id="0c61d-150">Tvůrce modelu přijme data ze dvou zdrojů, databáze SQL serveru nebo místní soubor ve formátu csv, tsv.</span><span class="sxs-lookup"><span data-stu-id="0c61d-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span> 

1. <span data-ttu-id="0c61d-151">V kroku data nástroj Tvůrce modelu, vyberte *souboru* z rozevíracího seznamu datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="0c61d-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="0c61d-152">Vyberte tlačítko vedle *vyberte soubor* textové pole a použití Průzkumníka souborů a procházet a vybrat *taxislužby. tarif test.csv* v *Data* adresáře</span><span class="sxs-lookup"><span data-stu-id="0c61d-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="0c61d-153">Zvolte *fare_amount* v *popisek nebo sloupec, který se Predict* rozevírací seznam a přejděte ke kroku trénování nástroje Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="0c61d-154">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-154">Train the model</span></span>

<span data-ttu-id="0c61d-155">Strojové učení úlohy využívají k tréninku modelu predikce ceny v tomto kurzu je regrese.</span><span class="sxs-lookup"><span data-stu-id="0c61d-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="0c61d-156">Během procesu trénování modelu trénovat Tvůrce modelu samostatných modelů pomocí různých regrese algoritmů a nastavení najít nejvýkonnějšího modelu pro datové sady.</span><span class="sxs-lookup"><span data-stu-id="0c61d-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="0c61d-157">Objem dat úměrné čas potřebný k natrénování modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="0c61d-158">Vyberte odpovídající hodnotu pomocí tohoto grafu jako vodítko `Time to train (seconds)` pole:</span><span class="sxs-lookup"><span data-stu-id="0c61d-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="0c61d-159">\* Velikost datové sady</span><span class="sxs-lookup"><span data-stu-id="0c61d-159">\*Dataset Size</span></span>  | <span data-ttu-id="0c61d-160">Typ datové sady</span><span class="sxs-lookup"><span data-stu-id="0c61d-160">Dataset Type</span></span>       | <span data-ttu-id="0c61d-161">Střední Čas k trénování \*</span><span class="sxs-lookup"><span data-stu-id="0c61d-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="0c61d-162">0 – 10 mb</span><span class="sxs-lookup"><span data-stu-id="0c61d-162">0 - 10 Mb</span></span>     | <span data-ttu-id="0c61d-163">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="0c61d-163">Numeric and Text</span></span>   | <span data-ttu-id="0c61d-164">10 sekund</span><span class="sxs-lookup"><span data-stu-id="0c61d-164">10 sec</span></span>
<span data-ttu-id="0c61d-165">10 – 100 mb</span><span class="sxs-lookup"><span data-stu-id="0c61d-165">10 - 100 Mb</span></span>   | <span data-ttu-id="0c61d-166">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="0c61d-166">Numeric and Text</span></span>   | <span data-ttu-id="0c61d-167">10 minut</span><span class="sxs-lookup"><span data-stu-id="0c61d-167">10 min</span></span>
<span data-ttu-id="0c61d-168">100 – 500 mb</span><span class="sxs-lookup"><span data-stu-id="0c61d-168">100 - 500 Mb</span></span>  | <span data-ttu-id="0c61d-169">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="0c61d-169">Numeric and Text</span></span>   | <span data-ttu-id="0c61d-170">30 minut</span><span class="sxs-lookup"><span data-stu-id="0c61d-170">30 min</span></span>
<span data-ttu-id="0c61d-171">500 - 1 Gb</span><span class="sxs-lookup"><span data-stu-id="0c61d-171">500 - 1 Gb</span></span>    | <span data-ttu-id="0c61d-172">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="0c61d-172">Numeric and Text</span></span>   | <span data-ttu-id="0c61d-173">60 min</span><span class="sxs-lookup"><span data-stu-id="0c61d-173">60 min</span></span>
<span data-ttu-id="0c61d-174">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="0c61d-174">1 Gb+</span></span>         | <span data-ttu-id="0c61d-175">Číselné a Text</span><span class="sxs-lookup"><span data-stu-id="0c61d-175">Numeric and Text</span></span>   | <span data-ttu-id="0c61d-176">3 hodiny +</span><span class="sxs-lookup"><span data-stu-id="0c61d-176">3 hour+</span></span>

1. <span data-ttu-id="0c61d-177">Protože školení datový soubor je větší než 10MB, použijte jako hodnotu pro 600 sekund (10 minut) *čas pro učení (v sekundách)* .</span><span class="sxs-lookup"><span data-stu-id="0c61d-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="0c61d-178">Vyberte *spustit Trénovací*.</span><span class="sxs-lookup"><span data-stu-id="0c61d-178">Select *Start Training*.</span></span>

<span data-ttu-id="0c61d-179">V průběhu procesu trénování průběh data se zobrazí v `Progress` část krok trénování.</span><span class="sxs-lookup"><span data-stu-id="0c61d-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="0c61d-180">Stav se zobrazí stav dokončení procesu trénování.</span><span class="sxs-lookup"><span data-stu-id="0c61d-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="0c61d-181">Největší přesností zobrazí přesnost nejvýkonnějšího modelu zatím objevila Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="0c61d-182">Vyšší přesnost znamená, že model více správně předpovědět na testovací data.</span><span class="sxs-lookup"><span data-stu-id="0c61d-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="0c61d-183">Nejlepší algoritmus zobrazí název algoritmu nejlépe provádí provést zatím objevila Tvůrce modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="0c61d-184">Poslední algoritmus zobrazí název algoritmu Tvůrce modelu naposledy použité pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="0c61d-185">Po dokončení školení přejděte ke kroku vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="0c61d-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="0c61d-186">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-186">Evaluate the model</span></span>

<span data-ttu-id="0c61d-187">Výsledek kroku školení bude jeden model, který měl nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="0c61d-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="0c61d-188">V kroku vyhodnotit nástroj Tvůrce modelu, bude obsahovat výstupní sekce algoritmus používaný serverem nejvýkonnějšího modelu v *nejlepší Model* položka společně s metrikami v *nejlepší kvalita modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="0c61d-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="0c61d-189">Kromě toho souhrnnou tabulku obsahující pěti hlavních modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="0c61d-189">Additionally, a summary table containing top five models and their metrics.</span></span> 

<span data-ttu-id="0c61d-190">Pokud si nejste spokojeni s metriky přesnosti, zvýšit množství času pro trénování modelu nebo používat další data jsou některé snadných způsobů, jak vyzkoušet a zlepšit přesnost modelu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="0c61d-191">V opačném případě přejděte ke kroku kódu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-191">Otherwise, navigate to the code step.</span></span> 

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="0c61d-192">Přidejte kód k vytvoření predikcí</span><span class="sxs-lookup"><span data-stu-id="0c61d-192">Add the code to make predictions</span></span>

<span data-ttu-id="0c61d-193">Dva projekty budou vytvořeny v důsledku procesu trénování.</span><span class="sxs-lookup"><span data-stu-id="0c61d-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="0c61d-194">TaxiFarePredictionML.ConsoleApp: Aplikace konzoly .NET Core obsahující kód modelu školení a využití.</span><span class="sxs-lookup"><span data-stu-id="0c61d-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="0c61d-195">TaxiFarePredictionML.Model: .NET Standard knihovny tříd obsahující datové modely, které definujete schéma vstupní a výstupní modelování dat, jakož i trvalou verzí nejvýkonnějšího modelu během cvičení.</span><span class="sxs-lookup"><span data-stu-id="0c61d-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>


1. <span data-ttu-id="0c61d-196">V kroku kód nástroj Tvůrce modelu, vyberte **přidat projekty** pro automaticky generované projekty do řešení přidat.</span><span class="sxs-lookup"><span data-stu-id="0c61d-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="0c61d-197">Klikněte pravým tlačítkem na *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="0c61d-198">Potom **Přidat > odkaz**.</span><span class="sxs-lookup"><span data-stu-id="0c61d-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="0c61d-199">Zvolte **projektů > řešení** uzlu a ze seznamu, zkontrolujte *TaxiFarePredictionML.Model* projektu a vyberte OK.</span><span class="sxs-lookup"><span data-stu-id="0c61d-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="0c61d-200">Otevřít *Program.cs* soubor *TaxiFarePrediction* projektu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="0c61d-201">Přidejte následující příkazy using tak, aby odkazovaly *Microsoft.ML* balíčku NuGet a *TaxiFarePredictionML.Model* projektu:</span><span class="sxs-lookup"><span data-stu-id="0c61d-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>


    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="0c61d-202">Přidat `ConsumeModel` metodu `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="0c61d-202">Add the `ConsumeModel` method to the `Program` class.</span></span> 

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

    <span data-ttu-id="0c61d-203">`ConsumeModel` Se načíst trénovaného modelu, vytvořit [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) modelu a jeho použití k vytvoření predikcí nová data.</span><span class="sxs-lookup"><span data-stu-id="0c61d-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

7. <span data-ttu-id="0c61d-204">K předpovědím na nová data pomocí modelu, vytvořte novou instanci třídy `ModelInput` třídy a použít `ConsumeModel` metody.</span><span class="sxs-lookup"><span data-stu-id="0c61d-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="0c61d-205">Všimněte si, že velikost tarif není součástí vstupu.</span><span class="sxs-lookup"><span data-stu-id="0c61d-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="0c61d-206">Je to proto, že model bude generovat předpovědi pro něj.</span><span class="sxs-lookup"><span data-stu-id="0c61d-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="0c61d-207">Přidejte následující kód, který `Main` metoda a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="0c61d-207">Add the following code to the `Main` method and run the application</span></span>

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

    <span data-ttu-id="0c61d-208">Výstup vygenerovaný program by měl vypadat podobně jako v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="0c61d-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="0c61d-209">Pokud potřebujete odkazovat na vygenerované projekty později uvnitř jiné řešení, najdete je uvnitř `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` adresáře.</span><span class="sxs-lookup"><span data-stu-id="0c61d-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c61d-210">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0c61d-210">Next Steps</span></span>

<span data-ttu-id="0c61d-211">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="0c61d-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0c61d-212">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-212">Prepare and understand the data</span></span>
> * <span data-ttu-id="0c61d-213">Zvolte scénář</span><span class="sxs-lookup"><span data-stu-id="0c61d-213">Choose a scenario</span></span>
> * <span data-ttu-id="0c61d-214">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="0c61d-214">Load the data</span></span>
> * <span data-ttu-id="0c61d-215">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-215">Train the model</span></span>
> * <span data-ttu-id="0c61d-216">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-216">Evaluate the model</span></span>
> * <span data-ttu-id="0c61d-217">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="0c61d-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0c61d-218">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="0c61d-218">Additional Resources</span></span>

<span data-ttu-id="0c61d-219">Další informace o tématech uvedených v tomto kurzu, najdete na následujících odkazech:</span><span class="sxs-lookup"><span data-stu-id="0c61d-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="0c61d-220">Scénáře Tvůrce modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="0c61d-221">Formáty dat tvůrce modelu</span><span class="sxs-lookup"><span data-stu-id="0c61d-221">Model Builder Data Formats</span></span>](../automate-training-with-model-builder.md#data-formats)
- [<span data-ttu-id="0c61d-222">Regrese</span><span class="sxs-lookup"><span data-stu-id="0c61d-222">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="0c61d-223">Regresní Model metriky</span><span class="sxs-lookup"><span data-stu-id="0c61d-223">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="0c61d-224">Cesty taxíkem TLC NYC datové sady</span><span class="sxs-lookup"><span data-stu-id="0c61d-224">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
