---
title: Předvídání cen pomocí learner regrese ML.NET
description: Předvídání cen pomocí ML.NET learner regrese.
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b97ea433b36aa52682e5e86ab493cfabf8f86193
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122080"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="efc6e-103">Kurz: Předvídání cen pomocí learner regrese ML.NET</span><span class="sxs-lookup"><span data-stu-id="efc6e-103">Tutorial: Predict prices using a regression learner with ML.NET</span></span>

<span data-ttu-id="efc6e-104">Tento kurz ukazuje, jak použít ML.NET k sestavení [regresní model](../resources/glossary.md#regression) pro odhad ceny, konkrétně, tarify taxislužby města New York City.</span><span class="sxs-lookup"><span data-stu-id="efc6e-104">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting prices, specifically, New York City taxi fares.</span></span>

> [!NOTE]
> <span data-ttu-id="efc6e-105">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="efc6e-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="efc6e-106">Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="efc6e-106">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="efc6e-107">Tento kurz a související ukázkové právě používáte **ML.NET verze 0,11**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-107">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="efc6e-108">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="efc6e-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="efc6e-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="efc6e-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="efc6e-110">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="efc6e-110">Understand the problem</span></span>
> * <span data-ttu-id="efc6e-111">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="efc6e-111">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="efc6e-112">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="efc6e-112">Prepare and understand the data</span></span>
> * <span data-ttu-id="efc6e-113">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="efc6e-113">Create a learning pipeline</span></span>
> * <span data-ttu-id="efc6e-114">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="efc6e-114">Load and transform the data</span></span>
> * <span data-ttu-id="efc6e-115">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="efc6e-115">Choose a learning algorithm</span></span>
> * <span data-ttu-id="efc6e-116">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-116">Train the model</span></span>
> * <span data-ttu-id="efc6e-117">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-117">Evaluate the model</span></span>
> * <span data-ttu-id="efc6e-118">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="efc6e-118">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="efc6e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efc6e-119">Prerequisites</span></span>

* <span data-ttu-id="efc6e-120">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="efc6e-120">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="efc6e-121">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="efc6e-121">Understand the problem</span></span>

<span data-ttu-id="efc6e-122">Tento problém je o predikci tarif cesty taxíkem v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="efc6e-122">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="efc6e-123">Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul.</span><span class="sxs-lookup"><span data-stu-id="efc6e-123">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="efc6e-124">Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební.</span><span class="sxs-lookup"><span data-stu-id="efc6e-124">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="efc6e-125">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="efc6e-125">Select the appropriate machine learning task</span></span>

<span data-ttu-id="efc6e-126">Chcete předpovídat cenu hodnotu, která je skutečná hodnota, na základě dalších faktorů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="efc6e-126">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="efc6e-127">Udělat, abyste zvolili [regrese](../resources/glossary.md#regression) machine learning úloh.</span><span class="sxs-lookup"><span data-stu-id="efc6e-127">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="efc6e-128">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="efc6e-128">Create a console application</span></span>

1. <span data-ttu-id="efc6e-129">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="efc6e-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="efc6e-130">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="efc6e-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="efc6e-131">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="efc6e-132">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="efc6e-133">V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="efc6e-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="efc6e-134">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-134">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="efc6e-135">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-135">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="efc6e-136">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="efc6e-136">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="efc6e-137">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="efc6e-137">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="efc6e-138">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-138">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="efc6e-139">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="efc6e-139">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="efc6e-140">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="efc6e-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="efc6e-141">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="efc6e-141">Prepare and understand the data</span></span>

1. <span data-ttu-id="efc6e-142">Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="efc6e-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="efc6e-143">Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model.</span><span class="sxs-lookup"><span data-stu-id="efc6e-143">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="efc6e-144">Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="efc6e-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="efc6e-145">V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-145">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="efc6e-146">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="efc6e-147">Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="efc6e-147">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="efc6e-148">Podívejte se na všech sloupcích.</span><span class="sxs-lookup"><span data-stu-id="efc6e-148">Take a look at each of the columns.</span></span> <span data-ttu-id="efc6e-149">Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-149">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="efc6e-150">**Popisek** je identifikátor sloupce, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="efc6e-150">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="efc6e-151">Identifikovanou **funkce** se používají k předpovědi popisek.</span><span class="sxs-lookup"><span data-stu-id="efc6e-151">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="efc6e-152">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="efc6e-152">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="efc6e-153">**vendor_id:** ID dodavatele taxislužby je funkce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-153">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="efc6e-154">**rate_code:** Typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-154">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="efc6e-155">**passenger_count:** Počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-155">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="efc6e-156">**trip_time_in_secs:** Dobu trvání cesty.</span><span class="sxs-lookup"><span data-stu-id="efc6e-156">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="efc6e-157">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="efc6e-157">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="efc6e-158">V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách.</span><span class="sxs-lookup"><span data-stu-id="efc6e-158">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="efc6e-159">Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-159">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="efc6e-160">**trip_distance:** Vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-160">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="efc6e-161">**payment_type:** Způsob platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-161">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="efc6e-162">**fare_amount:** Celkový počet taxislužby tarif placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="efc6e-162">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="efc6e-163">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="efc6e-163">Create data classes</span></span>

<span data-ttu-id="efc6e-164">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="efc6e-164">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="efc6e-165">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="efc6e-165">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="efc6e-166">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="efc6e-166">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="efc6e-167">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="efc6e-167">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="efc6e-168">Přidejte následující `using` direktivy do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="efc6e-168">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="efc6e-169">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="efc6e-169">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` <span data-ttu-id="efc6e-170">je třída vstupní data a obsahuje definice pro všechny sloupce datové sady.</span><span class="sxs-lookup"><span data-stu-id="efc6e-170">is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="efc6e-171">Použití <xref:Microsoft.ML.Data.LoadColumnAttribute> atributy indexů zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="efc6e-171">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="efc6e-172">`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="efc6e-172">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="efc6e-173">Obsahuje pole jednou čárkou `FareAmount`, s `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="efc6e-173">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="efc6e-174">V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.</span><span class="sxs-lookup"><span data-stu-id="efc6e-174">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="efc6e-175">Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.</span><span class="sxs-lookup"><span data-stu-id="efc6e-175">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="efc6e-176">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="efc6e-176">Define data and model paths</span></span>

<span data-ttu-id="efc6e-177">Přidejte následující další `using` příkazy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="efc6e-177">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="efc6e-178">Je potřeba vytvořit tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-178">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* `_trainDataPath` <span data-ttu-id="efc6e-179">obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-179">contains the path to the file with the data set used to train the model.</span></span>
* `_testDataPath` <span data-ttu-id="efc6e-180">obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-180">contains the path to the file with the data set used to evaluate the model.</span></span>
* `_modelPath` <span data-ttu-id="efc6e-181">obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-181">contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="efc6e-182">Přidejte následující kód přímo nad `Main` metoda zadat tyto cesty a `_textLoader` proměnné:</span><span class="sxs-lookup"><span data-stu-id="efc6e-182">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="efc6e-183">Při vytváření modelu s ML.NET spustíte tak, že vytvoříte objekt Context ML.</span><span class="sxs-lookup"><span data-stu-id="efc6e-183">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="efc6e-184">Toto je srovnatelná s hodnotou koncepčně pomocí `DbContext` v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="efc6e-184">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="efc6e-185">Prostředí poskytuje kontext pro úlohu machine learning, který lze použít pro sledování a protokolování výjimek.</span><span class="sxs-lookup"><span data-stu-id="efc6e-185">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="efc6e-186">Inicializace proměnné ve funkci Main</span><span class="sxs-lookup"><span data-stu-id="efc6e-186">Initialize variables in Main</span></span>

<span data-ttu-id="efc6e-187">Vytvořte proměnnou s názvem `mlContext` a inicializujte novou instanci třídy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="efc6e-187">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="efc6e-188">Nahradit `Console.WriteLine("Hello World!")` řádek s následujícím kódem v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-188">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="efc6e-189">Přidejte následující položky jako další řádek kódu v `Main` metoda se má volat `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-189">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="efc6e-190">`Train` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="efc6e-190">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="efc6e-191">Načte data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-191">Loads the data.</span></span>
* <span data-ttu-id="efc6e-192">Extrahuje a transformuje data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-192">Extracts and transforms the data.</span></span>
* <span data-ttu-id="efc6e-193">Trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-193">Trains the model.</span></span>
* <span data-ttu-id="efc6e-194">Model se uloží jako soubor ZIP.</span><span class="sxs-lookup"><span data-stu-id="efc6e-194">Saves the model as .zip file.</span></span>
* <span data-ttu-id="efc6e-195">Vrátí hodnotu modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-195">Returns the model.</span></span>

<span data-ttu-id="efc6e-196">`Train` Metoda trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-196">The `Train` method trains the model.</span></span> <span data-ttu-id="efc6e-197">Vytvoření metody hned pod `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-197">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="efc6e-198">Jsme prochází dva parametry do `Train` metoda; `MLContext` kontextu (`mlContext`) a řetězec pro cestu k datové sadě (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="efc6e-198">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="efc6e-199">Chceme znovu použít tuto metodu pro načtení datové sady.</span><span class="sxs-lookup"><span data-stu-id="efc6e-199">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="efc6e-200">Načítání a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="efc6e-200">Load and transform data</span></span>

<span data-ttu-id="efc6e-201">Načtení dat pomocí `MLContext.Data.LoadFromTextFile` obálky pro [LoadFromTextFile metoda](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="efc6e-201">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="efc6e-202">Vrátí <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="efc6e-202">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

<span data-ttu-id="efc6e-203">Jako vstup a výstup `Transforms`, `DataView` je základní datový kanál typ, srovnatelná s hodnotou `IEnumerable` pro `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="efc6e-203">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="efc6e-204">Data jsou v ML.NET, podobně jako zobrazení SQL.</span><span class="sxs-lookup"><span data-stu-id="efc6e-204">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="efc6e-205">Je laxně Vyhodnocená schematizovanými a heterogenní.</span><span class="sxs-lookup"><span data-stu-id="efc6e-205">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="efc6e-206">Objekt představuje první část kanálu a načte data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-206">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="efc6e-207">Pro účely tohoto kurzu načte datovou sadu s cesty taxíkem informace o cenách.</span><span class="sxs-lookup"><span data-stu-id="efc6e-207">For this tutorial, it loads a dataset with taxi trip pricing information.</span></span> <span data-ttu-id="efc6e-208">Slouží k vytvoření modelu a jeho trénování.</span><span class="sxs-lookup"><span data-stu-id="efc6e-208">This is used to create the model, and train it.</span></span>

<span data-ttu-id="efc6e-209">Přidejte následující kód jako první řádek `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-209">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="efc6e-210">V dalších krocích budeme odkazovat na sloupce pomocí názvy definované v `TaxiTrip` třídy.</span><span class="sxs-lookup"><span data-stu-id="efc6e-210">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="efc6e-211">Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat.</span><span class="sxs-lookup"><span data-stu-id="efc6e-211">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="efc6e-212">Protože chceme předpovědět tarif cesty taxíkem, zkopírujte `FareAmount` sloupec **popisek** sloupec.</span><span class="sxs-lookup"><span data-stu-id="efc6e-212">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="efc6e-213">Chcete-li to mohli udělat, použijte `CopyColumnsEstimator` transformace třídu a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="efc6e-213">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="efc6e-214">Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla (`VendorIdEncoded`, `RateCodeEncoded`, a `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="efc6e-214">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="efc6e-215">Chcete-li to mohli udělat, použijte Microsoft.ML.Transforms.OneHotEncodingTransformer > třídy transformace, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="efc6e-215">To do that, use the Microsoft.ML.Transforms.OneHotEncodingTransformer> transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="efc6e-216">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce `mlContext.Transforms.Concatenate` třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="efc6e-216">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="efc6e-217">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="efc6e-217">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="efc6e-218">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="efc6e-218">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="efc6e-219">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="efc6e-219">Choose a learning algorithm</span></span>

<span data-ttu-id="efc6e-220">Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vybereme algoritmu učení (**learner**).</span><span class="sxs-lookup"><span data-stu-id="efc6e-220">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="efc6e-221">Learner trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-221">The learner trains the model.</span></span> <span data-ttu-id="efc6e-222">Rozhodli jsme se **regrese** úkol pro tento problém, takže použijeme `FastTreeRegressionTrainer` learner, což je jedna studentů regrese poskytované ML.NET.</span><span class="sxs-lookup"><span data-stu-id="efc6e-222">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="efc6e-223">`FastTreeRegressionTrainer` Cvičení algoritmu využívá přechodu zvýšení skóre.</span><span class="sxs-lookup"><span data-stu-id="efc6e-223">The `FastTreeRegressionTrainer` training algorithm utilizes gradient boosting.</span></span> <span data-ttu-id="efc6e-224">Přechodu zvýšení skóre je strojové učení techniku pro regresní problémy.</span><span class="sxs-lookup"><span data-stu-id="efc6e-224">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="efc6e-225">Sestaví každém stromu regrese způsobem podle jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="efc6e-225">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="efc6e-226">Předdefinované ztráta funkce používá k měření chyb v každém kroku a opravit ho v dalším.</span><span class="sxs-lookup"><span data-stu-id="efc6e-226">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="efc6e-227">Výsledkem je, který je ve skutečnosti kompletu sady slabší prediktivní modely prediktivní model.</span><span class="sxs-lookup"><span data-stu-id="efc6e-227">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="efc6e-228">Další informace o přechodu zvýšení skóre, naleznete v tématu [Boosted regrese rozhodovacího stromu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="efc6e-228">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="efc6e-229">Přidejte následující kód do `Train` způsob, jak přidat `FastTreeRegressionTrainer` na zpracování dat kód přidaný v předchozím kroku:</span><span class="sxs-lookup"><span data-stu-id="efc6e-229">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="efc6e-230">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-230">Train the model</span></span>

<span data-ttu-id="efc6e-231">Posledním krokem je pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-231">The final step is to train the model.</span></span> <span data-ttu-id="efc6e-232">Model trénujeme <xref:Microsoft.ML.Data.TransformerChain>založená na datovou sadu, která má načíst a transformovat.</span><span class="sxs-lookup"><span data-stu-id="efc6e-232">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="efc6e-233">Po definování odhadu trénujeme pomocí modelu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> současně už načtený trénovací data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-233">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="efc6e-234">Vrátí model pro předpovědi.</span><span class="sxs-lookup"><span data-stu-id="efc6e-234">This returns a model to use for predictions.</span></span> `pipeline.Fit()` <span data-ttu-id="efc6e-235">trénovat kanálu a vrátí `Transformer` na základě `DataView` předán.</span><span class="sxs-lookup"><span data-stu-id="efc6e-235">trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="efc6e-236">Experiment není spuštěn, dokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="efc6e-236">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a><span data-ttu-id="efc6e-237">Uložit model</span><span class="sxs-lookup"><span data-stu-id="efc6e-237">Save the model</span></span>

<span data-ttu-id="efc6e-238">V tomto okamžiku máte model typu <xref:Microsoft.ML.Data.TransformerChain> , který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="efc6e-238">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="efc6e-239">Chcete-li uložit model do souboru .zip, přidejte následující kód na konci `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-239">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="efc6e-240">Model uložit jako soubor ZIP</span><span class="sxs-lookup"><span data-stu-id="efc6e-240">Save the model as a .zip file</span></span>

<span data-ttu-id="efc6e-241">Vytvořte `SaveModelAsFile` metoda, hned za `Train` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-241">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="efc6e-242">`SaveModelAsFile` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="efc6e-242">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="efc6e-243">Uloží modelu ve formě souboru .zip.</span><span class="sxs-lookup"><span data-stu-id="efc6e-243">Saves the model as a .zip file.</span></span>

<span data-ttu-id="efc6e-244">Potřebujeme vytvořit metodu ke uložit model, takže můžete opakovaně používat a využívat v jiných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="efc6e-244">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="efc6e-245">`ITransformer` Má <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodu, která přijímá `_modelPath` globální pole a <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="efc6e-245">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="efc6e-246">Protože chceme uložit jako soubor zip, vytvoříme `FileStream` bezprostředně před volání `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="efc6e-246">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="efc6e-247">Přidejte následující kód, který `SaveModelAsFile` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="efc6e-247">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="efc6e-248">Také jsme může zobrazit, kde soubor byl zapsán napsáním zprávu konzoly s `_modelPath`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-248">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="efc6e-249">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-249">Evaluate the model</span></span>

<span data-ttu-id="efc6e-250">Hodnocení je proces kontroly, jak dobře model předpovídá hodnoty popisků.</span><span class="sxs-lookup"><span data-stu-id="efc6e-250">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="efc6e-251">Je důležité, že model vytváří dobré předpovědi na data, která nebyla použita pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-251">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="efc6e-252">Jedním ze způsobů k tomu je rozdělení dat na trénovací a testovací datové sady, jak je tomu v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-252">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="efc6e-253">Teď, když jsme natrénovali model na trénovací data, zobrazí se, jak dobře funguje na testovací data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-253">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="efc6e-254">`Evaluate` Metoda vyhodnocuje modelu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-254">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="efc6e-255">Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-255">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="efc6e-256">`Evaluate` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="efc6e-256">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="efc6e-257">Načte datovou sadu testů.</span><span class="sxs-lookup"><span data-stu-id="efc6e-257">Loads the test dataset.</span></span>
* <span data-ttu-id="efc6e-258">Chyba při vyhodnocování regrese vytvoří.</span><span class="sxs-lookup"><span data-stu-id="efc6e-258">Creates the regression evaluator.</span></span>
* <span data-ttu-id="efc6e-259">Vyhodnotí modelu a vytvoří metriky.</span><span class="sxs-lookup"><span data-stu-id="efc6e-259">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="efc6e-260">Zobrazuje metriky.</span><span class="sxs-lookup"><span data-stu-id="efc6e-260">Displays the metrics.</span></span>

<span data-ttu-id="efc6e-261">Přidejte volání do nové metody z `Main` metody, v rámci `Train` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-261">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="efc6e-262">Načíst testovací datové sady pomocí `MLContext.Data.LoadFromTextFile` obálky.</span><span class="sxs-lookup"><span data-stu-id="efc6e-262">Load the test dataset using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="efc6e-263">Můžete si vyzkoušet modelu s použitím tohoto objektu dataset jako kontrola kvality.</span><span class="sxs-lookup"><span data-stu-id="efc6e-263">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="efc6e-264">Přidejte následující kód, který `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-264">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="efc6e-265">Dále pomocí služby machine learning `model` parametr (transformace) pro vstup funkce a vrátí předpovědi.</span><span class="sxs-lookup"><span data-stu-id="efc6e-265">Next, use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="efc6e-266">Přidejte následující kód, který `Evaluate` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="efc6e-266">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="efc6e-267">`RegressionContext.Evaluate` Metoda vypočítá metrik kvality pro `PredictionModel` pomocí zadané datové sady.</span><span class="sxs-lookup"><span data-stu-id="efc6e-267">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="efc6e-268">Vrátí <xref:Microsoft.ML.Data.RegressionMetrics> objekt, který obsahuje celkový metriky počítají tak, že nástroje pro vyhodnocení regrese.</span><span class="sxs-lookup"><span data-stu-id="efc6e-268">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="efc6e-269">Chcete-li zobrazit tyto k určení kvality tohoto modelu, budete muset získat metriky první.</span><span class="sxs-lookup"><span data-stu-id="efc6e-269">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="efc6e-270">Přidejte následující kód jako další řádek `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-270">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="efc6e-271">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="efc6e-271">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="efc6e-272">[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="efc6e-272">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="efc6e-273">RSquared trvá hodnoty v rozmezí 0 až 1.</span><span class="sxs-lookup"><span data-stu-id="efc6e-273">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="efc6e-274">Čím blíž její hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="efc6e-274">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="efc6e-275">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="efc6e-275">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="efc6e-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model.</span><span class="sxs-lookup"><span data-stu-id="efc6e-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="efc6e-277">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="efc6e-277">The lower it is, the better the model is.</span></span> <span data-ttu-id="efc6e-278">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="efc6e-278">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="efc6e-279">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="efc6e-279">Use the model for predictions</span></span>

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="efc6e-280">Předpověď data výsledek testu s modelem a jednoho komentáře</span><span class="sxs-lookup"><span data-stu-id="efc6e-280">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="efc6e-281">Vytvořte `TestSinglePrediction` metoda, hned za `Evaluate` metodu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-281">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="efc6e-282">`TestSinglePrediction` Metoda spustí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="efc6e-282">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="efc6e-283">Vytvoří jeden komentář testovací data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-283">Creates a single comment of test data.</span></span>
* <span data-ttu-id="efc6e-284">Předpovídá tarif velikost na základě dat testu.</span><span class="sxs-lookup"><span data-stu-id="efc6e-284">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="efc6e-285">Kombinuje testovací data a předpovědi pro vytváření sestav.</span><span class="sxs-lookup"><span data-stu-id="efc6e-285">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="efc6e-286">Zobrazí predikované výsledky.</span><span class="sxs-lookup"><span data-stu-id="efc6e-286">Displays the predicted results.</span></span>

<span data-ttu-id="efc6e-287">Přidejte volání do nové metody z `Main` metody, v rámci `Evaluate` volání metody, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="efc6e-287">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="efc6e-288">Protože chceme, aby načíst model ze souboru zip jsme předtím uložili, a My vytvoříme `FileStream` bezprostředně před volání `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="efc6e-288">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="efc6e-289">Přidejte následující kód, který `TestSinglePrediction` metody jako další řádek:</span><span class="sxs-lookup"><span data-stu-id="efc6e-289">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="efc6e-290">Zatímco `model` je `transformer` , který pracuje na mnoho řádky dat, je potřeba k předpovědím na jednotlivé příklady o velmi běžný scénář produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="efc6e-290">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="efc6e-291"><xref:Microsoft.ML.PredictionEngine%602> Představuje obálku, která je vrácena z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="efc6e-291">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="efc6e-292">Přidejte následující kód k vytvoření `PredictionEngine` jako další řádek `TestSinglePrediction` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-292">Let's add the following code to create the `PredictionEngine` as the next line in the `TestSinglePrediction` Method:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="efc6e-293">Tento kurz používá jeden test latence v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="efc6e-293">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="efc6e-294">Později můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="efc6e-294">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="efc6e-295">Přidat cestu k otestování předpovědi trénovaného modelu nákladů `TestSinglePrediction` metodu tak, že vytvoříte instanci `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="efc6e-295">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="efc6e-296">Který můžeme použít k predikci tarif založené na jednu instanci data o jízdách taxislužby.</span><span class="sxs-lookup"><span data-stu-id="efc6e-296">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="efc6e-297">Chcete-li získat predikcí, použijte <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na data.</span><span class="sxs-lookup"><span data-stu-id="efc6e-297">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="efc6e-298">Poznamenat, že vstupní data na řetězec a tento model zahrnuje snadné.</span><span class="sxs-lookup"><span data-stu-id="efc6e-298">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="efc6e-299">Kanálu se synchronizuje během trénování a predikcí.</span><span class="sxs-lookup"><span data-stu-id="efc6e-299">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="efc6e-300">Nemáte psát kód předzpracování/snadné speciálně pro předpovědi a stejného rozhraní API se postará o batch i jednorázové předpovědi.</span><span class="sxs-lookup"><span data-stu-id="efc6e-300">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="efc6e-301">K zobrazení předpokládané tarif zadané cesty, přidejte následující kód do `TestSinglePrediction` metody:</span><span class="sxs-lookup"><span data-stu-id="efc6e-301">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="efc6e-302">Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="efc6e-302">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="efc6e-303">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="efc6e-303">Congratulations!</span></span> <span data-ttu-id="efc6e-304">Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="efc6e-304">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="efc6e-305">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="efc6e-305">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="efc6e-306">Další kroky</span><span class="sxs-lookup"><span data-stu-id="efc6e-306">Next steps</span></span>

<span data-ttu-id="efc6e-307">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="efc6e-307">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="efc6e-308">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="efc6e-308">Understand the problem</span></span>
> * <span data-ttu-id="efc6e-309">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="efc6e-309">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="efc6e-310">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="efc6e-310">Prepare and understand the data</span></span>
> * <span data-ttu-id="efc6e-311">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="efc6e-311">Create a learning pipeline</span></span>
> * <span data-ttu-id="efc6e-312">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="efc6e-312">Load and transform the data</span></span>
> * <span data-ttu-id="efc6e-313">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="efc6e-313">Choose a learning algorithm</span></span>
> * <span data-ttu-id="efc6e-314">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-314">Train the model</span></span>
> * <span data-ttu-id="efc6e-315">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="efc6e-315">Evaluate the model</span></span>
> * <span data-ttu-id="efc6e-316">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="efc6e-316">Use the model for predictions</span></span>

<span data-ttu-id="efc6e-317">Přejděte k dalšímu kurzu, kde Další informace.</span><span class="sxs-lookup"><span data-stu-id="efc6e-317">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="efc6e-318">Clustering Iris</span><span class="sxs-lookup"><span data-stu-id="efc6e-318">Iris clustering</span></span>](iris-clustering.md)
