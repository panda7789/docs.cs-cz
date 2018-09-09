---
title: ML.NET používají k vytváření prognóz tarify taxislužby města New York (regrese)
description: Další informace o použití ML.NET ve scénáři regrese.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 133b7ad17a98e4eea510f1704555b690b98e9091
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252841"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="0ee8a-103">Kurz: Použití ML.NET předpovědět tarify taxislužby města New York (regrese)</span><span class="sxs-lookup"><span data-stu-id="0ee8a-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="0ee8a-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0ee8a-105">Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0ee8a-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="0ee8a-106">Tento kurz ukazuje, jak použít ML.NET k sestavení [regresní model](../resources/glossary.md#regression) pro predikci tarify taxislužby města New York City.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="0ee8a-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0ee8a-108">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="0ee8a-108">Understand the problem</span></span>
> * <span data-ttu-id="0ee8a-109">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="0ee8a-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="0ee8a-110">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0ee8a-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="0ee8a-111">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="0ee8a-112">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="0ee8a-112">Load and transform the data</span></span>
> * <span data-ttu-id="0ee8a-113">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0ee8a-114">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-114">Train the model</span></span>
> * <span data-ttu-id="0ee8a-115">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-115">Evaluate the model</span></span>
> * <span data-ttu-id="0ee8a-116">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="0ee8a-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ee8a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ee8a-117">Prerequisites</span></span>

* <span data-ttu-id="0ee8a-118">[Visual Studio 2017 15.6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="0ee8a-119">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="0ee8a-119">Understand the problem</span></span>

<span data-ttu-id="0ee8a-120">Tento problém je o predikci tarif cesty taxíkem v New Yorku.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="0ee8a-121">Na první pohled to nemusí závisí jednoduše na vzdálenost přesunul.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="0ee8a-122">Ale taxislužby dodavatelů v New Yorku poplatky různá množství dalších faktorů, jako je například další cestujících nebo placení pomocí platební karty místo platební.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="0ee8a-123">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="0ee8a-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="0ee8a-124">Chcete předpovídat cenu hodnotu, která je skutečná hodnota, na základě dalších faktorů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="0ee8a-125">Udělat, abyste zvolili [regrese](../resources/glossary.md#regression) machine learning úloh.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0ee8a-126">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="0ee8a-126">Create a console application</span></span>

1. <span data-ttu-id="0ee8a-127">Otevřete Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="0ee8a-128">Vyberte **souboru** > **nový** > **projektu** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0ee8a-129">V **nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0ee8a-130">Vyberte **Konzolová aplikace (.NET Core)** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0ee8a-131">V **název** textového pole zadejte "TaxiFarePrediction" a pak vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="0ee8a-132">Vytvořte adresář *Data* ve vašem projektu a uložit datovou sadu a soubory modelu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="0ee8a-133">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **novou složku**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0ee8a-134">Zadejte "Data" a stiskněte Enter.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="0ee8a-135">Nainstalujte **Microsoft.ML** balíček NuGet:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="0ee8a-136">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0ee8a-137">Zvolte možnost "nuget.org" jako zdroj balíčku, vyberte **Procházet** kartu, vyhledejte **Microsoft.ML**, vyberte tento balíček v seznamu a vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0ee8a-138">Vyberte **OK** tlačítko **náhled změn** dialogového okna a pak vyberte **souhlasím** tlačítko **přijetí licence** dialogové okno Pokud jste Souhlasím s licenčními podmínkami pro balíčky uvedené.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0ee8a-139">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0ee8a-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="0ee8a-140">Stáhněte si [taxislužby. tarif train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) a [taxislužby. tarif test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) dat nastaví a uloží je do *Data* složky, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="0ee8a-141">Používáme tyto datové sady pro trénování modelu strojového učení a pak vyhodnotit, jak přesný je model.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="0ee8a-142">Tyto datové sady jsou původně z [sady dat o jízdách taxislužby TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="0ee8a-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="0ee8a-143">V **Průzkumníka řešení**, klikněte pravým tlačítkem na jednotlivé \*soubory CSV a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="0ee8a-144">V části **Upřesnit**, změňte hodnotu vlastnosti **kopírovat do výstupního adresáře** k **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="0ee8a-145">Otevřít **taxislužby. tarif train.csv** nastavení data a podívejte se na záhlaví sloupců v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="0ee8a-146">Podívejte se na všech sloupcích.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-146">Take a look at each of the columns.</span></span> <span data-ttu-id="0ee8a-147">Vysvětlení dat a rozhodnout, které sloupce budou **funkce** a který je **popisek**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="0ee8a-148">**Popisek** je identifikátor sloupce, který chcete předpovědět.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="0ee8a-149">Identifikovanou **funkce** se používají k předpovědi popisek.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="0ee8a-150">Zadaná datová sada obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="0ee8a-151">**vendor_id:** ID dodavatele, taxi je funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="0ee8a-152">**rate_code:** typ kursu cesty taxíkem je funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="0ee8a-153">**passenger_count:** počet cestujících na cestě je funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="0ee8a-154">**trip_time_in_secs:** trvalo cesty časového intervalu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="0ee8a-155">Chcete předpovědět tarif cesty před dokončením cesty.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="0ee8a-156">V daném okamžiku by trvalo chvíli si nejste jisti, jak dlouho o jízdách.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="0ee8a-157">Proto doba jízdy není funkce a budete vylučte tento sloupec z modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="0ee8a-158">**trip_distance:** vzdálenost cesty je funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="0ee8a-159">**payment_type:** platby (hotovosti nebo kreditní karta) je funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="0ee8a-160">**fare_amount:** tarif celkový taxislužby placené je popisek.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="0ee8a-161">Vytvoření datových tříd</span><span class="sxs-lookup"><span data-stu-id="0ee8a-161">Create data classes</span></span>

<span data-ttu-id="0ee8a-162">Vytvoření třídy pro vstupní data a předpovědí:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="0ee8a-163">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="0ee8a-164">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="0ee8a-165">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="0ee8a-166">Přidejte následující `using` direktivy do nového souboru:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="0ee8a-167">Odeberte stávající definice třídy a přidejte následující kód, který má dvě třídy `TaxiTrip` a `TaxiTripFarePrediction`, možnosti *TaxiTrip.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="0ee8a-168">`TaxiTrip` je třída vstupní data a obsahuje definice pro všechny sloupce datové sady.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="0ee8a-169">Použití [sloupec](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atributy indexů zdrojových sloupců v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-169">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="0ee8a-170">`TaxiTripFarePrediction` Třída reprezentuje předpokládané výsledky.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="0ee8a-171">Obsahuje pole jednou čárkou `FareAmount`, s `Score` [Názevsloupce](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-171">It has a single float field, `FareAmount`, with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="0ee8a-172">V případě úloh regrese **skóre** sloupec obsahuje hodnoty předpovězené popisků.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="0ee8a-173">Použití `float` typ pro reprezentaci hodnoty s plovoucí desetinnou čárkou v datových tříd vstupu a předpovědí.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="0ee8a-174">Definovat cesty k datům a model</span><span class="sxs-lookup"><span data-stu-id="0ee8a-174">Define data and model paths</span></span>

<span data-ttu-id="0ee8a-175">Přejděte zpět *Program.cs* a přidejte tři pole pro uložení cest k souborům s datovými sadami a soubor uložte modelu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-175">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="0ee8a-176">`_datapath` obsahuje cestu k souboru s datovou sadou, využívají k tréninku modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-176">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="0ee8a-177">`_testdatapath` obsahuje cestu k souboru s datovou sadou, používá k vyhodnocení modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-177">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="0ee8a-178">`_modelpath` obsahuje cestu k souboru, kde je uložený trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-178">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="0ee8a-179">Přidejte následující kód vpravo nahoře `Main` metoda zadat tyto cesty:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-179">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="0ee8a-180">Aby předchozí kód zkompilovat, přidejte následující `using` direktivy v horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-180">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="0ee8a-181">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-181">Create a learning pipeline</span></span>

<span data-ttu-id="0ee8a-182">Přidejte následující další `using` direktivy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-182">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="0ee8a-183">V `Main` metoda, nahraďte `Console.WriteLine("Hello World!")` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-183">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="0ee8a-184">`Train` Metoda trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-184">The `Train` method trains the model.</span></span> <span data-ttu-id="0ee8a-185">Vytvoření metody hned pod `Main`, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="0ee8a-186">Kanál learning načte všechna data a algoritmy, které jsou nezbytné pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="0ee8a-187">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="0ee8a-188">Načítání a transformace dat.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-188">Load and transform data</span></span>

<span data-ttu-id="0ee8a-189">Prvním krokem k provedení je k načtení dat z trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-189">The first step to perform is to load data from the training data set.</span></span> <span data-ttu-id="0ee8a-190">V našem případě trénovací datové sady se ukládají v textovém souboru s cestu definovanou `_datapath` pole.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="0ee8a-191">Tento soubor má záhlaví s názvy sloupců, takže první řádek by měl ignorovat při načítání dat.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-191">That file has the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="0ee8a-192">Sloupce v souboru jsou oddělené čárkou (",").</span><span class="sxs-lookup"><span data-stu-id="0ee8a-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="0ee8a-193">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="0ee8a-194">V dalších krocích budeme odkazovat na sloupce pomocí názvy definované v `TaxiTrip` třídy.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="0ee8a-195">Když je model trénují a vyhodnocují, ve výchozím nastavení, hodnoty **popisek** sloupce se považují za správné hodnoty pro předpovídat.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-195">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="0ee8a-196">Protože chceme předpovědět tarif cesty taxíkem, zkopírujte `FareAmount` sloupec **popisek** sloupec.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="0ee8a-197">K tomuto účelu použijte <xref:Microsoft.ML.Transforms.ColumnCopier> a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-197">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="0ee8a-198">Algoritmus, který trénovat modelu vyžaduje **číselné** funkcí, takže je nutné transformovat data zařazená do kategorií (`VendorId`, `RateCode`, a `PaymentType`) hodnoty na čísla.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="0ee8a-199">K tomuto účelu použijte <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, která přiřadí různé číselné hodnoty na různé hodnoty v každém sloupci klíče a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-199">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="0ee8a-200">Posledním krokem přípravy dat je kombinací všech sloupců funkce do **funkce** pomocí sloupce <xref:Microsoft.ML.Transforms.ColumnConcatenator> třídy transformace.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="0ee8a-201">Ve výchozím nastavení, algoritmu učení zpracovává pouze funkce **funkce** sloupce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-201">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="0ee8a-202">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="0ee8a-203">Všimněte si, že `TripTime` sloupec, který odpovídá `trip_time_in_secs` sloupec v souboru datové sady není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="0ee8a-204">Už jste zjistili, že to není užitečné předpovědi funkce.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="0ee8a-205">Tyto kroky je nutné přidat do kanálu v pořadí určeném výše pro úspěšné provedení.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0ee8a-206">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-206">Choose a learning algorithm</span></span>

<span data-ttu-id="0ee8a-207">Po přidání dat do kanálu a jejich transformace na správný formát vstupu, vyberte algoritmus učení (**learner**).</span><span class="sxs-lookup"><span data-stu-id="0ee8a-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="0ee8a-208">Learner trénovat modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-208">The learner trains the model.</span></span> <span data-ttu-id="0ee8a-209">Jste si zvolili **regrese** úkol pro tento problém, proto použijete <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, což je jedna studentů regrese poskytované ML.NET.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-209">You chose a **regression** task for this problem, so you use a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="0ee8a-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner využívá přechodu zvýšení skóre.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="0ee8a-211">Přechodu zvýšení skóre je strojové učení techniku pro regresní problémy.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="0ee8a-212">Sestaví každém stromu regrese způsobem podle jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="0ee8a-213">Předdefinované ztráta funkce používá k měření chyb v každém kroku a opravit ho v dalším.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="0ee8a-214">Výsledkem je, který je ve skutečnosti kompletu sady slabší prediktivní modely prediktivní model.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="0ee8a-215">Další informace o přechodu zvýšení skóre, naleznete v tématu [Boosted regrese rozhodovacího stromu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="0ee8a-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="0ee8a-216">Přidejte následující kód do `Train` metoda po zpracování dat kód přidaný v předchozím kroku:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="0ee8a-217">Přidat všechny předchozí kroky do kanálu jako jednotlivé příkazy, ale jazyka C# má syntaxe inicializace kolekce po ruce, který usnadňuje vytváření a inicializace kanálu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="0ee8a-218">Nahraďte kód přidaný zatím na `Train` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="0ee8a-219">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-219">Train the model</span></span>

<span data-ttu-id="0ee8a-220">Posledním krokem je pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-220">The final step is to train the model.</span></span> <span data-ttu-id="0ee8a-221">Až do této chvíle byl proveden nic v kanálu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="0ee8a-222">`pipeline.Train<TInput, TOutput>` Metoda vytváří model, který přijímá instanci `TInput` zadejte a vypíše instance `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="0ee8a-223">Přidejte následující kód do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="0ee8a-224">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="0ee8a-224">And that's it!</span></span> <span data-ttu-id="0ee8a-225">Úspěšně jste trénuje model, který může předpovídat tarify taxislužby města v NYC strojového učení.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="0ee8a-226">Nyní Pojďme podívat, abyste pochopili, jak přesný je model a zjistěte, jak ho použít k předpovědi hodnot tarif taxislužby.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="0ee8a-227">Uložit model</span><span class="sxs-lookup"><span data-stu-id="0ee8a-227">Save the model</span></span>

<span data-ttu-id="0ee8a-228">V tomto okamžiku máte model, který je možné integrovat do všech existujících nebo nových aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-228">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="0ee8a-229">Chcete-li uložit model do souboru .zip, přidejte následující kód na konci `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-229">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="0ee8a-230">Přidávání `await` příkazu `model.WriteAsync` volání znamená, že `Train` metoda musí být změněna na asynchronní metoda vracející úlohu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="0ee8a-231">Upravte podpis metody `Train` jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="0ee8a-232">Změna návratového typu `Train` metoda znamená, že chcete přidat `await` kódu, který volá `Train` v `Main` způsob, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="0ee8a-233">Pomocí `await` v `Main` znamená, že metoda `Main` metoda musí mít `async` modifikátor a vraťte se `Task`:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="0ee8a-234">Budete také muset přidat následující `using` direktiv v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="0ee8a-235">Vzhledem k tomu, `async Main` metoda je funkce přidané v jazyce C# 7.1 a výchozí jazyková verze projektu je C# 7.0, budete muset změnit verzi jazyka C# 7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="0ee8a-236">Chcete-li to mohli udělat, klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="0ee8a-237">Vyberte **sestavení** kartě a vyberte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="0ee8a-238">V rozevíracím seznamu vyberte **jazyka C# 7.1** (nebo vyšší verze).</span><span class="sxs-lookup"><span data-stu-id="0ee8a-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="0ee8a-239">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="0ee8a-240">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-240">Evaluate the model</span></span>

<span data-ttu-id="0ee8a-241">Hodnocení je proces kontroly, jak dobře model předpovídá hodnoty popisků.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="0ee8a-242">Je důležité, že model vytváří dobré předpovědi na data, která nebyla použita pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="0ee8a-243">Jedním ze způsobů k tomu je rozdělení dat na trénovací a testovací datové sady, jak je tomu v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-243">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="0ee8a-244">Teď, když jsme natrénovali model na trénovací data, zobrazí se, jak dobře funguje na testovací data.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-244">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="0ee8a-245">Přejděte zpět `Main` metoda a přidejte následující kód pod volání `Train`– metoda:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="0ee8a-246">`Evaluate` Metoda vyhodnocuje modelu.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="0ee8a-247">Chcete-li vytvořit tuto metodu, přidejte následující kód níže `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="0ee8a-248">Přidejte následující kód do `Evaluate` metodu pro nastavení načítání testovacích dat:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="0ee8a-249">Přidejte následující kód k vyhodnocení modelu a vytvoření metriky vyhodnocení:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="0ee8a-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) je jedním z hodnocení metriky regresní model.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="0ee8a-251">Čím nižší je, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="0ee8a-252">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RMS:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="0ee8a-253">[RSquared](../resources/glossary.md#coefficient-of-determination) je jiný metrik hodnocení, regresních modelů.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="0ee8a-254">RSquared trvá hodnoty v rozmezí 0 až 1.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="0ee8a-255">Čím blíž její hodnota je 1, tím lepší je model.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="0ee8a-256">Přidejte následující kód do `Evaluate` metody k zobrazení hodnoty RSquared:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="0ee8a-257">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="0ee8a-257">Use the model for predictions</span></span>

<span data-ttu-id="0ee8a-258">Vytvoření třídy, která porušuje testovací data instancí:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-258">Create a class to house test data instances:</span></span>

1. <span data-ttu-id="0ee8a-259">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak vyberte **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="0ee8a-260">V **přidat novou položku** dialogu **třídy** a změnit **název** pole *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="0ee8a-261">Vyberte **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="0ee8a-262">Upravte třídu pro statické stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="0ee8a-263">Tento kurz používá jeden test latence v rámci této třídy.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="0ee8a-264">Později můžete přidat další scénáře můžete experimentovat s modelem.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="0ee8a-265">Přidejte následující kód do `TestTrips` třídy:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="0ee8a-266">Tuto cestu skutečné tarif je 29,5.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="0ee8a-267">Model bude předpovídat tarif, použijte jako zástupný znak, 0.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="0ee8a-268">Pokud chcete předpovědět tarif zadané cesty, přejděte zpět na *Program.cs* a přidejte následující kód do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="0ee8a-269">Spusťte program, abyste viděli tarif předpokládané taxislužby pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="0ee8a-270">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="0ee8a-270">Congratulations!</span></span> <span data-ttu-id="0ee8a-271">Právě jste úspěšně sestaven modelu strojového učení pro predikci tarify cesty taxíkem, vyhodnotit jeho přesnost a použít ho k následné predikci.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="0ee8a-272">Zdrojový kód najdete v tomto kurzu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ee8a-273">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0ee8a-273">Next steps</span></span>

<span data-ttu-id="0ee8a-274">V tomto kurzu jste zjistili, jak:</span><span class="sxs-lookup"><span data-stu-id="0ee8a-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0ee8a-275">Pochopení problému</span><span class="sxs-lookup"><span data-stu-id="0ee8a-275">Understand the problem</span></span>
> * <span data-ttu-id="0ee8a-276">Vyberte úlohu odpovídající machine learning</span><span class="sxs-lookup"><span data-stu-id="0ee8a-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="0ee8a-277">Příprava a pochopení dat</span><span class="sxs-lookup"><span data-stu-id="0ee8a-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="0ee8a-278">Vytvoření kanálu učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="0ee8a-279">Načíst a transformovat data</span><span class="sxs-lookup"><span data-stu-id="0ee8a-279">Load and transform the data</span></span>
> * <span data-ttu-id="0ee8a-280">Vyberte algoritmus učení</span><span class="sxs-lookup"><span data-stu-id="0ee8a-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0ee8a-281">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-281">Train the model</span></span>
> * <span data-ttu-id="0ee8a-282">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="0ee8a-282">Evaluate the model</span></span>
> * <span data-ttu-id="0ee8a-283">Použít model pro předpovědi</span><span class="sxs-lookup"><span data-stu-id="0ee8a-283">Use the model for predictions</span></span>

<span data-ttu-id="0ee8a-284">Přejděte k dalšímu kurzu, kde Další informace.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0ee8a-285">Iris clustering</span><span class="sxs-lookup"><span data-stu-id="0ee8a-285">Iris clustering</span></span>](iris-clustering.md)
