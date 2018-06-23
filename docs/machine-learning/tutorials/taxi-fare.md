---
title: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 690e39dcbd02d81b8d4afe918a74795aa02f7fc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314962"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="34418-103">Kurz: Použití ML.NET k předvídání New Yorku taxíkem tarify (regrese)</span><span class="sxs-lookup"><span data-stu-id="34418-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="34418-104">Toto téma označuje ML.NET, který je aktuálně ve verzi Preview, a materiálů, mohou se měnit.</span><span class="sxs-lookup"><span data-stu-id="34418-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="34418-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="34418-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="34418-106">Tento kurz ukazuje, jak používat ML.NET pro vytváření [regresní model](../resources/glossary.md#regression) pro predikci tarify taxíkem New Yorku.</span><span class="sxs-lookup"><span data-stu-id="34418-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="34418-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="34418-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="34418-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="34418-108">Understand the problem</span></span>
> * <span data-ttu-id="34418-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="34418-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="34418-110">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="34418-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="34418-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="34418-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="34418-112">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="34418-112">Load and transform the data</span></span>
> * <span data-ttu-id="34418-113">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="34418-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="34418-114">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="34418-114">Train the model</span></span>
> * <span data-ttu-id="34418-115">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="34418-115">Evaluate the model</span></span>
> * <span data-ttu-id="34418-116">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="34418-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34418-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34418-117">Prerequisites</span></span>

* <span data-ttu-id="34418-118">[Visual Studio 2017 15,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována.</span><span class="sxs-lookup"><span data-stu-id="34418-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="34418-119">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="34418-119">Understand the problem</span></span>

<span data-ttu-id="34418-120">Tento problém je zaměřená na **predikci tarif služby taxíkem dojít v New Yorku**.</span><span class="sxs-lookup"><span data-stu-id="34418-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="34418-121">Na první pohled se zdá se, že jednoduše na vzdálenost, kterou urazit závisí.</span><span class="sxs-lookup"><span data-stu-id="34418-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="34418-122">Dodavatelé taxíkem v New Yorku však účtují různých objemy pro dalších faktorech, například další cestujících nebo platícího platební kartou místo peněžních.</span><span class="sxs-lookup"><span data-stu-id="34418-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="34418-123">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="34418-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="34418-124">K předvídání taxíkem tarif, nejprve vyberte úlohu odpovídající machine learning.</span><span class="sxs-lookup"><span data-stu-id="34418-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="34418-125">Hledáte k předvídání skutečná hodnota (dvojitou hodnotu představující cena) založená na jiných faktorech v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="34418-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="34418-126">Můžete vybrat [ **regrese** ](../resources/glossary.md#regression) úloh.</span><span class="sxs-lookup"><span data-stu-id="34418-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="34418-127">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="34418-127">Create a console application</span></span>

1. <span data-ttu-id="34418-128">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="34418-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="34418-129">Vyberte **soubor** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="34418-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="34418-130">V **nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="34418-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="34418-131">Vyberte **konzolové aplikace (.NET Core)** šablona projektu.</span><span class="sxs-lookup"><span data-stu-id="34418-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="34418-132">V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="34418-133">Vytvořte adresář s názvem *Data* ve vašem projektu a ukládat soubory datové sady:</span><span class="sxs-lookup"><span data-stu-id="34418-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="34418-134">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="34418-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="34418-135">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="34418-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="34418-136">Nainstalujte **balíček NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="34418-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="34418-137">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="34418-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="34418-138">Vyberte "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartě, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="34418-139">Vyberte **OK** tlačítko **zobrazení náhledu změn** dialogové okno a potom vyberte **souhlasím** na tlačítko **přijetí licence** dialogové okno Pokud jste souhlas s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="34418-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="34418-140">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="34418-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="34418-141">Stáhnout [taxíkem. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxíkem. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data nastaví a uložte je do *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="34418-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="34418-142">Používáme tyto sady dat a natrénuje strojového učení modelu a pak vyhodnotit, jak přesný je modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="34418-143">Tyto sady dat se původně z [NYC TLC taxíkem cestě datové sady](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="34418-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="34418-144">V **Průzkumníku řešení**, klikněte pravým tlačítkem na každý z \*soubory .csv a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="34418-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="34418-145">V části **Upřesnit**, změňte hodnotu **kopírovat do výstupního adresáře** k **vždy**.</span><span class="sxs-lookup"><span data-stu-id="34418-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="34418-146">Otevřete **taxíkem. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="34418-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="34418-147">Podívejte se na všechny sloupce.</span><span class="sxs-lookup"><span data-stu-id="34418-147">Take a look at each of the columns.</span></span> <span data-ttu-id="34418-148">Pochopení dat a rozhodněte, které sloupce jsou **funkce** a která je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="34418-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="34418-149">**Popisek** je identifikátor sloupce, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="34418-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="34418-150">Identifikovanou **funkce** se používají k předvídání popisku.</span><span class="sxs-lookup"><span data-stu-id="34418-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="34418-151">Zadaná sada dat obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="34418-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="34418-152">**vendor_id:** ID dodavatele, taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="34418-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="34418-153">**rate_code:** typ míry taxíkem cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="34418-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="34418-154">**passenger_count:** počet cestujících na cestu je funkce.</span><span class="sxs-lookup"><span data-stu-id="34418-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="34418-155">**trip_time_in_secs:** trvalo množství času, cestu.</span><span class="sxs-lookup"><span data-stu-id="34418-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="34418-156">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="34418-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="34418-157">V daném okamžiku by nevíte, jak dlouho bude cesta chvíli trvat.</span><span class="sxs-lookup"><span data-stu-id="34418-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="34418-158">Proto času není funkce a budete v tomto sloupci vyloučíte z modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="34418-159">**trip_distance:** vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="34418-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="34418-160">**payment_type:** platby (peněžních nebo platební karty) je funkce.</span><span class="sxs-lookup"><span data-stu-id="34418-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="34418-161">**fare_amount:** tarif celkový taxíkem placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="34418-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="34418-162">Vytvořit datové třídy</span><span class="sxs-lookup"><span data-stu-id="34418-162">Create data classes</span></span>

<span data-ttu-id="34418-163">Vytvoření třídy pro vstupní data a jsou předpovědi:</span><span class="sxs-lookup"><span data-stu-id="34418-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="34418-164">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="34418-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="34418-165">V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="34418-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="34418-166">Pak vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="34418-167">Přidejte následující `using` příkazy na nový soubor:</span><span class="sxs-lookup"><span data-stu-id="34418-167">Add the following `using` statements to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="34418-168">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, na *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="34418-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="34418-169">`TaxiTrip` je třída vstupní data a obsahuje definice pro každý z datové sady sloupců.</span><span class="sxs-lookup"><span data-stu-id="34418-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="34418-170">Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atribut k určení indexy zdrojové sloupce v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="34418-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="34418-171">`TaxiTripFarePrediction` Třída se používá k reprezentování předpokládaných výsledky.</span><span class="sxs-lookup"><span data-stu-id="34418-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="34418-172">Má jednou čárkou (`FareAmount`) pole s `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut použitý.</span><span class="sxs-lookup"><span data-stu-id="34418-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="34418-173">**Skóre** sloupec je speciální sloupec v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="34418-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="34418-174">Model výstupy předpovězené hodnoty do sloupce.</span><span class="sxs-lookup"><span data-stu-id="34418-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="34418-175">Definování dat a model cesty</span><span class="sxs-lookup"><span data-stu-id="34418-175">Define data and model paths</span></span>

<span data-ttu-id="34418-176">Přejděte zpět *Program.cs* souboru a vytvořte tři globální konstanty pro uložení cest k souborům s datových sad a uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="34418-176">Go back to the *Program.cs* file and create three global constants to hold the paths to the files with data sets and to save the model:</span></span>

* <span data-ttu-id="34418-177">`_datapath` obsahuje cestu k datům používá pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-177">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="34418-178">`_testdatapath` obsahuje cestu k datům používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-178">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="34418-179">`_modelpath` má cestu k uložení naučeného modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-179">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="34418-180">Přidejte následující kód řádku vpravo nahoře `Main` metoda k určení těchto cestách:</span><span class="sxs-lookup"><span data-stu-id="34418-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="34418-181">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="34418-181">Create a learning pipeline</span></span>

<span data-ttu-id="34418-182">Přidejte následující další `using` příkazů do horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="34418-182">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="34418-183">V `Main`, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="34418-183">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="34418-184">`Train` Metoda nastaví model.</span><span class="sxs-lookup"><span data-stu-id="34418-184">The `Train` method trains the model.</span></span> <span data-ttu-id="34418-185">Vytvoření dané metody právě níže `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="34418-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="34418-186">Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="34418-187">Přidejte následující kód do `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="34418-188">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="34418-188">Load and transform data</span></span>

<span data-ttu-id="34418-189">První krok, který provádí learning kanálu načítá data z trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="34418-189">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="34418-190">V našem případě trénovací datové sady je uložený v textovém souboru s cestou definované `_datapath` konstantní.</span><span class="sxs-lookup"><span data-stu-id="34418-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` constant.</span></span> <span data-ttu-id="34418-191">Tento soubor obsahuje záhlaví s názvy sloupců, takže první řádek má ignorovat při načítání dat.</span><span class="sxs-lookup"><span data-stu-id="34418-191">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="34418-192">Sloupce v souboru oddělených čárkou (",").</span><span class="sxs-lookup"><span data-stu-id="34418-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="34418-193">Přidejte následující kód do `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="34418-194">V dalších krocích označujeme sloupce názvy definované v `TaxiTrip` třídy.</span><span class="sxs-lookup"><span data-stu-id="34418-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="34418-195">Když je model trénují a vyhodnocují, hodnoty **popisek** sloupce jsou považovány za jako správné hodnoty pro předpovědět.</span><span class="sxs-lookup"><span data-stu-id="34418-195">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="34418-196">Jak chcete předpovídat tarif cestě taxi, zkopírujte `FareAmount` sloupce do **popisek** sloupce.</span><span class="sxs-lookup"><span data-stu-id="34418-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="34418-197">Chcete-li provést, použijte <xref:Microsoft.ML.Transforms.ColumnCopier> a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="34418-197">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="34418-198">Algoritmus, která provede modelu vyžaduje **číselné** funkce, takže budete mít k transformaci kategorizovaná data (`VendorId`, `RateCode`, a `PaymentType`) hodnoty do čísla.</span><span class="sxs-lookup"><span data-stu-id="34418-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="34418-199">Chcete-li provést, použijte <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, které přiřadí různé číselné hodnoty pro různé hodnoty v jednotlivých sloupců klíče a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="34418-199">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="34418-200">Poslední krok v rámci přípravy dat kombinuje všechny sloupce funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Transforms.ColumnConcatenator> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="34418-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="34418-201">Tento krok je nezbytný, protože student zpracovává pouze funkce z **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="34418-201">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="34418-202">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="34418-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="34418-203">Všimněte si, že `TripTime` sloupec, který odpovídá `trip_time_in_secs` není zahrnutý sloupec v souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="34418-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="34418-204">Již je třeba určit, že to není funkce užitečné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="34418-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="34418-205">Tyto kroky je nutné přidat do tohoto kanálu v pořadí určeném výše pro úspěšné provedení.</span><span class="sxs-lookup"><span data-stu-id="34418-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="34418-206">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="34418-206">Choose a learning algorithm</span></span>

<span data-ttu-id="34418-207">Po přidání dat do kanálu a transformace na správný formát vstupu, vyberte algoritmus učení (**Student**).</span><span class="sxs-lookup"><span data-stu-id="34418-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="34418-208">Student soupravy modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-208">The learner trains the model.</span></span> <span data-ttu-id="34418-209">Jste si zvolili **regrese úloh** pro tento problém, takže můžete přidat <xref:Microsoft.ML.Trainers.FastTreeRegressor> student, což je jedna ze regrese inteligentních algoritmů, poskytované ML.NET.</span><span class="sxs-lookup"><span data-stu-id="34418-209">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="34418-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> Student využívá přechodu zvyšovat skóre.</span><span class="sxs-lookup"><span data-stu-id="34418-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="34418-211">Přechodu zvyšovat skóre je machine learning technika pro regresní problémy.</span><span class="sxs-lookup"><span data-stu-id="34418-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="34418-212">Sestavuje každém stromu regrese step-wise způsobem.</span><span class="sxs-lookup"><span data-stu-id="34418-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="34418-213">Předem definované ztrátě funkce používá k měření chyby v jednotlivých kroků a opravte ho v dalším.</span><span class="sxs-lookup"><span data-stu-id="34418-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="34418-214">Výsledkem je předpovědi model, který je ve skutečnosti kompletu slabší předpovědi modelů.</span><span class="sxs-lookup"><span data-stu-id="34418-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="34418-215">Další informace o přechodu zvyšovat skóre najdete v tématu [Boosted rozhodovací strom regrese](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="34418-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="34418-216">Přidejte následující kód do `Train` metoda po zpracování dat kódu přidali v předchozím kroku:</span><span class="sxs-lookup"><span data-stu-id="34418-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="34418-217">Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale C# má syntaxi inicializace užitečný kolekce, která usnadňuje vytváření a inicializace kanálu.</span><span class="sxs-lookup"><span data-stu-id="34418-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="34418-218">Nahraďte kód, který jste přidali, pokud na `Train` metoda následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="34418-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="34418-219">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="34418-219">Train the model</span></span>

<span data-ttu-id="34418-220">Posledním krokem je pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-220">The final step is to train the model.</span></span> <span data-ttu-id="34418-221">Dokud nebude tento bod byl proveden nic v kanálu.</span><span class="sxs-lookup"><span data-stu-id="34418-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="34418-222">`pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přebírá instanci `TInput` zadejte a výstupy instanci `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="34418-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="34418-223">Přidejte následující kód do `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="34418-224">A je to!</span><span class="sxs-lookup"><span data-stu-id="34418-224">And that's it!</span></span> <span data-ttu-id="34418-225">Úspěšně jste Trénink machine learning model, který může předpovídat taxíkem tarify v NYC.</span><span class="sxs-lookup"><span data-stu-id="34418-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="34418-226">Nyní Pojďme prohlédněte pochopit, jak přesný je model a zjistěte, jak ji použít k předpovědi hodnot tarif taxíkem.</span><span class="sxs-lookup"><span data-stu-id="34418-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="34418-227">Uložit model</span><span class="sxs-lookup"><span data-stu-id="34418-227">Save the model</span></span>

<span data-ttu-id="34418-228">Než přejdete na další krok, model uložte do souboru ZIP a přidáním následující kód na konci `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-228">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="34418-229">Přidávání `await` příkaz, který má `model.WriteAsync` volání znamená, že `Train` metoda musí změnit tak, aby asynchronní metody, který vrátí úlohu.</span><span class="sxs-lookup"><span data-stu-id="34418-229">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="34418-230">Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="34418-230">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="34418-231">Změna návratový typ `Train` metoda znamená, že budete muset přidat `await` na kód, který volá `Train` v `Main` metoda, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="34418-231">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="34418-232">Pomocí `await` v `Main` metoda znamená `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:</span><span class="sxs-lookup"><span data-stu-id="34418-232">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="34418-233">Také je nutné přidat následující `using` příkaz v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="34418-233">You also need to add the following `using` statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="34418-234">Protože `async Main` metoda je funkce přidané v C# 7.1 a je výchozí jazykovou verzi projektu C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="34418-234">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="34418-235">To lze provést, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="34418-235">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="34418-236">Vyberte **sestavení** a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-236">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="34418-237">V rozevírací nabídce, a vyberte **C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="34418-237">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="34418-238">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-238">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="34418-239">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="34418-239">Evaluate the model</span></span>

<span data-ttu-id="34418-240">Vyhodnocení je proces kontroly, jak dobře model předpovídá popisek hodnoty.</span><span class="sxs-lookup"><span data-stu-id="34418-240">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="34418-241">Je důležité, aby model vytváří dobrý předpovědi na data, která nebyla použita pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-241">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="34418-242">Jeden způsob, jak to udělat je rozdělení dat do vlaku a testování sad dat, jak se provádí v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="34418-242">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="34418-243">Teď, když jsme natrénovali model na základě dat train, se zobrazí její výkon na testovací data.</span><span class="sxs-lookup"><span data-stu-id="34418-243">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="34418-244">Přejděte zpět `Main` metoda a přidejte následující kód pod voláním `Train`metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-244">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="34418-245">`Evaluate` Metoda vyhodnotí modelu.</span><span class="sxs-lookup"><span data-stu-id="34418-245">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="34418-246">Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-246">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="34418-247">Přidejte následující kód do `Evaluate` metodu za účelem instalace načítání testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="34418-247">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="34418-248">Přidejte následující kód k vyhodnocení modelu a vytvořit metriku vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="34418-248">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="34418-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z vyhodnocení metriky regresní model.</span><span class="sxs-lookup"><span data-stu-id="34418-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="34418-250">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="34418-250">The lower it is, the better the model is.</span></span> <span data-ttu-id="34418-251">Přidejte následující kód do `Evaluate` metodu pro zobrazení hodnota RMS:</span><span class="sxs-lookup"><span data-stu-id="34418-251">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="34418-252">[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrika vyhodnocení modelů regrese.</span><span class="sxs-lookup"><span data-stu-id="34418-252">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="34418-253">RSquared přijímá hodnoty mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="34418-253">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="34418-254">Čím bližší její hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="34418-254">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="34418-255">Přidejte následující kód do `Evaluate` metodu pro zobrazení RSquared hodnotu:</span><span class="sxs-lookup"><span data-stu-id="34418-255">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="34418-256">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="34418-256">Use the model for predictions</span></span>

<span data-ttu-id="34418-257">Dále vytvořte třídu úklidové testovací scénářů, které můžete použít a ujistěte se, že model pracuje správně:</span><span class="sxs-lookup"><span data-stu-id="34418-257">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="34418-258">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="34418-258">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="34418-259">V **přidat novou položku** dialogové okno, vyberte **třída** a změňte **název** do *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="34418-259">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="34418-260">Pak vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34418-260">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="34418-261">Upravte třídy, která má být statické jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="34418-261">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="34418-262">Tento kurz používá jeden testovací cesty v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="34418-262">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="34418-263">Později můžete přidat další scénáře a experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="34418-263">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="34418-264">Přidejte následující kód do `TestTrips` třídy:</span><span class="sxs-lookup"><span data-stu-id="34418-264">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="34418-265">Tuto cestu skutečné tarif je 29.5.</span><span class="sxs-lookup"><span data-stu-id="34418-265">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="34418-266">Model bude předpovídat tarif použijte jako zástupný znak, 0.</span><span class="sxs-lookup"><span data-stu-id="34418-266">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="34418-267">K předvídání tarif zadané cesty, přejděte zpět na *Program.cs* souboru a přidejte následující kód do `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="34418-267">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="34418-268">Spusťte program zobrazíte předpokládaných taxíkem tarif pro testovacího případu.</span><span class="sxs-lookup"><span data-stu-id="34418-268">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="34418-269">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="34418-269">Congratulations!</span></span> <span data-ttu-id="34418-270">Jste teď úspěšně sestaven model machine learning pro predikci taxíkem cestě tarify, vyhodnotit jeho přesnost a použít k předpovědi.</span><span class="sxs-lookup"><span data-stu-id="34418-270">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="34418-271">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště.</span><span class="sxs-lookup"><span data-stu-id="34418-271">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="34418-272">Další kroky</span><span class="sxs-lookup"><span data-stu-id="34418-272">Next steps</span></span>

<span data-ttu-id="34418-273">V tomto kurzu jste se dozvěděli, jak:</span><span class="sxs-lookup"><span data-stu-id="34418-273">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="34418-274">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="34418-274">Understand the problem</span></span>
> * <span data-ttu-id="34418-275">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="34418-275">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="34418-276">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="34418-276">Prepare and understand the data</span></span>
> * <span data-ttu-id="34418-277">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="34418-277">Create a learning pipeline</span></span>
> * <span data-ttu-id="34418-278">Načítání a transformace dat</span><span class="sxs-lookup"><span data-stu-id="34418-278">Load and transform the data</span></span>
> * <span data-ttu-id="34418-279">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="34418-279">Choose a learning algorithm</span></span>
> * <span data-ttu-id="34418-280">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="34418-280">Train the model</span></span>
> * <span data-ttu-id="34418-281">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="34418-281">Evaluate the model</span></span>
> * <span data-ttu-id="34418-282">Použití modelu předpovědi</span><span class="sxs-lookup"><span data-stu-id="34418-282">Use the model for predictions</span></span>

<span data-ttu-id="34418-283">Podívejte se na našem úložišti GitHub a pokračujte ve čtení najít další ukázky.</span><span class="sxs-lookup"><span data-stu-id="34418-283">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="34418-284">úložiště GitHub DotNet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="34418-284">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
