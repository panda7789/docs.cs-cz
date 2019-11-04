---
title: 'Kurz: předpověď cen pomocí regrese pomocí Tvůrce modelů'
description: V tomto kurzu se naučíte, jak vytvořit regresní model pomocí Tvůrce modelů ML.NET pro předpověď cen, konkrétně v New Yorku City taxislužby tarifs.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f5010f944dba007e24d3c0e22d4e339f9ed0522a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459183"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="edcb9-103">Kurz: předpověď cen pomocí regrese pomocí Tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="edcb9-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="edcb9-104">Naučte se používat Tvůrce modelů ML.NET k vytvoření regresního modelu pro předpověď cen.</span><span class="sxs-lookup"><span data-stu-id="edcb9-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="edcb9-105">Aplikace konzoly .NET, kterou vyvíjíte v tomto kurzu, předpovídá taxislužby tarify na základě historických dat o taxislužby tarifech z historických Praha.</span><span class="sxs-lookup"><span data-stu-id="edcb9-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="edcb9-106">Šablona předpovědi ceny tvůrce modelů se dá použít pro libovolný scénář, který vyžaduje hodnotu číselné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="edcb9-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="edcb9-107">Mezi příklady scénářů patří: předpověď ceny na pracovišti, Předpověď poptávky a prognózování prodeje.</span><span class="sxs-lookup"><span data-stu-id="edcb9-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="edcb9-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="edcb9-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="edcb9-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="edcb9-110">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="edcb9-110">Choose a scenario</span></span>
> - <span data-ttu-id="edcb9-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-111">Load the data</span></span>
> - <span data-ttu-id="edcb9-112">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-112">Train the model</span></span>
> - <span data-ttu-id="edcb9-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-113">Evaluate the model</span></span>
> - <span data-ttu-id="edcb9-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="edcb9-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="edcb9-115">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="edcb9-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="edcb9-116">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="edcb9-116">Pre-requisites</span></span>

<span data-ttu-id="edcb9-117">Seznam požadavků a pokyny k instalaci najdete v [Průvodci instalací modelu modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="edcb9-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="edcb9-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="edcb9-118">Create a console application</span></span>

1. <span data-ttu-id="edcb9-119">Vytvořte **konzolovou aplikaci .NET Core** nazvanou "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="edcb9-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="edcb9-120">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="edcb9-121">Vytvořte v projektu adresář s názvem *data* pro uložení souborů datové sady.</span><span class="sxs-lookup"><span data-stu-id="edcb9-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="edcb9-122">Sada dat, která se používá ke studiu a vyhodnocení modelu Machine Learning, je původně ze sady dat NYC TLC taxislužby Trip.</span><span class="sxs-lookup"><span data-stu-id="edcb9-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="edcb9-123">Datovou sadu stáhnete tak, že přejdete na [odkaz ke stažení taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="edcb9-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="edcb9-124">Po načtení stránky klikněte pravým tlačítkem myši kamkoli na stránku a vyberte **Uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="edcb9-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="edcb9-125">Pomocí **dialogového okna Uložit jako** uložte soubor do složky *data* , kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="edcb9-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="edcb9-126">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *taxi-Fare-Train. csv* a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="edcb9-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="edcb9-127">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="edcb9-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="edcb9-128">Každý řádek v datové sadě `taxi-fare-train.csv` obsahuje podrobnosti o cestách provedených taxislužby.</span><span class="sxs-lookup"><span data-stu-id="edcb9-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="edcb9-129">Otevřete sadu dat **taxi-Fare-Train. csv.**</span><span class="sxs-lookup"><span data-stu-id="edcb9-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="edcb9-130">Poskytnutá datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="edcb9-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="edcb9-131">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="edcb9-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="edcb9-132">**rate_code:** Typ rychlosti taxislužby Trip je funkce.</span><span class="sxs-lookup"><span data-stu-id="edcb9-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="edcb9-133">**passenger_count:** Počet cestujících na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="edcb9-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="edcb9-134">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="edcb9-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="edcb9-135">Chcete předpovědět jízdné za cestu před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="edcb9-135">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="edcb9-136">V tuto chvíli nevíte, jak dlouho trvá služební cyklus.</span><span class="sxs-lookup"><span data-stu-id="edcb9-136">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="edcb9-137">Doba odezvy tedy není funkcí a tento sloupec z modelu vyloučíte.</span><span class="sxs-lookup"><span data-stu-id="edcb9-137">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="edcb9-138">**trip_distance:** Vzdálenost na cestách je funkce.</span><span class="sxs-lookup"><span data-stu-id="edcb9-138">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="edcb9-139">**payment_type:** Způsob platby (hotovost nebo platební karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="edcb9-139">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="edcb9-140">**fare_amount:** Celková částka taxislužby jízdné je štítek.</span><span class="sxs-lookup"><span data-stu-id="edcb9-140">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="edcb9-141">`label` je sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="edcb9-141">The `label` is the column you want to predict.</span></span> <span data-ttu-id="edcb9-142">Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-142">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="edcb9-143">V tomto scénáři odhadu cen se předpokládá, že náklady na taxislužby jízdní část budou předpovězeny.</span><span class="sxs-lookup"><span data-stu-id="edcb9-143">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="edcb9-144">Proto je **fare_amount** jmenovka.</span><span class="sxs-lookup"><span data-stu-id="edcb9-144">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="edcb9-145">Identifikované `features` jsou vstupy, které modelu udělíte pro předpověď `label`.</span><span class="sxs-lookup"><span data-stu-id="edcb9-145">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="edcb9-146">V tomto případě se zbývající sloupce s výjimkou **trip_time_in_secs** používají jako funkce nebo vstupy pro předpověď množství tarifů.</span><span class="sxs-lookup"><span data-stu-id="edcb9-146">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="edcb9-147">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="edcb9-147">Choose a scenario</span></span>

<span data-ttu-id="edcb9-148">Abyste mohli model vyškolit, musíte si vybrat ze seznamu dostupných scénářů strojového učení, které poskytuje tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="edcb9-148">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="edcb9-149">V takovém případě je scénář `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="edcb9-149">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="edcb9-150">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt *TaxiFarePrediction* a vyberte **Přidat** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="edcb9-150">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="edcb9-151">V kroku scénář nástroje Tvůrce modelů vyberte možnost scénář *předpovědi cen* .</span><span class="sxs-lookup"><span data-stu-id="edcb9-151">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="edcb9-152">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-152">Load the data</span></span>

<span data-ttu-id="edcb9-153">Tvůrce modelů přijímá data ze dvou zdrojů, SQL Server databáze nebo místního souboru ve formátu CSV nebo TSV.</span><span class="sxs-lookup"><span data-stu-id="edcb9-153">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="edcb9-154">V kroku dat nástroje Tvůrce modelů vyberte v rozevíracím seznamu zdroj dat *soubor* .</span><span class="sxs-lookup"><span data-stu-id="edcb9-154">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="edcb9-155">Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů Procházejte a vyberte soubor *taxi-Fare-test. csv* v *datovém* adresáři.</span><span class="sxs-lookup"><span data-stu-id="edcb9-155">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="edcb9-156">V rozevíracím seznamu *sloupec pro předpověď (popisek)* vyberte *fare_amount* .</span><span class="sxs-lookup"><span data-stu-id="edcb9-156">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="edcb9-157">Rozbalte rozevírací seznam *vstupní sloupce (funkce)* a zrušte kontrolu sloupce *trip_time_in_secs* , aby se vyloučil jako funkce během školení.</span><span class="sxs-lookup"><span data-stu-id="edcb9-157">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="edcb9-158">Přejděte do kroku výuka nástroje Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="edcb9-158">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="edcb9-159">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-159">Train the model</span></span>

<span data-ttu-id="edcb9-160">Úkol strojového učení, který se používá k výuce modelu předpovědi cen v tomto kurzu, je regrese.</span><span class="sxs-lookup"><span data-stu-id="edcb9-160">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="edcb9-161">V průběhu procesu školení modelů vlacích sestaví model modelování samostatné modely pomocí různých regresních algoritmů a nastavení, které pro datovou sadu vyhledají nejlepší model provádění.</span><span class="sxs-lookup"><span data-stu-id="edcb9-161">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="edcb9-162">Čas potřebný ke školení modelu je úměrný množství dat.</span><span class="sxs-lookup"><span data-stu-id="edcb9-162">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="edcb9-163">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas do výuky (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="edcb9-163">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="edcb9-164">Ponechte výchozí hodnotu tak, aby byla pro *čas do výuky (sekundy)* , pokud nechcete, aby se vlak vydával po delší dobu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-164">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="edcb9-165">Vyberte *Spustit školení*.</span><span class="sxs-lookup"><span data-stu-id="edcb9-165">Select *Start Training*.</span></span>

<span data-ttu-id="edcb9-166">V průběhu procesu školení se data o průběhu zobrazují v části `Progress` kroku výukového programu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="edcb9-167">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="edcb9-167">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="edcb9-168">Nejlepší přesnost zobrazuje přesnost nejlepšího modelu, kterou najde tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="edcb9-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="edcb9-169">Vyšší přesnost znamená, že model se v testovacích datech podrobnějším způsobem vypovídat.</span><span class="sxs-lookup"><span data-stu-id="edcb9-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="edcb9-170">Nejlepší algoritmus zobrazuje název nejlepšího výkonu, který našel tvůrce modelů, zatím.</span><span class="sxs-lookup"><span data-stu-id="edcb9-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="edcb9-171">Poslední algoritmus zobrazuje název algoritmu naposledy, který tvůrce modelů použil k vytvoření výukového modelu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="edcb9-172">Po dokončení školení přejděte k kroku vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="edcb9-172">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="edcb9-173">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-173">Evaluate the model</span></span>

<span data-ttu-id="edcb9-174">Výsledkem kroku školení bude jeden model, který má nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="edcb9-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="edcb9-175">V kroku vyhodnocení nástroje pro sestavování modelů bude v sekci výstup obsahovat algoritmus používaný modelem nejlepšího provádění v *nejlepším záznamu modelu* spolu se metrikami v *nejlepší kvalitě modelu (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="edcb9-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="edcb9-176">Navíc Souhrnná tabulka obsahující pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="edcb9-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="edcb9-177">Pokud nejste spokojeni s metrikami přesnosti, můžou vám některé jednoduché způsoby, jak zkusit a zlepšit přesnost modelu, zvýšit množství času pro výuku modelu nebo použít víc dat.</span><span class="sxs-lookup"><span data-stu-id="edcb9-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="edcb9-178">V opačném případě přejděte do kroku Code (kód).</span><span class="sxs-lookup"><span data-stu-id="edcb9-178">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="edcb9-179">Přidejte kód, který provede předpovědi</span><span class="sxs-lookup"><span data-stu-id="edcb9-179">Add the code to make predictions</span></span>

<span data-ttu-id="edcb9-180">V důsledku školicího procesu se vytvoří dva projekty.</span><span class="sxs-lookup"><span data-stu-id="edcb9-180">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="edcb9-181">TaxiFarePredictionML. ConsoleApp: Konzolová aplikace .NET Core, která obsahuje kód pro školení modelů a ukázku kódu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-181">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="edcb9-182">TaxiFarePredictionML. model: .NET Standard knihovny tříd obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou verzi modelu nejlepšího provádění během školení a pomocnou třídu s názvem `ConsumeModel` pro vytvoření předpovědi.</span><span class="sxs-lookup"><span data-stu-id="edcb9-182">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="edcb9-183">V kroku kód nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="edcb9-183">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="edcb9-184">Otevřete soubor *program.cs* v projektu *TaxiFarePrediction* .</span><span class="sxs-lookup"><span data-stu-id="edcb9-184">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="edcb9-185">Přidejte následující příkaz using pro odkaz na projekt *TaxiFarePredictionML. model* :</span><span class="sxs-lookup"><span data-stu-id="edcb9-185">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="edcb9-186">Chcete-li vytvořit předpovědi pro nová data pomocí modelu, vytvořte novou instanci třídy `ModelInput` uvnitř metody `Main` vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="edcb9-186">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="edcb9-187">Všimněte si, že částka tarifů není součástí vstupu.</span><span class="sxs-lookup"><span data-stu-id="edcb9-187">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="edcb9-188">Důvodem je to, že model vygeneruje předpověď pro něj.</span><span class="sxs-lookup"><span data-stu-id="edcb9-188">This is because the model will generate the prediction for it.</span></span> 

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="edcb9-189">Použijte metodu `Predict` ze třídy `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="edcb9-189">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="edcb9-190">Metoda `Predict` načte školený model, vytvoří pro model [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) a použije ho k předpovědií nových dat.</span><span class="sxs-lookup"><span data-stu-id="edcb9-190">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span> 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="edcb9-191">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="edcb9-191">Run the application.</span></span>

    <span data-ttu-id="edcb9-192">Výstup generovaný programem by měl vypadat podobně jako následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="edcb9-192">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="edcb9-193">Pokud potřebujete odkazovat na vygenerované projekty později v jiném řešení, můžete je najít v adresáři `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="edcb9-193">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="edcb9-194">Další kroky</span><span class="sxs-lookup"><span data-stu-id="edcb9-194">Next Steps</span></span>

<span data-ttu-id="edcb9-195">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="edcb9-195">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="edcb9-196">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-196">Prepare and understand the data</span></span>
> - <span data-ttu-id="edcb9-197">Zvolit scénář</span><span class="sxs-lookup"><span data-stu-id="edcb9-197">Choose a scenario</span></span>
> - <span data-ttu-id="edcb9-198">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="edcb9-198">Load the data</span></span>
> - <span data-ttu-id="edcb9-199">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-199">Train the model</span></span>
> - <span data-ttu-id="edcb9-200">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-200">Evaluate the model</span></span>
> - <span data-ttu-id="edcb9-201">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="edcb9-201">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="edcb9-202">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="edcb9-202">Additional Resources</span></span>

<span data-ttu-id="edcb9-203">Další informace o tématech uvedených v tomto kurzu najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="edcb9-203">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="edcb9-204">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="edcb9-204">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="edcb9-205">Nevýhody</span><span class="sxs-lookup"><span data-stu-id="edcb9-205">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="edcb9-206">Metriky regresního modelu</span><span class="sxs-lookup"><span data-stu-id="edcb9-206">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="edcb9-207">Sada dat pro cestu NYC TLC taxislužby</span><span class="sxs-lookup"><span data-stu-id="edcb9-207">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
