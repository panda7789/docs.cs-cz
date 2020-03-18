---
title: 'Kurz: Předvídejte ceny pomocí regrese pomocí tvůrce modelů'
description: Tento kurz ukazuje, jak vytvořit regresní model pomocí ML.NET Model Builder předpovědět ceny, konkrétně new york city taxi tarify.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c027fe57f571c791784b0bdb7ad9503fc49daa1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187699"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="cdf93-103">Kurz: Předvídejte ceny pomocí regrese pomocí tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="cdf93-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="cdf93-104">Naučte se používat ML.NET Tvůrce modelů k vytvoření regresního modelu k předvídání cen.</span><span class="sxs-lookup"><span data-stu-id="cdf93-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="cdf93-105">Konzolová aplikace .NET, kterou vyvíjíte v tomto kurzu, předpovídá tarify taxi na základě historických dat o jízdném taxi v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="cdf93-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="cdf93-106">Šablonu předpovědi ceny tvůrce modelu lze použít pro libovolný scénář, který vyžaduje číselnou hodnotu předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf93-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="cdf93-107">Příklady scénářů zahrnují: předpověď cen domů, předpověď poptávky a prognózu prodeje.</span><span class="sxs-lookup"><span data-stu-id="cdf93-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="cdf93-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="cdf93-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cdf93-109">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="cdf93-110">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="cdf93-110">Choose a scenario</span></span>
> - <span data-ttu-id="cdf93-111">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-111">Load the data</span></span>
> - <span data-ttu-id="cdf93-112">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-112">Train the model</span></span>
> - <span data-ttu-id="cdf93-113">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-113">Evaluate the model</span></span>
> - <span data-ttu-id="cdf93-114">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="cdf93-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="cdf93-115">Tvůrce modelů je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="cdf93-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="cdf93-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdf93-116">Pre-requisites</span></span>

<span data-ttu-id="cdf93-117">Seznam předpokladů a pokynů k instalaci naleznete v [instalační příručce výrobce modelů](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="cdf93-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="cdf93-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="cdf93-118">Create a console application</span></span>

1. <span data-ttu-id="cdf93-119">Vytvořte **aplikaci základní konzoly C# .NET** s názvem "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="cdf93-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="cdf93-120">Ujistěte se, že **umístit řešení a projekt ve stejném adresáři** je **nezaškrtnuté** (VS 2019) nebo **vytvořit adresář pro řešení** je **zaškrtnuto** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="cdf93-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="cdf93-121">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="cdf93-122">Vytvořte adresář s názvem *Data* v projektu pro uložení souborů sady dat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="cdf93-123">Datová sada použitá k trénování a vyhodnocování modelu strojového učení je původně z datové sady NYC TLC Taxi Trip.</span><span class="sxs-lookup"><span data-stu-id="cdf93-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="cdf93-124">Chcete-li stáhnout sadu dat, přejděte na [odkaz ke stažení taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="cdf93-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="cdf93-125">Po načtení stránky klikněte pravým tlačítkem myši na libovolné místo na stránce a vyberte **Uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="cdf93-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="cdf93-126">Pomocí **dialogového okna Uložit jako** uložte soubor do složky *Data,* kterou jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="cdf93-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="cdf93-127">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *taxi-fare-train.csv* a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cdf93-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="cdf93-128">V části **Upřesnit**změňte hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="cdf93-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="cdf93-129">Každý řádek `taxi-fare-train.csv` v datové sadě obsahuje podrobnosti o cestách taxi.</span><span class="sxs-lookup"><span data-stu-id="cdf93-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="cdf93-130">Otevřete datovou sadu **taxi-fare-train.csv**</span><span class="sxs-lookup"><span data-stu-id="cdf93-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="cdf93-131">Zadaný soubor dat obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="cdf93-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="cdf93-132">**vendor_id:** ID dodavatele taxi služby je funkce.</span><span class="sxs-lookup"><span data-stu-id="cdf93-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="cdf93-133">**rate_code:** Typ sazby taxi cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="cdf93-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="cdf93-134">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="cdf93-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="cdf93-135">**trip_time_in_secs:** Doba, po kterou cesta trvala.</span><span class="sxs-lookup"><span data-stu-id="cdf93-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="cdf93-136">Chcete předpovědět jízdné cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="cdf93-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="cdf93-137">V tu chvíli nevíte, jak dlouho cesta bude trvat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="cdf93-138">Doba jízdy tedy není funkcí a tento sloupec z modelu vyloučíte.</span><span class="sxs-lookup"><span data-stu-id="cdf93-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="cdf93-139">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="cdf93-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="cdf93-140">**payment_type:** Platební metoda (v hotovosti nebo kreditní kartou) je funkce.</span><span class="sxs-lookup"><span data-stu-id="cdf93-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="cdf93-141">**fare_amount:** Celková zaplacená taxi služba je štítek.</span><span class="sxs-lookup"><span data-stu-id="cdf93-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="cdf93-142">Je `label` sloupec, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="cdf93-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="cdf93-143">Při provádění regresní úlohy je cílem předpovědět číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="cdf93-144">V tomto scénáři predikce ceny se předpovězí náklady na jízdu taxíkem.</span><span class="sxs-lookup"><span data-stu-id="cdf93-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="cdf93-145">Proto **fare_amount** je popisek.</span><span class="sxs-lookup"><span data-stu-id="cdf93-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="cdf93-146">Identifikované `features` jsou vstupy, které poskytnete `label`modelu předpovědět .</span><span class="sxs-lookup"><span data-stu-id="cdf93-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="cdf93-147">V tomto případě se zbývající sloupce s výjimkou **trip_time_in_secs** používají jako funkce nebo vstupy k předvídání částky jízdného.</span><span class="sxs-lookup"><span data-stu-id="cdf93-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="cdf93-148">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="cdf93-148">Choose a scenario</span></span>

<span data-ttu-id="cdf93-149">Chcete-li trénovat model, musíte vybrat ze seznamu dostupných scénářů strojového učení poskytovaných tvůrcem modelů.</span><span class="sxs-lookup"><span data-stu-id="cdf93-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="cdf93-150">V tomto případě je `Price Prediction`scénář .</span><span class="sxs-lookup"><span data-stu-id="cdf93-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="cdf93-151">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt *TaxiFarePrediction* a vyberte **přidat** > **strojové učení**.</span><span class="sxs-lookup"><span data-stu-id="cdf93-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="cdf93-152">V kroku scénáře nástroje Tvůrce modelů vyberte scénář *Předpověď cen.*</span><span class="sxs-lookup"><span data-stu-id="cdf93-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="cdf93-153">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-153">Load the data</span></span>

<span data-ttu-id="cdf93-154">Tvůrce modelů přijímá data ze dvou zdrojů, databáze serveru SQL Server nebo místního souboru ve formátu CSV nebo tsv.</span><span class="sxs-lookup"><span data-stu-id="cdf93-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="cdf93-155">V datovém kroku nástroje Tvůrce modelů vyberte *Soubor* z rozevíracího souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="cdf93-156">Vyberte tlačítko vedle textového pole *Vybrat soubor* a pomocí Průzkumníka souborů procházet a vyberte *soubor taxi-fare-test.csv* v adresáři *Data.*</span><span class="sxs-lookup"><span data-stu-id="cdf93-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="cdf93-157">V rozevíracím seznamu Sloupec zvolte *fare_amount,* *který chcete předpovědět (Popisek).*</span><span class="sxs-lookup"><span data-stu-id="cdf93-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="cdf93-158">Rozbalte rozbalovací seznam *Vstupní sloupce (Funkce)* a odškrtnout sloupec *trip_time_in_secs,* abyste ho během tréninku vyloučili jako funkci.</span><span class="sxs-lookup"><span data-stu-id="cdf93-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="cdf93-159">Přejděte ke kroku vlaku nástroje Tvůrce modelů.</span><span class="sxs-lookup"><span data-stu-id="cdf93-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="cdf93-160">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-160">Train the model</span></span>

<span data-ttu-id="cdf93-161">Úloha strojového učení slouží k trénování modelu předpověď cen v tomto kurzu je regrese.</span><span class="sxs-lookup"><span data-stu-id="cdf93-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="cdf93-162">Během procesu školení modelu Model Builder trénuje samostatné modely pomocí různých regresní algoritmy a nastavení najít nejvýkonnější model pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="cdf93-163">Doba potřebná pro vyškolení modelu je úměrná množství dat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="cdf93-164">Tvůrce modelů automaticky vybere výchozí hodnotu pro **čas pro trénování (sekundy)** na základě velikosti zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="cdf93-165">Ponechte výchozí hodnotu jako *čas pro trénování (sekundy),* pokud nechcete trénovat delší dobu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="cdf93-166">Vyberte *možnost Zahájit trénink*.</span><span class="sxs-lookup"><span data-stu-id="cdf93-166">Select *Start Training*.</span></span>

<span data-ttu-id="cdf93-167">V průběhu tréninkového procesu se `Progress` údaje o průběhu zobrazují v části kroku vlaku.</span><span class="sxs-lookup"><span data-stu-id="cdf93-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="cdf93-168">Stav zobrazuje stav dokončení procesu školení.</span><span class="sxs-lookup"><span data-stu-id="cdf93-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="cdf93-169">Nejlepší přesnost zobrazuje přesnost nejvýkonnějšího modelu, který dosud našel Model Builder.</span><span class="sxs-lookup"><span data-stu-id="cdf93-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="cdf93-170">Vyšší přesnost znamená, že model byl na testovacích datech předpovězen správněji.</span><span class="sxs-lookup"><span data-stu-id="cdf93-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="cdf93-171">Nejlepší algoritmus zobrazí název nejvýkonnějšíalgoritmus u kterého našel Model Builder tak daleko.</span><span class="sxs-lookup"><span data-stu-id="cdf93-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="cdf93-172">Poslední algoritmus zobrazí název algoritmu, který byl naposledy použit tvůrcem modelů k trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="cdf93-173">Po dokončení školení přejděte ke kroku vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="cdf93-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="cdf93-174">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-174">Evaluate the model</span></span>

<span data-ttu-id="cdf93-175">Výsledkem tréninkového kroku bude jeden model, který měl nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="cdf93-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="cdf93-176">V kroku vyhodnocení nástroje Tvůrce modelů bude výstupní část obsahovat algoritmus používaný nejvýkonnějším modelem v položce *Nejlepší model* spolu s metrikami v *best model quality (RSquared).*</span><span class="sxs-lookup"><span data-stu-id="cdf93-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="cdf93-177">Kromě toho souhrnná tabulka obsahující prvních pět modelů a jejich metriky.</span><span class="sxs-lookup"><span data-stu-id="cdf93-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="cdf93-178">Pokud nejste spokojeni s metrikami přesnosti, některé jednoduché způsoby, jak se pokusit zlepšit přesnost modelu, jsou prodloužení doby pro trénování modelu nebo použití více dat.</span><span class="sxs-lookup"><span data-stu-id="cdf93-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="cdf93-179">V opačném případě přejděte na krok kódu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="cdf93-180">Přidání kódu pro předpověď</span><span class="sxs-lookup"><span data-stu-id="cdf93-180">Add the code to make predictions</span></span>

<span data-ttu-id="cdf93-181">V důsledku procesu školení budou vytvořeny dva projekty.</span><span class="sxs-lookup"><span data-stu-id="cdf93-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="cdf93-182">TaxiFarePredictionML.ConsoleApp: Aplikace .NET Core Console, která obsahuje trénování modelu a kód spotřeby vzorku.</span><span class="sxs-lookup"><span data-stu-id="cdf93-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="cdf93-183">TaxiFarePredictionML.Model: Knihovna třídy .NET Standard obsahující datové modely, které definují schéma vstupních a výstupních dat modelu, uloženou `ConsumeModel` verzi nejvýkonnějšího modelu během trénování a pomocnou třídu volánou k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf93-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="cdf93-184">V kroku kódu nástroje Tvůrce modelů vyberte **Přidat projekty** a přidejte do řešení automaticky generované projekty.</span><span class="sxs-lookup"><span data-stu-id="cdf93-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="cdf93-185">Otevřete soubor *Program.cs* v projektu *TaxiFarePrediction.*</span><span class="sxs-lookup"><span data-stu-id="cdf93-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="cdf93-186">Přidejte následující příkaz using, abyste odkazovali na projekt *TaxiFarePredictionML.Model:*</span><span class="sxs-lookup"><span data-stu-id="cdf93-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="cdf93-187">Chcete-li předpovědět nová data pomocí modelu, vytvořte `ModelInput` novou `Main` instanci třídy uvnitř metody vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf93-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="cdf93-188">Všimněte si, že částka jízdného není součástí vstupu.</span><span class="sxs-lookup"><span data-stu-id="cdf93-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="cdf93-189">Důvodem je, že model bude generovat předpověď pro něj.</span><span class="sxs-lookup"><span data-stu-id="cdf93-189">This is because the model will generate the prediction for it.</span></span>

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

1. <span data-ttu-id="cdf93-190">Použijte `Predict` metodu `ConsumeModel` z třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf93-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="cdf93-191">Metoda `Predict` načte trénovaný [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model, vytvořit pro model a používá jej k vytváření předpovědí na nová data.</span><span class="sxs-lookup"><span data-stu-id="cdf93-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="cdf93-192">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cdf93-192">Run the application.</span></span>

    <span data-ttu-id="cdf93-193">Výstup generovaný programem by měl vypadat podobně jako výstřižek níže:</span><span class="sxs-lookup"><span data-stu-id="cdf93-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="cdf93-194">Pokud potřebujete odkazovat na generované projekty později uvnitř jiného řešení, `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` můžete je najít uvnitř adresáře.</span><span class="sxs-lookup"><span data-stu-id="cdf93-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cdf93-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cdf93-195">Next Steps</span></span>

<span data-ttu-id="cdf93-196">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="cdf93-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cdf93-197">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="cdf93-198">Výběr scénáře</span><span class="sxs-lookup"><span data-stu-id="cdf93-198">Choose a scenario</span></span>
> - <span data-ttu-id="cdf93-199">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="cdf93-199">Load the data</span></span>
> - <span data-ttu-id="cdf93-200">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-200">Train the model</span></span>
> - <span data-ttu-id="cdf93-201">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-201">Evaluate the model</span></span>
> - <span data-ttu-id="cdf93-202">Použití modelu pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="cdf93-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cdf93-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cdf93-203">Additional Resources</span></span>

<span data-ttu-id="cdf93-204">Další informace o tématech uvedených v tomto kurzu naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="cdf93-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="cdf93-205">Scénáře tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="cdf93-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="cdf93-206">Regrese</span><span class="sxs-lookup"><span data-stu-id="cdf93-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="cdf93-207">Metriky regresního modelu</span><span class="sxs-lookup"><span data-stu-id="cdf93-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="cdf93-208">NYC TLC Taxi Výlet datový soubor</span><span class="sxs-lookup"><span data-stu-id="cdf93-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
