---
title: ML.NET používají k vytváření prognóz tarify taxislužby města New York (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e3ff2124a43cf42ce26cf94cfd5384387eef0ed9
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937069"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="8d41d-103">Kurz: Použití ML.NET předpovědět tarify taxislužby města New York (regrese)</span><span class="sxs-lookup"><span data-stu-id="8d41d-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="8d41d-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="8d41d-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8d41d-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8d41d-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="8d41d-106">Tento kurz ukazuje, jak použít ML.NET k sestavení [regresní model](../resources/glossary.md#regression) pro predikci tarify taxislužby města New York City.</span><span class="sxs-lookup"><span data-stu-id="8d41d-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="8d41d-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="8d41d-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8d41d-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8d41d-108">Understand the problem</span></span>
> * <span data-ttu-id="8d41d-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="8d41d-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8d41d-110">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="8d41d-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="8d41d-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="8d41d-112">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="8d41d-112">Load and transform the data</span></span>
> * <span data-ttu-id="8d41d-113">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8d41d-114">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-114">Train the model</span></span>
> * <span data-ttu-id="8d41d-115">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-115">Evaluate the model</span></span>
> * <span data-ttu-id="8d41d-116">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d41d-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d41d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d41d-117">Prerequisites</span></span>

* <span data-ttu-id="8d41d-118">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8d41d-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="8d41d-119">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8d41d-119">Understand the problem</span></span>

<span data-ttu-id="8d41d-120">Tento problém je zaměřená na **předpověď tarif taxislužby dojít v New Yorku**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="8d41d-121">Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul.</span><span class="sxs-lookup"><span data-stu-id="8d41d-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="8d41d-122">Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební.</span><span class="sxs-lookup"><span data-stu-id="8d41d-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="8d41d-123">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="8d41d-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="8d41d-124">Pro předpověď tarif taxi, nejprve vyberte úlohu učení příslušný počítač.</span><span class="sxs-lookup"><span data-stu-id="8d41d-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="8d41d-125">Pokud chcete předpovědět, skutečné hodnoty (double, který představuje cenu) na základě dalších faktorů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="8d41d-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="8d41d-126">Můžete vybrat [ **regrese** ](../resources/glossary.md#regression) úloh.</span><span class="sxs-lookup"><span data-stu-id="8d41d-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8d41d-127">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="8d41d-127">Create a console application</span></span>

1. <span data-ttu-id="8d41d-128">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8d41d-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="8d41d-129">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="8d41d-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8d41d-130">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8d41d-131">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8d41d-132">V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="8d41d-133">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu souborů:</span><span class="sxs-lookup"><span data-stu-id="8d41d-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="8d41d-134">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8d41d-135">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="8d41d-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="8d41d-136">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="8d41d-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8d41d-137">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8d41d-138">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8d41d-139">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="8d41d-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8d41d-140">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="8d41d-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="8d41d-141">Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="8d41d-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="8d41d-142">Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model.</span><span class="sxs-lookup"><span data-stu-id="8d41d-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="8d41d-143">Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="8d41d-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="8d41d-144">V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="8d41d-145">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **vždy**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="8d41d-146">Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="8d41d-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="8d41d-147">Podívejte se na všech sloupcích.</span><span class="sxs-lookup"><span data-stu-id="8d41d-147">Take a look at each of the columns.</span></span> <span data-ttu-id="8d41d-148">Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="8d41d-149">**Popisek** je identifikátor sloupce, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="8d41d-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="8d41d-150">Identifikovanou **funkce** se používají k předpovědi popisek.</span><span class="sxs-lookup"><span data-stu-id="8d41d-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="8d41d-151">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="8d41d-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="8d41d-152">**vendor_id:** ID dodavatele, taxi je funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="8d41d-153">**rate_code:** typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="8d41d-154">**passenger_count:** počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="8d41d-155">**trip_time_in_secs:** trvalo cesty časového intervalu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="8d41d-156">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="8d41d-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="8d41d-157">V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách.</span><span class="sxs-lookup"><span data-stu-id="8d41d-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="8d41d-158">Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="8d41d-159">**trip_distance:** vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="8d41d-160">**payment_type:** platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="8d41d-161">**fare_amount:** tarif celkový taxislužby placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="8d41d-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="8d41d-162">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="8d41d-162">Create data classes</span></span>

<span data-ttu-id="8d41d-163">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="8d41d-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="8d41d-164">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8d41d-165">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="8d41d-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="8d41d-166">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8d41d-167">Přidejte následující `using` direktivy do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="8d41d-167">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="8d41d-168">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="8d41d-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="8d41d-169">`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady.</span><span class="sxs-lookup"><span data-stu-id="8d41d-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="8d41d-170">Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atributy indexů zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="8d41d-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="8d41d-171">`TaxiTripFarePrediction` Třída se používá k reprezentování předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d41d-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="8d41d-172">Má jednou čárkou (`FareAmount`) pole `Score` [Názevsloupce](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="8d41d-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="8d41d-173">**Skóre** sloupec je speciální sloupce v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8d41d-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="8d41d-174">Model výstupy předpovězeným hodnotám. do tohoto sloupce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="8d41d-175">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="8d41d-175">Define data and model paths</span></span>

<span data-ttu-id="8d41d-176">Přejděte zpět *Program.cs* a přidejte tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="8d41d-176">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="8d41d-177">`_datapath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-177">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="8d41d-178">`_testdatapath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-178">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="8d41d-179">`_modelpath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-179">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="8d41d-180">Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="8d41d-180">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="8d41d-181">Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="8d41d-181">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="8d41d-182">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-182">Create a learning pipeline</span></span>

<span data-ttu-id="8d41d-183">Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="8d41d-183">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="8d41d-184">V `Main`, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8d41d-184">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="8d41d-185">`Train` Metoda trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-185">The `Train` method trains the model.</span></span> <span data-ttu-id="8d41d-186">Vytvoření metody hned pod `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d41d-186">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="8d41d-187">Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-187">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="8d41d-188">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-188">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="8d41d-189">Načítání a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="8d41d-189">Load and transform data</span></span>

<span data-ttu-id="8d41d-190">Prvním krokem prováděnou kanálem learning načítá data z trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="8d41d-190">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="8d41d-191">V našem případě trénovací datové sady se ukládají v textovém souboru s cestu definovanou `_datapath` pole.</span><span class="sxs-lookup"><span data-stu-id="8d41d-191">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="8d41d-192">Proto první řádek by měl být ignorovány při načítání dat, jestli tento soubor obsahuje záhlaví s názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="8d41d-192">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="8d41d-193">Sloupce v souboru jsou oddělené čárkou (",").</span><span class="sxs-lookup"><span data-stu-id="8d41d-193">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="8d41d-194">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-194">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="8d41d-195">V dalších krocích budeme odkazovat na sloupce pomocí názvy definované v `TaxiTrip` třídy.</span><span class="sxs-lookup"><span data-stu-id="8d41d-195">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="8d41d-196">Když je model trénují a vyhodnocují, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat.</span><span class="sxs-lookup"><span data-stu-id="8d41d-196">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="8d41d-197">Protože chceme předpovědět tarif cesty taxíkem, zkopírujte `FareAmount` sloupec **popisek** sloupec.</span><span class="sxs-lookup"><span data-stu-id="8d41d-197">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="8d41d-198">K tomuto účelu použijte <xref:Microsoft.ML.Transforms.ColumnCopier> a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8d41d-198">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="8d41d-199">Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla.</span><span class="sxs-lookup"><span data-stu-id="8d41d-199">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="8d41d-200">K tomuto účelu použijte <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8d41d-200">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="8d41d-201">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Transforms.ColumnConcatenator> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="8d41d-201">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="8d41d-202">Tento krok je nutné, protože learner zpracovává pouze funkce z **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-202">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="8d41d-203">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="8d41d-203">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="8d41d-204">Všimněte si, že `TripTime` sloupec, který odpovídá `trip_time_in_secs` sloupec v souboru datové sady není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="8d41d-204">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="8d41d-205">Už jste zjistili, že to není užitečné předpovědi funkce.</span><span class="sxs-lookup"><span data-stu-id="8d41d-205">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="8d41d-206">Tyto kroky je nutné přidat do kanálu v pořadí určeném výše pro úspěšné provedení.</span><span class="sxs-lookup"><span data-stu-id="8d41d-206">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8d41d-207">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-207">Choose a learning algorithm</span></span>

<span data-ttu-id="8d41d-208">Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vyberte algoritmus učení (**learner**).</span><span class="sxs-lookup"><span data-stu-id="8d41d-208">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="8d41d-209">Learner trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-209">The learner trains the model.</span></span> <span data-ttu-id="8d41d-210">Jste si zvolili **regrese úloh** pro tento problém, proto přidat <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, což je jedna studentů regrese poskytované ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8d41d-210">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="8d41d-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner využívá přechodu zvýšení skóre.</span><span class="sxs-lookup"><span data-stu-id="8d41d-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="8d41d-212">Přechodu zvýšení skóre je strojové učení techniku pro regresní problémy.</span><span class="sxs-lookup"><span data-stu-id="8d41d-212">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="8d41d-213">Sestaví každém stromu regrese způsobem podle jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="8d41d-213">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="8d41d-214">Předdefinované ztráta funkce používá k měření chyb v každém kroku a opravit ho v dalším.</span><span class="sxs-lookup"><span data-stu-id="8d41d-214">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="8d41d-215">Výsledkem je, který je ve skutečnosti kompletu sady slabší prediktivní modely prediktivní model.</span><span class="sxs-lookup"><span data-stu-id="8d41d-215">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="8d41d-216">Další informace o přechodu zvýšení skóre, naleznete v tématu [Boosted regrese rozhodovacího stromu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="8d41d-216">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="8d41d-217">Přidejte následující kód do `Train` metoda po zpracování dat kód přidaný v předchozím kroku:</span><span class="sxs-lookup"><span data-stu-id="8d41d-217">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="8d41d-218">Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale jazyka C# má syntaxe inicializace kolekce po ruce, který usnadňuje vytváření a inicializace kanálu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-218">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="8d41d-219">Nahraďte kód přidaný zatím na `Train` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8d41d-219">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="8d41d-220">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-220">Train the model</span></span>

<span data-ttu-id="8d41d-221">Posledním krokem je pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-221">The final step is to train the model.</span></span> <span data-ttu-id="8d41d-222">Až do této chvíle byl proveden nic v kanálu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-222">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="8d41d-223">`pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přijímá instanci `TInput` zadejte a vypíše instance `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-223">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="8d41d-224">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-224">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="8d41d-225">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="8d41d-225">And that's it!</span></span> <span data-ttu-id="8d41d-226">Úspěšně jste trénuje model, který může předpovídat tarify taxislužby města v NYC strojového učení.</span><span class="sxs-lookup"><span data-stu-id="8d41d-226">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="8d41d-227">Nyní Pojďme podívat, abyste pochopili, jak přesný je model a zjistěte, jak ho použít k předpovědi hodnot tarif taxislužby.</span><span class="sxs-lookup"><span data-stu-id="8d41d-227">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="8d41d-228">Uložit model</span><span class="sxs-lookup"><span data-stu-id="8d41d-228">Save the model</span></span>

<span data-ttu-id="8d41d-229">Před přechodem na další krok, uložit model do souboru ZIP a přidejte následující kód na konci `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-229">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="8d41d-230">Přidávání `await` příkazu `model.WriteAsync` volání znamená, že `Train` metoda musí být změněna na asynchronní metoda vracející úlohu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="8d41d-231">Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8d41d-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="8d41d-232">Změna návratového typu `Train` metoda znamená, že chcete přidat `await` kódu, který volá `Train` v `Main` způsob, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8d41d-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="8d41d-233">Pomocí `await` v `Main` znamená, že metoda `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:</span><span class="sxs-lookup"><span data-stu-id="8d41d-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="8d41d-234">Budete také muset přidat následující `using` direktiv v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="8d41d-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="8d41d-235">Vzhledem k tomu, `async Main` metoda je funkce přidané v jazyce C# 7.1 a výchozí jazyková verze projektu je C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8d41d-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="8d41d-236">Chcete-li to mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="8d41d-237">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="8d41d-238">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="8d41d-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="8d41d-239">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="8d41d-240">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-240">Evaluate the model</span></span>

<span data-ttu-id="8d41d-241">Hodnocení je proces kontroly, jak dobře model předpovídá hodnoty popisků.</span><span class="sxs-lookup"><span data-stu-id="8d41d-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="8d41d-242">Je důležité, že model vytváří dobré předpovědi na data, která nebyla použita pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="8d41d-243">Jedním ze způsobů k tomu je rozdělení dat na trénování a testování datových sad, jak je tomu v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-243">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="8d41d-244">Teď, když jsme natrénovali model trénovat na základě modelu dat, zobrazí se, jak dobře funguje na testovací data.</span><span class="sxs-lookup"><span data-stu-id="8d41d-244">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="8d41d-245">Přejděte zpět `Main` metoda a přidejte následující kód pod volání `Train`– metoda:</span><span class="sxs-lookup"><span data-stu-id="8d41d-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="8d41d-246">`Evaluate` Metoda vyhodnocuje modelu.</span><span class="sxs-lookup"><span data-stu-id="8d41d-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="8d41d-247">Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="8d41d-248">Přidejte následující kód do `Evaluate` metodu pro nastavení načítání testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="8d41d-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="8d41d-249">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="8d41d-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="8d41d-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model.</span><span class="sxs-lookup"><span data-stu-id="8d41d-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="8d41d-251">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="8d41d-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="8d41d-252">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="8d41d-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="8d41d-253">[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="8d41d-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="8d41d-254">RSquared trvá hodnoty v rozmezí 0 až 1.</span><span class="sxs-lookup"><span data-stu-id="8d41d-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="8d41d-255">Čím blíž její hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="8d41d-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="8d41d-256">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="8d41d-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="8d41d-257">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d41d-257">Use the model for predictions</span></span>

<span data-ttu-id="8d41d-258">Dále vytvořte třídu pro uložení testovacích scénářů, které vám pomůže se ujistěte se, že model funguje správně:</span><span class="sxs-lookup"><span data-stu-id="8d41d-258">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="8d41d-259">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="8d41d-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8d41d-260">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="8d41d-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="8d41d-261">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d41d-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8d41d-262">Upravte třídu pro statické stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8d41d-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="8d41d-263">Tento kurz používá jeden test latence v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="8d41d-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="8d41d-264">Později můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="8d41d-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="8d41d-265">Přidejte následující kód do `TestTrips` třídy:</span><span class="sxs-lookup"><span data-stu-id="8d41d-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="8d41d-266">Tuto cestu skutečné tarif je 29,5.</span><span class="sxs-lookup"><span data-stu-id="8d41d-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="8d41d-267">Model bude předpovídat tarif, použijte jako zástupný znak, 0.</span><span class="sxs-lookup"><span data-stu-id="8d41d-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="8d41d-268">Pokud chcete předpovědět tarif zadané cesty, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8d41d-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="8d41d-269">Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="8d41d-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="8d41d-270">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="8d41d-270">Congratulations!</span></span> <span data-ttu-id="8d41d-271">Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="8d41d-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="8d41d-272">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště.</span><span class="sxs-lookup"><span data-stu-id="8d41d-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8d41d-273">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8d41d-273">Next steps</span></span>

<span data-ttu-id="8d41d-274">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="8d41d-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8d41d-275">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="8d41d-275">Understand the problem</span></span>
> * <span data-ttu-id="8d41d-276">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="8d41d-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8d41d-277">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="8d41d-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="8d41d-278">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="8d41d-279">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="8d41d-279">Load and transform the data</span></span>
> * <span data-ttu-id="8d41d-280">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="8d41d-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8d41d-281">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-281">Train the model</span></span>
> * <span data-ttu-id="8d41d-282">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="8d41d-282">Evaluate the model</span></span>
> * <span data-ttu-id="8d41d-283">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="8d41d-283">Use the model for predictions</span></span>

<span data-ttu-id="8d41d-284">Přejděte k dalšímu kurzu, kde Další informace.</span><span class="sxs-lookup"><span data-stu-id="8d41d-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8d41d-285">Clustering Iris</span><span class="sxs-lookup"><span data-stu-id="8d41d-285">Iris clustering</span></span>](iris-clustering.md)
